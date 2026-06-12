---
title: "Using fsck on a wbi install?"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by Steve.G on 2009-11-18
Ok, so I'm running Karmic on a wubi installation, with Vista cohabitating on the drive. Whenever I shutdown, my system hangs with a bunch of errors involving I/O errors.. I posted them in a thread already and no one has responded yet.

Anyhow, I think it might be advisable to run fsck to clean up any bad blocks that I might have.. however, I would like to know the best way to go about it. I would be ok using a live cd, but I'm curious as to how this would work with my particular install.

Would I be better doing a shudown -F -r and letting it do it itself? I tried running the recovery mode and ended up at a shell telling me to run fsck manually. I tried to, but I was unable to umount /dev/sda1 since it told me that /host was in use.

Advice, please?

---

### Post by garvinrick4 on 2009-11-18
Code:  "sudo apt-get shutdown -r now"   without qoutes to reboot

Code:   "sudo apt-get shutdown -h now"    without qoutes to shutdown.

 use this always for now.

Every 20 or so boots it will drop to a maintinance shell on its own.
no problem.

put in your login and password.

 Code;  'fsck"   with qoutes  and then hit "y" key when asks to clean. Watch what it asks you while doing maintinance.

Comes to your prompt.   sudo apt-get shutdown -r now


Here is a link that you can go to, look at #19 it will give you a fix just changing 2 letters.
[Bug #468589 in sysvinit (Ubuntu): &#8220;Unable to shut down or restart on Karmic&#8221;]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/468589") 

Use the terminal to shutdown as in start of this post always until the send out the fix.
You will have now problems. Something to do with mounting or unmounting of loop/0

---

### Post by Steve.G on 2009-11-18
Thank you so much for that. So tell me this: can I just apply that fix and expect the problem to be resolved, or will I still to use the shutdown command manually? I have no problem with it, just curious for my wife who has finally come around to using my Ubuntu install. ;) Anything that even resembles a CLI sends her packing back to Windows. 

Anyhow, I am at work now, and will apply this fix when I get home tonight. Again, thank you.

---

### Post by garvinrick4 on 2009-11-18
Okay get your WUBI set up to go then go to System to Addministration to Update manager
and update. There was a fix in last nights upgrades for the problem, usually works these fixes.
  Go to Synaptic Package Manager in Administration and make sure you have.
ubuntu-restricted-extras  selected.    Just type in upper right hand corner and have
left selection highlighted on All.  Check box and Apply.

If you have not fixed to good looking True Type fonts on desktop and Browser let me
know it is a quick fix.

On right hand upper corner where it says your log-in name there is a drop down list and
2 of them are restart and shutdown. They say will do it in 60 seconds when accessed.
There is a little trick to make them just do it with no wait time. 
Only "fsck" without qoutes when you are prompted to a maintanence shell for now.
You should not be getting any errors now where it go's in the  I/0 errors or mount problems in Loop/0.    Loop/0 is you it is the ext4 or ext3 that is Linux.  NTFS is the
Windows programs and they are your host in Wubi. Your ext4 or ext3 is inside a folder
in Windows NTFS format. Once you get this done I got some great material for you to
read to understand what you are doing. Once you get it, you will never want to use Windows again. 

Anyone out there want to get rid of wait box on shutdown or restart go to alt/F2
Type in gconf-editor enter    go to apps  indicator session click on it. In right hand bos
check the suppress logout restart shutdown box, only one there. And it is done. It will reboot or shutdown like now. Lot of things in conf-editor. GUI App in system tools.

---

### Post by Steve.G on 2009-11-19
Just did a successful restart. Thanks for the tips. I'm always down to learn something new, though this thread might not be the best place in the world. ;)

---

### Post by garvinrick4 on 2009-11-19
Good luck and glad you do not get the error message anymore.

---

