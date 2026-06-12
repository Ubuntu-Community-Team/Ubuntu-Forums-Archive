---
title: "Wg111t Usb Nightmare"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by awd_scot on 2006-12-13
Hi,

im new to Ubuntu and have been first of all trying to get my netgear wg111t usb dongle to work.  Ive looked at loads of threads but havent came across one that really says they have managed to get it to work. All i want to know really is does this USB adapter actually work under Ubuntu...or have I been wasting my team. Lastly if it does work can someone please point me in the direction of a decent site/forum that shows me how to install this troublesome piece of equipment.

AD

---

### Post by padre999 on 2006-12-13
I guess it will work with Ubuntu, but it will not be too easy I think when I look at [https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

Maybe it would be easier to buy a USB WLan stick that is compatible to Ubuntu...

---

### Post by liamjames91 on 2007-01-04
it works for me! some good news, it DOES NOT work in edgy, but works fine in dapper drake, enable all the universe and multiverse repositories in synaptic, search for ndis, install ndiswrapper utils and ndisgtk, then download the drivers for netgear wg111t from netgear website, make sure its version 1.2, unzip it, and drag and drop athfmwdl.inf and netwg11t.inf into the windows wireless drivers window (system-administration-windows wireless drivers) shutdown your system plug in the adapter switch it back on and (fingers crossed) it will work, make sure you install the drivers from the folder wg111t you downloaded not the ndis5 folder inside wg111t folder (youll see what i mean) thyen set up the network ssid and wep or wpa key in the system-administration-networking, and just disable the ethernet connection, if this works for you or someone else then please post it in other forums with this problem,, im sure it will help alot of people! 8) 

ps: ask me if you want more detailed instructions

---

### Post by awd_scot on 2007-01-05
Ok.  My queries are - 

1. Where about id the windows wireless drivers window (as system-administration-windows wireless drivers does not exist). Did you create this yourself?
2. After downloading these files i should then plug in the adapter?
3. I should then install the appropriate drivers - both the netwg11t.inf and athfmwdl.inf 
4. Should i disable the ethernet connection before doing anything?
5. I presume the adapter should be displayed in networking even before setting up the WEP or anything like that.

I would like nothing more than to get this working.

AD

---

### Post by awd_scot on 2007-01-05
As usual i asked question before trying this route. And can i just say ......................

THIS IS ABSOLUTELY BRILLIANT! I am now currently using my Wg111t usb adapter via Ubuntu and its working perfectly. This method DOES work, well it worked for me, no idea how the 100+ things that i tried before didnt but this time it does. 

Many thanks, i will spread this post as much as possible.

AD

---

