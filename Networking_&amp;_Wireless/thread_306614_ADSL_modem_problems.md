---
title: "ADSL modem problems"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by hardeep27 on 2006-11-25
Hi All,

I've just installed the latest version of Ubuntu on one machine and although everything else works i'm unable to get on the internet using the pci ADSL modem.

The modem is definately working (i have been using it sucessfully on XP for ages). Ubuntu also seems to have detected it(with no obvious issues)as the two entries below are listed in Device manager 

Conexant ADSL Acess Runner PCI Arbitration Device
Access Runner PCI ADSL Interface device 

The thing is when i go to Networking, only my Network card and a dial up modem are available. (which is strange as i dont have a dial up modem installed in the computer???)

Any help on this would be much appreciated.

thanks everyone

Hardeep

---

### Post by cilynx on 2006-11-25
The "dial up modem" that network-manager sees is probably your PCI ADSL.  In my opinion, network-manager is still in its infancy.

Install and run pppoeconf.  It should walk you through what you need.

```
sudo apt-get install pppoeconf && pppoeconf
```

---

### Post by hardeep27 on 2006-12-01
thanks for the info Cilynx. I did type that command in a terminal window but get the following:

Couldnt find package.

Would you have any other ideas? Could you also confirm whether the adsl modem is installed and recognized by Ubuntu given the two entries in device manager (i dont see any icons indicating there are any problems, not sure if Ubuntu even shows resource conflicts etc in that way).

The modem obviously is having problems as under windows when you boot it makes a number of clicking noises. I assume thats just how the hardware works so it should happen no matter what operating system is running. That doesnt happen with Ubuntu. Do i need to install to just install drivers for it?

thanks again.

---

### Post by hardeep27 on 2006-12-01
I'm sorry i just realized i wasnt connected to the internet before running that command. I connected the computer to my router from the network card and ran the command again.

I get pppoeconf is already installed, 0 to remove and 0 not upgraded.
Please become root before running pppoeconf !

I assume that means everything is installed as it should be?

How should i proceed.

Really appreciate the advice.

---

### Post by hardeep27 on 2006-12-01
I also just ran 'sudo pppoeconf' and the following happened:

1.1 Ethernet device found
2. Looking for PPPoE Access Concentrator on eth0
3. Looking for PPPoE Access Concentrator on eth- (multi-modem mode)
4. Sorry i scanned 1 interface, but the Acess Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may also be another unning pppoe process which controls the modem.

thanks again for your time everyone.

---

### Post by cilynx on 2006-12-03
Ok, saying that it can't find the Access Concentrator is the problem.  The modem was plugged into eth0 at the time, yes?

---

### Post by thelinuxguy on 2006-12-09
I am having the same problem. pppoeconf gives me the same message even though my router is connected to eth0 and the "dsl" link is on. In addition, i tried the following:

1) Installed rp-pppoe 3.8 from Roaring Penguin. Ran pppoe-setup. It asks me the expected questions (the same ones that adsl-setup on FC6 does). And it also prints that it is modifying the config files. But when I issue pppoe-start, the command just exits without printing anything on the console. It exits as soon as I press enter. Doesn't seem like its trying to connect.

2) pppoe-discovery says "Timeout waiting for PAD0 packets". My router is connected and working (from XP).

3) pppoe-connect gives the following output
```

Using interface ppp0
connect: pppo <--> /dev/pts/0
LCP: timeout sending Config-Requests
connection terminated
Modem hangup
PPPoE: Timeout waiting for PAD0 packets

```


My router  is in bridge-mode. So there is no DHCP server running there. I am able to connect using WindowsXP and was able to connect using Fedora Core 6 after using the adsl-setup command. I have tried the steps given at [ubuntu help on adsl]("https://help.ubuntu.com/community/ADSLPPPoE") but can't proceed as pppoeconf doesn't get to the stage to ask username password etc.

Any ideas or pointers?

Thanks.

---

### Post by thelinuxguy on 2006-12-09
Ok I am posting from my Ubuntu setup. Finally got it working :D 

Google search reveals that getting an ADSL connection to work using ethernet is the most straightforward. And that getting USB routers to work is a lot of work since the USB drivers need to be downloaded....compiled.....etc....etc.

But I found that Ubuntu 6.06 did a great job at it. Its been around 9 hours since I posted the previous question and was almost at the brink of banging my head. In the last 10 minutes, all that I did was connect my router using the USB interface. No drivers...no nothing. It worked out-of-the-box.

After connecting through the USB interface, ifconfig showed eth1. To test whether my machine could talk to my router through that interface, I typed
```

pppoe -I eth1
(thats capital 'aai' and not 'el' as it looks)

```
It didnt give me any errors. With eth0, it used to timeout. The next step was pppoe-setup from the rp-pppoe-3.8 package which I had installed already. Answered some questions and here I am surfing the net.

Only if this had occurred to me 9 hours earlier ;) 
But I still don't understand why I wasn't able to communicate with my router through the ethernet interface. If someone finds out why, do let the rest of us know.

Thanks.

---

