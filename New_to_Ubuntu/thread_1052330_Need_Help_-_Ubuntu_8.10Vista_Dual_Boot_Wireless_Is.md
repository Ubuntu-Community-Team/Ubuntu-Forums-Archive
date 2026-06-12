---
title: "Need Help - Ubuntu 8.10/Vista Dual Boot Wireless Issue"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by phoenixhawke on 2009-01-27
Ok, I'm a complete newb to ubuntu.  I have it installed, seems to work fine, recognizes my laptop's wireless card, connects to my home network... everything appears to be great.  However, when I booted back into Vista (No comments necessary, I hate vista too), I began to experience wireless issues.  Specifically, my wireless card appears to be recognized by vista, it sees my home network, but when I try to connect, it just won't.  I get a message stating "Did not receive any response from the network".  I did all the normal troubleshooting steps from vista, got fed up and left it for a couple hours, came back, tried to connect again, and it worked.

So I was like, Great! But then I booted into Ubuntu again to play around with it some more, went back to vista to do some work, and once again, no connection.  Nothing i could do to bring it up, but then a few hours later I tried again and it worked.  The next time I rebooted, I didn't even log into Ubuntu (forgot to tell it to switch to Vista), and I had the same problem.  This never happened before i started playing with Ubuntu... help?

I'm typing this up from Vista because I'm afraid to boot back into linux and lose my internet connection again (for the time being, for various reasons, i need to stick with vista as my primary OS).  

This is the model of my wireless card:

Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter

I can supply any other specs at need.  I really want to get this working so i can continue the business of learning about linux

Thanks,
~Brian

---

### Post by mjheagle8 on 2009-01-27
does linux detect your wireless card?
please post the output of 
```
lshw -c network
```

---

### Post by phoenixhawke on 2009-01-27
Yes, as I mentioned ubuntu recognizes the wireless card without problems.  I switched over to run that code you sent (which means when i switch back to vista i won't be able to connect again...)  But hopefully this will get worked out and I'll be able to switch back and forth seamlessly

The output:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:5a:14:61
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:44:ad:08:da
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.3 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: fe:8f:b7:ea:66:42
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by mjheagle8 on 2009-01-28
[https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html](https://help.ubuntu.com/7.10/internet/C/wireless-connecting.html)
did you see this page for help connecting to the internet?  maybe your connection settings are a little screwed up.

---

### Post by phoenixhawke on 2009-01-28
No, the problem is when I switch back to Vista.  Ubuntu is connecting with no problems... The problem with vista seems to be caused by ubuntu, as it only shows up after i've booted ubuntu.  If I only boot from vista into vista, it doesn't happen, but if i boot from ubuntu to vista, then it spazzes out on me.  Really, really weird interaction problem

---

### Post by mjheagle8 on 2009-01-29
thats not caused by ubuntu. ubuntu does not modify the card settings or anything that would cause it to not work. there is nothing i know of that could cause ubuntu to interfere with another system.

---

### Post by phoenixhawke on 2009-01-29
This *only* happens after booting from ubuntu directly into vista.  I discovered late last night that if I power the computer completely off before booting vista, then the card works fine.  I am suspecting at this point that ubuntu (or the linux driver for the wireless card) is not resetting the state of the wireless card properly before shutting down.

---

