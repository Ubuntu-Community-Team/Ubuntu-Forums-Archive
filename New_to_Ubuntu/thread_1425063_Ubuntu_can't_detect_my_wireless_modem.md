---
title: "Ubuntu can't detect my wireless modem"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by InternetDominus on 2010-03-08
Hi,

I have just installed ubuntu 9.10 to my laptop with dual boot with windows 7.  I am trying to connect with wifi, but ubuntu simply won't detect my modem.

After I type in terminal: iwconfig, I get this:

=================
lo        no wireless extensions.

eth0      no wireless extensions.
=================

So, that tells me that my modem is not being recognized, but I have not way to install it. 

I read other post saying that I should add a line to /boot/grub/menu.lst, but then I read another post saying that ubuntu 9.10's menu.lst file is empty, and does not use, which I think is my case because my menu.lst file is empty.

Any other suggestions to make my modem work?

Thanks in advance.

---

### Post by PRC09 on 2010-03-08
You have probably not installed the driver for your wireless card.Go to System > Admin > Hardware Drivers and see if there is a driver listed there.If so activate or install and then see if it detects your modem....

---

### Post by InternetDominus on 2010-03-08
That did not help, I only see driver for Nvidia, but I don't want to update that driver as last time I did, it messed up my ubuntu installation. :(

---

### Post by PRC09 on 2010-03-08
Could you post the results of:
     ```
lshw -C network
```

---

### Post by PRC09 on 2010-03-08
I have to step out for awhile but maybe this will help....

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#lshw+-C+network)

---

### Post by InternetDominus on 2010-03-08
Hi,

This is what I get with lshw -c network:

===========================================
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:b800(size=256) memory:fbffc000-fbffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 03
       serial: 90:e6:ba:9e:c0:8b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:30 ioport:d800(size=256) memory:cdfff000-cdffffff(prefetchable) memory:cdff8000-cdffbfff(prefetchable) memory:fcfe0000-fcffffff(prefetchable)
===========================================


Thanks

---

### Post by MichealH on 2010-03-08
Quoting another Thread with Same problem It worked for Other Guy

> > **obi42 said:**
> I have tried adding the network manually, but that didn't work either. :(

The network starts with an "a", so it should easily show up on the list...

> **kitschl said:**
> You could try adding your network manually. Go to System>Preferences>Network Connections, go to the Wireless tab, then click on Add.

[LIST]
[*]In "Connection Name", you can put whatever you want. 
[*]Check "Connect Automatically". 
[*]In the Wireless tab, enter the SSID of your network. Make sure "Mode" is set to "Infrastructure". 
[*]In the Wireless Security tab, change settings to match the security you set up on your router. 
[*]In the IPv4 Settings tab, change settings to match your router's configuration; if you're using DHCP, just set "Method" to "Automatic (DHCP)", and that's all.
[/LIST]

I assume since your Elitebook and Wii are able to find your router, your network isn't hidden; and I assume that your Ubuntu PC's wireless is configured correctly, since it is able to find other wireless networks in your building. 

Another thing you might consider: If your wireless network begins with a letter far down in the alphabet, like 'v', and there are many other wireless networks in your vicinity, perhaps your network is too far down on the list to be shown. May or may not be accurate, but it is something that I have seen before. 

Please let me know whether this helps you. Good luck!

> **kitschl said:**
> That is odd. Other wireless networks show up, but not your own... 

You've probably already tried disabling/re-enabling your laptop's wireless card, and power-cycling your router...

You could try making sure that you have updated your router to the latest official firmware, sometimes outdated firmware can cause issues with interfacing. The same for your wireless card drivers. 

The only other thing I can think of is to check that your router is broadcasting a signal that your Ubuntu laptop can recognize; maybe you are broadcasting in 802.11b, and your laptop can only recognize g.  

I hope this helps.



---

### Post by InternetDominus on 2010-03-08
Hi MichealH,

Thanks, but as far as I know all those suggestions may only work after my modem is recognized, so I need Ubuntu to find my modem first, then I can configure it manually or maybe it does so automatically.

---

### Post by kitschl on 2010-03-08
Just to make sure I understand correctly, you are trying to use a cellular modem? Is it USB or built-in?

---

### Post by InternetDominus on 2010-03-08
hi kitschl, this built in, it came with laptop.

---

### Post by kitschl on 2010-03-08
Hi, InternetDominus. 

You might try going to System>Preferences>Network Connections; then go to the "Mobile Broadband" tab; click Add. 

If we're lucky, your cellular modem may show up in the dropdown list in the "Set up a Mobile Broadband Connection" dialog window that appears. You might not need to know more than your service provider's name; when I set up my laptop to use my Samsung phone as a modem, all I needed was that Verizon was my provider. 

Apart from trying that, there's not much more help I can offer. Good luck!

---

### Post by InternetDominus on 2010-03-08
Hi,

I have found drivers on realtek website here, but **how do I know what the kernel of my current ubuntu installation is**? The drivers I found are for kernel 2.6.x and 2.4.x

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)

**Can anyone tell me how to install that driver?**

LINUX driver for kernel 2.6.x and 2.4.x (Support x86 and x64) 8.016.00 2010/1/19

---

### Post by InternetDominus on 2010-03-08
Hi,

Ok, my kernel is 2.6.31-20-generic.

But can anyone tell me **how to install a driver file**: r8168-8.016.00.tar.bz2

**where should install it?**

---

### Post by kitschl on 2010-03-08
I'm not 100% certain, but I think what you are trying to install is a driver for an ethernet NIC? Which won't help you with wireless internet. 

Just for clarification purposes, are you trying to connect to a wireless router, or are you trying to use cellular internet? 

Finally, if you unpack your downloaded .tar.bz2 file, you should find a README inside with details on how to install the driver. Again, though, I'm 90% sure that the driver you have downloaded is for an ethernet NIC, not for wireless anything.

---

### Post by InternetDominus on 2010-03-09
> **kitschl said:**
> I'm not 100% certain, but I think what you are trying to install is a driver for an ethernet NIC? Which won't help you with wireless internet. 

Just for clarification purposes, are you trying to connect to a wireless router, or are you trying to use cellular internet? 

Finally, if you unpack your downloaded .tar.bz2 file, you should find a README inside with details on how to install the driver. Again, though, I'm 90% sure that the driver you have downloaded is for an ethernet NIC, not for wireless anything.

I have a laptop with a built in modem, and I am trying to connect to a wireless router.  I was able to unpack and install the driver I found using the README file inside the zip file, but still, I could not connect via wifi. 

Any other suggestions?

---

### Post by Peter09 on 2010-03-09
Hi - from what I can see your wireless card is not seen by the kernel. Have you a hardware switch on the laptop for the card and is the card enabled?

---

### Post by 3rdalbum on 2010-03-09
What you need to do is find out the chipset model number for the wireless card (please don't call it a modem - it's just confusing other people who are trying to help, and it's not a modem anyway).

Since it's built-in, it might be internally connected through USB or through PCI. Try putting in the following two commands:

```
lsusb
lspci
```

One of these will show your wireless network device, and show you the model number. Then you can search Google for the model number and the words "Ubuntu 9.10" - for instance, "RTL8187 Ubuntu 9.10"

Usually, wireless drivers are built into the kernel, so you can probably ditch the thing that you downloaded. You may already have the correct driver, but the incorrect driver is taking control of the device and causing it not to work; whatever you find on Google may advise you if this is the case.

And whatever you do, don't try to follow HOWTOs for old versions of Ubuntu. Linux moves so quickly that anything written for 8.10 is likely not going to work, or is going to cause problems, on 9.10.

---

