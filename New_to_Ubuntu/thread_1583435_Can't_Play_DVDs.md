---
title: "Can't Play DVDs"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Burning_tree on 2010-09-27
Hey,

My name is Bridget and I'm new to Ubuntu.  I installed Ubuntu after my machine got owned.  I had to re-start everything and I didn't have/want to pay for a Windows disc.  I'd heard great things about Ubuntu so I wanted to give it a try.  Unfortunately I've had a lot of problems since I've started to use it. I would be very grateful if folks on this forum could help me.  

I'm not sure where to start, just because things have been such a mess.  I guess I'll start with one very basic and annoying thing.  I can't play my DVDs on Movie Player.

I get an error that says "An error occurred, could not read from resource."  Has anyone seen this before? 

Keep in mind I'm very new to this and didn't know what "sudo" meant until a couple of weeks ago so I hope you'll be patient with me.

---

### Post by Madrias on 2010-09-27
I've seen it, I just can't recall how I made it work.

---

### Post by NightwishFan on 2010-09-27
You need to install libdvdcss. Just install this package, choose the one for your arch:

> Ubuntu 10.04 Lucid 32-bit: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
> Ubuntu 10.04 Lucid 64-bit: [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)

---

### Post by Burning_tree on 2010-09-27
FYI: it will read CDs just fine.  It just hates DVDs.

---

### Post by wojox on 2010-09-27
Try this, open your terminal Applications > Accessories > Terminal and enter

```
sudo apt-get install libdvdread4
```

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then reboot and try playing a CD. :)

---

### Post by NightwishFan on 2010-09-27
DVDs are encrypted is all, and it is not legal for Ubuntu to include the decryption library in the installer.

Edit: The above will work as well. Use that way if you do not have Lucid.

---

### Post by Burning_tree on 2010-09-27
> **NightwishFan said:**
> You need to install libdvdcss. Just install this package, choose the one for your arch:


Tried installing the 32 bit version and got an "internal data flow error" when I tried to play a DVD.

---

### Post by Brandel Valico on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

A handy guide to setting up pretty much all the multi-media you need.

---

### Post by NightwishFan on 2010-09-27
Are you running Lucid?

If not, then run this and then try wojox's way. Forgive me I wanted to give a graphical way for it to work.
```
sudo apt-get purge libdvdcss2
```

If you ARE running lucid run:
```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Burning_tree on 2010-09-27
It says that I need the plugin "DVD subpicture decoder", but that the plugin isn't available.  

:icon_frown:

---

### Post by wojox on 2010-09-27
> **Burning_tree said:**
> It says that I need the plugin "DVD subpicture decoder", but that the plugin isn't available.  

:icon_frown:

Open Synaptic Package Manager and search for

```
gstreamer-plugins-bad
```

Mark it for installation. It may want to pull in some dependencies as well, that's ok.

---

### Post by Burning_tree on 2010-09-27
> **wojox said:**
> Open Synaptic Package Manager and search for

```
gstreamer-plugins-bad
```

Mark it for installation. It may want to pull in some dependencies as well, that's ok.

It worked!  Thank you! 

=D>

---

### Post by wojox on 2010-09-27
> **Burning_tree said:**
> It worked!  Thank you! 

=D>

Your welcome. :)

---

### Post by dgaud on 2010-10-08
> **NightwishFan said:**
> You need to install libdvdcss. Just install this package, choose the one for your arch:
 Thanks! This works. I had the same problem when I switched to Lucid 64 bits.

---

### Post by ratcheer on 2010-10-12
> **NightwishFan said:**
> You need to install libdvdcss. Just install this package, choose the one for your arch:

This worked for me on 10.10. Thank you.

Tim

---

### Post by ByteOneZero on 2010-11-21
i had this problem too.i installed vlc player and now i can play dvds fine

---

### Post by nengracia on 2010-11-24
> **Brandel Valico said:**
> [http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

A handy guide to setting up pretty much all the multi-media you need.

hi brandel, is there a comprehensive howto for 10.10? this link seems to be outdated and it doesn't seem to work on my 10.10.

Need help in switching entirely to ubuntu. thanks.

---

### Post by Rocko262c on 2011-01-15
Dear Ratcheer,
I have done everything in this foreum and many others for 2 computers with Ubuntu 10.10 freshly installed on them and still can't get a DVD to play.
Are you sure that is all you did was install libdvdcss via NightwishFan's method?
Cheers,
Rocko262c

---

### Post by NightwishFan on 2011-01-15
If you install libdvdcss and vlc most DVDs should work. For Totem you will need to install gstreamer plugins. If you can play more than .ogg files on totem you probably already have them.

---

