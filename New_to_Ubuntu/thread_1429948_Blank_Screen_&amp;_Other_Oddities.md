---
title: "Blank Screen &amp; Other Oddities"
date: 2010-03-14
forum: New to Ubuntu
---

### Post by lovetraxx on 2010-03-14
Hi Everyone!

I'm pretty new at this (installed Ubuntu about 1 yr ago) so go easy on me :] 

I'm on my laptop, a Dell XPS M1505 
Here's some extra stats in case it helps:
Intel Core 2 Duo 2.0Ghz 
4GB Ram
32-bit OS
Nvidia GeForce 8400m GS

Got Windows 7 and Karmic Koala and upgraded to Grub 2 a while ago. 

Windows boots fine, but Karmic has different problems every time. Sometimes it will boot all the way to the login screen with the error: "error initiating conversation with authentication system - general failure"

Other times it will boot  to a blank/black screen after the cursor in the upper left hand side of screen blinks for a bit. And when I try another kernel, it leads to a flickering white screen with multicolored lines. 

Thanks in advance.

edit: I can boot from the live cd and can get to the login screen but still get the message: "error intiating..."

---

### Post by lovetraxx on 2010-03-15
anyone?

---

### Post by user333 on 2010-03-15
Maybe your live cd is bad? I had a problem with 9.04 where I couldn't install it because it was corrupt. Maybe try re-installing the nividia drivers too

---

### Post by cerealtx on 2010-03-15
> **matbence said:**
> I was (JUST SOLVED IT A MINUTE AGO!!!) having the same problem. I saw on another post [elsewhere]("http://ubuntuforums.org/showthread.php?t=1271821") that the problem is due to trying to disable the keyring manager prompt. I'm a bit of a noob, but I really didn't want to have to reinstall ubuntu (I had spent ages getting it working perfectly for me).
Reversing changes caused by trying to disable the keyring prompt restored the login. For reference trying to access the /etc/pam.d/gdm file from my windows partition using installable ext2 file system didn't work.
I managed to delete the '@include common-pamkeyring' line through the terminal when booting from a live CD.
Then because I am such a newbie to linux I uninstalled the libpam-gnome-keyring package using my synaptic package manager instead of using a terminal.

Hope this helps you

google ftw

---

### Post by lovetraxx on 2010-03-28
> **Gionani7 said:**
> I got this ERROR shortly after trying to eliminate the need to enter my keyring for the network applet. This ("error initiating conversation with authentication system") at the login screen. I want to note some things.
-Im running 64 bit 9.10 Ubuntu
-I used (@include common-pamkeyring)
-I disabled the autologin option prior to restarting my desktop
-I could not log back in through graphical interface.
So at this point what I did was this.
Restart
Held "Esc"
Entered the root shell
And entered this command: sudo nano /etc/pam.d/gdm

I deleted the line(@include common-pamkeyring)

Hit "F3" to save

Hit "F2" to exit 

Ran command: sudo reboot

Now I was able to login regularly through the graphical interface.

HOPE THIS HELPS THOSE WHO FIND THEMSELVES AT THESE ODDS.

My Question is, Is there any way I can stop having to enter my keyring without going through this again with 9.10 Ubuntu??? HELP PLZ

So I tried this, but after I deleted the line, and then when I tried to save the file, it says "[Error Writing /etc/pam.d/gdm: Read-Only file system]" 

Hopefully I can fix this keyring problem because I need my Ubuntu back soon. Any help would be awesome.  :]

---

### Post by lovetraxx on 2010-03-28
still nothing. Anyone?

---

### Post by anewguy on 2010-03-28
> **lovetraxx said:**
> still nothing. Anyone?

Did you put the "sudo " in front of the edit command as mentioned?  The root user owns this file and you can't write to it (hence the read-only file stuff) unless you are root or use "sudo " in front of the command to run it as root.

Dave ;)

---

### Post by lovetraxx on 2010-03-28
> **anewguy said:**
> Did you put the "sudo " in front of the edit command as mentioned?  The root user owns this file and you can't write to it (hence the read-only file stuff) unless you are root or use "sudo " in front of the command to run it as root.

Dave ;)

Yup, I wrote it just as its written there.. I feel like I am missing something super easy.. hah 

I hit ESC, and wait for the little command line to pop up, and then type in the command just as its written :]

---

### Post by anewguy on 2010-03-28
Do the ESC thing to get to a command (terminal) window, then do the following:

cat /etc/pam.d/gdm <press enter>

copy the output and post it back here.


Dave :)

---

### Post by lovetraxx on 2010-03-29
> **anewguy said:**
> Do the ESC thing to get to a command (terminal) window, then do the following:

cat /etc/pam.d/gdm <press enter>

copy the output and post it back here.


Dave :)

#%PAM-1.0
auth requisite    pam_nologin.so
auth required    pam_env.so readenv=1
auth required    pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth     optional   pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required   pam_limites.so
@include common-session 
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional   pam_gnome_keyring.so  auto_start
@include common-password
@include common-pamkeyring




man I had to type that verbatim, because I have no idea how to copy it. Good thing I can type quick.. whew! ;)

---

### Post by anewguy on 2010-03-29
When the grub menu appears at boot, are you able to select the recovery mode option and get in?  After selecting recovery mode, a little menu will come up - select the one that says something like root console.

If so:

cd /etc/pam.d

nano gdm

remove the line as suggested

hold down CTRL and press the O (that's "oh" key)

hold down CTRL and press the X key to exit

shutdown -r now

You don't need to use "sudo" if you get in via recovery mode as it logs you in as a root user anyway.

Dave ;)

EDIT:  Additionally, you may want to boot the LiveCD you installed from, be sure the existing partition is mounted, and just use sudo gedit to edit the gdm file on your existing partition.  You would have no problems with authentification as long as you run from the LiveCD to do so.

---

### Post by lovetraxx on 2010-03-31
> **anewguy said:**
> When the grub menu appears at boot, are you able to select the recovery mode option and get in?  After selecting recovery mode, a little menu will come up - select the one that says something like root console.

If so:

cd /etc/pam.d

nano gdm

remove the line as suggested

hold down CTRL and press the O (that's "oh" key)

hold down CTRL and press the X key to exit

shutdown -r now

You don't need to use "sudo" if you get in via recovery mode as it logs you in as a root user anyway.

Dave ;)

EDIT:  Additionally, you may want to boot the LiveCD you installed from, be sure the existing partition is mounted, and just use sudo gedit to edit the gdm file on your existing partition.  You would have no problems with authentification as long as you run from the LiveCD to do so.

Hi Dave, 
thanks for all of the quick replies. I tried recovery mode with no luck. It loaded normally but the screen became scrambled in red chunks. Hard to explain, I know but I can't access the recovery menu properly. How frustrating! I'll try the Live CD thing and get back you soon.

---

