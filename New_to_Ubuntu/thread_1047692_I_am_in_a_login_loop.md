---
title: "I am in a login loop"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by BA Dawg on 2009-01-22
When I get to the login screen I enter my username then password just to return to the login screen, This is not a new install. How do I get around this or reset my password. Please be specific I am still on the lower side of the learning curve. I am running Ubuntu 8.10
Thanks 

John

---

### Post by Carl Hamlin on 2009-01-22
> **BA Dawg said:**
> When I get to the login screen I enter my username then password just to return to the login screen, This is not a new install. How do I get around this or reset my password. Please be specific I am still on the lower side of the learning curve. I am running Ubuntu 8.10
Thanks 

John

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

To be frank, there may not *be* a practical way around it - it sounds very much as though you've forgotten your password. If you have, you'll have to start tallying up the monetary value of the data you've locked yourself out of, and see if it's worth taking the drive to a professional data retrieval company.

What I'd do in this instance is to boot from the LiveCD and attempt to mount the drive. If it refuses your password there, you're in trouble. If it doesn't, then you've got more options available than if you've forgotten your password.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAkl4+vsACgkQyLm4ydrABvfPGwCg3bIVYu+UVdL0K1iFFd4pKroS
LjYAnifgAtDAfJvBdl97Pepez6NXKLTK
=ADEH
-----END PGP SIGNATURE-----

---

### Post by DezSP on 2009-01-22
I'm guessing you're getting a bad user/pass error? There can be other problems than your password being set wrong, but you can reset it as follows:

Reboot the machine, when the GRUB menu appears (you might need to mash ESC), choose recovery mode.

This should take you to a root prompt, i.e. root@yourcomputer:/#. If it doesn't, you may need to choose an option to drop to a recovery console, command line or similar (they changed this around so I'm not certain :().

Type in:

```
passwd yourusername
```

And follow instructions. :)

---

### Post by markbuntu on 2009-01-22
When you get to the login screen there is a little icon in the lower left corner, click on it and change your session to gnome safe mode and log in. See if that works.

---

### Post by BA Dawg on 2009-01-22
> **DezSP said:**
> Reboot the machine, when the GRUB menu appears (you might need to mash ESC), choose recovery mode.

This should take you to a root prompt, i.e. root@yourcomputer:/#. If it doesn't, you may need to choose an option to drop to a recovery console, command line or similar (they changed this around so I'm not certain :().

Type in:

```
passwd yourusername
```

And follow instructions. :)

When I do this I get 

Segmentation fault

John

---

### Post by BA Dawg on 2009-01-22
> **markbuntu said:**
> When you get to the login screen there is a little icon in the lower left corner, click on it and change your session to gnome safe mode and log in. See if that works.

Thanks Mark

But got the same results.

John

---

### Post by DezSP on 2009-01-22
Erk. That might be a corrupt file or something. Has your machine had any problems recently? Power loss or anything like that?

---

### Post by BA Dawg on 2009-01-22
> **DezSP said:**
> Erk. That might be a corrupt file or something. Has your machine had any problems recently? Power loss or anything like that?

None that I am aware of

---

### Post by BA Dawg on 2009-01-23
Will I have to reinstall or is there a way around not being able to login????

John

---

### Post by chuckyp on 2009-01-25
I'm also stuck in a loop just like this. I can't even log in via console or ssh just loops. I can go to recovery mode and su my user but if I try to reset the passwd for my user I get a segfault. If i type in the wrong password for my user I get an auth failure. This behavior is really bizarre

---

### Post by timbellomo on 2009-02-03
I'm having the same problem.  I've had no strange power outages or anything.  I shutdown last night, and today I can't log in.  It's not a password failure, as when I type an incorrect password it tells me.  If I type the correct password, it just displays the login again.

---

### Post by djbushido on 2009-02-03
okay, at login screen try this:
press CTRL-ALT-F2
This will give you a text only screen. Try logging in here.
Also, from another linux machine (or livecd) try doing ```
fsck /dev/sdXY
``` where /dev/sdXY is the letter of your drive.
Let me know if it doesn't work!

---

### Post by timbellomo on 2009-02-03
Login from the terminal fails as well.

I _can_ boot to recovery mode.  I ran the "check for corrupt packages" option, and it moved to upgrade brasero. Coincidentally (or not), Brasero was acting up last night, creating coasters, so I switch over to K3B and it worked fine.  Not sure if it's related to my login failure.  I couldn't update... recovery mode didn't load eth0 so I couldn't get the packages.

Subsequently, I ran fsck from recovery.  I left it running and went to work as it looked like it was going to take quite some time (250GB drive) - not sure if that's normal.

I'll update the thread with results.

---

### Post by djbushido on 2009-02-03
ok, try doing this from a live cd. This way, you don't have to mount the drive (which is what I think you are doing from recovery, which may cause errors), and many packages are installed in the livecd, like brasero. You might have to force a different version, but it won't be corrupt.

---

### Post by bapoumba on 2009-02-03
Another option is that your / or /home (if on a different partition) are full. From recovery mode, please run 
```
df -H
```
To see if that is the problem.

---

### Post by djbushido on 2009-02-03
> Another option is that your / or /home (if on a different partition) are full. From recovery mode, please run 

```
df -H
```
To see if that is the problem.
+1, totally didn't think of that.

> J'aime les fraises.Moi aussi.

