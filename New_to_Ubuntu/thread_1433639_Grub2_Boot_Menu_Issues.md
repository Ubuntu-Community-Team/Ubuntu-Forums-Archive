---
title: "Grub2 Boot Menu Issues"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by foghornsean on 2010-03-19
Hi guys,
 
I've got Ubuntu 9.10 installed on my machine and have run into an issue with the Grub2 boot menu. When I first installed Ubuntu, which is the only operating system on the computer, it used to boot straight away into Ubuntu. Now however it boots to the OS selection menu.
 
The problem I'm having is that nothing I do seems to stop the menu coming up at bootup. I've tried following the advice on the forums and fiddled around with /etc/default/grub. I've tried changing the GRUB_TIMEOUT field, with times both in " marks and without, GRUB_HIDDEN_TIMEOUT isn't commented out, trying to boot the previously saved OS selection doesn't work. I'd even be happy for the menu to come up and then select the default selection after a short time but the menu just sits there indefinately until I make a selection.
 
It may sound like I'm just being lazy and don't want the menu to come up but the whole reason I installed Ubuntu was to use this spare computer as a server at home so I want to leave it on and, should there be a powercut or something, I want it to start up on it's own and carry on from where it left off. Obviously if it's stuck in the Grub2 menu this isn't going to happen.
 
Any suggestions on where I can go from here guys? I'm kinda stuck!
 
Thanks in advance.
 
Sean

---

### Post by anaconda on 2010-03-19
did you remember to run the "sudo update-grub" after making changes to /etc/default/grub

---

### Post by foghornsean on 2010-03-19
Yeah sorry,
 
Forgot to say I'd run sudo update-grub after changing the file.

---

### Post by stoogiebuncho on 2010-03-19
Can you post your /etc/default/grub file here so we can look it over?

---

### Post by foghornsean on 2010-03-19
Yeah will do.
I'm at work at the moment so will repost over the weekend.
Thanks

---

### Post by foghornsean on 2010-03-28
Hi Guys,

Here's my /etc/default/grub file contents. Apologies for just copying it into the post, I couldn't work out how to attach the file to the post instead (It kept telling me that the file type was invalid)

Hope there's something simple that I've just missed.

Thanks

Sean

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_SAVEDEFAULT=true
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="0"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by stoogiebuncho on 2010-03-28
Hmmm, this looks like mine, except for the savedefault option.  Can you try commenting that line out, running sudo update-grub and seeing if that changes anything?

I have heard of this problem with grub2 before, but in all of the cases I've seen, there were multiple OSes installed on the computer.  You say you only have Ubuntu installed, and I've never heard of there being a problem with that.

Just for fun, I'll put my grub file in here also so you compare.  This is a laptop that only has Ubuntu installed on it.  It does not display the grub menu or a countdown, and boots automatically into Ubuntu when I start it.

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=1
#next line needs to be commented to see the options
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by foghornsean on 2010-03-28
Hi Stoogiebuncho,
 
Thanks for coming back to me.
 
I tried commenting out that line and I still get the boot menu at start up.
 
With regards to other installations on the system, there's only Ubuntu 9.10 on there but the start up menu seems to give me a choice of 3 different versions of 9.10 plus the memory test boot option. I'm not really sure why it did this but it only started happening after I downloaded the updates. It's almost like it's giving me the option to boot an older version of 9.10, not sure why you'd want to though.
 
Sean

---

### Post by PocketDog on 2010-03-28
That's because kernel updates are added to your grub but the old ones aren't removed automatically. You can do that yourself by removing the older, unwanted kernels using Synaptic

---

### Post by PocketDog on 2010-03-28
From the Grub2 documentation [quote=https://help.ubuntu.com/community/Grub2#Boot Display Behavior]GRUB 2 will boot straight into the default operating system if no other operating system is detected. No menu will be displayed. If another operating system is detected, the GRUB 2 menu will display.[/quote]

So it appears to me that if you remove the older kernels from Synaptic, you won't see the Grub menu

---

### Post by m4tic on 2010-03-28
sudo update-grub2
it will revert to default setup

---

