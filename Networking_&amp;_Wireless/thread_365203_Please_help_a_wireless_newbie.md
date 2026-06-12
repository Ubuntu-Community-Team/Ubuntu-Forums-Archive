---
title: "Please help a wireless newbie?"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by whitefort on 2007-02-19
Hi,

I've just purchased a netgear WG311T card, because it got a 5/5 rating with Ubuntu.

Problem 1 was when I opened the box - drivers for all flavours of Windows, nothing for Linux!


I put the card in anyway, hoping that when I fired up Ubuntu it would find it.

Problem 2:  Nope - it's not even present in the networking settings.  As far as Ubuntu's concerned, it doesn't exist!

I'm clueless, and googling has just made me more confused than ever.  I'm obviously missing some very basic step, and I'd be grateful if someone would point me in the right direction.

Thanks!

---

### Post by spd106 on 2007-02-19
Open Synaptic Package Manager and make sure that the 'linux-restricted-modules-generic' package is installed. 

If you don't have a direct Internet connection then download the linux-restricted-modules-2.6.17-11-generic (for edgy) or the similar package for dapper from [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by whitefort on 2007-02-19
Many thanks, SPD106.  I've downloaded the package on anoter machine - but I'm afraid I don't know what to do with it now!

Can I just put it on a disk, put it in the wireless machine, and click it?  I'm afraid of doing something stupid and breaking something (again...)

Thanks - I really appreciate the help.

---

### Post by spd106 on 2007-02-19
Sure, just double-click on it and it should install without any problems. If it doesn't want to work then you may need some of it's dependencies.

A quick look suggests that you will also need the linux-restricted-modules-common, module-init-tools and nvidia-kernel-common packages.

These may be on the installation disk.

---

### Post by whitefort on 2007-02-19
SPD106,

I really can't thank you enough for your help.  The wireless network is now up and running, and updating the system even as I type.

I had a few snags - the kernel was still at 2.6.17.10, but I just downloaded the relevant version - it let me know the other 3 packages I would need, so I download and installed them too.

Rebooted, and there was my card!  Added the network name, and suddenly I was on the net!

Migrating to Linux is turning out to be a long hard struggle for me - modem problems, printer problems, (wired) network problems, lack of the software I need.... the list goes on and on.  Honestly I was expecting my wireless adventure to be a week-long nightmare, and probably still not be working at the end of it.  THANK YOU for making it so easy and painless!!!!!!!!

---

### Post by ubuntu_demon on 2007-02-22
To find out which kernel you are running 
$ uname -r

Based on this result install one of the following :
$ sudo aptitude install linux-386
$ sudo aptitude install linux-686
$ sudo aptitude install linux-generic

**in your case** should install linux-generic:
$sudo aptitude install linux-generic

This packes makes sure that you will always have the relevant restricted modules even after a kernel upgrade.

You will need to configure some security settings. One which is very easy is mac-filtering. You can do this in your router and you don't have to do anything on your pc (wireless) settings.

You can additionally use WEP if you decide to use WEP you need to configure this on your router and in system->administration->networking.

Instead of WEP you can use WPA(2). Which is harder to setup. If you decide to do this then here's a guide :
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

I'm very interested in your experiences. I hope you get WPA2 personal running with CCMP/AES. I'm searching for a wireless card myself see :
[http://www.ubuntuforums.org/showthread.php?t=363633](http://www.ubuntuforums.org/showthread.php?t=363633)

the netgear WG311T is one of the candidates

---

### Post by armenj on 2007-02-23
i have a netgear WG511, i can not connect to a wireless network which is WEP secured? the server should generate me a key when i connect but it seems my laptop doesnt even ask for it?

---

### Post by ubuntu_demon on 2007-02-23
> **armenj said:**
> i have a netgear WG511, i can not connect to a wireless network which is WEP secured? the server should generate me a key when i connect but it seems my laptop doesnt even ask for it?
You have to login to your router and set/generate the WEP key. Write that same WEP key also in system->administration->networking. I have to hurry. No more time to explain right now. Good lucK!

(alternatives : you can also use networkmanager,wpasupplicant or manually edit your interfaces)

---

