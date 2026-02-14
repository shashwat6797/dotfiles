# TMUX + TPM Setup Guide

This guide documents how to properly install and configure tmux plugins using TPM (Tmux Plugin Manager).

---

## 1. Install tmux (if not installed)

Ubuntu/Debian:

    sudo apt update
    sudo apt install tmux

Verify installation:

    tmux -V

---

## 2. Install TPM (Tmux Plugin Manager)

Clone TPM into the correct directory:

    git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

Verify installation:

    ls ~/.tmux/plugins/tpm

You should see:

    tpm
    README.md
    bin/

---

## 3. Configure ~/.tmux.conf

Open your config file:

    nano ~/.tmux.conf

Add the following at the VERY BOTTOM of the file:

    # List of plugins
    set -g @plugin 'tmux-plugins/tpm'
    set -g @plugin 'tmux-plugins/tmux-sensible'

    # Add more plugins below if needed
    # set -g @plugin 'tmux-plugins/tmux-resurrect'

    # Initialize TPM (must be at the bottom)
    run '~/.tmux/plugins/tpm/tpm'

Important:
- Nothing should be below the `run` line.
- The path must be exactly:
      ~/.tmux/plugins/tpm/tpm

---

## 4. Restart tmux Completely

Kill any running tmux server:

    tmux kill-server

Start fresh:

    tmux

---

## 5. Install Plugins

Inside tmux:

Press:

    Ctrl + b then I

(Press Ctrl and b together, release, then press capital I)

Plugins will install automatically.

---

## 6. Reload Config (Optional)

Inside tmux:

    Ctrl + b then :

Then type:

    source-file ~/.tmux.conf

Press Enter.

---

## 7. Common Errors & Fixes

"unknown command" after Ctrl+b I:

- TPM not installed
- Wrong path in ~/.tmux.conf
- tmux not restarted
- `run` line not at bottom

Check current user:

    whoami

Your ~/.tmux.conf must be in:

    /home/<your-user>/.tmux.conf

---

## 8. Add New Plugins Later

Add inside ~/.tmux.conf:

    set -g @plugin 'author/plugin-name'

Then inside tmux:

    Ctrl + b then I

---

Done.

Your tmux plugin system is now reproducible and ready for fresh setups.

