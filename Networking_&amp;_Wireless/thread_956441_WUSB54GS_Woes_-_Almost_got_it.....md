---
title: "WUSB54GS Woes - Almost got it...."
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by PSUinDC on 2008-10-23
Edit: I am infact using WUSB54GS**v2**

Let me preface this with 2 things:
1) These forums are an EXCELLENT source of help. Thank you all for posting information, it's been great help to me so far.
2) I'm a complete Linux noob.  Well, not complete.  I use a unix command line for some operations at work, but I know nothing about the Linux OS.

I'm running Kubuntu 8.04 Hardy. So, I wanted to get my WUSB54GSv2 wireless adapter to work, and through some reading found out that its been the bane of many peoples existences.  I used a tutorial on these forums to use ndiswrapper to install the drivers, and got them installed.

After installing them, I went to the system settings, and found that it was indeed recognized, so I configured it with my routers ESSID and WEP Key. I saved the profile, exited out, unplugged my ethernet cord, and tried to surf wirelessly.  Didn't work.  Went back to check my settings in the network config, none of them saved!  Tried again, same thing, didn't save.  Tried restarting, and they still wouldn't save.

Read a little more, and found out that you can set your WEP and ESSID using 'sudo iwconfig wlan0 <command>'.  So,  I set that up, and ran a 'sudo iwconfig wlan0' and it showed a connection with 85/100 quality.  Awesome!  Went to my browser.... no dice.  So I thought I'd try something via the command line.  I ftped from the command line to my personal webspace SUCCESSFULLY. 

Synopsis:
- Running Kubuntu 8.04 Hardy
- Installed WUSB54GSv2 drivers seemingly successfully
- System Settings for network won't save (WEP and ESSID)
- Got settings to save via 'sudo iwconfig wlan0'
- Can connect via console using ftp, but can't surf with browser
- iwconfig settings won't save past a restart

Any ideas what is going on?

---

### Post by Ayuthia on 2008-10-23
This might be a silly question, but after you did the iwconfig, did you do:
```
sudo dhclient wlan0
```

EDIT: Also, when you type lshw -C network, does any info show up about your card?  I was thinking that the device is either a 4318 or a 4306.  Both are not having too many happy days in Hardy...  I have had the worst time trying to get those cards to work.

---

### Post by PSUinDC on 2008-10-23
> **Ayuthia said:**
> This might be a silly question, but after you did the iwconfig, did you do:
```
sudo dhclient wlan0
```

EDIT: Also, when you type lshw -C network, does any info show up about your card?  I was thinking that the device is either a 4318 or a 4306.  Both are not having too many happy days in Hardy...  I have had the worst time trying to get those cards to work.

Yeah I did.  I am at work currently, but I don't remember typing 'lshw -C network' yet.  I'll try.   I did do 'lusb' and it shows up there.

---

### Post by PSUinDC on 2008-10-23
Heh, maybe I just need to learn how to push ethernet wire through my walls :)

---

### Post by Ayuthia on 2008-10-23
When you get back, you might try to ping a website:
```
ping -c3 www.google.com
```
You might also try:
```
route
```It will help show you where you are connected.

As for the wire, why bother putting them in the walls?  Get some colorful wires and decorate!!!!

---

### Post by PSUinDC on 2008-10-23
Meh, I just bought a townhouse and I'm trying to stay away from the "ghetto fab" college style ethernet cord running up the ceiling :)

---

### Post by PSUinDC on 2008-10-23
Any ideas why the iwconfig settings wouldn't save to the system after restarting?  That seems like a problem to me.

EDIT: I found a post relating to iwconfig not saving.  Something about editing the interfaces file... so hopefully that will work.

---

### Post by pytheas22 on 2008-10-23
When you ftp'd, did you connect to a domain name (e.g. 'ftp myserver.com') or directly to an IP ('ftp 128.30.60.60')?  If you used a domain name, then DNS is probably not the problem, but if you were connecting directly to an IP, then I would highly suspect DNS issues as the culprit.

