---
title: "I need to have windows boot first"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Papa-san on 2009-06-01
If I am going to be able to keep Ubuntu on this laptop, I need to be able to have the first option in GRUB to be for it to boot into Vista. It's my wife's computer, and she is frustrated by the fact that if she turns it on and walks away, she returns to find it running Ubuntu. I want it to be able to go into windows unless I choose to go into Ubuntu.

If I can do this while I try to figure out how to fix the wireless issue [[SIZE="4"][COLOR="Red"]here[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=1175716"), I will eventually be able to get her to convert to Linux. 
So, please let me know what I need to do in order to accomplish this. 

I currently have that system running a 'Live' session of Ubuntu.
Thanks!

---

### Post by philinux on 2009-06-01
If you are new to to this then the simplest way is to install startupmanager.

System>admin>synaptic. Search startupmanager. Once installed it appears in system>admin. Then choose which boots first, ie default OS. Dead easy gui.

---

### Post by Cypher on 2009-06-01
Hit ALT-F2 and then the command
```

gksu gedit /boot/grub/menu.list

```
Enter your password and this will bring up the GRUB menu file. The first option there is "default 0" which indicates which of the boot options should be booted by default.

You can change that to "default saved" to boot the latest saved option. But in your particuilar case you should change it to "default X" where X is the specific number at which XP shows up in the list.

By default Ubuntu will create 3 entries (normal, recovery-mode and memtest86+). So Windows will show up after that, in this case you want "default 3" (the fourth entry starting the counting with 0) to always boot XP unless you specifically choose Ubuntu in the GRUB menu..

---

### Post by Mornedhel on 2009-06-01
> **Cypher said:**
> By default Ubuntu will create 3 entries (normal, recovery-mode and memtest86+). So Windows will show up after that, in this case you want "default 3" (the fourth entry starting the counting with 0) to always boot XP unless you specifically choose Ubuntu in the GRUB menu..

Wouldn't this break after every kernel upgrade ? I don't think the upgrade is smart enough to keep track of which line is what ?

---

### Post by Cypher on 2009-06-01
> **Mornedhel said:**
> Wouldn't this break after every kernel upgrade ? I don't think the upgrade is smart enough to keep track of which line is what ?
Yes, it certainly would..I suppose Philinx's approach might be a more fool-proof way of doing this..

---

### Post by Papa-san on 2009-06-01
Thanks!
I used the startup manager option, and it worked flawlessly.
Now I can fiddle around with the network issues at my leisure until I get it hammered down. Then I'll see if she'll try using the Ubuntu again!

I sure would like to get the Vista Virus off of this machine at some point!

---

### Post by mcduck on 2009-06-01
> **Mornedhel said:**
> Wouldn't this break after every kernel upgrade ? I don't think the upgrade is smart enough to keep track of which line is what ?

No, it doesn't if you also change "# updatedefaultentry=false" to "# updatedefaultentry=true".

Grub definitely is smart enough to keep track of entry lines, users just need to be smart enough to tell it to do so. ;)

---

### Post by egalvan on 2009-06-01
> **mcduck said:**
> No, it doesn't if you also change "# updatedefaultentry=false" to "# updatedefaultentry=true".

Grub definitely is smart enough to keep track of entry lines, users just need to be smart enough to tell it to do so. ;)

Yes, GRUB was designed to be "smarter than the average bear".
It has lots of options, understands lots of different file systems, and can even understand some Microsoft stuff...

But as for the easiest way to make sure Windows boots as default, and no update will break this...

Just put the Microsoft stanza before the Debian stanzas. ;)

Or any other OS you want to default to...

I have an older machine that defaults to Puppy...
the Puppy stanza is above the Debian ones.

---

### Post by Mark Phelps on 2009-06-01
> **Papa-san said:**
> Thanks!
I used the startup manager option, and it worked flawlessly.

Have a similar situation on a "family" machine (doesn't even want to see a menu), so if you haven't done this already, suggest the following:
1) Hide the GRUB menu
2) Change the timeout to something short ( 1-2 seconds)

This way, when you boot the machine, the "press esc ..." message passes by too quickly to be read, but when you are using the machine, you know to press Esc right away to get your GRUB menu.

Just an idea ...

---

### Post by Papa-san on 2009-06-01
How would I go about hiding the GRUB menu?

---

### Post by Didius Falco on 2009-06-01
> **Papa-san said:**
> How would I go about hiding the GRUB menu?

First, back up your current file - you can do this from within Ubuntu, and these instructions are for that. From a Terminal:

```
sudo cp  /boot/grub/menu.lst  /boot/grub/menu.lst.backup
```Then on to the editing:

```
gksu gedit boot/grub/menu.lst 
```The very top of the menu.lst file has options for you to set. Here is that section.

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Blue]timeout        5[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]#hiddenmenu[/COLOR]
```To lower the amount of time before it boots, change the number in the blue section (these colors are just to make it easier for you to see the appropriate parts)
to the desired number of seconds. 2-3 is very fast and still gives you time to intervene when you want to go to Ubuntu.

To hide the menu completely, simply remove the hash (#) in front of the red hiddenmenu section.

This will not show a menu at all.

Personally, I'd go for the low seconds value - unless you are very attentive, you may wind up booting Windows before you can intervene.

Regards,

Didius

---

### Post by Papa-san on 2009-06-01
Thank you!
I'll give it a try!

---

### Post by Didius Falco on 2009-06-01
> **Papa-san said:**
> Thank you!
I'll give it a try!

You are very welcome!

Have another look at my post, though - I made a mistake in the copy command, which I've now fixed. :redface:

Regards,

Didius

---

