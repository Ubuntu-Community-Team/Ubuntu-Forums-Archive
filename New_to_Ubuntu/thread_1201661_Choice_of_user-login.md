---
title: "Choice of user-login"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by linoob13 on 2009-07-01
Hi everybody :)

Question: how can I configure the systemstartup on [SIZE=2]**XBUNTU**[/SIZE] to stop before loading the login window?

I want it to act like [SIZE=2]**UBUNTU**[/SIZE], where you land on the system-prompt and can do "sudo su" before issuing the "startx" command.

Greetz   ):P

---

### Post by scrooge_74 on 2009-07-01
Like in Ubuntu?  Mines take me straight to the login window.

I guess you could remove the GDM step from your start config so it drops you in terminal mode

---

### Post by linoob13 on 2009-07-01
I'm looking thru all those scattered startup and resource files for 2 days now - but I haven't found a file yet where I could set an exit to land on the prompt :(

All docs I've read so far don't even mention this subject. But it's not very satisfying to land on the desktop with admin rights and so on and still not being able to do ROOT functions without always having to input your password or being closed out from some files at all (rootaccess only) [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]

One extra prayer for the person who could give me the name of the file in question.:lolflag:

---

### Post by scrooge_74 on 2009-07-01
Ok before you go any further with that line of toughts, lets get a few things clear that may help you.

First: when the system boots and gets you to the login screen you input your user and pass.  That user can manage the system to a point, admin task you need to put your pass again (this is a security meassure) to avoid you erasing something by mistake. You need to adapt to Linux, in Windows you are always the admin so you can mess the system (or a virus can).  

If what you want is to drop the GDM logging screen so it gets you into the system faster after you input your user and pass i have a link somewhere for that.

But never log as root as a normal user there is a reason behind that.

[This link]("http://forums.debian.net/viewtopic.php?t=14129&highlight=xfce4") is a bit old, but you will find what you are looking in it, it was design to use with Xfce (which is what Xubuntu uses as GUI)

---

### Post by ronaldprettyman on 2009-07-01
> **linoob13 said:**
> Hi everybody :)

Question: how can I configure the systemstartup on [SIZE=2]**XBUNTU**[/SIZE] to stop before loading the login window?

I want it to act like [SIZE=2]**UBUNTU**[/SIZE], where you land on the system-prompt and can do "sudo su" before issuing the "startx" command.

Greetz   ):P
```
sudo update-rc.d -f gdm remove
sudo update-rc.d -f xdm remove 
```
removes gdm or xdm respectively from the boot, your go straight to a prompt
you can also remove the splash and see the actual boot process by removing "quiet splash" from your menu.lst
```
sudo vi /boot/grub/menu.lst
```

to change graphical login screen from xdm to gdm or even kdm
```
sudo dpkg-reconfigure gdm
```
install all of them
```
sudo apt-get install gdm xdm kdm
```
Stop or start the graphical login screen with out adding it to boot, or start x though a login rather then starx or the easy way to change session
```
sudo /etc/init.d/gdm restart
```
> **linoob13 said:**
> sudo su
why not
```
sudo bash
```

Note you can always just hold
ALT+CTRL+F1
F1 - F6 are usually virtual terminal tty1-tty6 respectively where F7 would be x
you can change this in your inittab file
wait no thats not theirs its
I have no idea where the tty and virtual terminals are specified in ubuntu, I'll have to look into that got a lead on /etc/event.d/

---

### Post by linoob13 on 2009-07-01
Thanks for the tips :)

I'm gonna try it out by removing GDM.

Have to save my precious xorg.conf file - took me another 2 days to get the fullscreen desktop on my old notebook.

I'll let you know the result, when the system in back up again ;)

---

### Post by linoob13 on 2009-07-01
@[ronaldprettyman]("http://ubuntuforums.org/member.php?u=500296")

I've run all steps like described and edited the GRUB file.

The system boots up like before -- splash screen - login window - desktop [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

---

### Post by scorp123 on 2009-07-01
> **linoob13 said:**
>  "sudo su" before issuing the "startx" command  Running a GUI as root???  That's seriously a very bad idea. And a very good way to hose your system in no time. Just one accidental "drag & drop" over the wrong place will be enough.

---

### Post by linoob13 on 2009-07-01
I used to work with different Unixes 20 years ago - so I know what I do ;)

I just have to get used to all that new "X" stuff and where to find the appropriate files to play around with the system.
So when I want to run my session with root privileges, I think it's OK   :))

---

### Post by ronaldprettyman on 2009-07-01
> **linoob13 said:**
> I used to work with different Unixes 20 years ago - so I know what I do ;)

I just have to get used to all that new "X" stuff and where to find the appropriate files to play around with the system.
So when I want to run my session with root privileges, I think it's OK   :))

Tell em how it is brother. Their really sudo happy around here though, kinda freaks me out at times too.

Yeah I find it helpful to use alt+ctrl+f1-f6 from x to switch tty and alt+f1-f6 in a terminal to swtich tty

Couple quick things about linux vs Unix
You have virtualconsoles or getty instances of the serial console for tty1 - tty6 in ubuntu each linux distro is different and I think freebsd has the something similiar but anyway

You can get a better resolution on your console by editing your grub file
/boot/grub/menu.lst
(i guess grub.conf was too linuxy for grub2x)
Look for the line about your kernel, delete the 
silent and splash tags
silent makes it hide details, and splash is the splash
add
vga=ask
your be able to select your resolution on reboot, wrtie down the number that works for you and add 0x0### in place of the ask and your have a better resolution for your terminals
you can also link things like top to a terminal instead of a login prompt and issue message though the
/etc/event.d/tty(instert number here)
```
exec /sbin/getty -n -l /usr/bin/top 38400 tty6

```
Runs top on tty6 (ctrl+alt+f6)

