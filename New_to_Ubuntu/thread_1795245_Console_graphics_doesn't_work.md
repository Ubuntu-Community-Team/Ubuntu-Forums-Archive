---
title: "Console graphics doesn't work"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by Luke M on 2011-07-02
ubuntu 11.04. Hardware: nvidia 6200. The pre-boot console graphics (frame buffer is it called?) doesn't work. I see something but it's garbage. Suggestions?

---

### Post by Luke M on 2011-07-02
When I boot the live/install CD, I see the debug messages fine (appears to be 80x25 text mode). What's different from the installed version?

---

### Post by wildmanne39 on 2011-07-02
> **Luke M said:**
> ubuntu 11.04. Hardware: nvidia 6200. The pre-boot console graphics (frame buffer is it called?) doesn't work. I see something but it's garbage. Suggestions?Hi, did you install the nvidia driver that is in additional drivers? That is the difference, with the livecd it uses generic video card drivers that work for all cards in most cases but is does not have 3d capabilities.

---

### Post by jtarin on 2011-07-02
After installation what you are describing is for all practical purposes hidden by Plymouth, the splash application and will not be seen at all or only minimally.
Your using 11.04 and nvidia, so I wouldn't worry about seeing "anything". ;)

> I see something but it's garbage. Suggestions?Yes clean the pizza sauce off of your screen.:P

---

### Post by Luke M on 2011-07-03
> **wildmanne39 said:**
> Hi, did you install the nvidia driver that is in additional drivers? That is the difference, with the livecd it uses generic video card drivers that work for all cards in most cases but is does not have 3d capabilities.
 
No, you misunderstand. I'm not talking about X windows. This is before X windows starts.

---

### Post by Luke M on 2011-07-03
> **jtarin said:**
> After installation what you are describing is for all practical purposes hidden by Plymouth, the splash application and will not be seen at all or only minimally.
Your using 11.04 and nvidia, so I wouldn't worry about seeing &quot;anything&quot;. ;)
 
Yes clean the pizza sauce off of your screen.:P
 
It's actually a huge problem because if X windows doesn't start correctly for some reason, I can't see what happened or take any corrective action. So this basically makes ubuntu totally unusable.

---

### Post by Luke M on 2011-07-03
Ok, I found you have to modify the graphics settings in /etc/default/grub (then run update-grub). I don't know what mode it's trying to use by default, but whatever it is doesn't work.

---

### Post by jtarin on 2011-07-03
In a terminal issue the command ```
cat /etc/default/grub
``` and post the results by copy and paste.

---

### Post by Luke M on 2011-07-03
From 'vbeinfo', the highest mode supported by the card BIOS is 1400x1050. And that mode works. So maybe grub is trying to set a mode not in the list of valid modes (the monitor is 1920x1080).

---

### Post by jtarin on 2011-07-03
> **Luke M said:**
>  So maybe grub is trying to set a mode not in the list of valid modes (the monitor is 1920x1080).
Normally you will get a "out of range" signal ,in my experience.

---

### Post by Luke M on 2011-07-03
As an experiment I tried 1920x1080, and it failed the same way as auto. So that seems to confirm it: it's trying to use the monitor resolution even though it's not in the list of supported modes.

---

### Post by jtarin on 2011-07-03
Your not following instructions and posting results. I'm sorry to tell you I can no longer help at this point.

---

### Post by wildmanne39 on 2011-07-04
> **Luke M said:**
> As an experiment I tried 1920x1080, and it failed the same way as auto. So that seems to confirm it: it's trying to use the monitor resolution even though it's not in the list of supported modes.Hi try this and set the resolution to 800x600.

 Run this command in a terminal **gksudo gedit /etc/default/grub**

and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=800x600

Then save and exit the document.


Then do:
Code:

**sudo update-grub**

It would help if you ran the commands and post the results back here when we ask for them.

---

### Post by Luke M on 2011-07-04
Sorry for my brevity. Yes, wildman, that's what I've been doing. Works fine. As I said, I suspect the automatic default doesn't work because it's trying to use the monitor resolution, which is not a supported mode according to vbeinfo.

---

### Post by jtarin on 2011-07-04
It should not be trying to use the monitor mode when booting. Copy your "/etc/default/grub" and post here.

---

### Post by Luke M on 2011-07-04
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1400x1050

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by jtarin on 2011-07-04
GRUB_GFXMODE="1400x1050" (notice the quotes)

---

### Post by jtarin on 2011-07-04
If that doesn't work...
Try escaping additional quotes:
GRUB_GFXMODE="\"1400x1050;640x480\""

It will produce extra quotes in grub.cfg:

set gfxmode="1400x1050;640x480"

Remember update Grub

---

### Post by Luke M on 2011-07-04
Eh? As I said above, this works fine. It's the default (line commented out) which doesn't work.

---

### Post by jtarin on 2011-07-04
> **Luke M said:**
> Eh? As I said above, this works fine. It's the default (line commented out) which doesn't work.Highlight the line in red you are talking about.

---

### Post by Luke M on 2011-07-04
> **jtarin said:**
> Highlight the line in red you are talking about.

 GRUB_GFXMODE=1400x1050

---

