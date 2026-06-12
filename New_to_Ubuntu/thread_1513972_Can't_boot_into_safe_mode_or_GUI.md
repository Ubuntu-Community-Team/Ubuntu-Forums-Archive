---
title: "Can't boot into safe mode or GUI"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by phr0ze on 2010-06-20
Just installed 10.04. 
Radeon 5770 gfx (I know)
When I boot I get a black screen but hear the drums
I've tried everything I can to get to a grub prompt but nothing works
Holding shift didn't work
Pressing esc didnt work
pressing esc over and over from bios to boot didn't work

I see the purple 10.04 screen for literally 1 second before I hear the drums so I don't have much time to hit any buttons.

I was able to install via Alternate CD and desktop CD using some forcevesa command. I've installed multiple times.

Thanks,
John

---

### Post by jtarin on 2010-06-20
Is this a dual boot with windows? Do you get a GRUB prompt?

---

### Post by olbrannon on 2010-06-20
> **phr0ze said:**
> Just installed 10.04. 
Radeon 5770 gfx (I know)
When I boot I get a black screen but hear the drums
I've tried everything I can to get to a grub prompt but nothing works
Holding shift didn't work
Pressing esc didnt work
pressing esc over and over from bios to boot didn't work

I see the purple 10.04 screen for literally 1 second before I hear the drums so I don't have much time to hit any buttons.

I was able to install via Alternate CD and desktop CD using some forcevesa command. I've installed multiple times.

Thanks,
John

When the purple screen comes up hit the <TAB> key. Be quick about it. Should get a menu. The following worked for me-
with the first menu entry highlighted hit the letter 'e' on the keyboard to the end of the second line add 'nomce' then just hit enter. YMMV Also read the release notes.

---

### Post by -humanaut- on 2010-06-20
Can you get too a TTY console (try ctrl+alt+f1)

If you can login from there try this

sudo nano /etc/default/grub

Change the delays to 10

then run

sudo update-grub

After that hit escape when the screen is black and it should give you a list of kernels try using the previous one the last kernel update I got broke my Xorg and I've had to revert heres an example of what my grub looks like

 If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

[B]GRUB_DEFAULT=5
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10[/B]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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

change the bold ones to how I have them.

---

### Post by phr0ze on 2010-06-21
Tab was not working. I heard the new grub uses shift now.

It's a single boot. I've been pure ubuntu for the last 2 or 3 years. (well windows xp in a VM, but close enough)

I used the Right Shift key instead of the left... I don't know if that was it, or just timing, but I got to the grub menu.

I downloaded updates, installed the restricted driver, and rebooted.

It at least lets me get to the desktop but the driver speed sucks.

I'm going to open a new topic for the new issue.

---

