---
title: "[Lubuntu] nm-applet error after hibernation 14.04"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by steve234 on 2015-11-07
Hi there, 

I'm on 14.04 and am getting a "networking disabled" error after hibernation. I know the kill > re-launch nm-applet workaround, but am looking for a permanent fix.

Network setup is:

```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:4d:f4:1b:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-31-generic firmware=N/A ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:f3:db:de
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:27 ioport:2000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff 
```

Grateful for any help

Steve

---

### Post by Bucky Ball on 2015-11-07
Hello again. :) When you come out of hibernate, click the network icon. Is 'Enable Networking' disabled, i.e. not ticked, by any chance?

Enable it again and that should, hopefully, give you network again more easily while we dig.

* Also, click the network icon> Edit> Wireless name> Edit> General. Is the first box ticked, 'automatically connect to this network when available'?

---

### Post by steve234 on 2015-11-07
Hi mate,

There is no option to enable - the menu becomes simply one item which says "networking disabled" and is ghosted out.

screenshot below - doesn't actially show the ghosted menu because it's hard to use scrot when focussed on something other than terminal window.

[ATTACH=CONFIG]265402[/ATTACH]

---

### Post by Bucky Ball on 2015-11-07
I'm readin' you. Does the no network after hibernate issue only happen when you are on battery? Same when plugged in? Anyway ...

Try this:

```
sudo nano /var/lib/NetworkManager/NetworkManager.state
```

Make sure they are all set to 'true', e.g.:

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
```

And how about this in a terminal when it dies after hibernate?

```
sudo service network-manager restart
```

Does that bring it back? This might sound silly, but you don't have an ethernet cable plugged in at the same time as this is happening do you?

* Wonder if [this]("http://ubuntuforums.org/showthread.php?t=1505217&p=9435561#post9435561") might apply ... It's old but you never know.

---

### Post by steve234 on 2015-11-07
All the "true"'s are true (so to speak).

funnily I can't provoke the error now (on mains or battery). 

I need to hit the DIY this arvo, so will hibernate it now and resume later to see what it does.

S

---

### Post by Bucky Ball on 2015-11-07
Curious to know what does happen ... :-k

Hopefully it's fixed itself. Next time you're online, run these:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

And reboot. See how it goes. (That won't upgrade your release to a newer one.) If it throws anything unusual, post it.

---

### Post by steve234 on 2015-11-07
soz - forgot to say - no Ethernet cable...

Just got back - thawed (if that's the right term) and it was broken. So battery power defo causes it. 

Restarting the service worked perfectly - is there any way I can wite that into a shell script to launch on resume/thaw (whatever it's called) like sleepwatcher does on Mac. (I had a similar issue with a wifi card needing to be cycled on wake from sleep on Mac).

---

### Post by steve234 on 2015-11-07
Did the various updates, a few things got updated on the "upgrade" nothing needed to be updated on the dist-upgrade.

I put it back on battery power and it still requires the netman service restart workaround :( 

I wonder if a BIOS setting is messing it up - like one of the fast boot etc settings?

---

### Post by Bucky Ball on 2015-11-07
So you're saying it only gives this problem on battery? Not when plugged into the wall?

---

### Post by steve234 on 2015-11-08
As far as I can tell yes - only on battery

---

### Post by Bucky Ball on 2015-11-08
I created a shell script for you but then the forum wouldn't let me upload it. There must be a knack. So you're going to need to try this the hard way. 

Open a terminal and copy and paste the following as they need to be exactly as they are written here, control+shift+c or v for copy past in lxterminal.
```

sudo touch /etc/pm/sleep.d/10_resume_network
sudo nano /etc/pm/sleep.d/10_resume_network
```

Paste this in to the file (exactly as is) then control+x to close and y to save:

```
 #!/bin/sh
 #Tell Network Manager that resume was successful
case "$1" in
         thaw)
           /usr/bin/nmcli nm sleep false
          ;;
 esac
```

Then:

```
sudo chmod 775 /etc/pm/sleep.d/10_resume_network
```

Log out or reboot then hibernate, wake up. Any change? If not, delete this new file by:

```
sudo rm /etc/pm/sleep.d/10_resume_network
```

Thanks for info to Patrick Vande-Walle [here]("http://patrick.vande-walle.eu/software/ubuntu-13-10-no-network-after-resuming-from-hibernation/").

---

### Post by steve234 on 2015-11-08
Cheers for that - sadly it then refused to hibernate (just logged out without turning the machine off)... 

So I deleted the file and now it'll hibernate again

---

### Post by Bucky Ball on 2015-11-08
Follow previous instructions but try this in the file 10_resume_network:

```
#!/bin/sh

case "${1}" in
    resume|thaw)
        service network-manager restart;;
esac
```

... from [this link]("http://askubuntu.com/questions/450688/network-connection-error-after-suspend-ubuntu-14-04"). Then:

```
sudo chmod 775 /etc/pm/sleep.d/10_resume_network
```
Which command were you using to relaunch it last time? You could try that in place of 'service network-manager restart'.

---

### Post by steve234 on 2015-11-08
service network-manager restart was working for me - so far so good on the hibernation front. we'll see how we get on in the week in general use.

---

### Post by Bucky Ball on 2015-11-08
That is good news! We'll see how it goes for a day or two. Still no issues, please see first link in my signature and mark as solved. If things go pear-shaped anytime after that you can mark it unsolved again and we can keep digging, but I have my fingers crossed.

Pretty obscure bug, that one. :-k

---

