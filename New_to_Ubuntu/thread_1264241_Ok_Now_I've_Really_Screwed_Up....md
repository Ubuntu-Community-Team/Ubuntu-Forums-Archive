---
title: "Ok Now I've Really Screwed Up..."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Marlowe221 on 2009-09-11
Well I seem to have removed myself from some kind of group. I cannot change any setting now....

I was trying to get this thing to let me edit the alsa-config file to try to get my soundcard to work. It told me I didn't own the file and couldn't edit it. I went to Users and Groups and and played around a bit and now I can't even open that window back up!

Any ideas?

---

### Post by Marlowe221 on 2009-09-12
Edit: I have managed to regain access to the GUI administrative panels through use of the terminal. However, when I click on the unlock panel in the user and groups panel it locks up on me every time. Any way around this???

---

### Post by Whiffle on 2009-09-12
the command is "adduser <username> <group>"

And on my laptop, my user is in the following groups:
<username> adm dialout cdrom audio video plugdev fuse lpadmin netdev admin sambashare

---

### Post by Whiffle on 2009-09-12
Oh I think we can fix this :)

the command is "adduser <username> <group>"

And on my laptop, my user is in the following groups:
<username> adm dialout cdrom audio video plugdev fuse lpadmin netdev admin sambashare

---

### Post by Whiffle on 2009-09-12
Oh I think we can fix this :)

the command is "adduser <username> <group>"

And on my laptop, my user is in the following groups:
<username> adm dialout cdrom audio video plugdev fuse lpadmin netdev admin sambashare

---

### Post by shae on 2009-09-12
You should try the following as root:

```
useradd -G users,audio,lp,optical,storage,video,wheel,power,hal,dbus *youraccountname*
```

If this does not work, you could just create a new user with

```
adduser
```

as root and enter the information it asks for.  Afterwords, transfer the stuff from your old account and remove it.

---

### Post by Whiffle on 2009-09-12
EDIT:  Whoops...post trifecta!

---

### Post by Wim Sturkenboom on 2009-09-12
As normal user, can you issue the id command in a terminal and post the resuilt. Mine looks like below.
```
wim@aao:~$ **id**
uid=1000(wim) gid=1000(wim) groups=4(adm),20(dialout),24(cdrom),46(plugdev),106(lpadmin),121(admin),122(sambashare),1000(wim)
wim@aao:~$ 

```

With regards to future permission issues: when you get a message that you don't own the file or a permission denied, the normal way to override that is to use sudo in front of the command if you're in a terminal (e.g. *sudo vi /etc/X11/xorg.conf*).

---

### Post by Marlowe221 on 2009-09-12
Ok thanks I'll try this stuff and let you know....

And all this just trying to get some sound out of this thing

It says this:
micah@micah-laptop:~$ id
uid=1000(micah) gid=121(admin) groups=20(dialout),26(tape),121(admin)
micah@micah-laptop:~$

---

### Post by Whiffle on 2009-09-12
> **Marlowe221 said:**
> Ok thanks I'll try this stuff and let you know....

And all this just trying to get some sound out of this thing

Yeaaaah :)  It happens.

[img]http://imgs.xkcd.com/comics/success.png[/img]

---

### Post by Marlowe221 on 2009-09-12
I hear you man. I'm trying to mod the permissions on alsa-base.conf so I can add some line that MIGHT just let me listen to a song or hear a youtube vid....

But no matter what I do those permissions are greyed the hell out...

---

### Post by Marlowe221 on 2009-09-12
Ok that's weird - I've got sound out of the headphones but can't get it out of the main laptop speaker.... Any suggestions?

---

### Post by LewRockwell on 2009-09-12
> **Marlowe221 said:**
> Ok that's weird - I've got sound out of the headphones but can't get it out of the main laptop speaker.... Any suggestions?

for the lesser technically-inclined, it should be noted that, the normal output jack(sometimes called the headphone jack...sometimes denoted with the "headphones" symbol...sometimes denoted with the "speaker out" symbol) must not have anything plugged into it if the main speakers are located internally in the device

the reason for this is that the standard jack for these particular devices utilizes a disconnect so that when something is plugged into the jack...the internal speakers are disconnected(and then therefore silent...as they should become when headphones are plugged in for the benefit of others who might enjoy some quiet)

.

also, with respect to your hearing the output via the headphones, but not the speakers...this is sometimes due to the headphones ability to operate with just the unamplified signal, whereas the speakers need amplification to be driven to produce detectable sound

.

---

### Post by Marlowe221 on 2009-09-12
FIXED!!! I had been doing Google searches based on the name of the sound card, but a Google search on the model of my HP laptop proved more fruitful. All it took was adding a certian command to alsa-base.conf and it worked like a charm!
 
If you have an HP DvX (X=various numbers) run a Google search for your model number with the phrase "no sound" and you'll find a helpful ubuntuforums.org thread on the subject. There were a few suggestions since there are several variants of this model laptop but after trying two or three  different edits to alsa-base.conf it worked great.
 
I'm really enjoying this process - I'm learning a lot about how Linux works and how to use the terminal (I had to do this in the terminal, it wouldn't let me in the GUI for some reason...). I'm not sure I'll ever learn to program per se, but the idea of building up an OS just for me is pretty cool!
 
Thanks for all the help, hopefully I'll be able to return the favor as I learn more about Linux and Ubuntu. :)

---

