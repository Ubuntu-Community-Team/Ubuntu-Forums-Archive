---
title: "cannot connect with wireless, 7.10"
date: 2008-02-09
forum: Networking &amp; Wireless
---

### Post by thinman1189 on 2008-02-09
My wireless was working perfectly fine until I decided to install custom firmware on a spare router of mine. I ended up not doing, I forgot my pass to it so I decided to go back online until I remembered. When I did this I went into System>Administration>network and unchecked wireless and connected with wired. Now I can't reconnect wirelessly again. I've tried rebooting my computer and restarting my wireless many times.

Many months ago it was hard to get my card to work. I had to use ndiswrapper. My card is a Belkin F5D7000. info at [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

I have cable internet, with a linksys router downstairs and a dlink repeater upstairs (my computer is upstairs). I have had my computer set with a static IP. The connection is  WEPed.

I tried  to follow the pinned guide but it doesn't seem to work.

In the past I needed to specify the dns servers. When I was going through ipconfig on my dad's windows laptop to see if I had the right info I noticed that in place of the 3 dns servers that used to be there, there were 2 different ones. i tried adding these to the list and restarting but it didn't work.

I've been in the irc for some hours so I've use quite a few commands and I'm not really sure where I stand at the moment. I've used the following commands(in no particular order, just so you know what i've done. some may not make sense, obviously because i don't know what i'm doing):
lshw -C network
ifconfig
sudo /etc/init.d/networking restart
sudo ifconfig eth0 192.168.0.1
route -n
sudo ifconfig eth0 192.168.1.150
sudo ifconfig eth0 192.168.1.1
sudo ifconfig eth0 192.168.0.150
sudo ifconfig ath0 192.168.0.1
ifconfig -a
vi /etc/hosts
vi /etc/network/interfaces
/etc/rc0.d/S15wpa-ifupdown restart

---

### Post by Hightide on 2008-02-10
Hi thinman1189

can you post the output of 

lshw -C network and

iwconfig

regards

:)

---

### Post by evymetal on 2008-02-10
Can you connect wirelessly with another device? Try holding down the "reboot" button on the back of the router for 20 seconds (possibly with the power off), and it should restart the router with a blank password (it will forget all settings)


The next part won't help you fix it, but if you want to understand the commands someone gives you type "man [command]"

e.g. man lshw:

```

DESCRIPTION
       lshw is a small tool to extract detailed information  on  the  hardware
       configuration of the machine. It can report exact memory configuration,
       firmware version, mainboard configuration, CPU version and speed, cache
       configuration,  bus speed, etc. on DMI-capable x86 or IA-64 systems and
       on some PowerPC machines (PowerMac G4 is known to work).


```

(press q to escape the manual)

(I'm assuming you understand what "sudo" does )

---

