---
title: "Grub Menu Question"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by ZenChrono on 2009-11-02
I have ubuntu 9.04 for my PS3 and whenever i boot up it doesn't give me the option to open the Grub Menu.
Any help would be greatly appreciated.

---

### Post by kansasnoob on 2009-11-02
Open the menu.lst with the text editor:

```
gksudo gedit /boot/grub/menu.lst
```

Look for this section:

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
**[COLOR="Red"]#[/COLOR]**hiddenmenu

You probably don't have the comment mark **[COLOR="Red"]#[/COLOR]** that I highlighted in red.

Add that #, then click on Save, then File > Quit.

---

### Post by ZenChrono on 2009-11-02
> **kansasnoob said:**
> Open the menu.lst with the text editor:

```
gksudo gedit /boot/grub/menu.lst
```Look for this section:



You probably don't have the comment mark **[COLOR=Red]#[/COLOR]** that I highlighted in red.

Add that #, then click on Save, then File > Quit.

i cant do that. It asks for a administrative password and when i enter my username password it doesnt work.

---

### Post by kansasnoob on 2009-11-02
Hmmm, it should ask for your administrative password. It should be the same password you created when you installed Ubuntu.

Even installing new packages will ask for the same password.

Did you do the installation or did someone else?

---

### Post by ZenChrono on 2009-11-02
i did but it says its the wrong password and something about sudo

---

### Post by ZenChrono on 2009-11-02
do you want me to tell you exactly what it says

---

### Post by kansasnoob on 2009-11-02
> **ZenChrono said:**
> do you want me to tell you exactly what it says

Yes. Can you copy and paste it here?

---

### Post by ZenChrono on 2009-11-02
> **kansasnoob said:**
> Yes. Can you copy and paste it here?

Failed to run gedit '/boot/grub/menu.lst' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

### Post by ZenChrono on 2009-11-02
> **F_C said:**
> [[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

that would work, but system wont let me choose administration. The only options are help and evolve email.

---

### Post by kansasnoob on 2009-11-02
What happens if you try to open a gui app like Synaptic?

---

### Post by ZenChrono on 2009-11-02
Its under system right?
well i cant it wont let me. if i click on system it brings me to this email setup

---

### Post by ZenChrono on 2009-11-02
never mind i can get to synaptic but it does the same thing because im not administrator

---

### Post by kansasnoob on 2009-11-02
In terminal run:

```
ls ~ /home
```

and post the results here.

---

### Post by ZenChrono on 2009-11-02
/home:
zenchrono

/home/zenchrono:
Desktop    Firefox_wallpaper.png  Pictures  Templates
Documents  Music          Public    Videos
zenchrono@MANOS:~$

---

### Post by kansasnoob on 2009-11-02
The only thing I'd know to do is reset the password like it describes here (must be done from recovery mode):

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ZenChrono on 2009-11-02
thats the problem i cant get to recovery mode without grub :(

---

### Post by kansasnoob on 2009-11-02
Did you read where it says:

> If you have a single-boot (Ubuntu is the only operating system on your computer), you may have to press the Escape key during bootup in order to see the boot menu.

If that just won't work, will your machine run off a Live CD - that is choose Try Ubuntu without changes to disc?

If so we can fix at least part (or maybe all) of this from the Live CD.

---

### Post by Locke_99GS on 2009-11-02
Boot a LiveCD, mount the drive that contains /etc, then add yourself to the sudoers file.

/etc/sudoers

Afterwhich, you'll be able to use sudo to do whatever it is you want to do.

---

### Post by ZenChrono on 2009-11-02
> **Locke_99GS said:**
> Boot a LiveCD, mount the drive that contains /etc, then add yourself to the sudoers file.

/etc/sudoers

Afterwhich, you'll be able to use sudo to do whatever it is you want to do.

how do you mount the drive?
Sorry my first time with xubuntu

---

### Post by Locke_99GS on 2009-11-02
```
fdisk -l
``` to list partitions, then simply
```

mkdir /mnt/foo
mount /dev/sda2 /mnt/foo

```
Then, in this example, */mnt/foo* will contain the root of sda2. Of course, you will want to substitute /dev/sda2 with whatever actual partition you are looking for, and /mnt/foo can be changed to whatever floats your boat.
In this example, the sudoers file would thence be located at */mnt/foo/etc/sudoers*

All of this will of course require root to do; On the livecd in a terminal, the sudo password is blank. Alternatively, you can switch to root by issuing *sudo su* and providing a blank password.

Does this make sense? It is late here, sorry if my thoughts are being worded improperly.

---

### Post by ZenChrono on 2009-11-02
i tried but this came up 
mkdir: cannot create directory `/mnt/foo': Permission denied
and this
mount: only root can do that

---

### Post by Locke_99GS on 2009-11-02
From the livecd, do *sudo su* first, then do the rest. Your prompt should change from $ to #, indicating root. Those commands will work, then.

---

### Post by ranch hand on 2009-11-02
if you are doing this booted to the LiveCD you still need to use sudo before the commands.

---

### Post by Locke_99GS on 2009-11-02
Yes, or precede each command with *sudo*, as ranchhand mentioned.

---

### Post by ZenChrono on 2009-11-02
but everytime i try and use sudo commands it ask for a password and this comes up[I]sudo zenchrono is not in the sudoers file.  This incident will be reported.

[/I]

---

### Post by Locke_99GS on 2009-11-02
You have to boot to the livecd first. Put the Ubuntu LiveCD in, restart the computer and boot from CD. Choose "Try Ubuntu without making any changes to computer" (or something of that sort) from there you can enter a terminal, use sudo (without a password) and fix your install.

---

### Post by ZenChrono on 2009-11-02
Gah if i could just fix that sudo stuff everything would be fine! :mad:

---

### Post by ZenChrono on 2009-11-02
> **Locke_99GS said:**
> You have to boot to the livecd first. Put the Ubuntu LiveCD in, restart the computer and boot from CD. Choose "Try Ubuntu without making any changes to computer" (or something of that sort) from there you can enter a terminal, use sudo (without a password) and fix your install.
alright i'll try that

---

### Post by ranch hand on 2009-11-02
Yes, don't panic, we are trying to fix your permissions.  Settle down a hair.  Remember to breath.

Remember that this is Linux and you do not have to reinstall.

Relax.  Have FUN.

---

### Post by kansasnoob on 2009-11-03
Whoa! This is absolute beginners where most of the folks need specific commands!

Editing sudoers may be necessary but there's a
good reason it requires vi, which is possibly the most complicated text editor on the planet!

I was going to suggest mounting and chrooting just to edit the menu.lst and then seeing if the OP could run through creating a new password.

Either way I think my mount and chroot procedure is simple:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Of course we need some info to give specific commands, beginning with:

```
sudo fdisk -l
```

---

### Post by Locke_99GS on 2009-11-03
> **kansasnoob said:**
> Whoa! This is absolute beginners where most of the folks need specific commands!

Editing sudoers may be necessary but there's a
good reason it requires vi, which is possibly the most complicated text editor on the planet!

It didn't even dawn on me. You're right, of course. :)

---