Anyway, can you also see if you can post some system logs or something? (I believe it is /var/log/syslog - don't quote me)

---

### Post by timbellomo on 2009-02-03
fsck completed.  I think it said something like 3.9% non-contiguous.  

I removed brasero and re-ran the package check - it didn't try to upgrade anything, so I don't think it's a corrupt package...

df -H: showed 51% utilization on /. 1% or less on other entries.  Did throw "No such file or directory" on /proc/bus/usb/.usbfs... not sure if that matters.

Is the consensus that I completely re-install?  Is there a "repair essential files" option through the liveCD.  I'm comfortable re-installing, but I would prefer to try to get to the bottom of it in order to help others out in the future.

Thanks,
Tim

---

### Post by djbushido on 2009-02-03
Did you try and reboot to make sure this didn't fix it?
Also, can you post the output of this command:
```
sudo cat /etc/fstab
```
Doing this will tell me whether or not when errors are found on drive whether or not it will mount read only. When it's read only, the authorization file can't get written, thus GDM and X.org crashes. This is currently happening to me.

EDIT: NO, DO NOT reinstall yet. Only if no other cause can possibly be found should you reinstall. Not yet.

---

### Post by timbellomo on 2009-02-03
Yeah, rebooted.

sudo cat /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
# /dev/sdc1 UUID=... / ext3 relatime,errors=remount-ro 0 1
# /dev/sdc5 UUID=... none swap sw 0 0
/dev/md0 /media/Storage xfs
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
non /proc/bus/usb usbfs auto,busgid=126,busmod=0775,devgid=126,devmode=0664 0 0

```

I tried hitting Ctrl+Alt+Backspace at the login window to see what would happen.  It popped up with a black screen and "The greeter application appears to be crashing. Attempting to use a different one."  This popped up twice.  Shortly thereafter, I received: "The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting 2 minutes before trying again on display :0".  It froze there.  I could try the terminals (1-6), but the login loop persists.

---

### Post by djbushido on 2009-02-04
Okay, try this:
```
sudo nano /etc/fstab
```
This will open up a text browser window, allowing you to remove the section where it says "errors=remount-ro"
This is only a temporary test fix, and if it works should NOT stay.
Try taking out this line, and see what happens.

---

### Post by timbellomo on 2009-02-04
No change unfortunately.

I also got networking up in recovery mode, then re-invoked /usr/share/recovery-mode/recovery-menu and ran the dpkg corrupt packages item.  It repaired a few files (brasero and cups).  Optimistically, I rebooted.  No change.  As soon as I enter the password and hit enter, the screen flashes brown (like the desktop) then black (as though I'd hit Ctrl+Alt+Bkspc) and reloads the login screen.

I wanted to mention that I'm also receiving the Segmentation fault when running passwd *username* in recovery mode.  Not sure if that information is useful.

---

### Post by djbushido on 2009-02-04
Okay. So just to make sure, after my instructions you are trying to boot into normal mode? Not recovery? And it still isn't working after taking out errors=remount-ro?

Okay then. If so, I am officially stumped. I wouldn't reinstall just yet by any means. Wait and see if someone else has an idea, maybe get on IRC. Someone there will likely have an answer. If not, I can't think of anything else. Sorry...

---

### Post by timbellomo on 2009-02-04
Yes.  I've tried rebooting into normal mode with no luck.  Which IRC Channel would you suggest? I've never tried Ubuntu help through IRC before.

Thanks anyway!

EDIT: Nevermind, found #ubuntu on irc.freenode.net

---

### Post by timbellomo on 2009-02-04
grep "error" /var/log/syslog contained:

```
...error 4 in pam_smbpass.so...
```

I traced that to a problem with samba referenced here:
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458)

So I purged samba packages, removed /var/lib/samba, re-created it, then reinstalled samba...

And that fixed it.

Reconfiguring samba won't be too rough, though I wish I knew what messed it up in the first place.

Thanks All!

---

### Post by djbushido on 2009-02-05
Fixed at last?
Sweet!

---

### Post by Got wick? on 2009-02-28
Hi!

Ubuntu/Linux newbie here....I get this login loop too, it it the new install of AMD64 version, have tried 8.04 and 8.10, both AMD64 versions give me the same loop, only sometimes it gets to the desktop, which is completely blank except for the background graphic. (a bird of some type...heron perhaps?)

Anyway, the i386 version worked fine, but I need databases, and they all said they couldn't work on a 386 machine..  The other thing with the i386 version is I couldn't get online, the wireless adapter showed up on startup, but couldn't connect to the network, even though it could see it and I am sure I entered the correct key, even tried with no security and same results...

I could sure use some help, since I don't want (can't) use Windows anymore!

Thanks in advance....oh and ps: bump please?

Doris
gotwick.com

---

### Post by timbellomo on 2009-03-02
Doris (GotWick),

Not sure that's exactly the same behavior I was experiencing.  Are you able to log in from the console?  

To find out, Ctrl+Alt+F2 should drop you to a full text login where you can try.  Does it simple give you the login prompt again (without an "Incorrect password" message)? Or does it log in and show you something like "doris@computer-name:~$" ?

-Tim

---

### Post by NathanaelCulver on 2009-07-09
Anyone ever figure this one out? Running Jaunty on a laptop which lost power a couple of days ago. Now I'm stuck in this same login loop.

I can open a terminal (Ctrl-Alt-F2) and log into any of my user accounts, including root, but logging into the graphical screen just gets me a black screen, a brief flicker, then back to the login screen. No "login failed message", so it's not a credentials problem.

In my Sessions Type menu I have the following: Default, GNOME, GNOME/Openbox, KDE, KDE/Openbox, Openbox Session, Secure Remote Connection, Window maker, and Failsafe. I get the same loop no matter which one I try (except SRC, which gives me "Login failed"), so it's not Gnome- or KDE-specific.

Someone up-thread mentioned checking whether the home dir is full. Mine is; in fact, I was in the process of cleaning it out when I lost power.

I don't know where to go from here.

NathanaelCulver

---

### Post by NathanaelCulver on 2009-07-09
bump

---

### Post by NathanaelCulver on 2009-07-10
bump. NE1?

---

