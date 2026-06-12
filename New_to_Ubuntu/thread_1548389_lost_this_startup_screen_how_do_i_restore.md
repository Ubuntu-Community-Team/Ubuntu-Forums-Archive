---
title: "lost this startup screen how do i restore"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-08-08
how to i restore this so it shows at startup


Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found memtest86+ image: /boot/memtest86+.bin

that should give you the info you need/tks

---

### Post by rburkartjo on 2010-08-08
this might help here is my grub2 

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=" splash quiet"

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

### Post by rburkartjo on 2010-08-08
another suggestion if some one could post there output from grub2
i could compare it with mine and probably fix the error. sure it is something dumb

---

### Post by rburkartjo on 2010-08-11
i bumped this maybe someone has an idea. if no answers by this evening will mark this thread as closed/tks in advance

---

### Post by john newbuntu on 2010-08-11
I am not sure if you are you asking for the GRUB2 menu to be shown on startup.  If so, you could try commenting out the grub_hidden_timeout and then run "sudo update-grub" from a terminal.

#GRUB_HIDDEN_TIMEOUT=0

---

### Post by rburkartjo on 2010-08-11
john tks for the reply  i am using grub2 and it was already set for that. tried updating grub2 again and did not work. i know it is just something stupid but cant figure it out

---

### Post by arpanaut on 2010-08-11
If you only have a single OS installed the default is to not show the menu.

Maybe this will help:

GRUB_HIDDEN_TIMEOUT=0 [ Note: This setting only applies to computers with only a single operating system. ]

    * The hidden timeout option allows a screen to be displayed without the Grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
      On single-OS computers:
          o The menu will be hidden unless the user adds a # symbol to the beginning of this line ( # GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
          o If a background image is designated in 05_debian_theme it will be displayed rather than a blank screen during a hidden menu timeout.
          o For integers greater than 0:
                + The system will pause without displaying a menu for the designated number of seconds. If the user does not press the SHIFT key during the timeout the system will then boot the default OS/kernel.
                + If the user presses the SHIFT key to display the menu, the menu will be displayed for the number of seconds designated by the GRUB_TIMEOUT value unless the user again intervenes.
          o With a value of 0:
                + Unless the user intervenes, the system will boot the default OS/kernel with only a slight delay. No menu will be displayed.
                + The user may force displaying the menu as the computer boots by holding down the SHIFT key.

Taken from here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rburkartjo on 2010-08-11
arp tks at least i can get grub2 to appear if i hold shift

---

### Post by rburkartjo on 2010-08-11
arp just for your info got it to display for 10 seconds at startup as i wanted to just had to set this to -1
#GRUB_HIDDEN_TIMEOUT=-1

---

