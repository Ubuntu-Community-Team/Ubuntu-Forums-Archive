---
title: "Can't Connect to the Internet or to My External Hard Drives - Help!"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by LINDSAYT on 2008-12-20
Hi!  I'm having serious issues now with my Ubuntu partition.  I have Windows running on 10GB of my hard drive and Ubuntu on the other 50GB.

A few months (maybe many months) ago I lost my ability to connect to the internet.  I couldn't find the icon to find my available wireless connections, and my search for them through adding stuff to the top toolbar on the desktop came up with nothing.

I logged on to the Ubuntu partition to take screen shots so that I could post them here but when I tried to save the files to two different drives (a 240 GB external hard drive and a 1 GB flash drives), the system came back saying:

Cannot Mount Volume
Error org.freedesktop.Dbus.Error.AccessDenied

So now that's my first problem, that I can't access my hard drives so that I can post the screen shots of the errors I'm getting when I try to figure out how to connect to the internet.

As far as connecting to the internet or finding my wireless connections, etc, I know that I get to a certain point where I have to enter my admin password (I'm the only user, have been the only user), and it tells me Access Denied.

Please Help!  My Windows partition was never meant to do all the stuff I wanted or intended to do with Ubuntu

Lindsay

PS:  I'm not a terminal person, but if you give me specific directions I can follow, so please go easy with me : )

---

### Post by taurus on 2008-12-20
Make sure you have an external device plugged in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
dmesg | tail
```

---

### Post by Dedoimedo on 2008-12-20
Terminal person, I like it.

First, what it says in the Hitchhiker's Guide? Don't panic.

Can you please do the following:

Boot into Windows. Plug in the external drive. Unplug it safely.
Boot into Linux. Plug in the external drive. See what comes up.

Once we're past that stage, we'll try a "terminal" trick to get the drive mounted.

Can you use the administrator (sudo) password in other cases, or have you completely forgotten/lost it?

Dedoimedo

---

### Post by OllieGab on 2008-12-20
I'm more or less a total newbie so my advise may not get you very far but when I had a similar problem, ie getting Ubuntu to recognise my external harddrive, I had to go into Windows, go to the device manager, right click on the harddrive device and select 'disable'.
Then close down Windows the normal way.
After that Ubuntu had no problems recognising my external hardrive.

Ollie

---

### Post by LINDSAYT on 2008-12-20
Hi!  Thanks for your help!  Not panicking yet, considering it took me a couple months to even get in here and try to trouble shoot the issue.

I ejected both disks from windows, unplugged and then reboot my computer to the Ubuntu partition.  When I logged in, I plugged in each drive on their own and still got the same warning message!  I was really hoping it would be that easy!  Anyway, I'm back in Windows now and I plugged each drive in again and Windows is detecting them and I can see the files, so nothing wrong with the drives themselves.

Plan B?

---

### Post by OllieGab on 2008-12-20
You could always stick the files you want on a USB stick, I suppose.
While you're still in Windows and then retrieve them when back in Linux.

Ollie

---

### Post by LINDSAYT on 2008-12-20
OllieGab - I have a USB stick that Ubuntu's not recognizing.  The screenshots are on Ubuntu, I'm trying to get them to Windows so I can post them to the forums and get help on my internet/connection problems.

---

### Post by meistercobbman on 2008-12-20
I'm having the same issue with my friend's laptop. Both our ipod's won't connect to her Ubuntu laptop, but they work on mine (i'm running xUbuntu).

The error says: org.freedesktop.DBus.Error.AccessDenied.
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file.... blah blah blah

Is this a permissions issue? fdisk -l on her computer shows her ipod under /dev/sdb1 with system W95 FAT32

Should i just chmod it? 

Second issue (possibly related): On her computer, I CAN'T access anything for the system, i.e. going to System->Administration->Network gets the following error: "The configuration could not be loaded. You are not allowed to access the system configuration."

The same error happens when I go to "Users and Groups."

Okay, that was kinda 2 problems on one post, but I think they are related to each other. If not, I can make a different thread. I appreciate any help on these.

---

### Post by taurus on 2008-12-20
> **meistercobbman said:**
> I'm having the same issue with my friend's laptop. Both our ipod's won't connect to her Ubuntu laptop, but they work on mine (i'm running xUbuntu).

The error says: org.freedesktop.DBus.Error.AccessDenied.
A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file.... blah blah blah

Is this a permissions issue? fdisk -l on her computer shows her ipod under /dev/sdb1 with system W95 FAT32

Should i just chmod it? 

Second issue (possibly related): On her computer, I CAN'T access anything for the system, i.e. going to System->Administration->Network gets the following error: "The configuration could not be loaded. You are not allowed to access the system configuration."

The same error happens when I go to "Users and Groups."

Okay, that was kinda 2 problems on one post, but I think they are related to each other. If not, I can make a different thread. I appreciate any help on these.

Are you the original user on your machine, the one that you created during the installation?  What's the output of this command from a terminal?

```
id
```

---

### Post by LINDSAYT on 2008-12-20
> **taurus said:**
> Make sure you have an external device plugged in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
dmesg | tail
```
I did this.  It said for both eth0 and eth1 Link is not ready

---

### Post by meistercobbman on 2008-12-20
> Are you the original user on your machine, the one that you created during the installation? What's the output of this command from a terminal? id

Here's what I got:
```
uid=1000(cobbman) gid=1000(cobbman) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),1000(cobbman)

```

---

### Post by meistercobbman on 2008-12-20
p.s. it's the same way on her computer as well

---

