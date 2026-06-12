---
title: "Wireless network changed after upgrate"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by vifillr on 2008-05-25
I have recently upgraded to Ubuntu 8.04. My wireless network card worked fine before the upgrade - and it also works fine now, but only after I have pressed the network manager symbol up right, then manual configuration, then pressed unlock and filled in the su password, then filled in the WPA encryption key under preferences for the wireless network. Then it works fine. 

However, I would very much like the machine to remember these preferences and passwords - so that when I start my machine - it automatically logs on to my network. My wife also uses this machine - she would be even more thankful. It worked very fine in the previous Ubuntu version... 

I also miss the status-symbol for the wireless network that used to indicate the quality of the wireless network connection - the green color indicated when I was logged on - there is only the nv manager symbol in black now. 

I also miss that the network manager no longer lists the available wireless networks found as in the previous version.

I guess I am not the only one experiencing this - and that the solution may be simple ;-) 

Any help would be appreciated!

/Vifillr

---

### Post by spd106 on 2008-05-25
It sounds like you have disabled roaming mode, this will turn off Network-Manager. I suggest that you open the Network tool and make sure that your wireless device is set to roaming mode. 

You should be able to manage the configuration by right-clicking the wireless icon and selecting Edit Wireless Networks...

---

### Post by vifillr on 2008-05-26
> **spd106 said:**
> It sounds like you have disabled roaming mode, this will turn off Network-Manager. I suggest that you open the Network tool and make sure that your wireless device is set to roaming mode. 

You should be able to manage the configuration by right-clicking the wireless icon and selecting Edit Wireless Networks...

Yes, I had disabled roaming mode - that was the only way I got connected. I now tried to reset the connection to roaming mode, but it was no way I could get connected. When restarting the machine, the nm-applet showed up with a small warning sign... 

It should be mentioned that I have two wireless interfaces, one ath0 (PMCIA -card that I know is working) and one eth0 (I guess the internal NIC on the laptop - not working)

I also found other wireless networks in the drop-down menu for the SSID, so now I can find other networks if I use the machine at other locations. 

But still there is a lot of clicking every time I want to connect. There should be a way to automatically connect to a previously used wireless network, at least it should be an option to do so...

/Vifillr

---

### Post by spd106 on 2008-05-26
It should automatically connect to the last network you were on. This is what the nm-editor shows you. You access nm-editor via the right-click method I described earlier. If your network setting are not displayed in there then you will have to add them manually. I had to do this once, but it's usually done for you the first time you connect to a new network.

Nm-editor also allows you to delete network that you connected to mistakenly, so you don't automatically connect to it again.

---

### Post by kjurkic on 2008-05-29
Howdy,

I have been a linux user for over 10 years now, and while wireless support & configuration has improved by leaps & bounds, it is still VERY frustrating to finally get a new user onto linux (Ubuntu in this case) and then spend far too much time & frustration figuring out the quirks of Network manager. The issue here is not the NIC driver, but the the fact that Network Manager can't seem to play consistantly well with even the regular network at home, let alone bouncing from hotel to coffeeshop to other houses. Roaming is enabled, but getting Network manager to behave consistantly is like trying to herd cats. I think the developers might want to look into alternatives; I have noticed a few posts here & elsewhere vilifying network manager and its quirks.

On my PuppyLinux laptop, there is a utility called pwireless scanner...it "just friggin works", consistantly, clearly, and even a noob can figure it out....too bad its not in the repos for Ubuntu...

If there is a fix for NetManager, could someone point me to it?

Regards
Ken

---

### Post by vifillr on 2008-06-18
> **spd106 said:**
> It should automatically connect to the last network you were on. This is what the nm-editor shows you.

I have tried several times now. Well, all I can tell is that on my computer it does NOT automatically connect...

---

### Post by danta on 2008-06-18
Since the dist upgrade I have a new interface "wmaster0", I have no idea where it came from since my wireless connection is "eth1". Does anyone knows where it came from?



Since the updates of june 17, I have wireless problems, my internet speed is at a fraction of the normal speed (I'm now at 45kB/s). I thought it was my ISP, but when I boot to windows, I have no problem with the speed. Before the update, I had no problem. I also booted into the older kernel but it has the same problem now. Does anyone have an idea, what could have happened?

---

### Post by ash303 on 2008-06-18
Since the update I did just 10 minutes ago, wireless networking isn't working anymore. This update included an upgrade to kernel version 2.6.19 and I suspect this kernel is wrongly configured. When I restart and use 2.6.18, wireless works fine. This seems like a mistake of the Ubuntu dev team. Anyone knows what's going on?

I have a Dell Inspiron 6400 for what it's worth.

---

### Post by paulcaseyjr on 2008-06-19
Mine too -- both the internal Intel and PCMCIA Netgear Atheros cards have stopped working.

---

### Post by paulcaseyjr on 2008-06-20
I think I found a solution.  At least it's working for me...

I restarted with a wired network connection.  At that point, I could use the connection manager to switch to either the internal Intel or PCMCIA Netgear wifi devices and both of them worked fine.

I then unhooked the wired connection and wireless continued to work.

I then did a shutdown and power off and restarted without the wired connection and again both devices continued to work.

I restarted again and booted XP on the same machine in case there was any conflict there -- after both a warm and cold restart, Ubuntu came back with the wireless connection and no problems.

So -- in my case -- it seems that after those updates, it needs a wired connection just once and from that point on, it seems to be just fine.  The only thing I need to try, is to do a long shutdown -- 24 hours maybe -- and retry.  Just hard to find the time to do that one...  

Paul

---

### Post by chili555 on 2008-06-20
> The issue here is not the NIC driver, but the the fact that Network Manager can't seem to play consistantly well with even the regular network at home, let alone bouncing from hotel to coffeeshop to other houses.+1000

In my opinion, a majority of the problems on this forum are Network Manager problems, not driver problems. When it's good, it's very, very good; when it's bad it's horrid.

My heart goes out to the poor guys that struggle, then decide to install a different driver; find out that doesn't work either (because NM is not allowing it to connect) and then download some .tar.gz from the far end of the internet and then can't compile it. All the while, the real culprit, NM, is unchanged.

My heart break for the guys that have *wired* connections, that is, will not be dragging their desktop machine to the coffeshop, and who start their question with, "I clicked that Network Manager icon but I can't connect..."

End rant.

---

### Post by vifillr on 2008-11-01
Well, Ubuntu 8.10 is out, and an upgrade fixed the problem. During boot / logging in, the machine automatically connects to my wireless network. 

I also looked at Preferences -> Network Connections and I liked the overview of the network connections, GooD Work! I also noticed the "connect automatically" checkbox - that is how the settings should be!!!

/Vifillr

---

