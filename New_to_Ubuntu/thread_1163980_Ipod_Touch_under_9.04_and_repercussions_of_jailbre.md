---
title: "Ipod Touch under 9.04 and repercussions of jailbreak"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by RoyHobbs on 2009-05-19
Hi

I am trying to use my Ipod Touch under 9.04.  For whatever reason, it is not recognised at all when I connect it up via USB.  Do I have to jailbreak it and what does that actually mean?  Sorry for the dumb questions.  Thanks:)

---

### Post by s.fox on 2009-05-19
Hi,

[This ]("https://help.ubuntu.com/community/PortableDevices/iPhone")should help you understand.

-Ash R

---

### Post by RoyHobbs on 2009-06-04
Hi

thanks for this, however when I tried to instal VirtualBox I got an error due to having VirtualBox oe?  Is this a problem?  Thanks


> **Ash R said:**
> Hi,

[This ]("https://help.ubuntu.com/community/PortableDevices/iPhone")should help you understand.

-Ash R

---

### Post by olnir on 2009-06-04
Yes.

Virtualbox OSE does not come with USB support.

You need to use Suns "Proprietary" Version, which is free and supports usb devices.

---

### Post by clive littlewood on 2009-06-04
Hi

As olnir says download the NON ose version from the Sun site.

This is a .deb file so download to your desktop and double click the file.

It will then install.

When you load your guest OS (Windows) click on devices and install "guest additions" which will give you single mouse operation and many other things.

I have XP running in virtualbox only for my ipod sync.

Clive

---

### Post by deepclutch on 2009-06-05
Here is How I fixed to mount it on Jaunty.
[http://www.marsmenschen.com/content/how-mount-your-non-jailbroken-iphone-filesystem-ubuntu](http://www.marsmenschen.com/content/how-mount-your-non-jailbroken-iphone-filesystem-ubuntu)

[http://blog.zoomeren.nl/2009/03/24/mount-iphone-in-linux-using-usb-ifuse-libiphone/](http://blog.zoomeren.nl/2009/03/24/mount-iphone-in-linux-using-usb-ifuse-libiphone/)

---

### Post by clive littlewood on 2009-06-05
Hi

The problem with ifuse is they do not have a fix yet for ipods with 2.0 software.

Also you cannot update or change any apps.

Good look to them, if they finally crack the problems without a jailbreak they will have many supporters.

Of course Apple just keep moving the parameters to stop people doing just this !!!!!

My next mp3 player will NOT be Apple.

Clive

---

### Post by loveandequality on 2009-06-07
Yea my touch also works good with iFuse the only thing is i have to jailbreak and istall VLC player beacuse i cant find another way to put songs but this is good soince in 6 months or less they are going to make iFuse even better becuase right now is only for developers so when is polish you wont have to jailbreak and i dont have to use VLC player but VLC takes all formats even oog and all viedeo formats is as easy as drag and drop but be careful dont put folders since for some reason i cant erase them only songs and movies alone and you can erase folders via SSH that is the only way i foind. So if you dont have Wi-fi in your computer de WARNING about the FOLDER. Also if you try to put songs in a encrypted folder all the songs in your touch will be ERASE it happen to me.

websit it tells you what to do:[http://matt.colyer.name/projects/iphone-linux/index.php?title=Create_A_Trace](http://matt.colyer.name/projects/iphone-linux/index.php?title=Create_A_Trace)

PS>your touch will be reconize as iphone and there will be 2 just 1 works tho.

---

### Post by deepclutch on 2009-06-07
I don't have ipod touch.but my sister asked to copy some songs(mp3s) from my computer to ipod.but then ,I found it is not showing up.so installed ifuse and was able to copy around 4GB at 1.0mbps speed :P took long time.sometimes even it stopped showing error like "transfer end not responding"...kind of.

After copying ,ipod was not able to sync and identify these files.itunes software can help in this regard.yet to try gtkpod.

---

### Post by clive littlewood on 2009-06-08
Hi

The above post is only for Windoze or Mac.

I would have thought if you are going to use our forum for a blatant advert then produce a Linux version !!!!

Clive

Edit: I assume mods have removed the advert !!!  well done

---

