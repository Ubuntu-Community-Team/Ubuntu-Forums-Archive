---
title: "Changing Computer's IP Address"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by alanfang on 2009-03-25
How do I change the IP address of my computer in Ubuntu? I probably don't have the vocab down to say this correctly. To provide an example, you connect to a public wireless network and that network sees the IP address of your computer, how do you change the IP the network sees? Thanks.

---

### Post by sv1cdn on 2009-03-25
Top right corner, next to hour/date are two screens. This is network manager. Right click, edit connections.

---

### Post by alanfang on 2009-03-25
What exactly do I do after that? That just lets me edit the wireless networks I am connecting to, which is not what I want to do.

---

### Post by mhgsys on 2009-03-25
The easiest way to do that would be to click System>Administration>Network

Then click on unlock, 
enter your password
Then click on the device you want to set the ip adress for, click >Properties
Click the thingy to Disable roaming mode, and you can set an ip adress.

edit:
The other way sv1cdn came with would also work . 
just don't right click it , just click it and select manual configuration.

---

### Post by alanfang on 2009-03-25
All I can see on the menu you are referring to is about adding new wireless connections. I don't want to do this.

---

### Post by mhgsys on 2009-03-25
> **alanfang said:**
> All I can see on the menu you are referring to is about adding new wireless connections. I don't want to do this.

You mean the menu I'm referring to??
really?
?/?

---

### Post by aquascrotum on 2009-03-25
> **mhgsys said:**
> The easiest way to do that would be to click System>Administration>Network

Then click on unlock, 
enter your password
Then click on the device you want to set the ip adress for, click >Properties
Click the thingy to Disable roaming mode, and you can set an ip adress.

edit:
The other way sv1cdn came with would also work . 
just don't right click it , just click it and select manual configuration.

I'm interested in this too and don't have any of that....

All I have is System>Administration?Network Tools...I can select my ethernet adapter there but nowhere do I have a properties option of disable roaming mode?

---

### Post by DGortze380 on 2009-03-25
> **alanfang said:**
> How do I change the IP address of my computer in Ubuntu? I probably don't have the vocab down to say this correctly. To provide an example, you connect to a public wireless network and that network sees the IP address of your computer, how do you change the IP the network sees? Thanks.

This is not entirely correct ... now-a-days ... most of the time when you connect to a public network, you'll _receive_ an address from the DHCP server. Changing this address and potentially disconnect you from the network. 

Anyways, if you have/want a static address and know what you're doing. You can change the address through the default network manager in the top right of your desktop. You can also change this with the ifconfig command, or through /etc/network/interfaces.

If you can give us more of an idea why you want to change it, we can give more specific instructions.

---

### Post by alanfang on 2009-03-25
> **DGortze380 said:**
> This is not entirely correct ... now-a-days ... most of the time when you connect to a public network, you'll _receive_ an address from the DHCP server. Changing this address and potentially disconnect you from the network. 

Anyways, if you have/want a static address and know what you're doing. You can change the address through the default network manager in the top right of your desktop. You can also change this with the ifconfig command, or through /etc/network/interfaces.

If you can give us more of an idea why you want to change it, we can give more specific instructions.

Do you get a new and different address every time you connect to the server? Let me try to phrase my question better, 

Let's say I connect to a wireless network. As I understand it the network you connect to has a way of uniquely identifying your machine, and that ID stays constant even after you disconnect and reconnect later. My question is what is the name of that unique ID you are assigned?

---

### Post by DGortze380 on 2009-03-25
> **alanfang said:**
> Do you get a new and different address every time you connect to the server? Let me try to phrase my question better, 

Let's say I connect to a wireless network. As I understand it the network you connect to has a way of uniquely identifying your machine, and that ID stays constant even after you disconnect and reconnect later. My question is what is the name of that unique ID you are assigned?

That gets a bit complicated.

The Unique ID I think you are referring to is your IP Address. 

It's unique to your device _on a given network_. When you receive an IP from the DHCP Server, it's called a Lease. That lease expires at a certain time. That time can vary. You may get a new address every minute, or every 3 months, depends on the lease. Regardless, while you have a given address, in theory, no one else on the network should have the same address.

If you connect to network without DHCP, you have to set a Static IP Address and Netmask (as well as some other information). Again, this address is unique to your device on the network. It won't change automatically because there is no lease to expire, but it may be able to be changed.

Your network card also has a MAC Address, which theoretically is unique to your network card, period, only one in the world, although this too can be changed (spoofed).

---

### Post by Iowan on 2009-03-25
> **alanfang said:**
>  As I understand it the network you connect to has a way of uniquely identifying your machine, and that ID stays constant even after you disconnect and reconnect later. My question is what is the name of that unique ID you are assigned?Do you refer to the [MAC]("http://en.wikipedia.org/wiki/MAC_address") address? That information is coded into the network adapter (Wired or wireless). Although it can be artificially changed, it is intended to uniquely identify the adapter.  DHCP associates an IP address with a MAC address (and can use MAC address to assign "static lease").

---

### Post by DGortze380 on 2009-03-25
> **Iowan said:**
>  DHCP associates an IP address with a MAC address

Not always, in fact, usually not.

> **Iowan said:**
>  (and can use MAC address to assign "static lease").

Sometimes. If configured to do so.

---

### Post by alanfang on 2009-03-25
> **DGortze380 said:**
> That gets a bit complicated.

The Unique ID I think you are referring to is your IP Address. 

It's unique to your device _on a given network_. When you receive an IP from the DHCP Server, it's called a Lease. That lease expires at a certain time. That time can vary. You may get a new address every minute, or every 3 months, depends on the lease. Regardless, while you have a given address, in theory, no one else on the network should have the same address.

If you connect to network without DHCP, you have to set a Static IP Address and Netmask (as well as some other information). Again, this address is unique to your device on the network. It won't change automatically because there is no lease to expire, but it may be able to be changed.

Your network card also has a MAC Address, which theoretically is unique to your network card, period, only one in the world, although this too can be changed (spoofed).

Thanks, this explains it perfectly.

EDIT: Quick followup, is it possible to change the address you get from the DHCP server or force it to renew the lease?

---

### Post by mhgsys on 2009-03-25
I have a Static Ip Adress, 
I found this easier since I have more pc's running here, using ssh and samba, azureus etc.
Also I don't want DHCP-server running cause I feel my wireless network is a little bit safer this way,

Anyway, I noticed some user didn't have the option System>Administration>Network

See if you can enable it in 
System> Preferences> Main menu

I have it listed there under the System>Preferences>Administration.

Edit:If you don't have it use
```

sudo apt-get install gnome-network-admin

```

---

### Post by rplantz on 2009-03-26
> **mhgsys said:**
> I have a Static Ip Adress, 
Anyway, I noticed some user didn't have the option System>Administration>Network

See if you can enable it in 
System> Preferences> Main menu

I have it listed there under the System>Preferences>Administration.
Official Ubuntu help refers to System>Administration>Network. I don't have that option, and it does not appear under System>Preferences>Main menu.

Does anybody know how to get it?

Edit: Never mind, I figured it out. You need to install gnome-network-admin. I used Synaptic.

---

