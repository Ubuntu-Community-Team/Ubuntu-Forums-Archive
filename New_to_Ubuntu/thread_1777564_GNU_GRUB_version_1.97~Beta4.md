---
title: "GNU GRUB version 1.97~Beta4"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by Bob&amp;Frank on 2011-06-07
I upgraded my system from 10.4 to 10.10 then to 11.4 last night.
after upgrading from 10.10 to 11.4 i have not been able to boot from grub.
instead i have to Boot a Specific Kernel Manually in rescue mode. 

How do i boot normally with grub?

not sure if this is related but java applications were affected, 
vuze open intermittently and torrent fail. 
also all video output has blue people vlc, kaffine, ... .  

any help would be appreciated.

---

### Post by drs305 on 2011-06-07
You can tell which version of Grub 2 you are using on the initial boot screen or by running "grub-install -v". You might also confirm you are running Natty's kernel with "uname -r". It should be 2.6.38...

If you are stll using 1.97 and it's not working, I'd recommend booting a LiveCD, chrooting into your Natty installation, and purging and reinstalling Grub2. You would need a Natty LiveCD to do this.

This will give you the latest version of Grub 2, and it may also solve your boot issues. Your problems may be related to video issues, but you should probably upgrade to Grub 1.99 regardless.

The instructions for chrooting are in the following link:
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")
At the start of the 'Chroot' section I've added a link to a blog which has a good graphical explanation of how to chroot.

If you have questions, please download, extract and run the boot info script and post the contents of RESULTS.txt  You can get it from the "BIS" link in my signature line.

---

### Post by Bob&amp;Frank on 2011-06-07
Thanks for the help
I'll get some cd's and do that

the kernel version is 2.6.38
i'm using (GRUB) 1.99~rc1-13ubuntu3

---

### Post by drs305 on 2011-06-07
> **Bob&Frank said:**
> Thanks for the help
I'll get some cd's and do that

the kernel version is 2.6.38
i'm using (GRUB) 1.99~rc1-13ubuntu3

Purging/reinstalling may still help, but since you are running the latest grub and not 1.97, and the correct kernel, it isn't as likely to be causing your problems. It sounds much less like a Grub problem.

You could try editing the Grub menu when it appears by pressing 'e' to edit the menu entry. Go to the end of the "linux" line, remove 'quiet splash vt.handoff=7' or whatever is there, and add 'nomodeset'. Then CTRL-x to boot. That will prevent some of the modules from loading and may allow you to boot to a normal Desktop. It's something to try anyway.

---

### Post by alphacrucis2 on 2011-06-07
Maybe also try running

```
sudo update-grub
```

Just to see if it gives any errors as much as anything. It should cause the boot menu files to get rebuilt anyway.

---

### Post by Bob&amp;Frank on 2011-06-07
when i'm in rescue mode it loads with GNU GRUB version 1.97~Beta4
but i'll be sure to try everything you suggested.

---

### Post by Bob&amp;Frank on 2011-06-07
> **alphacrucis2 said:**
> Maybe also try running

```
sudo update-grub
```

Just to see if it gives any errors as much as anything. It should cause the boot menu files to get rebuilt anyway.

generated 

Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-2.6.38-8-generic-pae
Found initrd image: /boot/initrd.img-2.6.38-8-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by alphacrucis2 on 2011-06-07
> **Bob&Frank said:**
> when i'm in rescue mode it loads with GNU GRUB version 1.97~Beta4
but i'll be sure to try everything you suggested.

Odd. Sounds like the new version of grub didn't install properly when you upgraded. I'd reinstall it. (Edit: Just grub I mean, not 11.04).

---

### Post by Mac-ghost-hunter on 2011-06-07
Ok, get this error.....

I have ultimate 2.9 running on my drive.  I installed ubuntu 10.10 on another partition to test 11.04 on  I had some problems upgrading 10.10 to 11.04.  Now this 10.10 which I am upgrading to 11.04 right now has control of update-grub.  

 When I run update-grub from ultimate 2.9 it says it is complete and exits normal.  But a reboot does not show any changes to the boot partition.

I log on to the ubuntu 10.10 and ran update-grub and this one worked.  Boot partition and startup manager all agree.  

I eventually will delete the ubuntu after I test it and ditch unity.  How do I do this without crippling grub?  

