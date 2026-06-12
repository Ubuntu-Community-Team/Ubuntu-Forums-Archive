---
title: "OS Order"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by 7azem on 2010-07-31
I have Ubuntu for desktops installed on my LG Netbook, before i have installed Ubuntu, I had a Windows XP Home edition,,
After I installed Ubuntu (not as Wubi), the order of the operating systems to boot start with Ubuntu and other options like memory tests, and my windows OS is the last one!

now Ive asked some people and they told me to open the GRUB menu list or something using the terminal, I open that in a text editor, but the problem is that It's empty! there's nothing in it, so there's no (default 0) line!!

I've also tried to change the Order of the OSes using windows, but when i come to change it, windows only sees it self, and doesn't recognize that there's another OS called Ubuntu is installed, and it tells me that it's the Default OS while it's not!

All i want is to make my Windows the Default OS again!

and if i want to uninstall Ubnutu,, is there anyway without the necessary of formatting the desk again? cuz I just have two Disks one of them is full of programs, and the other has windows on it...and I really don't know how to know where's my Ubuntu at, cuz it has no files when i browse using windows!

please fix me this problem, it's so painful! :S
and thank you very much! :)

---

### Post by howefield on 2010-07-31
> **7azem said:**
> All i want is to make my Windows the Default OS again!

Don't understand much of the rest of what you are trying to say but as for making Windows the default boot, if you have a recent version of Ubuntu, there is no menu.lst file, you need to read up on Grub2

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Alternatively, the easy graphical way of doing it would be to install startupmanager, an application that you can install with Synaptic Package Manager.

---

### Post by hyperAura on 2010-07-31
the linux partition has no files when browsing through windows since it is of a format which it is not recognizable by windows. I dont know the reason why u cant read the menu.lst file but I think u can install easybcd program through windows and change the order of the OS's.. As soon as u change the order of the OS's u can format the linux partition but I dont know if it is safe because this depends on where your boot loader resides..

---

### Post by Mark Phelps on 2010-07-31
> **hyperAura said:**
> the linux partition has no files when browsing through windows since it is of a format which it is not recognizable by windows. I dont know the reason why u cant read the menu.lst file but I think u can install easybcd program through windows and change the order of the OS's.. As soon as u change the order of the OS's u can format the linux partition but I dont know if it is safe because this depends on where your boot loader resides..

You should really NOT be offering such advice.

First of all, the order of the OSs is set by GRUB, in a menu that it generates.  EasyBCD is an MS Windows program for modify the MS Windows BCD -- which has absolutely NOTHING to do with GRUB.

Second, why on earth would you tell someone to format their partition, and basically WIPE OUT everything they have in that partition -- simply to change the ORDER in which OSs are presented?

And finally, you obviously know so little about Ubuntu, that you're unaware that the current version uses a version of GRUB that does NOT use the menu.lst file -- at all!  And, even if it DID use menu.lst, you would NOT be able to read it from inside MS Windows because the default filesystem for Ubuntu 10.04 is Ext4 -- which, at present, there are no MS Windows utilities that can read it.

---

### Post by deb_untu on 2010-07-31
There is no menu.lst in the current ubuntu. Instead it is grub.cfg.
Though it is not recommended to edit directly, you can do it as   follows:
In gnome-terminal type

```
sudo gedit /boot/grub/grub.cfg
```

search for```
 set default="0"
```
change this zero to your windows entry ( grub menu entry minus one) 

[COLOR="Red"]Example:[/COLOR] If you see your windows entry in 4rd place in grub menu, set default="3"

save & exit

---

### Post by Old_Grey_Wolf on 2010-07-31
> **howefield said:**
> Alternatively, the easy graphical way of doing it would be to install startupmanager, an application that you can install with Synaptic Package Manager.

Agree with this recommendation.

---

### Post by Elmer Fudd on 2010-07-31
I believe the following is true. Corrections appreciated.

Do not change grub.cfg it will get reset whenever there is a kernel update.

Grub2's version of menu.lst is /etc/default/grub

In a terminal:
sudo gedit /etc/default/grub

change GRUB_DEFAULT=??? to GRUB_DEFAULT=3 
or whatever the win-Os menu number is minus one.
IF it is the 3rd one when grub starts then GRUB_DEFAULT=2.
save and quit "gedit"

