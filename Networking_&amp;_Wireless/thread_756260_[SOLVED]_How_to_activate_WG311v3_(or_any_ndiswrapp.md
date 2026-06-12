---
title: "[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by prshah on 2008-04-15
OK There seems to be a lot of people having trouble with NetGear's WG311v2/WG311v3. I just recently installed a new system and present below the full, gory details of a quick and easy wireless activation. Note that while this is specifically for the NetGear WG311v3, you can use this for any ndiswrapper based wireless card installation. 

For the impatient: Commands summary:
1) What kind of wireless do you have? ```
lspci | grep -i wireless
```
2) Install ndiswrapper (Can be installed from the CD, no need for an Internet connection) ```
sudo apt-get install ndiswrapper-utils*
```
3) Copy your NetGear .INF file (note; the location given here is the most likely; please check your exact location)```
mkdir inf && cp /media/sda1/windows/inf/WG311v3/* inf/
```
4) Change directory to where your INF file is located ```
cd inf
```
5) Get your INF file "wrapped" with ndiswrapper ```
sudo ndiswrapper -i WG311v3.INF 
```
6) Verify your device has been found ```
ndiswrapper -l
```
7) Add information about your "wrapped" device driver to the module library```
sudo ndiswrapper -m
```
8) Load your "wrapped" device driver ```
sudo modprobe ndiswrapper 
```
9) Check if your device has been detected```
iwconfig
```
10) Connect to your wireless network (Note my wireless network id is "netgear" because my access point is also of netgear make, it has nothing to do with the brand of the wireless card)```
sudo iwconfig wlan0 essid NETGEAR
``` 
11) Get DHCP information```
sudo dhclient wlan0
```
12) Check your DNS server settings ```
cat /etc/resolv.conf
```
13) Can you ping your DNS server (Get the address from the output of the above command) ```
ping 192.168.1.1
```
14) Can you ping a website? ```
ping www.google.com
```
15) That's it you're done!

For more information on each step, including expected output, explanations and usual errors and solutions continue below...

Notes:
	a) Output lines are in [color=blue]blue[/color]

The first command lists all the pci cards in your system and filters out entries which have the word wireless in them. Note that this may also show you other devices, so you have to figure out which line is relevant to you. (Usually it shows just one, and even if it shows more, it's pretty easy and common-sensey to figure out which card you have). For my WG311v3, I get the output> ```

geetha@geetha-desktop:~$ lspci | grep -i wireless
[color=blue]01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/color]
```

At this point you can run the command ```
iwconfig
``` to check if your card has already been detected and setup; if it has, you can skip to step 10. In my case, it's not detected, as mentioned by the message "no wireless extensions"> ```

geetha@geetha-desktop:~$ iwconfig
[color=blue]lo        no wireless extensions.
[/color]
```

Now we install ndiswrapper which acts as a cocoon around a windows driver and allows it to be used by linux. Note that the ndiswrapper-utils package and it's dependencies are present on the CDROM, so if you leave/put it in the drive, you don't need an already working Internet connection.
> ```

geetha@geetha-desktop:~/inf$ sudo apt-get install ndiswrapper-utils-1.9
[color=blue]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-utils-1.9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/33.5kB of archives.
After unpacking 131kB of additional disk space will be used.
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 88945 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.43-1ubuntu2_i386.deb) ...
Setting up ndiswrapper-utils-1.9 (1.43-1ubuntu2) ...
[/color]
```

The following bunch of commands copies the WG311v3 driver from their windows location (This is in a dual boot setup) and verifies their existence. If you don't have a dual-boot, then it's a little difficult to get the WG311v3 drivers. While most manufacturers give a driver CD, NetGear ships a "Smart Wizard" installation CD, where the drivers are not in the open but packed inside a windows installation program. So you will either have to get it off another computer, or ask around here, or download it from a drivers site such as [www.driverguide.com](www.driverguide.com). In this case, the windows install is located at /media/sda1. Note that CASE (UPPER/lower/Mixed) is very important. There's no real need to copy the files to your home directory; you can just as well "cd" to the driver directory and continue with the rest of the commands.
> ```

