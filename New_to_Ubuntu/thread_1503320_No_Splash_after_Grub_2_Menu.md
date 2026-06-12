---
title: "No Splash after Grub 2 Menu"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by doninsa on 2010-06-06
Trying to get grub image with a scrolling text box during boot. In the Grub 2 Guide it says to modify the /etc/default/grub as follows.  I still get a black screen with boot processes.


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (Grub Legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. For a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". This line is where other instructions, such as "acpi=off" are placed.

Here's what my grub file looks like.

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
#GRUB_CMDLINE_LINUX=" splash vga=788"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

