---
title: "[SOLVED] The internet hates me"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by TehLeProsy on 2007-10-14
I am attempting to configure the internet on my PC which I had previosly been running windows on.
I have installed the 64 bit 7.04 feisty( i have an AMD fx-53 with an asus sk8v motherboard) I have an integrated 3com 3c940 10/100/1000Base-T hard wired ethernet connection.
I am trying to get my ip address using Dhcp which was working fine on the computer while I had windows installed, but isn't working now that I switched to Feisty. I still have a windows install on one of my drives but is broken, and I have only left it there so I could pull my files of the old hard drive. I have done "sudo lspci" and the terminal reports back my ethernet controller, but I can't connect to the internet.

I ahve been trolling the forums for the last couple of days and alot of peoples problems looked similar but none of the fixes have worked.

Any help would be greatly appreciated I don't want to have to go back to Windows.

---

### Post by TehLeProsy on 2007-10-14
Bump.

---

### Post by Lambert on 2007-10-14
A simple first step. Power down your router/dhcp server for 30 seconds and then power back up.

After that open a terminal and try these commands.

```

sudo ifdown eth0

sudo ifup eth0

```

replace eth0 with whatever inteface name you're given. If you're not connected now then try this command.

```

sudo dhclient eth0

```

---

### Post by TehLeProsy on 2007-10-15
Bump

---

### Post by TehLeProsy on 2007-10-15
Thanks I'll give that a try.

---

### Post by TehLeProsy on 2007-10-15
Lambert, 
 I tried reseting my router, and using the commands you posted.
It tried listening through my eth0 a few times, but I didn't receive any DHCPOFFERS, and there were no working leases in my persistent database.

Thanks, any other suggestions would be greatly appreciated.

---

### Post by TehLeProsy on 2007-10-15
oh I also tried navigating to the routers Ip address with firefox but it could not find the server.

---

### Post by TehLeProsy on 2007-10-15
Bump.

---

### Post by noob12 on 2007-10-15
What driver is associating to the device?
```

sudo lshw -C network

```

What does **sudo ethtool eth0** (or whatever your actual interface name is) have to say about the link state?

---

### Post by TehLeProsy on 2007-10-16
ok, I  the driver is  "skge version 1.9"

and  sudo ethtool says that the link was detected.

Thanks.

---

### Post by TehLeProsy on 2007-10-16
Bump.

---

### Post by noob12 on 2007-10-16
Can you try to set your address manually (static address, gateway, and dns) and see if things work in that case?

Are you running any firewall rules **sudo iptables -nL** ?

---

### Post by TehLeProsy on 2007-10-17
I still can't connect when using a static IP addy, as for firewall rules I don't think so "Chain INPUT", "Chain FORWARD", and "Chain OUTPUT" are all set to accept, And the destinations are "prot opt source".

     I am going to try assigning a static IP addy from my router to my mac address next.

Thanks.

---

### Post by TehLeProsy on 2007-10-17
Bump.

---

### Post by TehLeProsy on 2007-10-17
Bump.

---

### Post by TehLeProsy on 2007-10-18
Bump.

---

### Post by jbaerbock on 2007-10-18
Another problem you may be having, is your driver 64-bit compatable? I had the same problem when installing a 32bit broadcom driver in a 64bit Ubuntu. Good luck though.

---

### Post by TehLeProsy on 2007-10-18
Jbaerbock,
    Thanks for the the comment. I haven't been able to find anything specific about my chipset and the skge driver, but the driver does seem to have a lot of issues.

When you had your problems were you running Fiesty? or "skge version 1.9"?
 most of the problem I have found were with older versions of the driver.

Thanks.

---

### Post by jbaerbock on 2007-10-18
I had the problem with a different card (broadcom) but I was running Feisty 64-bit. Basically the way drivers work differ some in 64-bit vs. 32-bit environments. So in a lot of cases a 32-bit driver will either not work at all or work poorly because of this. Try a google search for your card's driver in 64-bit format. I did that and found someone who had ported the 32-bit driver to 64-bit.

Another question is did you install the driver via ndiswrapper or its GUI equivelant? Ndiswrapper also has a 64-bit version vs. a 32-bit version so that as well may be a problem. Also after installing a windows driver via ndiswrapper or its GUI you must blacklist the default driver ubuntu wants to use for it. However if your harware is found and it just wont connect then this should not be the case.

---

### Post by TehLeProsy on 2007-10-18
Hmm, I am not sure. 
    I will have to take a look for my chipset and driver. 
However, I am using the default driver installed by the 64-bit ubuntu distro for my card. 
I have not used any programs like Ndiswrapper. though I will take a look and see if theyu have a driver for my network device, and if they do I will try that.
 I think I will also check if the winxp driver will work with Fiesty.

Thanks.

---

### Post by jbaerbock on 2007-10-18
Yeah what some people do is they use ndiswrapper to install the windows driver. That's what I did with my broadcom and it worked (now that I am back with a 32-bit OS). Just open up synaptic package manager and search for ndiswrapper and it will find a GUI version of it which works best.

---

### Post by Cannaregio on 2007-10-18
One pragmatic and relatively quick possibility is to check if your settings work with DIFFERENT Gnu/Linux distributions (for instance Mint, Sabayon, PcLinuxOS...). Start with live distros.

Then you'll know for sure if it is a ubuntu-related problem or a driver related problem.

---

### Post by TehLeProsy on 2007-10-18
Jbaerbock, great I have a copy if the winxp driver lying around I will try that next.
    And thanks Cannaregio, I will start downloading the live cd for dome other 64-bit distro's and see if they work any better. 
      I have my doubt's though, I TRIED INSTALLING "BREEZY BADGER" a year or two ago and encountered the same problem with configuring my network acess.
All the same I will pull down copy's of Mint, Sabayon, PCLinusOs, and any other 64-bit distro I can find with a live cd.

Thanks.

---

### Post by TehLeProsy on 2007-10-18
I am puliing down two other 64-bit linux distro's and one 32-bit distro. I will try the live cd for them, and see if the internet works when not using ubuntu.

---

### Post by TehLeProsy on 2007-10-19
Bah; I have a couple of 64 bit distro' and a couple of 32 bit distro's to try out now. However it will be a while before I can do that because a power outage just blew either my psu or mother-board. so I need to fix that first.
At any rate, thanks to everyone that had a  suggestion, I will probably be back to tryying to deal with the nework problems next week.

Thanks.

---

### Post by TehLeProsy on 2007-10-20
Well, yayish.
 I replaced my psu, and shockingly enough my comp stopped randomly crashing.
and I am presently trying a live cd for the 64 bit distro of sabayon, and the internet is working right off the bat.

---

### Post by TehLeProsy on 2007-10-20
well I have tried sabayon and mint, one 64bit distro and one 32bit distro. The internet works with both immediatly. and bizarrely enough Mint is even running the same skge driver version 1.9 that Ubuntu is. So at the moment I am re-downloading Feisty Fawn to see if the their was a error on the cd I installed from.

---

### Post by TehLeProsy on 2007-10-20
Well, the problem seems to have been with the Iso of ubuntu I pulled down. There must have been an error during the download or the burn, Because I just downloaded and burnt a fresh copy of the live cd and the Internet is working.

So thanks to Lambert, Noob12, jbaerbock, and Cannaregio, I appreciated the assistance.

---

### Post by Cannaregio on 2007-10-20
Happy to hear that.
Please post SOLVED in thread title.
All the best.

---