;) Mac-ghost-hunter

---

### Post by alphacrucis2 on 2011-06-07
> **Mac-ghost-hunter said:**
> Ok, get this error.....

I have ultimate 2.9 running on my drive.  I installed ubuntu 10.10 on another partition to test 11.04 on  I had some problems upgrading 10.10 to 11.04.  Now this 10.10 which I am upgrading to 11.04 right now has control of update-grub.  

 When I run update-grub from ultimate 2.9 it says it is complete and exits normal.  But a reboot does not show any changes to the boot partition.

I log on to the ubuntu 10.10 and ran update-grub and this one worked.  Boot partition and startup manager all agree.  

I eventually will delete the ubuntu after I test it and ditch unity.  How do I do this without crippling grub?  

;) Mac-ghost-hunter

I think that the particular grub and grub menu that gets invoked when there are multiple linuxes depends on which one actually wrote the MBR and the other stuff grub puts between the MBR and the first partition. Stored in there somewhere will be how it locates the grub stage II stuff. When you run grub-install, it updates the MBR and the stuff inserted between the MBR and the first partition, (though someone can correct me on exactly how this works), it will end up using the the grub menu that was created under the /boot/grub from the OS where grub-install was run. There is a pretty good doc about grub2 anyway:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by drs305 on 2011-06-08
As was mentioned, the fact that you have more than one Ubuntu partition changes things a bit. If you are seeing "Grub 1.97~beta4" on the boot screen it means that your desired Ubuntu partition isn't controlling the boot. 

So you should boot to the Ubuntu you want to normally run and then run:
```
sudo grub-install /dev/sda
```
Don't include the partition number, and this assumes Ubuntu is on the sda drive. This will change control of the boot to your currently running OS (assuming it's Ubuntu).

If this doesn't solve the boot issues, you should probably try purge/reinstalling Grub. As long as you are 'in' the OS you want, you don't have to 'chroot' - just follow the Steps 2-5 instructions in the 'chroot' guide.

---

### Post by Mac-ghost-hunter on 2011-06-08
Thank You.  IF that is the case I believe I will have to delete the ububtu and the ultimate 2.9 do a reinstall with ubuntu 11.04 first then reinstall the ultimate 10.10, the last instalation seams to be the MBR writer.
 
Never saw this before,it what I get for trying to install fedora 15.  it only uses grub .97 and 10.10 uses 1.97 and ubuntu 11.04 uses 1.99
 
do you think I can install fedora 15 first and then ubuntu 11.04 then Ultimate 2.9 then do a grub-update from ultimate 2.9 and let it write the MBR for all three on the distros?

---

### Post by drs305 on 2011-06-08
> **Mac-ghost-hunter said:**
> Thank You.  IF that is the case I believe I will have to delete the ububtu and the ultimate 2.9 do a reinstall with ubuntu 11.04 first then reinstall the ultimate 10.10, the last instalation seams to be the MBR writer.
 
Never saw this before,it what I get for trying to install fedora 15.  it only uses grub .97 and 10.10 uses 1.97 and ubuntu 11.04 uses 1.99
 
do you think I can install fedora 15 first and then ubuntu 11.04 then Ultimate 2.9 then do a grub-update from ultimate 2.9 and let it write the MBR for all three on the distros?

I don't think you need to reinstall all the OS's if the boot files are intact on each OS's partition. You should be able to chainload to Fedora's Grub legacy from Grub 2. I haven't used Fedora, so I'm not sure of the exact process, but here are a couple of links that should help:
[http://ubuntuforums.org/showthread.php?p=10914937]("http://ubuntuforums.org/showthread.php?p=10914937")
[HowTo: add Fedora 15 to Maverick Grub 2]("http://ubuntuforums.org/showthread.php?t=1714170")

---

### Post by Mac-ghost-hunter on 2011-06-09
Thank you Is did a sudo grub-install /dev/sdb and it fix my boot.  Now I have a nice spashimage running too.
 
Reinstalled Fedora to use Gnome 3 and install ushare but trying start the server was horable so I am staying on ubuntu.  Just saw that 11.10 ubuntu will have gnome 3.
 
Mac-ghost-hunter

---

### Post by Bob&amp;Frank on 2011-06-10
Thanks a lot this solved my grub problem.
everything boots normally now.

 :p

---

