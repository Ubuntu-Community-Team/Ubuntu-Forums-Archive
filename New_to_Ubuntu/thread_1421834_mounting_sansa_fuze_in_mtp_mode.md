---
title: "mounting sansa fuze in mtp mode"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by potato_head on 2010-03-04
i saw this on a INTERNET site but i don't know how to use it on my sansa fuse.
this is the command for the sansa view


This was a bit buggy for me, but you can try. Using mtpfs (uses FUSE) you can mount your device in MTP mode and browse like any other file system

Mount:sudo mtpfs -o allow_other /media/SansaView

please tell me the command in the terminal for the sansa fuze.:popcorn:

---

### Post by Jordanwb on 2010-03-04
```
sudo mtpfs -o allow_other /media/SansaView
```

;)

To make it writable (for your user):

```
sudo chown -R {your_username} /media/SansaView
```

I wrote a udev rule (which I can provide if you wish, that automounts my Creative ZEN but mtpfs is broken on lucid.

---

### Post by Jose Catre-Vandis on 2010-03-04
I use MSC USB mode as opposed to MTP for both  our Sansa Fuze and Sansa 260, and in Xubuntu with Thunar it just connects up on plug in, no need to run any mount commands. Try MSC.

---

### Post by Jordanwb on 2010-03-04
Using MSC mode will be easiest. Unfortunately for me, my ZEN doesn't have MSC mode. :(

---

### Post by potato_head on 2010-03-05
> **Jordanwb said:**
> ```
sudo mtpfs -o allow_other /media/SansaView
```;)

To make it writable (for your user):

```
sudo chown -R {your_username} /media/SansaView
```I wrote a udev rule (which I can provide if you wish, that automounts my Creative ZEN but mtpfs is broken on lucid.


tried them in ubuntu 9.10 and they don't work.
username? do you mean username for ubuntu?

---

### Post by Jordanwb on 2010-03-05
> **potato_head said:**
> tried them in ubuntu 9.10 and they don't work.
username? do you mean username for ubuntu?

No your username that you login with.

---

### Post by potato_head on 2010-03-05
> **potato_head said:**
> tried them in ubuntu 9.10 and they don't work.
username? do you mean username for ubuntu?

will the sansa view command work with the sansa fuse, it didn't .

---

### Post by anthro398 on 2010-03-31
> **Jordanwb said:**
> 
I wrote a udev rule (which I can provide if you wish, that automounts my Creative ZEN but mtpfs is broken on lucid.

Can you elaborate on this comment.  I'm using a Sansa Fuze on 9.10 and my mtp seems to not work correctly.  My external doesn't seem to be recognised and, well, there are a bunch of issues.  I'd use MSC but it's really , really slow to scroll through songs after I transfer music that way.

---

### Post by Jordanwb on 2010-03-31
Here is the udev rule I wrote:

```
ATTR{idVendor}=="041e", ATTR{idProduct}=="4157", RUN="/usr/bin/sudo -U jordanwb /bin/mount /media/Zen"
```

jordanwb is your username (in case mine). /media/Zen is the mount point. You need to find the idVendor and idProduct by running "lsusb -v" and look in the output for your Fuse. Put it in /etc/udev/rules.d/45-mtp-dev.rules

Also in /etc/fstab put this:

```
mtpfs	/media/Zen	fuse	noauto,user	0	0
```

in /etc/fuse.conf put this:

```
user_allow_other
```

You may need to chown the mountpoint to be owned by your user. I can't remember. Hope that made sense.

---

