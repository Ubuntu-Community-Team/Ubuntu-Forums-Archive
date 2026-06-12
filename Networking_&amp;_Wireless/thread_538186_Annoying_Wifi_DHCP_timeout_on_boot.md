---
title: "Annoying Wifi DHCP timeout on boot"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by luisfpg on 2007-08-29
Hi all!

I have a Kubuntu Feisty on an Acer 5002 laptop, with a Broadcom 4318 wireless card.
I'm using a wireless network with WEP, and it works perfectly with network manager and ndiswrapper. :)

There's an annoying problem, though. :mad: Every time I boot, there's a DHCP timeout, because the interface definition on /etc/network/interfaces, cannot be touched, or network manager won't see it. And the DHCP doesn't work because of the WEP key, that only network manager knows.

Any ideas of a workaround for this? :confused:

---

### Post by noob12 on 2007-08-30
You should remove the interface from /etc/network/interfaces if you are using NetworkManager to manage it in roaming mode.

You can also edit the duration of the timeout in **/etc/dhcp3/dhclient.conf**, but I'm not sure that is your issue.

What does your /etc/network/interfaces look like?  Can you post it?

---

### Post by luisfpg on 2007-08-31
When I remove the interface from /etc/network/interfaces, KNetworkManager cannot find it.
Perhaps it's an issue with KNetworkManager and does not happen with Gnome's network manager... I'll try installing gnome's one...

My interfaces file is:
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by noob12 on 2007-08-31
If you want to leave it in the file, but comment out the **auto** line, that will keep the interface from being enabled at boot.

---

### Post by luisfpg on 2007-08-31
I've tried both to remove the whole interface definition or just the auto wlan0, but in both cases, network manager stops recognizing the interface.
Can it be something like the kubuntu does not including some packages for roaming, or something like that?
Thanks!

---

### Post by noob12 on 2007-09-01
I was under the impression that the core behavior of NetworkManager was the same on these aspects, and that the nm-applet in gnome and knetworkmanager were just different front-ends.

My understanding is that if there is an entry in the interfaces file, then NM will consider it manually configured.  

The auto line is used by ifup when run at boot to decide whether to bring the interface up. 

If you have no entry, NM will consider the interface to be in roaming mode; ifup will not see it.

I'd have to double check these for the kubuntu case, but I think they are the same.

---

### Post by luisfpg on 2007-09-01
Ok, thanks for the quick assist!
I can confirm: When I remove the line from interfaces file (both the auto wlan0 or all definition), neither KNetworkManager nor nm-applet (I've installed it to check) recognizes the wireless interface. 
It was a clean Feisty installation (no dist upgrade).
Again, thanks a lot!

---

### Post by noob12 on 2007-09-01
> **luisfpg said:**
> Ok, thanks for the quick assist!
I can confirm: When I remove the line from interfaces file (both the auto wlan0 or all definition), neither KNetworkManager nor nm-applet (I've installed it to check) recognizes the wireless interface. 
It was a clean Feisty installation (no dist upgrade).
Again, thanks a lot!

This seems really odd to me.  For the gnome case which I'm most familiar with, when there is no entry in /etc/network/interfaces, the device should still be recognized by NM, it is just considered in "roaming mode". If you right-click the nm-applet icon and select Enable Wireless, it should still get used.  It could depend on the type of device though.  My range of direct experience is limited to three or four types of devices in laptops I use; these have all behaved the same in this regard.
Sorry I haven't been much help.

---

### Post by E_K on 2007-09-02
I can confirm i have the same problem, when i commented out the lines in the interfaces file, i lose the wireless completly. I'm using a Dell 1390, on an Acer Extensa 5210

---

### Post by noob12 on 2007-09-02
Perhaps you should try wicd.  A number of reliable voices on the forum have recommended it.  I am still using NM with gnome nm-applet, which has worked for my conditions just fine.

---

### Post by luisfpg on 2007-09-02
I've tried to install wicd, but it couldn't connect to my wireless network...
For some reason I can't explain, until edgy my wireless network used to work "standalone". 
On feisty only network manager can connect it... If I remove network manager, the "manual configuration" cannot connect either.
So, no luck again...

---

### Post by E_K on 2007-09-04
after the effort i have gone through to get the wireless working, i think i will just put up with the boot time taking a bit longer.

---

### Post by luisfpg on 2007-09-04
Well, It's a minor issue for sure, compared to having no wireless connection...
Perhaps it has something to do with ndiswrapper... are you using it?
What's your wireless device?
Mine is Broadcom 4318, which according to the bcm43xx home page is a "work in progress", and only partially supported. With it, I could connect for a few minutes, then the connection is lost. 
So, I must still stick with ndiswrapper until the driver is 100%.

But I'm really intrigued with the fact that on feisty I can only connect using network-manager. Why can't the interface go up without it? on dmesg, I get a ADDRCONF(NETDEV_UP): wlan0: link is not ready. And the damn link never goes ready!!! :)
On Edgy, I even wrote a startup script to initialize the wireless on background, so, when no wireless connections were active (normally when I forgot to turn the router on :(), there was no delay on boot.

Well, I think I've speak way too much!!! :oops:

---