then 
sudo update-grub

Now let me anticipate your next problem.
When there is a kernel update, update-grub will run and install a new selection (two actually) and the number "3" entry will no longer be your windows partition. You can edit the /etc/default/grub file again but I recommend removing older kernels.

-Ubuntu Tweak is probably the easiest for noobs.
(install from synaptic ubuntu-tweak
or the command line "sudo apt-get install ubuntu-tweak")
It will install in Applications/System Tools menu.
Start it and select Package Cleaner/ Clean Kernels
It will show a list of removable kernels.
Click unlock and put in your password.


Do keep the two most recent kernels that work.

---

### Post by Paqman on 2010-07-31
Installing startupmanager is by far the easiest solution here, as howefield mentioned.

> **Elmer Fudd said:**
> 
In a terminal:
sudo gedit /etc/default/grub


Gedit is a graphical app, so you should always use gksu instead of sudo.

---

### Post by Elmer Fudd on 2010-08-01
I always setup my linux converts with burg. It gives a much more polished look than grub. I don't believe that startupmanager recognizes it.
Yes, you are correct I should use/recommend gksu with a graphical app, but I have never had any problems so I forget.

---

### Post by 7azem on 2010-08-01
> **deb_untu said:**
> There is no menu.lst in the current ubuntu. Instead it is grub.cfg.
Though it is not recommended to edit directly, you can do it as   follows:
In gnome-terminal type

```
sudo gedit /boot/grub/grub.cfg
```

search for```
 set default="0"
```
change this zero to your windows entry ( grub menu entry minus one) 

[COLOR="Red"]Example:[/COLOR] If you see your windows entry in 4rd place in grub menu, set default="3"

save & exit


Thanks a lot! this actually worked!! finally it did! :D

---

### Post by 7azem on 2010-08-01
> **Elmer Fudd said:**
> I believe the following is true. Corrections appreciated.

Do not change grub.cfg it will get reset whenever there is a kernel update.

Grub2's version of menu.lst is /etc/default/grub

In a terminal:
sudo gedit /etc/default/grub

change GRUB_DEFAULT=??? to GRUB_DEFAULT=3 
or whatever the win-Os menu number is minus one.
IF it is the 3rd one when grub starts then GRUB_DEFAULT=2.
save and quit "gedit"

then 
sudo update-grub

Now let me anticipate your next problem.
When there is a kernel update, update-grub will run and install a new selection (two actually) and the number "3" entry will no longer be your windows partition. You can edit the /etc/default/grub file again but I recommend removing older kernels.

-Ubuntu Tweak is probably the easiest for noobs.
(install from synaptic ubuntu-tweak
or the command line "sudo apt-get install ubuntu-tweak")
It will install in Applications/System Tools menu.
Start it and select Package Cleaner/ Clean Kernels
It will show a list of removable kernels.
Click unlock and put in your password.


Do keep the two most recent kernels that work.


seems like it's the best way to do it! but it tells me that access is denied! it doesn't even ask me for a password!
but thanks anyway! :)

---

### Post by 7azem on 2010-08-01
thank you so much! it worked!

---

### Post by stlsaint on 2010-08-01
> And, even if it DID use menu.lst, you would NOT be able to read it from inside MS Windows because the default filesystem for Ubuntu 10.04 is Ext4 -- which, at present, there are no MS Windows utilities that can read it. - Mark Phelps

This is actually more advanced in development than most people know! [Ext2Read]("http://sourceforge.net/projects/ext2read/")

This is just one amongst others.

---

### Post by MockY on 2010-08-12
> **deb_untu said:**
> There is no menu.lst in the current ubuntu. Instead it is grub.cfg.
Though it is not recommended to edit directly, you can do it as   follows:
In gnome-terminal type

```
sudo gedit /boot/grub/grub.cfg
```

search for```
 set default="0"
```
change this zero to your windows entry ( grub menu entry minus one) 

[COLOR="Red"]Example:[/COLOR] If you see your windows entry in 4rd place in grub menu, set default="3"

save & exit

I use Burg on one of the machines I recently set up dual boot on, and it does not matter at all what number I put as default, it does not change anyway. The Windows entry is number four (4) in my case, but even when I set it to 4 and update both grub and burg, burg still uses Ubuntu as the default operating system to boot into.

Any ideas?

---