---

### Post by ronaldprettyman on 2009-07-01
> **linoob13 said:**
> @[ronaldprettyman]("http://ubuntuforums.org/member.php?u=500296")

I've run all steps like described and edited the GRUB file.

The system boots up like before -- splash screen - login window - desktop [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

```
ls /etc/init.d
```
These are all your startup scripts
```
ls /etc/init.d|grep dm
```
You might see, gdm, xdm, kdm if you have one or all disable them
```
sudo update-rc.d -f xdm remove
sudo update-rc.d -f gdm remove
sudo update-rc.d -f kdm remove
```

For the splash screen
```
sudo vi /boot/grub/menu.lst
```
Your will look similar to this
```

title		Xubuntu 9.04, kernel 2.6.28-13-generic
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro **quiet splash **
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/memtest86+.bin
quiet

```
Here is mine, I have everything turned off to get a regular boot screen and see everything in dmesg as it boot, I also am to lazy to remember my framebuffer hex and just have it set to ask. Though I should probably write it down and fix it on my next reboot
```

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro **vga=ask**
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9a7be591-5ffb-4886-a606-2e628acd5afb ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9a7be591-5ffb-4886-a606-2e628acd5afb
kernel		/boot/memtest86+.bin
quiet

```

Why does ubuntu use the uuid who the hell wants to memorize that, what ever happen to good old /dev/hd or /dev/sd (though it should be hd but ubuntu keep telling me I have scsi drives??????? I believe sd is for scsidrive(maybe sata) and hd is for harddrive but even my ide drive come up as sd in ubuntu, while in redhat/gentoo/slackware/random linux os they usually show up as hd) Though I had them go from /dev/sd to /dev/hd in debian before on a kernel update, wow was the a pain to get the system bootable and figuring out what the problem was, simple replacing hd with sd in fstab and it worked. But whats up with that???

In other verisons of linux this is accomplished by changing the standard runlevel from runlevel 5 to runlevel 4(its similar in solaris and hp-ux as well), but your notice ubuntu is different in alot of ways from unix and other *nix varients. But all the time your save with apt, and all the cool ..stuff your find with it make it worth it in the end, at least for me.

Note that ubuntu will overwrite your changes to menu.lst with each kernel or grub update. But your init.d settings with stay in after updates, your just have to edit it to remove the splash and set the framebuffer resolution after each kernel update. Kernel updates aren't too frequent though.

---

### Post by ~sHyLoCk~ on 2009-07-01
> **linoob13 said:**
> Hi everybody :)

Question: how can I configure the systemstartup on [SIZE=2]**XBUNTU**[/SIZE] to stop before loading the login window?

I want it to act like [SIZE=2]**UBUNTU**[/SIZE], where you land on the system-prompt and can do "sudo su" before issuing the "startx" command.

Greetz   ):P

You can mess with the /etc/rc.2 runlevels but i think you should install sysv-rc-conf and change gdm runlevel :
```
sudo sysv-rc-conf --level 2345 gdm off
```

---

### Post by scorp123 on 2009-07-02
> **linoob13 said:**
> I used to work with different Unixes 20 years ago - so I know what I do ;)  Ah OK ... I beg for thy forgiveness, oh brother. :lolflag:

It's just that there are too many beginners out here who want to work as "root" all the time because they're too lazy to type in the "sudo" password here and there. But if you have 20+ years of experience with HP-UX, Solaris and what not ... well yeah, you know the rest :)

---

### Post by scorp123 on 2009-07-02
> **ronaldprettyman said:**
>  Tell em how it is brother. Their really sudo happy around here though, kinda freaks me out at times too.  He knows what he does. You can't say the same about all the newcomers and newbies around here. No insult intended, it's just the way it is.

> **ronaldprettyman said:**
>  You can get a better resolution on your console by editing your grub file
/boot/grub/menu.lst

(i guess grub.conf was too linuxy for grub2x)
Look for the line about your kernel, delete the 
silent and splash tags
silent makes it hide details, and splash is the splash
add
vga=ask
your be able to select your resolution on reboot, wrtie down the number that works for you and add 0x0### in place of the ask and your have a better resolution for your terminals This will not work. At least not the way you intend it to work. With your method he'll be stuck to VGA text modes and font rendering there is downright ugly. It would be far better to re-enable the framebuffer and then pick a nice hi-res mode. Font rendering is so much better with framebuffers. But for some stupid reasons I fail yet to understand Ubuntu now comes with the framebuffer disabled. So you have to enable it first. Read here:

[http://ubuntuforums.org/showpost.php?p=4879140&postcount=61](http://ubuntuforums.org/showpost.php?p=4879140&postcount=61)

---

### Post by ronaldprettyman on 2009-07-02
> **~sHyLoCk~ said:**
> 
```
sudo sysv-rc-conf --level 2345 gdm off
```
This is identical to 
```
sudo update-rc.d -f gdm remove
```
It removes it from 2345

---

### Post by linoob13 on 2009-07-03
Many thanks for all the good tips guys :)

I solved my problem with a little workaround ;)
System is OK so far.

But after installing a dozen new packages my sound is gone :(

But more imporant for me is a working IrDA interface to exchange data with my PPC and mobile phone.
Guess I make up a new thread for the IrDA issue.


This one is SOLVED

---

