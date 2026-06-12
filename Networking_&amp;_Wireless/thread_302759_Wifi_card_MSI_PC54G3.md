---
title: "Wifi card MSI PC54G3"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Atropos44 on 2006-11-19
Hi,

I've got a little problem with Dapper :
I can't access to internet with my wifi card (MSI PC54G3 PCI).
It's recognized, there's datas send/received when I connect to the network but it's impossible to ping anything, And if I choose DHCP instead of Static IP I don't have any IP.
Here is a snapshot if it can help :

[[IMG]http://img354.imageshack.us/img354/8430/capturesx4.th.png[/IMG]](http://img354.imageshack.us/my.php?image=capturesx4.png)

Any solutions ? :confused: 

NB : Under Egdy my card wasn't recognized (interfaces wlan0 and wmaster0 instead of ra0) even with Ndiswrapper

(Sorry for any mistakes, I'm French ;)

---

### Post by FrodoB on 2006-11-19
Well if the output of iwconfig is to be believed, and I guess it is, your signal level is below the noise level, is this the ndiswrapper perhaps?

Can you get closer to the router for a test to see it this can be improved upon perhaps and supply new output data? Thanks for the very complete set of data.

---

### Post by Atropos44 on 2006-11-19
Thanks for your answer :) 
I don't use ndiswrapper here, since my card was recognized natively.
Concerning the signal level, I've made another try and it seems to be better :
[[IMG]http://img175.imageshack.us/img175/1610/reseaujf6.th.png[/IMG]](http://img175.imageshack.us/my.php?image=reseaujf6.png)
But anyway, I'm 2 meters from the router and in Win XP the signal is "very good"

Thanks again for your help

---

### Post by FrodoB on 2006-11-19
So you resolved your issue? It certainly looks very good now. Hopefully you are on the net with it now.

---

### Post by huygens on 2006-11-19
Hello,

I have the same card as you and I manage to make it work on Ubuntu 6.10 (Edgy Eft). As you said, the card is not working out of the box because of [bug in the driver]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/58117"). The MSI PC54G3 uses a Ralink chipset namely the RT61, and there is a [really cool guy]("http://ubuntuforums.org/member.php?u=192503") that posted an [how-to for RT61]("http://ubuntuforums.org/showthread.php?t=296822") to make it work under Edgy. I'm pretty sure it could be applicable also to Ubuntu 6.06 (Dapper Drake).

I hope this help, at least for me this how-to worked like a charm.

Huygens

---

### Post by Atropos44 on 2006-11-20
FrodoB > I'm not on the net yet :( Even if everything seems right, I can't access the router or the web

Huygens > Thanks for the tip :) I'll try to install Edgy and test it as soon as I can ;)

---

### Post by huygens on 2006-11-20
> **Atropos44 said:**
> I'll try to install Edgy and test it as soon as I can ;)
Instead of installing, you could try upgrading :-) Check the notes here:
[https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)

---

### Post by FrodoB on 2006-11-20
huygens;

Thanks for jumping in here. This sounds very promising.

[URL="http://www.ubuntuforums.org/member.php?u=77473"]
[/URL]

---

### Post by huygens on 2006-11-20
It is promising :-) since last Friday, I use my MSI PC54G3 to access Internet from my Ubuntu 6.10 computer! So I'm happy and I thought I should share it...

Huygens

---