geetha@geetha-desktop:~$ ls
[color=blue]Desktop    Examples  Music     Public     Videos
Documents  Home.jpg  Pictures  Templates[/color]
geetha@geetha-desktop:~$ mkdir inf
geetha@geetha-desktop:~$ cp /media/sda1/windows/inf/WG311v3/* inf/
geetha@geetha-desktop:~$ cd inf
geetha@geetha-desktop:~/inf$ ls
[color=blue]CopyWHQLDriver.exe  WG311v3.cat  WG311v3.INF  WG311v3.sys  WG311v3XP.sys
[/color]
```


The next command will "wrap" the windows driver for use in linux.
> ```

geetha@geetha-desktop:~/inf$ sudo ndiswrapper -i WG311v3.INF 
[color=blue]installing wg311v3 ...[/color]
```

This command will tell us if everything went well, and if the driver we have chosen is correct. Note that this may also display an "alternate" driver suggestion. The alternate suggestion will be a native linux driver, which may (and usually does) give better performance than "ndiswrapper"ed drivers. If it in fact suggests an alternate, you should skip to command #8 and try the suggested name in command #8, rather than "ndiswrapper" and continue with the rest of the commands. If that fails, you can always pickup from this point anytime. In this case, there is no "alternate". Note that it detects the device; if it does not show the device as "present" then you are probably using the wrong driver. You can feel free to continue but it will be rather pointless. Once you get the correct drivers, you can continue from the previous step.

> ```

geetha@geetha-desktop:~/inf$ ndiswrapper -l
[color=blue]wg311v3 : driver installed
        device (11AB:1FAA) present
[/color]
```

This command adds information about your "wrapped" device driver to the module library
> ```

geetha@geetha-desktop:~/inf$ sudo ndiswrapper -m
[color=blue]adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...[/color]
```

Now, we activate the driver: If you have an "alternate" driver suggestion, use that instead of "ndiswrapper" below, unless you have already tried it and it doesn't work. Note that if the command is successful, there will be NO output, so you should run the command "iwconfig" to make sure that your device has indeed appeared. Note the new entry (in **bold**, as compared to the output of the same command before.

> ```

geetha@geetha-desktop:~/inf$ sudo modprobe ndiswrapper 
geetha@geetha-desktop:~/inf$ iwconfig
[color=blue]lo        no wireless extensions.

[b]wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/b][/color]
```

This command restarts the networking service; it is usually not required, but if your last command still doesn't show any new interfaces, it a good trouble-shooting step. In this case, there is no change.

> ```

geetha@geetha-desktop:~/inf$ sudo /etc/init.d/networking restart
[color=blue] * Reconfiguring network interfaces...                                   [ OK ] [/color]
geetha@geetha-desktop:~/inf$ iwconfig
[color=blue]lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/color]
```

From this point on, you can either continue in the terminal, or switch to the GUI. Usually, in Ubuntu, clicking on the "network manager applet" will now display any wireless networks within range. This is the preferred method, because it will setup a permanent connection that will persist across reboots. If you would like to continue manually, commands from #8 onwards will have to be done every reboot. If you wish you can add the commands to your "/etc/rc.local" file so that they will be automatically executed every startup. There are other ways also (discussed below).

Now we assign an access point to your wireless card: In this case, to keep things simple, I am connecting to a "unsecured" access point.

Note the first command gave an error because I forgot to add the "sudo" (for super-user mode). A successful command gives no output, so a fresh "iwconfig" command lets us see the change from the last result (in **bold**). Your results will be different, but in the same format.
> ```

geetha@geetha-desktop:~/inf$ iwconfig wlan0 essid NETGEAR
[color=blue]Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.[/color]
geetha@geetha-desktop:~/inf$ sudo iwconfig wlan0 essid NETGEAR
geetha@geetha-desktop:~/inf$ iwconfig
[color=blue]lo        no wireless extensions.

wlan0     IEEE 802.11g  **ESSID:"NETGEAR"  **
          Mode:Managed  **Frequency:2.462 GHz  Access Point: 00:1A:2C:54:08:0D   **
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
**          Link Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/color]
```

The next command checks if the card has been assigned an IP address for Internet/network communication. Usually this is done automatically through a service called DHCP. The address is assigned by your DHCP "server" (usually your broadband router/"modem", in home networking). For static IP, you should assign your IP manually at this point. In this case, no IP address has been assigned to the wireless, and hence it is not yet usable.

> ```

geetha@geetha-desktop:~/inf$ ifconfig wlan0
[color=blue]wlan0     Link encap:Ethernet  HWaddr 00:18:4D:EE:8B:4A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:ff8e0000-ff8f0000 
[/color]
```

Now we inform the system to find a DHCP server and get an IP address assigned to the wireless card. The "DHCPOFFER" and "DHCPACK" output tells us the address of the DHCP server. (Marked in [color=green]green[/color]), you should note this for later use further down.

> ```

geetha@geetha-desktop:~/inf$ sudo dhclient wlan0
[color=blue]Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:18:4d:ee:8b:4a
Sending on   LPF/wlan0/00:18:4d:ee:8b:4a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPOFFER from [color=green]192.168.1.1[/color]
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from [color=green]192.168.1.1[/color]
[color=red]grep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory[/color]
bound to 192.168.1.22 -- renewal in 38674 seconds.
[/color]
```

Now, note the **change** in output for the "ifconfig" command:
> ```

geetha@geetha-desktop:~/inf$ ifconfig wlan0
[color=blue]wlan0     Link encap:Ethernet  HWaddr 00:18:4D:EE:8B:4A  
**          inet addr:192.168.1.22  Bcast:192.168.1.255  Mask:255.255.255.0**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
**          RX bytes:899 (899.0 b)  TX bytes:3049 (2.9 KB)**
          Interrupt:11 Memory:ff8e0000-ff8f0000 
[/color]
```

Note in the previous output the errors marked in red; you cannot browse the net without a DNS "translator" that converts names such as [www.google.com](www.google.com) to an internet IP address. Usually, in home networking / broadband situations, your DHCP and DNS servers will be the same; so you should check your "/etc/resolv.conf" file, which tells the system where to find the DNS server. Note that sometimes this may contain something other than the DHCP server address; that is normal as well, depends on your ISP's setup. As long as you are using DHCP (Automatic IP configuration), you cannot make changes to this file. (Well you can, but it will be wiped out later). In this case, the [color=green]DNS server[/color] is the same as the DHCP server. This file should _not_ be blank!

> ```

geetha@geetha-desktop:~/inf$ cat /etc/resolv.conf 
[color=blue]nameserver [color=green]192.168.1.1[/color]
[/color]
```

Check if you can reach your DNS server, and then if you can reach an Internet address: Note that your numbers may vary but the format will be the same:
> ```

geetha@geetha-desktop:~/inf$ ping -c 3 192.168.1.1
[color=blue]PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=7.70 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.77 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.77 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 1.771/3.749/7.701/2.794 ms[/color]
geetha@geetha-desktop:~/inf$ ping -c 3 www.google.com
[color=blue]PING www.l.google.com (209.85.153.104) 56(84) bytes of data.
64 bytes from im-in-f104.google.com (209.85.153.104): icmp_seq=1 ttl=246 time=43.1 ms
64 bytes from im-in-f104.google.com (209.85.153.104): icmp_seq=2 ttl=246 time=40.7 ms
64 bytes from im-in-f104.google.com (209.85.153.104): icmp_seq=3 ttl=246 time=39.6 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 39.603/41.165/43.141/1.473 ms
[/color]
```

And that's it; from this point on you are connected. Until your next reboot that is. Once everything is verified working, to make the wireless networking permanent, you should do the following:

1) Add the line "ndiswrapper" to your "/etc/modules" file. This will ensure that your wireless card is automatically loaded at startup.

2) Add the following lines to your "/etc/network/interfaces" file:
```

iface wlan0 inet dhcp
auto wlan0
```

This will automatically activate your wireless card for Internet / network use.

While the example here is specific for NetGear's WG311v3, the above steps and commands will work for all ndiswrapper / "native" or "alternate" wireless card drivers.

I hope you find this small guide useful.

---

### Post by mandrill on 2008-04-17
I will bet you ANYTHING you cannot get MY wireless to work with ndiswrapper.

---

### Post by prshah on 2008-04-17
> **mandrill said:**
> I will bet you ANYTHING you cannot get MY wireless to work with ndiswrapper.

No I don't take your bet, you win. I can't get YOUR wireless to work. Best of luck elsewhere. Thank you for your time and trouble.

---

### Post by boob11 on 2008-04-24
thnx

---

### Post by parkereagerton on 2008-05-08
prshah,

Thank you for your timely response and your willingness to try and help. I only got to step "2" and had a failure. Here is the text:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting ndiswrapper-utils for regex 'ndiswrapper-utils*'
Note, selecting ndiswrapper-utils-1.9 for regex 'ndiswrapper-utils*'
0 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up proftpd (1.3.0-24ubuntu1) ...
 * Starting ftp server proftpd                                                   - IPv4 getaddrinfo 'asg-customer' error: Name or service not known
 - warning: unable to determine IP address of 'asg-customer'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
                                                                         [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


It looks like have have an IP error for sure. I am connected via ethernet cable and the computer is connected to the internet and working. Then it looks like an error with the FTP program but mind you, I am guessing. Again, I will look for your response and I am grateful!

---

### Post by parkereagerton on 2008-05-08
My goodness prshah,

I see that "SOLVED" is attached when actually it is not yet solved. I am new to this too!

Parker

---

### Post by rskay00 on 2008-06-08
Hi,

This my first posting. I really am an absolute beginner. A few months ago I installed Edgy on an old PC. It was connected to my wired home network. I stumbled around with a few things but was able with no effort to browse the internet.

I then moved and have just set up that old PC in a new house where I have wireless network. I have a Linksys Wireless-B WUSB11 ver. 4  USB wireless adapter. I'd like to use it with ubuntu but though I have read a zillion things still feel at sea.

Can I try and follow your instructions with this adapter?

Now- just to make clear how ignorant I am-- I suppose you are typing these commands in a terminal (something I just discovered yesterday).Also do I need to have the Windows driver for the adapter already installed? I don't. If so I need to know how to get it installed. I can download it from the Linksys site (with the laptop I'm using right now)on to a flash drive. Then what? Also if I need the Windows driver which version of windows should  I get the driver for?

If, in fact, there's no way to get my adapter to work which (cheap) USB adapter should I get? Then I will have all the same questions for that  one. :)

So you see I'm not kidding about the absolute beginner stuff. For example, I don't know what a kernel is:confused:

I never cease to wonder about the generosity and patience of people who post on these forums and I am really grateful for the help. I wish I knew enough about anything to be able to do something like that.

thanks,

Rick

---

### Post by prshah on 2008-06-10
> **rskay00 said:**
> 
Can I try and follow your instructions with this adapter?

I suppose you are typing these commands in a terminal
Also do I need to have the Windows driver for the adapter already installed? 

Yes you can follow these instructions. Just be sure to plug the adapter in before running any of these commands. And you can skip the lspci command, or use just plain ```
lsusb
``` in it's place.

You do not need to have the driver _installed_, but you do need access to it. Downloading it on the flash drive is fine, but be sure to "unzip" it (from windows) if it is "zipped" or packed. You can also do this in linux, but if you're more comfortable in windows...

If you get stuck, post back here at which point you have problems, along with error messages, if any.

---

### Post by rskay00 on 2008-06-10
Thanks a lot. I will give it a try within the next couple of days and report back.

Rick

---

### Post by rskay00 on 2008-06-11
Well it didn't take long for things to go wrong. :)

After step 3  (install newswrapper) I get all of the output down through  "After unpacking --kB of additional disk apace will be used."

Then it says:

Do you want to continue [Y/n]?

I type "y"

Then I get the following:


[COLOR="Blue"]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-common 1.18-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-utils-1.1 1.1-5
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-utils 1.1-5
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-utils-1.8 1.18-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.18-1ubuntu2_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper-1.1/ndiswrapper-utils-1.1_1.1-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper-1.1/ndiswrapper-utils-1.1_1.1-5_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper-1.1/ndiswrapper-utils_1.1-5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper-1.1/ndiswrapper-utils_1.1-5_all.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.8_1.18-1ubuntu2_i386.deb)  Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rskay@basement:~$ [/COLOR]

I tried the original command and just stuck fix-missing on the end but that didn't work. It looked unsuccessfully for some package called "fix missing"

Thanks for any further help!

Rick

---

### Post by prshah on 2008-06-11
> **rskay00 said:**
> 

[COLOR="Blue"]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main ndiswrapper-common 1.18-1ubuntu2
  Temporary failure resolving 'us.archive.ubuntu.com'
Temporary failure resolving 'us.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
rskay@basement:~$ [/COLOR]



Edgy has reached EOL (End of Life), and so edgy repositories are offline now. Do you have the CD? You can get ndiswrapper from that. Or upgrade/install Fiesty/Gutsy/Hardy.

---

### Post by rskay00 on 2008-06-12
Thanks.I no longer have the CD and no CD Burner on my only currently available network-connected PC.  I will be able to down load a newer version in a week or so. Is there anything I can do in the meantime. There is ndiswrapper website

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)

Can I get what I need from there and transfer it over by flash drive? And just what do I want??

Thanks again.  Rick

---

### Post by prshah on 2008-06-12
> **rskay00 said:**
> 
Can I get what I need from there and transfer it over by flash drive? And just what do I want??


ndiswrapper-common 1.18-1ubuntu2.deb
ndiswrapper-utils-1.1 1.1-5.deb
ndiswrapper-utils 1.1-5.deb
ndiswrapper-utils-1.8 1.18-1ubuntu2.deb


then:
```

sudo dpkg -i ndiswrapper-common 1.18-1ubuntu2.deb
sudo dpkg -i ndiswrapper-utils-1.1 1.1-5.deb
sudo dpkg -i ndiswrapper-utils 1.1-5.deb
sudo dpkg -i ndiswrapper-utils-1.8 1.18-1ubuntu2.deb

```

---

### Post by rskay00 on 2008-06-12
I am able to download a compressed file called

 ndiswrapper 1.18.tar.gz

The files it contains are listed. I can't find the exact files you mentioned. Are they in there? I hope you can make sense of it. I could emailyou the original html files in which the columns make more sense.

Thank you.

Rick

[COLOR="Blue"][SIZE="2"][SIZE="1"][SIZE="3"]
#  Archive C:\Documents and Settings\Rick\Local Settings\Temp\ndiswrapper-1.18.tar.gz
2006-06-22 08:09        Folder        Folder  ndiswrapper-1.18
2006-06-22 08:09           116             0  ndiswrapper-1.18\AUTHORS
2006-06-22 08:09         16683             0  ndiswrapper-1.18\ChangeLog
2006-06-22 08:09          2762             0  ndiswrapper-1.18\INSTALL
2006-06-22 08:09          2368             0  ndiswrapper-1.18\Makefile
2006-06-22 08:09          1410             0  ndiswrapper-1.18\README
2006-06-22 08:09          2883             0  ndiswrapper-1.18\ndiswrapper.spec
2006-06-22 08:09            38             0  ndiswrapper-1.18\version
2006-06-22 08:09          3462             0  ndiswrapper-1.18\ndiswrapper.8
2006-06-22 08:09        Folder        Folder  ndiswrapper-1.18\utils
2006-06-22 08:09           833             0  ndiswrapper-1.18\utils\Makefile
2006-06-22 08:09         22677             0  ndiswrapper-1.18\utils\ndiswrapper
2006-06-22 08:09         17205             0  ndiswrapper-1.18\utils\loadndisdriver.c
2006-06-22 08:09          3342             0  ndiswrapper-1.18\utils\ndiswrapper-buginfo
2006-06-22 08:09        Folder        Folder  ndiswrapper-1.18\driver
2006-06-22 08:09          6274             0  ndiswrapper-1.18\driver\divdi3.c
2006-06-22 08:09          3596             0  ndiswrapper-1.18\driver\hal.c
2006-06-22 08:09         67827             0  ndiswrapper-1.18\driver\iw_ndis.c
2006-06-22 08:09          6568             0  ndiswrapper-1.18\driver\iw_ndis.h
2006-06-22 08:09         25752             0  ndiswrapper-1.18\driver\loader.c
2006-06-22 08:09          2252             0  ndiswrapper-1.18\driver\loader.h
2006-06-22 08:09         46140             0  ndiswrapper-1.18\driver\longlong.h
2006-06-22 08:09          7823             0  ndiswrapper-1.18\driver\Makefile
2006-06-22 08:09         20505             0  ndiswrapper-1.18\driver\misc_funcs.c
2006-06-22 08:09         74314             0  ndiswrapper-1.18\driver\ndis.c
2006-06-22 08:09         37218             0  ndiswrapper-1.18\driver\ndis.h
2006-06-22 08:09          2722             0  ndiswrapper-1.18\driver\ndiswrapper.h
2006-06-22 08:09         71900             0  ndiswrapper-1.18\driver\ntoskernel.c
2006-06-22 08:09         35827             0  ndiswrapper-1.18\driver\ntoskernel.h
2006-06-22 08:09         27763             0  ndiswrapper-1.18\driver\ntoskernel_io.c
2006-06-22 08:09         16060             0  ndiswrapper-1.18\driver\pe_linker.c
2006-06-22 08:09         33678             0  ndiswrapper-1.18\driver\pe_linker.h
2006-06-22 08:09         22092             0  ndiswrapper-1.18\driver\pnp.c
2006-06-22 08:09          1790             0  ndiswrapper-1.18\driver\pnp.h
2006-06-22 08:09         14434             0  ndiswrapper-1.18\driver\proc.c
2006-06-22 08:09         42350             0  ndiswrapper-1.18\driver\usb.c
2006-06-22 08:09         11247             0  ndiswrapper-1.18\driver\usb.h
2006-06-22 08:09         40533             0  ndiswrapper-1.18\driver\winnt_types.h
2006-06-22 08:09          3393             0  ndiswrapper-1.18\driver\workqueue.c
2006-06-22 08:09          2370             0  ndiswrapper-1.18\driver\wrapmem.h
2006-06-22 08:09          7441             0  ndiswrapper-1.18\driver\wrapmem.c
2006-06-22 08:09          3560             0  ndiswrapper-1.18\driver\wrapper.c
2006-06-22 08:09          1849             0  ndiswrapper-1.18\driver\wrapndis.h
2006-06-22 08:09         57485             0  ndiswrapper-1.18\driver\wrapndis.c
2006-06-22 08:09          5174             0  ndiswrapper-1.18\driver\x86_64_stubs.S
#
# Total                   Size        Packed  Files
#                       773716             0  45[/SIZE][/SIZE][/SIZE][/COLOR]

---

### Post by prshah on 2008-06-12
> **rskay00 said:**
> I am able to download a compressed file called

 ndiswrapper 1.18.tar.gz


This file is the source code, and you need to compile it to install it. Can you not try for .deb files? that can be easily installed with "dpkg -i"

btw, you have to download _each_ of the files mentioned in my previous post; and each with a .deb extension.

If you can't get hold of a suitable .deb, I can assist you with compilation, but I think it will be impossible on your system since certain basic utilities may not be available (eg., build-essential) and cannot be installed since Edgy repositories are closed and unavailable. In short; compiling might well be impossible.

---

### Post by rskay00 on 2008-06-13
I've been unable to locate the deb files and fear I'm just going to have to wait a couple of weeks until I can burn an update CD (Feisty?). Alternatively I may see if I can get a different adapter that will work without ndiswrapper. Thanks for going with me this far. I'll let you know when I get to the next roadblock

Rick.

---

### Post by rskay00 on 2008-07-03
Well I upgraded to Feisty  (being told with just 256 memory I shouldn't go higher) and tried again. Everything went great up to step 8. It showed "no wireless extensions". As suggested I tried step 9. No joy. Here's the output:

rskay@basement:~/inf$ sudo ndiswrapper -m 
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ... 
rskay@basement:~/inf$ sudo modprobe ndiswrapper 
rskay@basement:~/inf$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

rskay@basement:~/inf$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                                  Cannot find device "eth1" 
There is already a pid file /var/run/dhclient.eth1.pid with pid 7576 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Bind socket to interface: No such device 
eth1: ERROR while getting interface flags: No such device 
Error for wireless request "Set Encode" (8B2A) : 
    SET failed on device eth1 ; No such device. 
Error for wireless request "Set ESSID" (8B1A) : 
    SET failed on device eth1 ; No such device. 
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
eth1: ERROR while getting interface flags: No such device 
eth1: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up eth1. 
eth2: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
eth2: ERROR while getting interface flags: No such device 
eth2: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up eth2. 
ath0: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
ath0: ERROR while getting interface flags: No such device 
ath0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up ath0. 
wlan0: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
wlan0: ERROR while getting interface flags: No such device 
wlan0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
Failed to bring up wlan0.

Thanks for any suggestions

Rick

---

### Post by prshah on 2008-07-03
> **rskay00 said:**
> 
rskay@basement:~/inf$ sudo ndiswrapper -m 
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ... 



Please post the output of ```
ndiswrapper -l
```

---

### Post by rskay00 on 2008-07-03
Here it is:

WUSB11v4  :  driver installed
     device (13B1 : 000B) present

Rick

---

### Post by prshah on 2008-07-04
> **rskay00 said:**
> Here it is:
WUSB11v4  :  driver installed
     device (13B1 : 000B) present


Fine that tells us the driver is installed fine and device is recognized and found. Now, give the following commands, one-by-one (ie, dont copy and poste all lines at once)```

sudo depmod -a
sudo modprobe ndiswrapper
```

If these give any errors, maybe your wireless is being recognised _without_ need for ndiswrapper. Just post the output of ```
iwconfig
```

---

### Post by rskay00 on 2008-07-04
I got no errors (or any other response)from either of these commands but iwconfig yields:

lo     no wireless extensions
eth0   no wireless extensions

Thanks.

Rick

---

### Post by prshah on 2008-07-04
> **rskay00 said:**
> I got no errors (or any other response)from either of these commands but iwconfig yields:
lo     no wireless extensions
eth0   no wireless extensions


I regret that there is no cut-n-dried solution for you and that we have to do so much experimenting; but dont give up yet!

Now, ndiswrapper has located your device; it _seems_ to load properly; but no wireless device actually enabled... hmm... can you post the output of ```
cat /etc/network/interfaces
``` After that, try the modprobe command (as mentioned in earler post) again, then post output of ```
dmesg | tail
```

---

### Post by rskay00 on 2008-07-04
Here goes:

rskay@basement:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 


iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 
wireless-essid eastman 
wireless-key 8606560520 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 

rskay@basement:~$ sudo modprobe ndiswrapper 
rskay@basement:~$ dmesg | tail 
[ 1699.884136] sda: Write Protect is off 
[ 1699.884150] sda: Mode Sense: 03 00 00 00 
[ 1699.884158] sda: assuming drive cache: write through 
[ 1699.896133] SCSI device sda: 2038272 512-byte hdwr sectors (1044 MB) 
[ 1699.899146] sda: Write Protect is off 
[ 1699.899160] sda: Mode Sense: 03 00 00 00 
[ 1699.899168] sda: assuming drive cache: write through 
[ 1699.899180]  sda: sda1 
[ 1699.905391] sd 1:0:0:0: Attached scsi removable disk sda 
[ 1699.905541] sd 1:0:0:0: Attached scsi generic sg0 type 0 
rskay@basement:~$ 


iwconfig gives the same (non)result. On the brighter side I now see that my ssid (eastman)and wireless key are correctly identified.

Happy Independence Day.

Rick

---

### Post by bemental on 2008-07-10
Thank you so much.  This guide was extremely helpful in aiding my setup of Linux Mint on a Dell Latitude with the aforementioned Netgear wireless card.

Again, my thanks!

---

