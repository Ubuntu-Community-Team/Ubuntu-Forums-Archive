---
title: "Madwifi sucks... very low signal compared to ndiswrapper"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by jeznet on 2007-04-11
I have a D-Link DWL-G510 and I just recently installed Feisty Fawn beta. I liked it how it automatically detected my wifi card, however its has a poor performance.

First, my signal is less than 30% compared when I dual booted to windows and using another linux distro using ndiswrapper which is more than 50%.

Second, transfer rates when downloading files are not so good. When I download from repositories and websites I get around 40kb/s, which should be around 120kb/s average when I'm using windows.

Third, response times are slow. I checked my DNS configuration and theres nothing wrong with it. My router is configured as static addressing so I can enter my info exactly how I want it...

My theory is that I don't think its the configuration but the driver. When it roams, and connects to my next door neighbor's AP, its still slow.

So I tried uninstalling madwifi to be replaced with ndiswrapper (which works perfectly fine in Fedora). But I'm having no luck trying to completely remove it and get ndiswrapper running so I could see a wifi device in ifconfig. I even installed the gui frontend for ndiswrapper and all it said after added my .inf file was 'No hardware' found. It could be that its conflicting with the atheros driver, which I'm trying to remove.

Sigh..What to do, what to do...

---

### Post by spd106 on 2007-04-11
If you want to disable the atheros driver, try blacklisting the ath_hal and ath_pci modules in the /etc/modprobe.d/blacklist file.

---

### Post by lawentzel on 2007-04-11
I have had no problems at all with the wireless drivers in 7.04.  Prior to it, I had installed Madwifi myself and again had no problems.  I am using a D-Link card as well, so the problems may lie else where.  Just my two cents.

---

### Post by jeznet on 2007-04-11
I finally got it to work...The signal is now around 50%.  switched to OpenDNS, the response time is a little better now.The only thing is I'm still getting low transfer rates around 20kb/s. I disabled ipv6 with no improvement. Is it possible to tweak packet size?

---

### Post by masjito on 2007-04-23
any one have solutions for this bugS? plsss help.. i have same problem, low signal

---

### Post by s0larian on 2007-04-23
I have exactly the same problem: very unstable and slow wireless connection. I am using a Thinkpad T40p with Atheros IBM a/b/g II wireless card and Linksys router. In XP the connection is rock stable and zero dropouts, so I cannot blame the hardware.

---

### Post by jeznet on 2007-04-24
Here's my partial solution: 

First blacklist the atheros driver module ath_pci 
 vi to /etc/modprobe.d/blacklist add ath_pci or just type ***sudo echo "ath_pci" >> /etc/modprobe.d/blacklist***. Then reboot the computer. 

Second. install ndiswrapper ***sudo apt-get install ndiswrapper***. Get your wifi drivers from your CD or floppy disk and use type*** ndiswrapper -i /pathtodriver/somenet.inf***. Also type in ***ndiswrapper -m *** just to make sure its activated during boot sequence.

Check ***ifconfig*** and ***iwconfig*** to see if your wifi device is enabled. You can now proceed setting up your access points and keys via upper right corner icon of the desktop.

-Jez

---

### Post by stchman on 2007-04-25
> **jeznet said:**
> I have a D-Link DWL-G510 and I just recently installed Feisty Fawn beta. I liked it how it automatically detected my wifi card, however its has a poor performance.

First, my signal is less than 30% compared when I dual booted to windows and using another linux distro using ndiswrapper which is more than 50%.

Second, transfer rates when downloading files are not so good. When I download from repositories and websites I get around 40kb/s, which should be around 120kb/s average when I'm using windows.

Third, response times are slow. I checked my DNS configuration and theres nothing wrong with it. My router is configured as static addressing so I can enter my info exactly how I want it...

My theory is that I don't think its the configuration but the driver. When it roams, and connects to my next door neighbor's AP, its still slow.

So I tried uninstalling madwifi to be replaced with ndiswrapper (which works perfectly fine in Fedora). But I'm having no luck trying to completely remove it and get ndiswrapper running so I could see a wifi device in ifconfig. I even installed the gui frontend for ndiswrapper and all it said after added my .inf file was 'No hardware' found. It could be that its conflicting with the atheros driver, which I'm trying to remove.

Sigh..What to do, what to do...

It might be that the madwifi drivers were not properly installed.  Follow my procedure to install madwifi properly.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I have no trouble at all.  I can surf the net anywhere in my house and get AWESOME transfer rate.  I would uninstall the ndiswrapper and do the procedure I have.

I hope this helps.

---

### Post by masjito on 2007-04-25
Thank`s jeznet

Problem solved with ndiswrapper :)
I got more than 75% signal streng now, reconfigure with ndiswrapper 1.4.2 

Thanks thanks very much :)

---

