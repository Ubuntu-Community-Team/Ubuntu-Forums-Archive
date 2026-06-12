---
title: "Sorry folks need help setting up"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by Peleus on 2005-11-03
Ok guys, to give you the run down of what I've got at the moment. 

ADSL Modem/Router >> Swtich >> Plug one ethernet to computer, Plug two ethernet to laptop, Plug 3 going to D-Link Access Point DWL-2100AP. 

On the other side of that is my computer which I am trying to set up, running a DWL-G520 card, which as far as I can tell is working and installed. 

I'm using Ubuntu 1.10 and I have tried mucking around in the network options but it just seems like I can't get anything to work. Can't ping my router either, just get the response network not avalible. 

To help out I've tried to show you guys the responses I get for certain commands below, sorry I had to save them into open office to transfer them to the computer I'm trying on. 

lsmod
[www.iinet.net.au/~djcatterall/lsmod.odt](www.iinet.net.au/~djcatterall/lsmod.odt)

ifconfig
[www.iinet.net.au/~djcatterall/ifconfig.odt](www.iinet.net.au/~djcatterall/ifconfig.odt)

iwconfig
[www.iinet.net.au/~djcatterall/iwconfig.odt](www.iinet.net.au/~djcatterall/iwconfig.odt)

dmesg
[www.iinet.net.au/~djcatterall/dmesg.odt](www.iinet.net.au/~djcatterall/dmesg.odt)

Any help would be greatly appreciated. 

Oh, I can access the access point via the laptop plugged in via ethernet, so I know the IP assigned on the network is 192.168.1.50 if that helps at all. (Router 192.168.1.254). I am of course willing to output any commands you want me to try, to help sort the problem. Anything I have left out or any comments at all in aid would be greatly apprecaited, this is starting to drive me nuts! :D

---

### Post by tehwa on 2005-11-03
iinet eh? Im on iinet...Represent.

What is the output of ifdown/ifup in succession:```
sudo ifdown wlan0
sudo ifup wlan0
```
And perhaps post the content of ```
/etc/network/interfaces
```

---

