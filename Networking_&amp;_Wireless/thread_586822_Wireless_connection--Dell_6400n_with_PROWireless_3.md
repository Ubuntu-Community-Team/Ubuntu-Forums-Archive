---
title: "Wireless connection--Dell 6400n with PRO/Wireless 3945ABG"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Howl01 on 2007-10-22
Hey,
I'm new (today) to Linux and Ubuntu, so please excuse any ignorance I may have, and understand I am not familiar with mist linux commands. Thanks.
I have jus purchased a Dell 6400n notebook which has an Intel PRO/Wireless 3945ABG card.
I am trying to connect to my wireless connection (a NETGEAR DG834G router). Other laptops have been able to connect.

I really don't know what to do, and i am (ironically) powerless to fix it it seems wothout an internet connection.

I've set up a connection using the 'network' option in administrative tools, set the correct password and what i think is the correct name. Ive set it to static IP and typed in my home computers IP address etc.
It still shows a red icon though, and i cannot connect to any websites.
Ive been round in circles trying to do and understand millions of pieces of 'advice' on the internet...but i genuinely havent a clue.

Has anybody got any ideas?(that i can understand)

Thanks alot in advance,
Ben

p.s. I expect you need more information, if you do ask and ill be able to get it.

---

### Post by loveshackdave on 2007-10-22
looks like intel publishes an official driver for linux, have you tried installing it?  you can get it here: [http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/10315/eng/iwlwifi-1.0.0-1.tgz&agr=N&ProductID=2259&DwnldId=10315&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/10315/eng/iwlwifi-1.0.0-1.tgz&agr=N&ProductID=2259&DwnldId=10315&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

---

### Post by Howl01 on 2007-10-22
Yes i downloaded it on my home computer, then transferred it across to my laptop on a usb stick.
I could not however install it on my laptop as I couldn't understand/carry out the installation instructions.
I tried, but it is really quite complicated tbh, and seemed impossible w/out a working internet connection. Thanks though.

---

### Post by loveshackdave on 2007-10-22
I just read the readme that came with those drivers and they do seem overly complicated (what with the mac80211 subsystem and kernel rebuild. ;P). If you let us know where your stuck/what errors your getting, we can help you walk through them though.

Also, you might want to consider using ndiswrapper with the windows drivers instead, this may be less complicated.

to do this, install ndiswrapper with the synaptics package manager (it should come on your distro cd), copy the windows drivers for your card onto your laptop, run the following commands from the directory where you extracted the drivers:

sudo ndiswrapper -i the_inf_file_that_came_with_your_driver.inf
sudo ndiswrapper -l                 (this should say something like: driver present/hardware present)
sudo ndiswrapper -m
sudo modprobe ndiswrapper

---

### Post by loveshackdave on 2007-10-22
hey, I also found this thread: [http://ubuntuforums.org/showthread.php?t=305662](http://ubuntuforums.org/showthread.php?t=305662)
Apparently you need to turn the wifi radio on after reboot by pressing the wifi button or fn f2. Maybe this helps

---

### Post by Howl01 on 2007-10-23
Thanks alot for your help...
I cannot find ndiswrapper on Synaptics...so I assume it's not there, or I'm doing something wrong?

Can anyone answer these questions please?-
1 )Should it show up in 'Network' as 'Wireless Connection' or as my wireless card?
2)The icon next 2Wireless Connection is red--will it be green when it's working?
3 )In the properties i've set it as static IP and typed in the same settings (IP address etc.) as my home computer, which is connected to the router - is this wrong?

Sorry for my lack of brevity....but I really haven't a clue.

If you need any more details jus ask

Thanks,
Ben

---

### Post by subvertigo on 2007-10-23
I have the same notebook (6400) with the same wireless card.

You have to do nothing with that card, except be sure:

- You have "linux-restricted-modules" packet installed
- You have "network-manager" and "network-manager-gnome" installed
- Under System -> Administration -> Restricted driver manager -> you have to enable the 3945 driver.

You can use Synaptic to verify and install those packets. Previously you have to enable restricted repositories.

Then left-click on the network icon in the system tray, so you can connect to your wireless network.

---

### Post by Howl01 on 2007-10-23
I have done all those things (I think i've done that repositries thing)

But it's still not working.

What properties have you set for your Wireless Connection?Because I've played w/mine, so I don't know what they were origonally.

I'm really perplexed tbh...

p.s.is your Wireless Connection icon green?

---

### Post by Howl01 on 2007-10-25
Here is some additional info:

howl@dell:~$ lshw
 *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0b:00.0
                logical name: eth1
                version: 02
                serial: 00:1b:77:d2:b8:0b
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
                resources: iomemory:efdff000-efdfffff irq:16



howl@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:96   Missed beacon:0



howl@dell:~$ sudo iwlist scan
Password:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:B5:CE:F5:9E
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=99/100  Signal level=-22 dBm  Noise level=-22 dBm
                    Extra: Last beacon: 376ms ago

---

