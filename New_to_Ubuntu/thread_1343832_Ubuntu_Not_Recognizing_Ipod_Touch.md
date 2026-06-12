---
title: "Ubuntu Not Recognizing Ipod Touch"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by cmoney12051 on 2009-12-02
Cant sync my ipod touch on my ubuntu 9.10. I followed this link[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html") and installed ifuse from repos and did everything it says. When i connect my ipod it thinks its a camera. Does it matter thats its jailbroken? please help

---

### Post by stalkier on 2009-12-02
> **cmoney12051 said:**
> Cant sync my ipod touch on my ubuntu 9.10. I followed this link[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html]("http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html") and installed ifuse from repos and did everything it says. When i connect my ipod it thinks its a camera. Does it matter thats its jailbroken? please help

I do not have an iPod but I believe the iPhone and the iPod touch can be synced using Amarok if they are jailbroken. I could be wrong. Like I said I do not own a iPod.

---

### Post by cmoney12051 on 2009-12-02
from what i read it says that ifuse is suppose to be the best and easiest way. Im not really looking to sync it just connect it to the computer, like a removeable drive.

---

### Post by cmoney12051 on 2009-12-04
bump

---

### Post by jquest68 on 2009-12-06
can I still SSH into my ipod touch like I used to do with windows? for example, if I wanted to load a theme (cause my ipod touch is jailbroken) can I use FTTP?

---

### Post by LuisGMarine on 2009-12-06
Hello,

Have you tried managing your ipod with other applications other than this ifuse?  If so try out banshee or rhythmbox.  If you still continue to have other pograms other than rhythmbox detect your ipod, try this:

Disconnect your ipod from the PC, open up terminal by going to **Applications > Accessories > Terminal ** once there type in this into the window 
```
killall -9 nautilus
```

Connect your iPod, wait about a minute then hit Alt + F2 and type in **nautilus** to start it up again.  Now your iPod should be recognisable by other apps other than rhythmbox.

---

### Post by joes7 on 2009-12-11
Install Wine. Install Linux. And you're ready to rock n roll!

---

### Post by durand on 2009-12-11
When it does show up as a camera, can't you right click on its icon in Computer and open it as a drive?

---

### Post by tacantara on 2009-12-11
As the Linux community finds ways to make iPods sync with Linux-based software, Apple comes up with ways to modify the device databases so they can't sync with Linux.  The iPod Touch is particularly tough in this respect.  I have a first generation Touch, and an iPod Classic.  The Classic syncs with Banshee (after some tweaking), but the Touch won't play nice.  You're better off either setting up a dual-boot with Windows or run Windows in a VM, and install iTunes.  That is, unless someone has had success with syncing the Touch without falling back on Windows and iTunes.

---

### Post by durand on 2009-12-11
> **tacantara said:**
> As the Linux community finds ways to make iPods sync with Linux-based software, Apple comes up with ways to modify the device databases so they can't sync with Linux.  The iPod Touch is particularly tough in this respect.  I have a first generation Touch, and an iPod Classic.  The Classic syncs with Banshee (after some tweaking), but the Touch won't play nice.  You're better off either setting up a dual-boot with Windows or run Windows in a VM, and install iTunes.  That is, unless someone has had success with syncing the Touch without falling back on Windows and iTunes.

Is there a way to use MSC mode for the ipod touch so that it appears as a removable drive? I'm not familiar with ipods but I know that many other music players will let you do that..

---

### Post by LowSky on 2009-12-11
> **durand said:**
> Is there a way to use MSC mode for the ipod touch so that it appears as a removable drive? I'm not familiar with ipods but I know that many other music players will let you do that..

Nope. Apple codes all the music and video files in a weird way. its to stop pirating they claim. In practice its really to stop you from using another application that isn't iTunes.

---

### Post by durand on 2009-12-11
> **LowSky said:**
> Nope. Apple codes all the music and video files in a weird way. its to stop pirating they claim. In practice its really to stop you from using another application that isn't iTunes.

Well, that sucks for ipod users :(

---

### Post by joes7 on 2009-12-11
> **durand said:**
> When it does show up as a camera, can't you right click on its icon in Computer and open it as a drive?
No. It won't work if he is having the described problem.

---

### Post by Dubbayoo on 2009-12-12
> **tacantara said:**
>  You're better off either setting up a dual-boot with Windows or run Windows in a VM, and install iTunes.  That is, unless someone has had success with syncing the Touch without falling back on Windows and iTunes.

Will the ipod work in a VM? If so what kind? I use vmware.

---

### Post by durand on 2009-12-12
It will probably be buggy. I don't think it's a good idea.

---

### Post by tacantara on 2009-12-12
> **Dubbayoo said:**
> Will the ipod work in a VM? If so what kind? I use vmware.

I've successfully synced an iPod, using iTunes, in VirtualBox (the version that you download from Sun Microsystems website), with Win XP as the virtual OS.  As long as VMWare supports USB connections, you should have no problem (VirtualBox has access to your host computer's hardware, thus USB support is available).

If VMWare doesn't have USB support, check out VB.  Again, download it from Sun, because the version in the repos (Virtualbox OSE) doesn't have USB support.

---

### Post by CanadianBac0n77 on 2009-12-12
If your device is jailbroken you should try out this:

[http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux](http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux)

---

### Post by LinuXGo on 2010-01-01
Well did any try this website I found, I've tried it but some of the packages won't install so someone could at least test it to see if it works or not. [http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/](http://marcansoft.com/blog/2009/10/iphone-syncing-on-linux/)

---

### Post by puzzler995 on 2010-01-01
What Firmware Version do you have on your iPod. This makes all the Difference

---

### Post by Haitoyou on 2010-01-01
The Ipod Touch does not normally come with the ability to be used as a removable drive. My brother found this out when he bought one and was unable to find the drive when connected to the computer. I don't know why Apple removed its ability to do this but it may be related to attempting to stop music pirating.

Now if you've somehow jailbroken it to have this functionality then ignore my post, but if you haven't, then you're out of luck it seems :(.

---

### Post by LinuXGo on 2010-01-01
Well I've heard that someone had managed to sync the ipod touch device using itunes while running Wine. But we are know that's impossible because there an abundant of witness says that Wine can't configure itune software to properly sync with ipod devices. However, it just might be possible with Wine intergrated with miminal patches that found to be successful announced by a developer whom name I can't recall.

---

