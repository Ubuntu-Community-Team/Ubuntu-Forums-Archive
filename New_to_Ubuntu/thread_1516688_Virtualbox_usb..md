---
title: "Virtualbox usb."
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Vege 4wd on 2010-06-24
Hi all, after a bit of advice for virtualbox.
Host is Lucid. Guest is xp.
I have installed the latest version of vb from the web and not the repositories. 
Have enabled usb and set up a filter for the guest. Still the guest does not recognise the device. It comes up as faded in the device tab.

Anyone have a script for the command line that would enable the guest xp to recognise the usb device?

---

### Post by yeleek on 2010-06-24
Checked the basics?

Is guest running XP SP2+?

and

Have you carried out the following

```
sudo usermod -aG vboxusers <your username>
```

---

### Post by Vege 4wd on 2010-06-24
Hi yellek,
             yes it is service pack 2. I also ran the code. Still the same though. In device tab the device is still faded along with the other usb devices that I have not set up a filter for.

Just a quick check. By username you mean the username  I log into host with?

---

### Post by yeleek on 2010-06-24
username = your ubuntu host username.

if complete from a terminal type

```
groups <your ubuntu username>
```

Should list vboxusers

---

### Post by Vege 4wd on 2010-06-24
I ran the code and got this:  aaron adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare vboxusers

---

### Post by yeleek on 2010-06-24
Thats right - according to what I've done in the past it should only require vboxusers and XP SP2+ in the guest.  This is with Virtualbox from SUN (oracle now), rather than the OSE.

Sure the filter is right?  Thats the only thing I can think of.  (you did let windows install the drivers from vb didn;t you?)

---

### Post by Vege 4wd on 2010-06-24
Well, no i didnt. How do I do that? I dwonloaded the drivers for device within guest.

---

