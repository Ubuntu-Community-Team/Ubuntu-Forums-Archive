---
title: "Wireless Internet and WUA-0605"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Fishbot4000 on 2011-02-12
I installed Ubuntu 9.10 onto my desktop computer (full install), and for some reason I can't access the internet. I have a Levelone Wireless adapter, model WUA-0605.

It worked perfectly fine when I ran Windows, but for some reason I now can't detect any wireless network.

I know that there are many different threads exactly like this one, but they are for different models, and I can't make heads or tails of the instructions. I'm very new to Linux.

---

### Post by robsoles on 2011-02-12
9.10 wasn't a super release for me and I don't want to try to help anybody do anything with it, sorry - maybe my posting this and 'bumping' your thread to the top will attract somebody who liked the 9.10 release and they will pursue that for you.


If you insist on using 9.10 then maybe a look at [http://ubuntuforums.org/archive/index.php/t-846917.html](http://ubuntuforums.org/archive/index.php/t-846917.html) can help you.


Would you please try Ubuntu 10.04 from the LiveCD and give it a few minutes of 'Try Ubuntu' and then see if it has picked up your wireless card and whether or not it lists your wireless network under the network icon on the top panel.

If 10.04 doesn't pick it up and use it off the LiveCD give it a couple more minutes and check 'hardware drivers' under 'system'->'administration' and make sure it doesn't mention having a proprietary driver for the wireless device available for download there (no point trying to install it to LiveCD though, just an indicator if it's available at that stage.)


If it doesn't work off the LiveCD and a proprietary driver isn't offered for it then (in my humble opinion at least) you are still better off installing 10.04 and 'ringing the bell for assistance' because there are a lot more people willing to respond about difficulties with 10.04 and upwards rather than downwards.

---

### Post by walt.smith1960 on 2011-02-12
Posting the result of terminal command "lsusb" would be a start. It looks like a Ralink chip set but which one? I agree with Robsoles, you may have better luck with a newer version.  Wifi N support is a work in progress but it seems to be getting better.  I have 2 different wifi N adapters which need work even in 10.10 but are plug & play in 11.04 alpha 2.

---

### Post by Fishbot4000 on 2011-02-13
Thanks for the help.

I did as was suggested and attempted to install 10.04 and the install kept freezing. After I finally got it to work all of my USB ports didn't work, which means I didn't have a mouse or keyboard.

I then installed 10.10 with the same results. Finally, I went and installed 8.04 because I've never had problems with it and it has always been a personal favorite of mine.

So now I'm in the process of getting my wifi adapter to work but I can't find the proper drivers, or what to do with them once I get them.

The computer in question isn't connected to the internet yet, so I can't copy and paste anything here. What I can do is give the model, vender, and pci numbers:

Model: RTL8191S WLAN Adapter
Vender: Realtek Semiconductor Corp.
PCI NUMBER: pci_1039_7002

Is there any chance anyone could help me get this device to work?

---

### Post by Fishbot4000 on 2011-02-13
Well, thanks again for the help and advice. I think I have everything working.

My next problem is related, but might require a different topic:

I managed to get my wifi adapter installed with NdisWrapper and now it detects various available networks.

However, for some reason I can't connect to my network. It is secured with WEP and I'm entering the correct password, but for some reason it's still not connecting. Any suggestions?

---

### Post by Dojan on 2011-02-13
I have a similar situation with a HP Pavilion dv6110eu in Ubuntu 10.10. The networkmanager applet seems to find a wireless device, but it simply reads disconnected where different networks would be, but Enable Wireless is checked if i right-click on the applet.

lsusb returns: 
dojan@dojan-HP-LapTop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The "Terminus" device i think is my usb hub, and "Huawei" is my mobile broadband. 

Thanks beforehand!

---

### Post by robsoles on 2011-02-13
<edited-in>Ah, should have previewed my reply and checked for other replies - lunch time at work now and I had this thread open since earlier!</edited-in>

Please post specifications of the PC - motherboard & cpu in particular.


It will be a lot faster to get places with this machine if you can drag it up to a router and plug it into an ethernet port - among other things this would allow 'hardware drivers' to search for non-proprietary drivers for you and the following will be a lot easier with a temporary hard wired connection.

Have you looked into ndiswrapper? I wonder if ndisgtk (GUI version) is available in the 8.04(/9.04) repositories?

Look: [http://community.spiceworks.com/how_to/show/1250](http://community.spiceworks.com/how_to/show/1250)

---

### Post by robsoles on 2011-02-13
> **Fishbot4000 said:**
> ...
However, for some reason I can't connect to my network. It is secured with WEP and I'm entering the correct password, but for some reason it's still not connecting. Any suggestions?

Would it be terribly inconvenient to switch that to wpa-psk2 (or at least a wpa based method)? (I mean at the wireless router - the only place it can be set or unset.)

Just a chance that if your system isn't sending the wep password correctly it might send a wpa one better - wep isn't a security measure anymore anyway.

---

### Post by Fishbot4000 on 2011-02-13
Like I said, I downloaded NdisWrapper and used it to install the appropriate drivers. The wifi adapter is working now, and I see several available networks, including my own.

My network is secured with a WEP password, however, and for some reason no matter how many times I enter it in I can't connect. I've quadruple checked, I'm using the correct password. Is there something I'm missing?

---

### Post by robsoles on 2011-02-13
Would it be terribly inconvenient to switch that to wpa-psk2 (or at least a wpa based method)? (I mean at the wireless router - the only place it can be set or unset.)

---

