---
title: "need some help, please!"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by 2roombas on 2009-03-08
I just bought and received my Dell mini two days ago. It uses the Ubuntu 8.04 OS. I loved it ...it was working great until I went into **Systems/Administration/Users and Groups**, unlocked it then chose my account (I'm he only user of this mini). I then clicked **Properties**, then the **Advanced **tab where I "thought" I could simply remove the extra "w" that I incorrectly typed in my name in the set up. I deleted the extra "w" from my name in the Home directory field and the Main Group field.

I have learned the hard way that doesn't work! Now when I boot up I see....

*"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writable by otter users."*

I then click **OK **and see the message...
[I]
"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."[/I]

There is a "**View detail"** link and those details are below...

/etc/gdm/Xsession: Beginning session setup...
Can't save user-dirs.dirs
Setting IM through: im-switch for locale-en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Could not create gnome accelerators directory '/home/jennette/.gnome2/accels': Permission denied

I then click **OK**... wait for the login screen, then click the little options icon in the bottom left corner. I choose "**failsafe GNOME**" and return to login. Incorrect...invalid.

I have tried repeatedly so I know I have used the correct pswd. This is making me nauseous. I'm deaf and I was all excited to be taking this as a communication aid to a meeting I have next month. I want to cry.:(

---

### Post by miegiel on 2009-03-08
I think there is no home directory for the user, I'm not 100% sure though. You can take a look in /home and see if you can find it. Possibly you will need to copy or more your old user's directory to the new user directory.

---

### Post by LowSky on 2009-03-08
OK don't panic, its all fixable... boot and press escape during boot (this will bring you to the grub menu), choose recovery mode of the newest kernel.

Once the boot sequence ends, you will be at a prompt similar to:

```
root@machine:~#
```

The home directory for the user is /home/username (replace "username" with the actual user's username; ex: /home/james). You need to confirm that it exists. Do so like this:
```
ls -l /home
```

If it's not there, create it and give it the proper permissions. Again, as an example, we are using the username "james": 

```
mkdir /home/james
chown james:james /home/james
```



Instead of repairing the existing user you can create a fresh new user and then deal with automatic login.

Type in the following command to create the user and grant him administrator rights. As an example, we will use the username "john":

```
adduser john
adduser john admin
```

You will be asked a series of questions. The only one you need to answer is for the password. You can safely press Enter for all the others. Note that the password will not be visible on the screen. You will be prompted to enter the password correctly twice.


I got all this from 
[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

good luck, hope this isn't too hard to understand

---

### Post by 2roombas on 2009-03-08
When I press esc while booting I only get a black screen with **MBR 2Fa:**   no recovery menu?!

---

### Post by Temposs on 2009-03-08
hi 2roombas,
   Sounds like quite a situation you've got. First thing you'll want to do is be able to drop into recovery mode. Right before Ubuntu starts to boot up, you should be able to press escape and get into a menu where you can select recovery mode. When you have gotten to a menu with a bunch of recovery options, you want to choose the option to use the root shell. 

   I think this is what you want to do once you've booted into the root shell(all black screen with command line interface):

```
usermod -d /home/originalname -g originalname loginname
```

*originalname* is what you had with the extra "w". *loginname* is probably the same as *originalname*. So, I've never had to do this, but I think this is what will let you revert what you changed back to what it needs to be.

If that doesn't work, go back to the root shell and add a new user:

```
adduser newusername
```

where *newusername* is any new user name you'd like to have. Then you should have a new account to login with, and you should be able to use Ubuntu as normal with the graphical interface and try to fix your original account through there, or just delete your original account.

---

### Post by Temposs on 2009-03-08
> **2roombas said:**
> When I press esc while booting I only get a black screen with **MBR 2Fa:**   no recovery menu?!

You need to do it before you see Ubuntu start to boot up. See if you can get it.

---

### Post by 2roombas on 2009-03-08
...and then if I press esc after the ubuntu logo appears, it only goes to that first error message.

---

### Post by Temposs on 2009-03-08
> **2roombas said:**
> ...and then if I press esc after the ubuntu logo appears, it only goes to that first error message.

You need to do it before the Ubuntu logo appears.

---

### Post by 2roombas on 2009-03-08
> **Temposs said:**
> You need to do it before you see Ubuntu start to boot up. See if you can get it.

I don't understand this... I press esc and hold it down immediately after pushing the "on" button of the mini, and it still goes only to that MBR 2FA:

---

### Post by Temposs on 2009-03-09
I found this in the help for the DellMini9 that LowSky posted earlier. Here's how to get into recovery mode:

Booting into Recovery mode

If you have an original Dell Mini 9 with Ubuntu pre-installed, you may have a hard time entering the GRUB menu as the default delay is zero. This is particularly problematic if you're trying to reset your password using the passwd command.

You can enter the recovery mode following these steps:

   1. Boot the mini 9 while pressing ESC every second
   2. When you see the "MBR 2FA:" prompt or similar, the boot process is stopped.
   3. Press ENTER and ESC very fast one after the other.
   4. You should then see the GRUB menu. Using the up and down arrows, highlight the second option and press ENTER to boot into recovery mode.

---

### Post by 2roombas on 2009-03-09
hmmm... while pressing esc. a "boot Menu" popped up.   The options are....

Hard Drive
CD/DVD/CD-RW
Removeable Devices
Network Boot
Diagnostics

I see no recovery option.

---

### Post by Temposs on 2009-03-09
That doesn't look right...did you follow the instructions in my most recent post?

---

### Post by miegiel on 2009-03-09
> **2roombas said:**
> hmmm... while pressing esc. a "boot Menu" popped up.   The options are....

Hard Drive
CD/DVD/CD-RW
Removeable Devices
Network Boot
Diagnostics

I see no recovery option.

That looks like a BIOS boot menu to select a boot device. It's definitely not the grub menu

I guess you'll need to try it a few times till you time it right. It's a bit hard to explain when is the right moment, only that when you see the ubuntu logo you just missed it :twisted:

---

### Post by 2roombas on 2009-03-09
> **Temposs said:**
> That doesn't look right...did you follow the instructions in my most recent post?

One more press of esc and I got to that MB4 2FA:.  I have been trying the enter/esc method you suggested "over and over" and sill cannot get that GRUB menu.  Why the (bleep) does Dell make it so difficult to get to?  I will continue trying.... sigh...

---

### Post by LowSky on 2009-03-09
ok you dont hit escape right when the thing starts... give it a second let the bios start up screen go by.... then hit ESC before the ubuntu load screen pops up

---

### Post by 2roombas on 2009-03-09
Ah-ha... got it!  (happy-dance) :D

---

### Post by miegiel on 2009-03-09
cheers \\:D/ good luck on the rest

---

### Post by 2roombas on 2009-03-09
It worked, I'm in!  Thank you so you so very much for helping me with this!  :D

---

