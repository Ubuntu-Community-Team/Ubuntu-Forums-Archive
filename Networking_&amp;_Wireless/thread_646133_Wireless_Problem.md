---
title: "Wireless Problem"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by realGaurab on 2007-12-20
This is my first day ever using Linux. I installed Ubuntu in my desktop this evening and started working on getting the wireless working. I have a Belkin f5d9050b usb wireless receiver. I tried to install rutil to get the wireless working but was unsuccessful. So I instead installed ndiswrapper and got my wireless working. 

So I connected to my network and browsed the internet happily for about 15 mins. After that suddenly the wireless got disconnected. I opened up **Administration -> Network** and could not see the option for wireless connection. Only wired connection and modem connection options were available. So I restarted the comptuer and tried to do a lot of things to fix it but couldn't. When I typed in lsusb in the terminal it doesn't show the belkin component, and when I do ifconfig, it doesn't show wlan0. Can somebody please explain what is happening.


edit: as I am typing htis message (in my laptop), I rebooted the desktop for the 4th time and now I can see the wireless option in the network. However, it doesn't let me pick the desired network form the options (actually there are no options). I manually entered my network name and wpa key, and its working fine now. Can somebody please explain what the problem is what I can do if the same problem persists in teh future.

edit 2: now internet is not working again. I can see my belkin device when I do lsusb and can see wlan0 with ifconfig. I can also see Wireless Connection in the Network place, in which I have manually assigned the correct Network Name and WPA key. But I am not able to connect to the internet while it is working perfectly with my laptop right on the side of the desktop. The wireless indicator on the top side says network connectivity is 0%. Does anybody know what's happening here.

Thanks.


edit 3: I had followed the instruction on the page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) to setup ndiswrapper in my comptuer. Today, I saw that we have to blacklist bcm43xx, which if not might conflict with ndiswrapper. After doing that, I have been able to browse the internet for a while without any problem. I hope it says that way forever from now on.

If there's any more issue, I'll mention it here. 

Thanks for everything.

---

### Post by realGaurab on 2008-01-05
Its been a long time since I started this post, now I have a new problem. Actually, I had been having it from the start, but I was too lazy to post it.

The problem I have is I am connected to the internet. But after a while (variable length of time - 10mins to 2hrs) the wireless gets disconnected and I cannot reconnect it. I have to shut the computer down and boot it again to get the wireless working again. Even restarting the machine won't help. I have to shut it down, wait for like half a minute and the boot it. Only then I will get the wireless and again the same stuff. It's driving me mad. 

Like I said above, I'm using windows driver using ndiswrapper. Does anybody have any idea what the problem might be? Thanks.

---