If DNS is not the problem, it could be an issue just with http traffic.  If you type:
```

wget google.com
```

in a browser, does it work (it should download the home page of google.com and save it to your working directory)?  wget works over http, so if it works but Firefox doesn't, then I'd blame Firefox.  It would also be interesting to know if ping works, since this is a third service.

It's easy enough to make your iwconfig changes persist through reboots once we get the rest of this straightened out.

---

### Post by PSUinDC on 2008-10-23
I connected by ftp with my DNS hostname, not IP.  I'll try the wget when I get home from work (t-minus 3hrs).  So, check back later tonight :) 

Thanks for all the help.

---

### Post by PSUinDC on 2008-10-23
Ok, so I'm home from work, and here's a few things:

- I tried all the commands that you all talked about, and all signs pointed to me having an internet connection.  So, I thought "Hey, maybe its the browser?". A quick apt-get install firefox, and I was surfing the net. Some reason, Konqeuror didn't like my connection.

- I still can't get my WEP and essid to save after starting up.  Also, I need to "sudo modprobe ndiswrapper" every time I restart to get the damn wlan0 to show up.  I know very little about the "kernel" but I think that I'm modifying the kernel and maybe not restarting with the new one? 

I tried editing the /etc/network/interfaces file to only have a wlan0 entry instead of a 'lo' entry, but for some reason THAT isn't saving either. 

Any ideas here guys? I don't want to have to do this every time I start up... ESPECIALLY since my damn eth0 device keeps "enabling" itself it seems, and when both eth0 and wlan0 are enabled, they seem to fight each other.

So... onto a slightly different problem gents.  Thanks so far!

---

### Post by Ayuthia on 2008-10-23
> **PSUinDC said:**
> Ok, so I'm home from work, and here's a few things:

- I tried all the commands that you all talked about, and all signs pointed to me having an internet connection.  So, I thought "Hey, maybe its the browser?". A quick apt-get install firefox, and I was surfing the net. Some reason, Konqeuror didn't like my connection.

- I still can't get my WEP and essid to save after starting up.  Also, I need to "sudo modprobe ndiswrapper" every time I restart to get the damn wlan0 to show up.  I know very little about the "kernel" but I think that I'm modifying the kernel and maybe not restarting with the new one? 

I tried editing the /etc/network/interfaces file to only have a wlan0 entry instead of a 'lo' entry, but for some reason THAT isn't saving either. 

Any ideas here guys? I don't want to have to do this every time I start up... ESPECIALLY since my damn eth0 device keeps "enabling" itself it seems, and when both eth0 and wlan0 are enabled, they seem to fight each other.

So... onto a slightly different problem gents.  Thanks so far!

Not for sure if you have done this or not, but it might help if ndiswrapper is in /etc/modules so that it will load on boot:```
echo ndiswrapper | sudo tee -a /etc/modules
```

Hopefully that will help get you a little further.

EDIT: I forgot that you are using Kubuntu.  Sometimes Konqueror will not respond to the internet unless it is connected through network manager.  I know that Konqueror is sometimes a little sensitive.

---

### Post by pytheas22 on 2008-10-23
You could solve your problem by writing a boot script in order to run at boot the commands necessary to connect.  To do so, open up a blank file for your script:
```

sudo kate /etc/init.d/wifi-fix.sh
```

Add to the file these lines:
```

#!/bin/bash

ifconfig eth0 down
modprobe ndiswrapper
ifconfig wlan0 up
**iwconfig wlan0 ... put in arguments to connect to your network**
sudo dhclient wlan0
```

Then save and close the file, and run these commands so that this script will be run each time your computer starts:
```

cd /etc/init.d
sudo chmod +x wifi-fix.sh
sudo update-rc.d wifi-fix.sh defaults
```

This shoudl do the trick, provided that the script contains the appropriate commands to get you online.  Please let us know if it works.

(You could also have edited /etc/network/interfaces, but in my opinion writing a boot script is easier and they both accomplish the same thing.)

---

