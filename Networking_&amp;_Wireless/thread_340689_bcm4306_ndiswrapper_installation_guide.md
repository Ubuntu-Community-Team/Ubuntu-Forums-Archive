---
title: "bcm4306 ndiswrapper installation guide"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by maclenin on 2007-01-17
Having just completed a successful migration from fwcutter to ndiswrapper (with gentle compelling from some who will be cited directly and indirectly, below), I thought I'd send along a revised standard version of the ndiswrapper installation process for those of us who consider ourselves relative noobs (such as myself).

NOTE: This guide is based, quite substantially, on this comprehensive [_howto_]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show"), so please refer to it for additional detail and post-install configuration and set-up assistance. I will continue to add additional configuration comments to my guide, as necessary.

So, without further ado – here's how I got my bcm4306 wireless card working with ndiswrapper on a Dell Inspiron 600m running Xubuntu 6.10 from a LiveCD:

**A. STARTING CONFIGURATION**

Dell Inspiron 600m laptop
Broadcom 4306 wireless chipset 
Xubuntu 6.10 (Edgy Eft) on a LiveCD
Ethernet connection

**B.  PREPARE YOUR SYSTEM FOR DOWNLOAD AND INSTALLATION OF UTILITIES AND WIRELESS DRIVER**

1. Open up the terminal (**Applications – System – Terminal**) and make the following directories:

```
mkdir ~/ndiswrapper
mkdir ~/bcm4306
```

2. Modify the sources.list file to allow for the downloading of additional required utilities...

```
sudo nano /etc/apt/sources.list
```

...by uncommenting (removing the # next to) the following entries in the sources.list file...

```
deb http://archive.ubuntu.com/ubuntu edgy universe
deb-src http://archive.ubuntu.com/ubuntu edgy universe
```

...then saving the file.

3. Remove the "old" bcm43xx driver module (IMPORTANT NOTE: Please skip step 3. and proceed to step 3.a. if you have installed ubuntu on your hard drive and/or are able to reboot to saved settings/configurations):

```
sudo modprobe -r bcm43xx
```

3.a. Blacklist the bcm43xx wireless driver:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

3.b. Comment out (add a # next to) any and all references to eth1:

```
sudo nano /etc/iftab
sudo nano /etc/network/interfaces
```

4. Install the build-essential tool set:

```
sudo aptitude update 
sudo aptitude install build-essential
```

5. Identify your kernel version, using...

```
uname -r
```

...which should output something similar to...

```
2.6.17-10-generic
```

...and update your linux headers, using the output from uname -r, as indicated:

```
sudo aptitude install linux-headers-2.6.17-10-generic 
sudo ln -s /usr/src/linux-2.6.17-10-generic /lib/modules/2.6.17-10-generic/build
```

**C. DOWNLOAD AND INSTALL UTILITIES AND WIRELESS DRIVER**

6. Download ndiswrapper and the wireless driver:

```
wget http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.34.tar.gz
wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
```

7. Move ndiswrapper and the wireless driver to their working directories:

```
mv ndiswrapper-1.34.tar.gz ~/ndiswrapper
mv sp33008.exe ~/bcm4306
```

8. Unpack and install ndiswrapper:

```
cd ~/ndiswrapper
sudo tar -xvzf ndiswrapper-1.34.tar.gz
cd ~/ndiswrapper/ndiswrapper-1.34
make distclean
make
sudo make install
```

9. Install the extraction utitlity:

```
cd
sudo aptitude install cabextract
```

10. Extract the wireless driver:

```
cd ~/bcm4306
cabextract sp33008.exe
```

11. Install the wireless driver using ndiswrapper:

```
sudo ndiswrapper -i bcmwl5.inf
```

12. Copy the .conf file:

```
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
```

**D. LOAD WIRELESS DRIVER AND CONFIGURE YOUR WIRELESS CARD**

13. Load the wireless driver:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

13.a. Should you receive the following error after you run the modprobe command...

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-
generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

...enter the following...

```
sudo aptitude install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

...and then repeat step 13., which should run, error free.

14. Make certain your wireless card is identified as wlan0 using:

```
iwconfig
```

14.a. Should your wireless card not be identified as wlan0, please return to steps 3.a. and 3.b. (NOTE: Restart your computer (then return to step 14.) if you've had to make any modifications.)

15. Proceed to **Application – System – Networking** to configure your wireless connection (via the desktop, or proceed to 15.a.).

15.a. Edit the network file to configure your wireless connection...

```
sudo nano /etc/network/interfaces
```

...by making certain your wlan0 record is similar to:

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_essid
```

16. Make the ndiswrapper driver permanent:

```
sudo ndiswrapper -m
```

17. Inspect the /etc/modprobe.d/ndiswrapper file...

```
sudo nano /etc/modprobe.d/ndiswrapper
```

...to make certain it contains nothing other than:

```
alias wlan0 ndiswrapper
```

18. For WEP and WAP assistance, please refer to Step 6 (unto the end) of my [primary source]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show").

That should do it!

**E. CREDITS**

**Ndiswrapper installation and further configuration notes and nuances**
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show)
[http://ubuntuforums.org/showthread.php?t=328272&page=2](http://ubuntuforums.org/showthread.php?t=328272&page=2)

**Ndiswrapper fatal error resolution**
[http://www.ubuntuforums.org/showthread.php?t=325518&page=2](http://www.ubuntuforums.org/showthread.php?t=325518&page=2)

---

### Post by teaker1s on 2007-01-17
;)

---

### Post by LavaHot on 2007-01-17
You are a god, sir. It works perfectly, if not a little slow, but the wired connection was about as slow for some reason. It even works with 128-bit WEP! Now if somebody could create a script to do this, if I ever have to install again it'll save me 30 minutes and some neck pain. Such a script should be included in the distro. Many, Many thanks from the bottom of my heart!

---

### Post by maclenin on 2007-01-18
Thanks for the kind commentary - glad it worked for you!

Re: WEP configuration - I assume you found this in the latter portions (Step 6) of the "[ÜBERGUIDE]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")"....

---

### Post by jmrichky on 2007-01-18
I have followed this and several other procedure guides with no success.  I got no errors while completing this guide and followed it step-by-step.  I am running Edgy 2.6.19.2 on a AMD64 laptop.
The wireless connection is activated and shows up in the "Networking" utility.  The wireless radio button on my laptop does not light up when pressed.  I know that more information will be needed but I know what commands to run.  I will reply with the output of any commands that are needed.

---

### Post by maclenin on 2007-01-18
Can you post the output of these commands...

lshw -C network

iwconfig

uname -r (which should be 2.6.19.2)

...and we'll see from there....

---

### Post by jmrichky on 2007-01-18
[COLOR="Red"] lshw -C network output[/COLOR]
 *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@03:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:ab:ec:3f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.34 firmware=Broadcom,03/23/2006, 4.40.19.0 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b0204000-b0205fff irq:21
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@03:06.0
       logical name: eth1
       version: 10
       serial: 00:0f:b0:6b:e0:30
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.101 multicast=yes
       resources: ioport:a000-a0ff iomemory:b0209400-b02094ff irq:22

[COLOR="Red"]iwconfig output[/COLOR]
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[COLOR="Red"]uname -r output[/COLOR]
2.6.19.2-custom

---

### Post by maclenin on 2007-01-18
Try:

sudo iwconfig wlan0 essid (and whatever your router's ssid is without the ())....

Let me know what happens....

---

### Post by jmrichky on 2007-01-18
Justin@ubuntulaptop:~$ sudo iwconfig wlan0 essid Home
justin@ubuntulaptop:~$

It does nothing.

---

### Post by maclenin on 2007-01-18
Now try:

ping -c 4 192.168.1.1 (which should be the IP address of your router)

and post the out put - if you get "0% packet loss" you should be connected to the internet....

---

### Post by jmrichky on 2007-01-18
[COLOR="Red"]with network cable unplugged I get:[/COLOR]

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3000ms

[COLOR="Red"]with network cable plugged in I get:[/COLOR]

justin@ubuntulaptop:~$ ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=5.36 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.690 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.689 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.688 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 0.688/1.857/5.362/2.023 ms

---

### Post by jmrichky on 2007-01-18
Your guide definitely worked.  It turns out that the problem was there was a conflict with pci bus and the one that the wireless card was on was hidden.  It was solved by adding "pci=assign-busses" to the Linux boot line.  Thanks for your help and your guide.

---

### Post by maclenin on 2007-01-18
Glad to hear it worked for you.... I am interested, however, to hear more about the pci bus issue - and what you mean by 'adding "pci=assign-busses" to the Linux boot line'?

---

### Post by LavaHot on 2007-01-19
actually no, i used the network client to set it up. I do have one problem though, I always have to do this
```
sudo modprobe -r bcm43xx
sudo modprobe ndiswrapper
```
on bootup, other wise the interface doesn't mount correctly.
And recently I've had to set the essid in the console to connect to the correct AP. I don't have to reset the WEP key though. 
I'm also still stuck as eth1 for some reason.

---

### Post by maclenin on 2007-01-19
I would consider blacklisting bcm43xx - as described, [**_here_**]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show"), in Step 2. Then read through Step 6 to address the essid and more on the eth1 isuue....

I am going to expand my guide a wee bit to account for these nuances, once I've had a chance to test them, for myself.... However, in the meantime - take a peek at what I've referenced....

---

### Post by jmrichky on 2007-01-19
> **maclenin said:**
> Glad to hear it worked for you.... I am interested, however, to hear more about the pci bus issue - and what you mean by 'adding "pci=assign-busses" to the Linux boot line'?

When I looked through output of "dmesg" I found:
```
16.111939] PCI: Bus #04 (-#07) is hidden behind transparent bridge #03 (-#03) (try 'pci=assign-busses')
16.111944] Please report the result to linux-kernel to fix this permanently
```

Then I edited /boor/grub/menu.lst to look like this:
```
title		Ubuntu, kernel 2.6.19.2-custom
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.19.2-custom root=/dev/hda1 ro quiet splash [COLOR="Red"]pci=assign-busses[/COLOR]
initrd		/boot/initrd.img-2.6.19.2-custom
quiet
savedefault
boot
```

I assume that the error had something to do with my wireless not working because when I rebooted, the wireless light came on and everything worked.

---

### Post by maclenin on 2007-01-20
Thanks for the info - I'll have to file that one away for future reference.... Again, glad that you got things working.

---

### Post by John Jason Jordan on 2007-01-25
Thanks to maclenin for the instructions in the first post in this thread. I finally got it working, but I had some problems. It might be helpful to others for me to document here how I solved them

1) I upgraded Dapper amd64 to Edgy amd64 on my Compaq R3240 laptop which has the Broadcom 4306 chip. I had it working with ndiswrapper just fine under Dapper, but the upgrade broke it. I followed the instructions, but it would not work. Eventually I discovered in Synaptic that ndiswrapper 1.8 was still installed. Of course it would be -- this is an upgrade, not a fresh install. Duh! So I used Syanptic and uninstalled the old ndiswrapper. However, then modprobe said ndiswrapper wasn't installed at all. So I went back through the instructions and reinstalled 1.34.

2) It still was not working. I had blacklisted bcm43xx in /etc/modprobe.d/blacklist, but ndiswrapper -l still showed it as an alternate driver. For a long time I thought this might be the problem, but eventually I discovered that it was a driver issue. The bcmwl5 driver just wasn't working. Online I found other copies of the bcmwl56 driver that I had been using before and I installed them (because they were more recent). It still wouldn't work. Finally, I reinstalled the old driver that I had been using before. That did it. Finally System > Administration > Networking showed the wireless connection.

3) Although I could see the wireless connection in the Networking dialog box, the appearance of the box had changed from Dapper. In Dapper the wireless would have shown as "inactive" and there would be buttons to the right labeled "activate," "deactivate" (one or the other of these would be grayed out, depending on whether the wireless was active or not), and another button for "properties." After upgrading to Edgy the activate and deactivate buttons have been removed. Instead it said the device was not configured. I found this very confusing. I clicked on the properties button, but no wireless networks appeared. Therefore, I assumed that ndiswrapper was not yet working.

Eventually I searched in Synaptic and found a little utility called wifi-radar. I installed it and it saw wireless networks from two of my neighbors. Now, I'm kinda dumb about these things, but if wifi-radar can see wireless networks, then the Broadcom 4306 must be working and active. However, I couldn't prove this as I do not have wireless myself at home and my neighbors' wireless networks are secure. So today I came to the university and booted uo the computer. I opened System > Administration > Networking and it still said the device was not configured. I clicked on the properties button and then on the connection points drop-down, but no wireless networks were visible (previously I would see several for the university).

So then I fired up wifi-rader and it saw the university and several nearby businesses. It had an option the select one and to connect to it, so I tried the university. A few moments later it said it was connected. Then I launched Firefox and told it to go to eBay. That caused the university wireless network to pop up a window asking for my account and password. I entered it and here I am, online.

Strangely, System > Administration > Networking still says the device is not configured. And when I ciick on the properties button, it sees no networks. Well, as long as wifi-radar will get me connected I guess I don't care about the System > Administration > Networking popup window.

I should add that iwconfig does see it as wlan0.

Someone should fix that popup window because it made me spend hours scratching my head trying to figure out why it was not working, when it was really working all along.

---

### Post by maclenin on 2007-01-25
Glad you were able to sort it all out and thanks for the additional fyi....

---

### Post by Mithryn on 2007-01-27
sudo depmod -a
sudo modprobe ndiswrapper

whenever i enter the last line, my computer always freezes, nothing short of hitting the power button stops it.  Any insight?

---

### Post by maclenin on 2007-01-27
Not immediately.... My suggestion would be to remove nidswrapper (as indicated [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show"), in Step 1) and then reinstall ndiswrapper. There might have been some error during install that a re-install could resolve....

---

### Post by zeddock on 2007-01-27
You have done a WONDERFUL job on this!

In step 8 where we do a tar extract of ndiswrapper...
On my new install of ubuntu I got an error back; complaining that I tried to use an invalid option.

The real problem it seems was that my home directory did not have the proper permissions. So I guess a chmod line would be helpful to others.

Thanx again!

zeddock

---

### Post by maclenin on 2007-01-27
Thanks for the kudos! Regarding your tarball comment, I think using "sudo tar" should obviate any permissions issues (assuming I've understood your issue, correctly).... Thanks, again, for the fb!

---

### Post by bazan on 2007-01-29
hi,
i got a little problem, when i type 

```
iwconfig
```

i get 

lo no wireless extensions

eth0 no wireless extensions

sit0 no wireless extensions

eth1 IEEE 802.11g ESSID: off/any
       

and when i type ```
dmesg
```

the last entry is 
ndiswrapper: changing interface name from 'wlan0' to 'eth1'

what do I have to do?

---

### Post by maclenin on 2007-01-29
I would go to Step 2 and then Step 6 'till the end of this [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") to make certain that you comment out (i.e. place a # next to) any references to eth1. Ndiswrapper uses wlan0 as it's "wireless address" and if your wireless card is still associated with eth1 (in those places the guide suggests you modify) - ndiswrapper will not work properly. Once you've completed these tasks, restart your computer - this should solve your problem!

---

### Post by bazan on 2007-01-29
I found another solution but thx for your help.

```
nano /etc/iftab
```

and change eth1 to wlan0

After that it works! But thx for your help!

---

### Post by maclenin on 2007-01-29
Congrats on the solution! Keep in mind, however, should you need to do any additional ndis-related trouble-shooting, the [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") is a great source....

---

### Post by zeddock on 2007-01-30
> **maclenin said:**
> Thanks for the kudos! Regarding your tarball comment, I think using "sudo tar" should obviate any permissions issues (assuming I've understood your issue, correctly).... Thanks, again, for the fb!


I have installed again and get hung at the same place each time. In fact, it might not be all about the permissions.  It will not allow me to do the sudo tar operation. Always giving the "invalid option" error. 

I have to chmod the ndiswrapper directory, then go to nautilus and right-click to "extract here"  then I can go on with the install following your directions. 

Anyone know what this newb is doing wrong?  Everything else works like clockwork!

Thanx again maclenin.

zeddock

---

### Post by maclenin on 2007-01-30
Not to be flip, but I have received the "invalid option" - a wee more than a few times - and more often than not, it's turned out to be a typo (especially with unwieldy tarball names).... So, proceed with caution - or just copy and paste the tar line from the guide.... The other thing you might want to try is "tab" as you complete the command - i.e. sudo tar -xvzf and then "tab" - which will "autofill" the name of file (assuming you are in the proper directory, which is something else you might want to verify - i.e. cd /home/nd then type "tab", then enter)...then unwrap the tarball.... Give it a whirl!

---

### Post by zeddock on 2007-01-30
> **maclenin said:**
> Not to be flip, but I have received the "invalid option" - a wee more than a few times - and more often than not, it's turned out to be a typo (especially with unwieldy tarball names).... So, proceed with caution - or just copy and paste the tar line from the guide.... The other thing you might want to try is "tab" as you complete the command - i.e. sudo tar -xvzf and then "tab" - which will "autofill" the name of file (assuming you are in the proper directory, which is something else you might want to verify - i.e. cd /home/nd then type "tab", then enter)...then unwrap the tarball.... Give it a whirl!


All excellent advice. But I was doing a cut/paste to make sure I didn't fat-finger it.

All I can tell you is it just did the same thing again on yet, another install.  To give you a little more information and to verify what I am telling you, when I go to my home folder (through the gui) I get to ndiswrapper directory with the compressed file inside. If I right-click my options include Extract, and allows me to pick where to extract the files. It is only after I give the command-line command of:
sudo chmod 755 -R ndiswrapper               (from the home directory)
...that I can right-click on that compressed file and have the Extract Here option.

Hope others can verify that ndiswrapper folder under the home folder has permissions that do not allow you to tar-extract until the are changed.

Thanx again.

zeddock

---

### Post by maclenin on 2007-01-31
I tend to like the "control" that the "command" line affords...never ventured to the gui when installing ndiswrapper - but I understand why you have....

Is there anyway you could post the output of (prior to unpacking ndiswrapper)...

```
ls &#8211;l /home/ndiswrapper
```

...and then your output of...

```
sudo tar -xvzf ndiswrapper-1.34.tar.gz
```

...so that I can get a more specific sense of the errors your receiving?

---

### Post by zeddock on 2007-01-31
I guess I can't since I have already expanded on this computer.
I am doing your routine again though, so I can give you some information.

```
jim@lat-lap:~$ cd /home/ndiswrapper
jim@lat-lap:/home/ndiswrapper$ sudo tar –xvzf  ndiswrapper-1.34.tar.gz
tar: invalid option -- 
Try `tar --help' or `tar --usage' for more information.
jim@lat-lap:/home/ndiswrapper$ 

```

The first command you gave for me to try gave this:
```
jim@lat-lap:/home/ndiswrapper$ ls –l /home/ndiswrapper
ls: –l: No such file or directory
/home/ndiswrapper:
ndiswrapper-1.34  ndiswrapper-1.34.tar.gz
jim@lat-lap:/home/ndiswrapper$ 
```


hmmm. That is interesting!

If you look at the original sudo tar line... you will see that there is an extra space between the options and the beginning of the filename. 

```
sudo tar -xvzf  ndiswrapper-1.34.tar.gz
```
should be
```
sudo tar -xvzf ndiswrapper-1.34.tar.gz
```


I guess that would do it, huh?

zeddock

---

### Post by Cochese on 2007-01-31
I have followed the guide but ran into a problem. When I type iwconfig the access point says "Invalid".  I haven't had any error messages and everything else seems to be correct. The router doesn't have an encryption as it's used by everyone here.  Anyone know what could cause this? I'm using Dapper and my card is a BCM4306.

---

### Post by maclenin on 2007-01-31
A. zeddock:

The extra /home/ndiswrapper would be relevant only if you were in your ":~$" directory. For example, here are what I **believe to be **workable formats:

1.

```
jim@lat-lap:~$ ls -l /home/ndiswrapper
```

1.a. 

```
jim@lat-lap:~$ ls -l ../ndiswrapper
```

2.

```
jim@lat-lap:/home/ndiswrapper$ ls -l
```


AND YES - you were exactly correct - there was an errant space in the tar line - thanks for the catch, I have made the requisite edit!

B. Cochese:

Yep. Give this command a whirl...

```
sudo iwconfig wlan0 essid "your_access_point_name"
```

...or you can try **Applications > System > Networking** (or however you'd access your applications / settings) via the desktop and enter you ap info, there....

Either of these steps should connect you to your router. Try firefox to verify....

After you've tested your connection - and it works, see Step 6 'till the end of this [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") - to make your settings permanent!

---

### Post by Cochese on 2007-01-31
> jeff@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

jeff@ubuntu:~$ sudo iwconfig wlan0 essid linksys
Password:
jeff@ubuntu:~$

Not sure what I am doing wrong.

---

### Post by maclenin on 2007-01-31
I would take a peek at the [guide]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") - and return to Step 2 (and Step 6) where it tells you to, essentially, comment out (add a # next to) all references to eth1 and, perhaps, to blacklist bcm43xx.... These might be causing a conflict with ndiswrapper.... Again, take a read through those aspects of the guide - i.e. Step 2 and then Step 6 'till the end to rid yourself of the eth1 (and bcm43xx) menace! After you've completed this process, reboot and try an iwconfig, again - eth1 should have vanised....good luck!

NOTE TO YOU AND TO SELF: I need to revise my guide to be a tad clearer about the eth1 / bcm43xx scourge....

---

### Post by zeddock on 2007-01-31
I know I am doing something wrong somewhere because everything looks good right after I go through the steps, but when I power down and bring it back up wlan0 has become eth1 again!   (I will look to make sure that I commented eth1 out, and I will black list as you suggest.)

When I try to look at wlan0 I get an error of:
SIOCGIFFLAGS error: No such device

This mean anything to others?  A search suggest this has a lot to do with eth1 not being commented out.

...I'll be back  <===voice-over by Arnold


zeddock

---

### Post by maclenin on 2007-02-01
Take another amble through page one of this thread - I've made a few special modifications, myself.... I think your error (as you mention) is related to eth1 still hangin' around. If eth1 still governs somewhere - ndiswrapper can't do its job (re: assigning wlan0)....

---

### Post by Cochese on 2007-02-01
> jeff@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:9E:2D:B8
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:87/100  Signal level:-40 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

jeff@ubuntu:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.


eth0 mac 00:90:4b:61:29:ff arp 1


> jeff@ubuntu:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface


iface lo inet loopback

iface eth0 inet dhcp
wireless-essid linksys

auto eth0


Wanted to post this, because it's working now.  This is with ndiswrapper 1.35, Dapper, and a bcm4306.  I just deleted eth1 out of /etc/iftab. I never could get rid of eth1 or change eth0 to wlan0 in iwconfig even when I used gedit to change the interfaces file.  I don't know how I did it before when it wasn't working. I think I blacklisted the incorrect driver also; bcm4306 instead of bcm43xx. After I fixed that, deleted eht1 and rebooted that's when it started working.  I still had to go to network settings and activate it, but that's all.

---

### Post by maclenin on 2007-02-01
I fear that because your wireless card in "misaliased" (i.e. as eth0 vs. wlan0) - you will run into problems - at some point.... Do you have an ethernet card? Mine is located at eth0.... Perhaps version 1.35 aliases differently - however, I doubt it.... I would try to work your way - meticulously - through the installation, once again - maybe start by removing ndiswrapper (see Step 1, [here]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")) - and re-installing, fresh - wlan0 should be where your wireless card is, ultimately, located!

NOTE: If you've installed ndiswrapper properly, I am quite certain that eth1 shouldn't even show up under iwconfig....

---

### Post by Cochese on 2007-02-01
[IMG]http://i42.photobucket.com/albums/e342/iam_koomy/screenshot.jpg[/IMG]

My ethernet card is eth1.  I'll keep playing with it and see if any problems occur, but so far it seems to be working fine.  Thank you for your help!!

---

### Post by maclenin on 2007-02-01
I guess, if it ain't broke.... You're welcome. Good luck!

---

### Post by Cochese on 2007-02-01
I went through the installation again the wireless card and ethernet card are now located at wlan0 and eth0, respectively.

It's working the same as it did before, but I am feeling better about it now.  Now I just need to set it up so I don't have to activate everytime I boot.

---

### Post by maclenin on 2007-02-01
Congrats - that's the way it should be.... As far as the boot issue - I would take a peek at the guide at the top of this thread (as I've made a couple of mods - to address the boot issue) - or [THIS GUIDE]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") will, most certainly, also be of use....

In a nutshell, you are going to make certain the /etc/network/interfaces is configured properly - and then you'll make the ndiswrapper module permanent via ndiswrapper -m.... Follow the directions, and you'll be all set.

---

### Post by maclenin on 2007-02-02
If anyone has holes to poke or comments on the guide - please comment and poke!

---

### Post by zeddock on 2007-02-03
> **maclenin said:**
> I tend to like the "control" that the "command" line affords...never ventured to the gui when installing ndiswrapper - but I understand why you have....

Is there anyway you could post the output of (prior to unpacking ndiswrapper)...

```
ls &#8211;l /home/ndiswrapper
```

...and then your output of...

```
sudo tar -xvzf ndiswrapper-1.34.tar.gz
```

...so that I can get a more specific sense of the errors your receiving?


Your first request:
```
susie@susielap:/home/ndiswrapper$ ls &#8211;l /home/ndiswrapper
ls: &#8211;l: No such file or directory
/home/ndiswrapper:
ndiswrapper-1.34.tar.gz
susie@susielap:/home/ndiswrapper$ 

```

I am unsure what you wanted to get from this. did you know there were 2 dashes in front of the "l"?

output of same with -xla
```
susie@susielap:/home/ndiswrapper$ ls -xla /home/ndiswrapper
total 200
drwxr-xr-x 2 root root   4096 2007-02-03 00:55 .
drwxr-xr-x 5 root root   4096 2007-02-03 00:45 ..
-rw-r--r-- 1 root root 190156 2007-01-08 13:52 ndiswrapper-1.34.tar.gz
susie@susielap:/home/ndiswrapper$ 

```

zeddock

---

### Post by maclenin on 2007-02-03
I think at the time, I was trying to get a sense of possible permission issues - and also to make certain that your tarball was where it was supposed to be (i.e. in the directory within which you were running the tar command).... 

Here are the revised ls -l [instructions]("http://www.ubuntuforums.org/showpost.php?p=2089490&postcount=34")....

This is probably water under the bridge - as I assume all is working as it should?

---

### Post by MalVeauX on 2007-02-04
Gentlemen,

I'm a total novice to Linux, but I'm eager to migrate away from XP. Anyhow, I have a Compaq Presario R3000, which means I have one of those Broadcom wif-fi chipsets on my internal wi-fi, specifically the bcm4306 chipset. I was immediately drawn to ubuntu because it's the most widely used Linux distro (to my knowledge, I could very well be incorrect), and I really liked the look of it. I downloaded the 6.10 distro and burned my CD. Booting it as a LiveCD to test everything before installing is such a great option. I can install at any time. I'm totally ready to install too, except one problem: Internet. That's where this thread comes in, and you, my wonderful people who bother to help us ignorant fools (i.e., me, lol).

Here's my problem - I'm completely on a wi-fi setup at the moment, so I don't have an ethernet option to run this guide with. So my 2nd option has been to use my USB drive, to pre-download files and have them right at hand and ready to use when I boost into Ubuntu (LiveCD) just like this guide is written for. But instead of downloading files like the guide says, I just copy them over from the USB drive and work with them that way. Everything goes well until I hit a problem:

> 4. Install the build-essential tool set:

Code:

sudo aptitude update 
sudo aptitude install build-essential



Step 4 stops me cold. I have ndiswrapper and I even have my driver for the card all set. I could use the wrapper right away if I could just compile the bugger, but alas, I cannot. Step 4 requires me to get something here, this build-essential, and I have no idea what it is, nor versions, etc. If this is software, required to make compiling ndiswrapper work, then I certainly need it. But that's where I need help. I haven't a clue as to where to start on this one. I was able to get ndiswrapper and my driver, and extract them and everything. I copy them fine. But this build-essential part? No clue.

Is there a way that I can get what is needed before I boot into the LiveCD for Ubuntu? I seem to be able to get everything ready to go, except for this part here. After this, I'm all set to use the wrapper and it should work out. 

Currently, because I skip Part4 since I cannot accomplish it (no internet connection without wi-fi), the `make' for the ndiswrapper fails (it does several parts, the first two are successful, then the third part, it starts to report a huge list of file missing notices and just ends in an error, unsuccessful).

Is there a way for me to pre-get these build-essential files?

Very best, :)

---

### Post by renegade1029 on 2007-02-05
I have a wierd problem following the steps with this guide. I have followed every step exactly as it is said, but when I type 'iwconfig' this is what it returns :

```
lo        no wireless extensions.

eth0      no wireless extensions.

sudo      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

Now, how could my wireless card be named 'sudo', and how can I name it 'wlan0' ?

I am a total newbie with Linux in general, Ubuntu being the first distro I install myself....

---

### Post by Cochese on 2007-02-05
@MalVeauX, I'm not sure about the update one but this should get build-essential installed.

Look in the top left corner, System>Administration>Synaptics Package Manager

Do a search for build-essential and check it for mark for installation. Then hit apply. It will show you all the other packages it needs to install(dependencies), just hit ok.  You will need the disc in your drive, but if you are running a live cd then it probably already is. Actually, can you install software while running off a live cd? I honestly don't know, I am new to this also.

You can download the .deb package from

[http://packages.ubuntu.com/edgy/devel/build-essential](http://packages.ubuntu.com/edgy/devel/build-essential)

but you will need the other packages with the red dots next to them installed as well to be able to install it.
Synaptics does all that for you so it is much easier to go that route.  If you decide to download the .deb file, just double click it and it will check to make sure you have all the dependencies it needs before it installs.  If it doesn't have them it won't let you do it.

@Renegade, post your output for each
> cat /etc/iftab
cat /etc/network/interfaces

---

### Post by maclenin on 2007-02-05
**malveaux**

I ran into a similar problem when I was trying to get my wireless card jump-started from the livecd. The irony is that build-essential, an "essential" part of being able to get your wireless card up and running is, indeed, not among those packages offered on the livecd (at least it was not on mine)...you have to download / install it from one of the repositories (or libraries of linux software) - and these repositories are accessible only via an internet connection....

Depending on your patience / stamina, it may very well be practicable to download the build-essential package and all of it's dependencies (other packages upon which a certain package relies to be able to install / function properly) remotely and then copy / install them to your laptop (via a USB flash drive or other, because the cd drive is taken up by the livecd - assuming you have not yet installed linux onto your hard drive). And, though you may want to try a google search for build-essential, and then download the package and its dependencies (from a computer with an internet connection) for install on your laptop, I see this as a tricky proposition.... 

Should you wish to try the "remote install" method, I would recommend taking a peek at these sites:

[http://packages.debian.org/unstable/devel/build-essential](http://packages.debian.org/unstable/devel/build-essential)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

My advice is to find a way to connect your laptop to the internet (via ethernet) and run the sudo aptitude update and install commands.... Much more reliable (to say nothing of less time consuming)....

Good luck!

**renegade:**

I would try a re-install - and be overly cautious as you make your way through the process - I think you must have made some sort (of) nasty typo along the way!

**cochese:**

Thanks - I think your reply in combo with mine will get malveaux over the hump!

---

### Post by MalVeauX on 2007-02-05
Heya,

Thanks for the reply. I actually went ahead and plugged into my ethernet and ran it as the guide states. All went well and I was wireless.

The problem is, I rebooted and it's not working now. The driver states it's still there, with ndiswrapper -l, and nothing apparently changed. But when I look to my wireless connection, it just says that the device can no longer be found, etc. And at another point, it showed the wireless connection but just reported "error" for status.

It's weird it was working totally cool last night.
Now, this morning, it's just busted.

No clue where to go from here. When I click the networking, it gives me a SIOCIGIFFLAGGS error: no such device.

So how did it go from working to busted? :confused: 

Edit,

Adding images. My driver is loaded. But my device isn't showing up any more. No clue why.

Very best,

---

### Post by maclenin on 2007-02-05
Glad that you're seeing (at least) a whiff of success....

Here's what I would suggest...

...post the output of...

```
iwconfig
```

...and of...

```
cat /etc/network/interfaces
```

...and of...

```
cat /etc/modprobe.d/ndiswrapper
```

...and we'll see what might need doing from there....

---

### Post by MalVeauX on 2007-02-05
Heya,

Here's an update then:

iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

cat /etc/network/interfaces:

(I removed my key and stuff from the following for obvious reasons)

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

# auto eth1
# iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid (name removed by me)
wireless-key (code removed by me)

```

cat /etc/modprobe.d/ndiswrapper:

```
alias wlan0 ndiswrapper

```

The problem is, most of this looks to me like it should be working. Yet isn't....

Very best,

---

### Post by maclenin on 2007-02-05
Hmmm, your iwconfig output worries me - as I don't see wlan0 (your wireless card's address)....

Can you also pass along the output of:

```
sudo lshw -C network
```

...(properly sanitized, as necessary) to see what it tells us....

---

### Post by MalVeauX on 2007-02-05
Heya,

Yea, the wlan0 just dissapeared. It was there, when I followed your guide after a fresh install of ubuntu 6.10. And the wireless adapter appeared in the networking too (unconntected). After following your guide the first time, it worked, and stayed. Now, it just decided to go away. I've since whiped and re-installed clean ubuntu (full format and everything). So far, the wireless hasn't come back to me for some reason and that's when the wlan0 stopped appearing.

Anyhow, more information:

```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:0e:8f:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:185
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:e0104000-e0105fff irq:11

```

(I didn't see anything in particular that needed to be sanitized here.)

Thanks for keeping up with this.

Very best,

---

### Post by maclenin on 2007-02-05
I am starting to see some familiar signs....

Can you send along two more outputs (sorry - but better to measure twice and cut only once)....

```
ndiswrapper -l
```

and

```
cat /etc/iftab/
```

...then I might have found (I feel) the magic words!

---

### Post by MalVeauX on 2007-02-05
Heya,

The more the merrier! Anything that leads to a sollution.

```

Installed drivers:
bcmwl5          driver installed, hardware present 

```

Very best,

---

### Post by maclenin on 2007-02-05
Ok, did you "modprobe -r bcm43xx" or "blacklist bcm43xx"? (I think the former....)

Also send along...

```
cat /etc/iftab
```

I think I may have found your solution....

---

### Post by MalVeauX on 2007-02-05
Heya,

Yea, I blacklisted and did those things; just as your guide stated (successfully, multiple times).

Here's the new info:

```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:b0:0e:8f:f3 arp 1
# eth1 mac 00:90:4b:97:9f:13 arp 1

```

Very best,

---

### Post by maclenin on 2007-02-05
Ok:

1. Type this (into the terminal):

```
lsmod | more
```

2. Click through 'till the end of the output in search of any references to **bcm43xx**....

3. If you do (which I think you will), find any references to **bcm43xx**, type this:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

4. Reboot your laptop....

5. After you've logged back in, open the terminal and type:

```
iwconfig
```

You should see wlan0 associated with your wireless card and you should be able to (with a wee bit of disabling of the ethernet connection and enabling of the wireless card via the Networking gui) be able to browse, wirelessly....

Does it work?

(If this doesn't work, I've got another suggestion....)

---

### Post by MalVeauX on 2007-02-05
Heya,

Well, I followed as you instructed, but found no reference to the driver you listed (nothing even close). But I carried on and blacklisted anyhow.

Rebooted, and followed it up.

Same old story:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

On we go! :)

Very best,

---

### Post by maclenin on 2007-02-05
Wow, the plot thickens!

So, lets try this:

```
sudo modprobe ndiswrapper
```

Then:

```
iwconfig
```

Has wlan0 reappeared?

If not, can you send me the output of:

```
cat /etc/modprobe.d/blacklist
```

...and we'll continue slogging....

---

### Post by MalVeauX on 2007-02-05
Heya,

The modprobe with ndiswrapper produced nilth for wlan0.

So here's the new report:

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
blacklist bcm43xx
#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx

```

Very best,

---

### Post by maclenin on 2007-02-06
When you first installed ndiswrapper did you BOTH modprobe -r bcm43xx AND blacklist it? Or just blacklist it?

It seems to me that there is still a driver competing for control of your wireless card - and this competition is preventing wlan0 from associating properly....

Can you send me the output of:

```
lsmod
```

Also, you might want to do a bit of house cleaning - don't think you need so many **blacklist bcm43xx** in the blacklist file....

In order to do clean these, first make a backup copy of the blacklist file...

```
sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist_backup
```

...just in case, and...

```
sudo nano /etc/modprobe.d/blacklist
```

...then cursor down to the bottom of the file and delete all the **blacklist bcm43xx**, but for this one...

```
#module below does not work with Broadcom 4318 wireless cards
blacklist bcm43xx
```

...and save the file (Y, and enter)....

Onward!

---

### Post by MalVeauX on 2007-02-06
Heya,

I've only blacklisted; I haven't used the -r command you listed.

Here's our new report:

```

Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
powernow_k8            15008  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ipv6                  272288  8 
ndiswrapper           200724  0 
sbp2                   24584  0 
lp                     12964  0 
af_packet              24584  2 
8139cp                 24832  0 
joydev                 11200  0 
tsdev                   9152  0 
pcmcia                 40380  0 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
8139too                29056  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
evdev                  11392  2 
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
psmouse                41352  0 
serio_raw               8452  0 
pcspkr                  4352  0 
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
mii                     6912  2 8139cp,8139too
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
i2c_nforce2             8192  0 
i2c_core               23424  2 i2c_ec,i2c_nforce2
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
amd64_agp              13124  1 
agpgart                34888  1 amd64_agp
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ohci_hcd               22532  0 
usbcore               134912  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
generic                 5764  0 
amd74xx                15260  0 [permanent]
sata_nv                11268  0 
libata                 74892  1 sata_nv
scsi_mod              144648  2 sbp2,libata
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

Very best, :)

---

### Post by maclenin on 2007-02-06
Try this:

```
sudo depmod -a
```

and then:

```
sudo modprobe ndiswrapper
```

and then

```
iwconfig
```

and send me the results....

If you your wireless card is still not showing up - add the output of this to the myriad lists of goodies you've been sending me:

```
cat /etc/ndiswrapper/bcmwl5/.conf
```

---

### Post by MalVeauX on 2007-02-06
Heya,

No go on the first few things.
But something interesting at least:

```

cat: /etc/ndiswrapper/bcmwl5/.conf: No such file or directory

```

You asked for this and it doesn't exist for me, so maybe this will lead to something useful.

Very best, :)

---

### Post by maclenin on 2007-02-06
That is WONDERFUL news - try this:

```
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
```

and then...

```
sudo depmod -a
```

and then...

```
sudo modprobe ndiswrapper
```

and then...

```
iwconfig
```

and then...

```
sudo let me know what happens....
```

---

### Post by MalVeauX on 2007-02-06
Heya,

Something is still amok.

The thing is, I already did those things when following your guide. But I did them again now, and followed it up and the report remains:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Something else to point out, that while you've seen my driver is loaded, etc, my wireless led displays that it is on (and has been on this whole time). I just don't get why it's on, why the driver is loaded and all, and that it worked previously just fine--but now, suddenly is broken and the wlan0 totally gone. That just doesn't make sense to me.

Very best,

---

### Post by maclenin on 2007-02-06
I agree - but because that file was missing that tells me something went amok during the installation - but I can't figure out what, exactly - why don't you try a re-boot - and see where you stand - if it's still a no go, I am going to have to re-fresh - and get back to you after a bit of a brain re-charge....

If you are still up to it - you might want to walk your way through a re-install of ndiswrapper - just to make certain that you didn't miss any steps - also, take a peek at this [**überguide**]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show") for additional insights!

Good luck.

More, anon....

---

### Post by spd106 on 2007-02-06
Hi MalVeauX ,

Could you post the output of these commands please

```
dmesg | grep bcm
```
```
dmesg | grep ndis
```
and
```
ndiswrapper -v
```

---

### Post by MalVeauX on 2007-02-06
@Maclenin,

Sure thing. I've actually done a few fresh installs over the past few days, trying to recreate the success or recreate the problem. So far, it's just been the problem. I followed the guide exactly each time too, so I have no idea why the first time worked. I've installed without my ethernet plugged in and with it, because it seemed to change things (it downloaded stuff when I installed with the ethernet plugged in, and made your guide produce a few unsuccessful things which ultimately wouldn't work).

I'm willing to keep doing fresh installs since it only takes a few minutes any ways, I just wish I could get it to work like the first time.

If I have to uninstall ndiswrapper, that's ok. I'll just look into how to do that I suppose.

@spd106

Sure thing,

dmesg | grep bcm - Produced nothing.

dmesg | grep ndis:

```

[17179598.904000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179598.948000] usbcore: registered new driver ndiswrapper

```

ndiswrapper -v:

```

utils Error: no version specified!
driver version:        1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

```

Very best, :)

---

### Post by spd106 on 2007-02-06
Okay, can you clean out the bcmwl5 driver and re-install it? 
Run these commands ```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -r bcmwl5
``` and check that the /etc/ndiswrapper/bcmwl5 directory is empty, if it isn't then delete any surviving files.  ```
ls /etc/ndiswrapper/bcmwl5/
``` 

Now pick up the guide at step 10 and finish it off.

It also might be useful to know which driver you are using and or where you obtained it from, if it's different to the one in the guide.

---

### Post by MalVeauX on 2007-02-06
Heya,

Well, I followed your advice. Went back and did steps 10+. My iwconfig still showed up with no wlan0. Same old same old so far.

I'm thinking a fresh install and trying the guide from scratch again at this point. As nothing seems to be working and it's the only way it worked the first time. Now, it's just getting messy I think.

Well, if I can try anything else, I'm all ears.

Very best, :)

---

### Post by maclenin on 2007-02-06
And still, hmmm....

I noticed (via your ndiswrapper -v) that you are missing the ndiswrapper utils....

Why don't you try...

```
sudo aptitude update
```

...and then...

```
sudo aptitude install ndiswrapper-utils-1.8
sudo rm /usr/sbin/ndiswrapper
sudo ln -s /usr/sbin/ndiswrapper-1.8 /usr/sbin/ndiswrapper
```

...and then...

```
ndiswrapper -v
```

...to make certain that you no longer see:

```
utils Error: no version specified!
```

...and then...

```
sudo depmod -a
sudo modprobe ndiswrapper
```

...and then...

```
iwconfig
```

what now?

---

### Post by MalVeauX on 2007-02-06
Heya,

Couldn't get very far. The update stopped:

```
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

I ran it again, and I did the apt-get update, and they both end in this every time. Then when I go ahead and keep following the update of ndis as you wrote, it still ends up saying the version error, etc.

Headache no?

Very best, :)

---

### Post by spd106 on 2007-02-06
You don't need the ndiswrapper-utils1.8 package, these userspace utilities are included in the ndiswrapper source file that you downloaded.
Try building ndiswrapper 1.34 from source again, or maybe download the newer [version 1.37]("http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=483506").


Well spotted maclenin.

[QUOTE=MalVeauX]W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems[/QUOTE]
If you want to use that repo, you will need to get the gpg key, see [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by MalVeauX on 2007-02-06
Heya,

I recompiled ndiswrapper and ran the ndiswrapper -v:

```

utils version: 1.9
driver version:        1.34
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1

```

Going to remove and then reinstall the driver now.

Very best,

::Edit::

Something good happened. I recompiled fine. Then I went ahead and uninstalled the driver. Reinstalled the driver (step 10 from guide). Now look:

```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"(removed by me)"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: (removed by me)
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

:) :)

---

### Post by maclenin on 2007-02-06
Now, that's what we like to see!

Great - so, now you are up and running - I suppose?

Thanks for your lead, spd!

---

### Post by MalVeauX on 2007-02-06
> **maclenin said:**
> Now, that's what we like to see!

Great - so, now you are up and running - I suppose?

Thanks for your lead, spd!

Yes! I am back to where I was before. It's good to be back on wi-fi. I hated sitting next to my router the past 2 days, lol.

This is what it was the first day: working. Then I don't know what happened, but I'm glad it ended up being simple. Ndis just needed to be remade and the driver reinstalled. But hey, this whole thing has been really educational to me being new to Linux. I'll have tools for trouble shooting this in the future should it break down again.

But yes, working wonderfully.

Thank you so much Maclenin. It was totally unneccessary for you to put up with these troubleshoots this long, so I really appreciate that you did regardless. You're a champ man.

And thank you spd106, your comment triggered a backtrack which lead to a fix. Wonderful!

Very, very best, :)

---

### Post by demonhunter on 2007-02-06
Thanks dude... I own you one... now I'm posting free of wires... :) 

My note has a texas instruments bcm4306 and it worked like a charm including the network manager integration (installed using the tutorial pointed in your howto)...

;)

After spending a lifetime trying to configure the wireless card, this was the unique howto to work.

:guitar: 

NO MORE WIRES...

---

### Post by camrcr on 2007-02-06
this install guide works for the wmp300n as well.thanks for the guide,being the newb to linux i was able to get it working.

---

### Post by demonhunter on 2007-02-07
Everytime that I reboot my machine I need to run a command like:

iwlist wlan0 scan

so the wireless card is recognized and apears in the available items in network manager. Does anyone have a problem like that? How did you solve that?

thanks.

---

### Post by particleMan86 on 2007-02-07
Hi,

I followed the guide on the first page and everything seems to work...except I have no signal, even though I know there is a public network here (i.e. I can connect to it in windows). Specifically:

```
[content-removed]:~/bcm4311$ iwlist wlan0 scanning
wlan0     No scan results
```

 iwconfig shows:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

(I had to edit /etc/network/interfaces to get wlan0, before it was eth1). One thing that is interesting: when I run ndiswrapper -l I get:

```
bcmwl5 : driver installed
        device (14E4:4320:1028:0003) present (alternate driver: bcm43xx)
        device (14E4:4320) present (alternate driver: bcm43xx)

```

Should there be 2 devices there? Is that a problem? I've also removed and remade/reinstalled ndiswrapper with no success. 

Let me know if you need any more output.

Cheers,

---

### Post by maclenin on 2007-02-07
**demonhunter **and **camrcr**: Thanks for the fb and pleased there are no strings attached!

**demonhunter**: I would suggest taking a peek at:

```
sudo nano /etc/network/interfaces
```

...to make certain your most frequently used wireless data is entered, properly, here...

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid your_essid
```

...and this will connect you, automatically, with your ap of choice, every time you boot up....

---

### Post by maclenin on 2007-02-07
**particleMan86**:

Can you send me the output of:

```
sudo lshw -C network
```

...I am a bit thrown by the multiple device listings from ndiswrapper -l....

And, actualy, while you're at it send me the output of...

```
cat /etc/ndiswrapper/bcmwl5/.conf
```

...as well....

---

### Post by renegade1029 on 2007-02-10
Sorry I haven't replied faster, I'm caught in mid-term frenzy ](*,) 

I made a fresh install of Ubuntu and followed the steps in the guide. I still have no wireless, but some things have improved.

To save a little time, I went and got the output of the most frequently asked commands, so here we go :

```
renegade@renegade-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

```
renegade@renegade-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@03:02.0
       logical name: wlan0
       version: 03
       serial: 00:90:4b:f4:0b:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.34 firmware=Broadcom,03/23/2006, 4.40.19.0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b0204000-b0205fff irq:169
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:74:6c:fc
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:a000-a0ff iomemory:b020a400-b020a4ff irq:233
```

```
renegade@renegade-laptop:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0f:b0:74:6c:fc arp 1
# eth1 mac 00:90:4b:f4:0b:33 arp 1
```

```
renegade@renegade-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp
wireless-essid Maison
auto wlan0
```

```
renegade@renegade-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
```

```
renegade@renegade-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
```

```
renegade@renegade-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
blacklist bcm43xx
```

```
renegade@renegade-laptop:~$ lsmod
Module                  Size  Used by
nls_cp437               8704  1 
vfat                   17920  1 
fat                    65456  1 vfat
sg                     44584  0 
sd_mod                 25728  2 
usb_storage            89792  1 
libusual               21544  1 usb_storage
ipv6                  334432  8 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  4 rfcomm,l2cap
powernow_k8            16576  0 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sony_acpi               7704  0 
sbs                    20928  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
i2c_core               29312  1 i2c_ec
hotkey                 14536  0 
dev_acpi               17540  0 
container               6656  0 
button                  9888  0 
battery                14088  0 
asus_acpi              21924  0 
ac                      8328  0 
ndiswrapper           279848  0 
nls_utf8                3840  2 
ntfs                  109128  1 
af_packet              29452  4 
sbp2                   29448  0 
scsi_mod              181424  4 sg,sd_mod,usb_storage,sbp2
parport_pc             43560  0 
lp                     16584  0 
parport                49932  2 parport_pc,lp
joydev                 14208  0 
tsdev                  11136  0 
pcmcia                 49048  0 
8139cp                 29696  0 
usbhid                 51360  0 
8139too                34816  0 
tifm_7xx1              11264  0 
tifm_core              12928  1 tifm_7xx1
yenta_socket           33420  1 
rsrc_nonstatic         16896  1 yenta_socket
pcmcia_core            52772  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                51088  0 
pcspkr                  5248  0 
sdhci                  22796  0 
mmc_core               40456  1 sdhci
mii                     8192  2 8139cp,8139too
snd_atiixp             26644  1 
serio_raw              10244  0 
evdev                  14592  2 
snd_atiixp_modem       21900  0 
snd_pcm_oss            57344  0 
snd_ac97_codec        127064  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            4352  1 snd_ac97_codec
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm               108168  4 snd_atiixp,snd_atiixp_modem,snd_pcm_oss,snd_ac97_codec
snd_timer              31112  1 snd_pcm
snd                    79016  9 snd_atiixp,snd_atiixp_modem,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  3 snd_atiixp,snd_atiixp_modem,snd_pcm
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
ext3                  164624  1 
jbd                    74024  1 ext3
ehci_hcd               40456  0 
ohci_hcd               25988  0 
usbcore               167840  7 usb_storage,libusual,ndiswrapper,usbhid,ehci_hcd,ohci_hcd
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
ide_disk               21248  4 
generic                 7940  0 
atiixp                  9232  1 
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit
```

```
renegade@renegade-laptop:~$ cat /etc/ndiswrapper/bcmwl5/.conf
NdisVersion|0x50001
Environment|1
class_guid|4d36e972-e325-11ce-bfc1-08002be10318
NetworkAddress|XX:XX:XX:XX:XX:XX
driver_version|Broadcom,03/23/2006, 4.40.19.0
BusType|5

11HNetworks|1
Afterburner|1
AssocRoamPref|0
BadFramePreempt|0
band|0
BandPref|0
BTCoexist|0
ccx_rm|1
ccx_rm_limit|300
Channel|11
Country|US
EFCEnable|0
EnableAutoConnect|0
EnableLeap|1
EnableSoftAP|0
frag|2346
FrameBursting|1
gpio0|3
gpio1|2
gpio2|0
gpio3|0
gpiotimerval|0xa0000
HelpText|The Broadcom 802.11 Network Adapter provides wireless local area networking.
IBSSGMode|2
IBSSGProtection|2
Interference_Mode|-1
LowerRange|ethernet
Managed|1
MixedCell|0
MPC|1
NetworkAddress|
NetworkType|-1
PLCPHeader|0
PowerSaveMode|0
PwrOut|100
Rate|0
RateA|0
RoamTrigger|-75
rts|2347
scan_channel_time|-1
scan_home_time|-1
scan_passes|-1
scan_unassoc_time|-1
Service|BCM43XX
SSID|
ssid_auto_promote|0
UpperRange|ndis5
vlan_mode|-1
WEP|
WME|-1
WZCCoexist|0
```

```
renegade@renegade-laptop:~$ iwlist wlan0 scanning
wlan0     No scan results
```

I also have the output of dmesg at hand, but I don't think it's that important for now. I hope  this helps.

---

### Post by spd106 on 2007-02-10
Please do post the dmesg output as well.

---

### Post by renegade1029 on 2007-02-10
Alright, here it is :

```
renegade@renegade-laptop:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/hda2 ro quiet splash)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003feff000 - 000000003ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f7df0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x000000003fef9500
[    0.000000] ACPI: FADT (v001 HP     Piranha  0x06040000 ATI  0x000f4240) @ 0x000000003fefee06
[    0.000000] ACPI: MCFG (v001 ATI    Piranha  0x06040000 LOHR 0x0000005f) @ 0x000000003fefee7a
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003fefeeb6
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x000000003fefefa6
[    0.000000] ACPI: DSDT (v001     HP     3085 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003fef0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003fef0000
[    0.000000] On node 0 totalpages: 256844
[    0.000000]   DMA zone: 2592 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254252 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ f884000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda2 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 997.134 MHz processor.
[   16.711551] Console: colour VGA+ 80x25
[   16.712747] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.714663] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   16.734560] Memory: 1019964k/1047488k available (2129k kernel code, 27136k reserved, 1424k data, 188k init)
[   16.812684] Calibrating delay using timer specific routine.. 1996.49 BogoMIPS (lpj=3992999)
[   16.812782] Security Framework v1.0.0 initialized
[   16.812792] SELinux:  Disabled at boot.
[   16.812830] Mount-cache hash table entries: 256
[   16.813071] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.813077] CPU: L2 Cache: 512K (64 bytes/line)
[   16.813083] CPU 0/0(1) -> Node 0 -> Core 0
[   16.813106] SMP alternatives: switching to UP code
[   16.813329] Freeing SMP alternatives: 20k freed
[   16.813554] checking if image is initramfs... it is
[   17.822339] Freeing initrd memory: 5751k freed
[   17.829491] ACPI: Core revision 20060707
[   17.829838] ACPI: Looking for DSDT ... not found!
[   18.509288] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   18.549297] Using local APIC timer interrupts.
[   18.649498] result 12464192
[   18.649501] Detected 12.464 MHz APIC timer.
[   18.651116] Brought up 1 CPUs
[   18.651156] testing NMI watchdog ... OK.
[   18.691250] migration_cost=0
[   18.691664] NET: Registered protocol family 16
[   18.691708] ACPI: bus type pci registered
[   18.698759] PCI: Using MMCONFIG at e0000000
[   18.698806] PCI: No mmconfig possible on device 0:18
[   18.728008] ACPI: Interpreter enabled
[   18.728013] ACPI: Using IOAPIC for interrupt routing
[   18.728829] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.728834] PCI: Probing PCI hardware (bus 00)
[   18.801746] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   18.802141] Boot video device is 0000:01:05.0
[   18.827927] PCI: Transparent bridge - 0000:00:14.4
[   18.828011] PCI: Bus #04 (-#07) is hidden behind transparent bridge #03 (-#04) (try 'pci=assign-busses')
[   18.828016] Please report the result to linux-kernel to fix this permanently
[   18.828051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.833373] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   18.833799] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   18.834219] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   18.834644] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   18.835089] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   18.835508] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   18.835927] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   18.836347] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   18.837392] ACPI: Embedded Controller [EC0] (gpe 26) interrupt mode.
[   19.094846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   19.120377] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   19.121078] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   19.121993] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.122008] pnp: PnP ACPI init
[   19.279718] pnp: PnP ACPI: found 10 devices
[   19.279793] PCI: Using ACPI for IRQ routing
[   19.279799] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.279813] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   19.279860] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   19.280087] PCI-DMA: Disabling IOMMU.
[   19.280487] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   19.280493] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[   19.280498] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   19.280504] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   19.280812] PCI: Bridge: 0000:00:01.0
[   19.280817]   IO window: 9000-9fff
[   19.280822]   MEM window: b0100000-b01fffff
[   19.280827]   PREFETCH window: c0000000-cfffffff
[   19.280831] PCI: Bridge: 0000:00:04.0
[   19.280834]   IO window: disabled.
[   19.280837]   MEM window: disabled.
[   19.280840]   PREFETCH window: disabled.
[   19.280849] PCI: Bus 4, cardbus bridge: 0000:03:04.0
[   19.280854]   IO window: 0000a400-0000a4ff
[   19.280858]   IO window: 0000a800-0000a8ff
[   19.280864]   PREFETCH window: 50000000-51ffffff
[   19.280869]   MEM window: 52000000-53ffffff
[   19.280874] PCI: Bridge: 0000:00:14.4
[   19.280879]   IO window: a000-afff
[   19.280884]   MEM window: b0200000-b02fffff
[   19.280889]   PREFETCH window: 50000000-51ffffff
[   19.280907] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.280938] GSI 16 sharing vector 0xB1 and IRQ 16
[   19.280944] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[   19.281052] NET: Registered protocol family 2
[   19.314538] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   19.314994] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   19.317670] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.319041] TCP: Hash tables configured (established 131072 bind 65536)
[   19.319047] TCP reno registered
[   19.319623] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   19.320229] audit: initializing netlink socket (disabled)
[   19.320245] audit(1171103835.616:1): initialized
[   19.320496] VFS: Disk quotas dquot_6.5.1
[   19.320529] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.320613] Initializing Cryptographic API
[   19.320620] io scheduler noop registered
[   19.320633] io scheduler anticipatory registered
[   19.320646] io scheduler deadline registered
[   19.320675] io scheduler cfq registered (default)
[   19.321494] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   19.321502] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
[   19.321522] assign_interrupt_mode Found MSI capability
[   19.321572] Allocate Port Service[0000:00:04.0:pcie00]
[   19.321630] Allocate Port Service[0000:00:04.0:pcie01]
[   19.357633] Real Time Clock Driver v1.12ac
[   19.357693] Linux agpgart interface v0.101 (c) Dave Jones
[   19.357699] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.358546] GSI 17 sharing vector 0xC9 and IRQ 17
[   19.358553] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[   19.358563] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[   19.358660] mice: PS/2 mouse device common for all mice
[   19.359535] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.359845] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   19.359852] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   19.360184] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   19.367186] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.367206] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.367573] TCP bic registered
[   19.367586] NET: Registered protocol family 1
[   19.367597] NET: Registered protocol family 8
[   19.367602] NET: Registered protocol family 20
[   19.367845] ACPI: (supports S0 S3 S4 S5)
[   19.367915] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.367952] Freeing unused kernel memory: 188k freed
[   19.373769] input: AT Translated Set 2 keyboard as /class/input/input0
[   19.461687] vga16fb: initializing
[   19.461697] vga16fb: mapped to 0xffff8100000a0000
[   19.548199] Console: switching to colour frame buffer device 80x25
[   19.548208] fb0: VGA16 VGA frame buffer device
[   20.636546] Capability LSM initialized
[   20.901033] ACPI: Processor [CPU0] (supports 8 throttling states)
[   21.009066] ACPI Exception (acpi_thermal-0417): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[   21.116798] ACPI: Thermal Zone [THRM] (38 C)
[   21.704964] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   21.704990] GSI 18 sharing vector 0xD1 and IRQ 18
[   21.704996] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 209
[   21.705012] ATIIXP: chipset revision 0
[   21.705016] ATIIXP: not 100% native mode: will probe irqs later
[   21.705029]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   21.705048]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   21.705060] Probing IDE interface ide0...
[   21.996356] hda: FUJITSU MHU2100AT, ATA DISK drive
[   22.673890] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.711285] Probing IDE interface ide1...
[   23.451002] hdc: TSSTcorpCD/DVDW TS-L532R, ATAPI CD/DVD-ROM drive
[   24.135962] ide1 at 0x170-0x177,0x376 on irq 15
[   24.157077] hda: max request size: 128KiB
[   24.169941] hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[   24.172033] hda: cache flushes supported
[   24.172095]  hda: hda1 hda2 hda3
[   24.266127] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[   24.266142] Uniform CD-ROM driver Revision: 3.20
[   24.824517] ieee1394: Initialized config rom entry `ip1394'
[   24.826846] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 20 (level, low) -> IRQ 177
[   24.877147] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[b0208000-b02087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.909831] usbcore: registered new driver usbfs
[   24.910621] usbcore: registered new driver hub
[   24.913706] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   24.914534] GSI 19 sharing vector 0xD9 and IRQ 19
[   24.914541] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 217
[   24.914800] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   24.915255] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   24.915288] ohci_hcd 0000:00:13.0: irq 217, io mem 0xb0000000
[   24.977427] usb usb1: configuration #1 chosen from 1 choice
[   24.977611] hub 1-0:1.0: USB hub found
[   24.977631] hub 1-0:1.0: 4 ports detected
[   25.085268] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 217
[   25.085505] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   25.085847] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   25.085877] ohci_hcd 0000:00:13.1: irq 217, io mem 0xb0001000
[   25.149224] usb usb2: configuration #1 chosen from 1 choice
[   25.149395] hub 2-0:1.0: USB hub found
[   25.149412] hub 2-0:1.0: 4 ports detected
[   25.268777] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 217
[   25.269048] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   25.269166] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   25.269242] ehci_hcd 0000:00:13.2: irq 217, io mem 0xb0002000
[   25.269258] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.269390] usb usb3: configuration #1 chosen from 1 choice
[   25.269424] hub 3-0:1.0: USB hub found
[   25.269436] hub 3-0:1.0: 8 ports detected
[   25.452035] Attempting manual resume
[   25.496468] kjournald starting.  Commit interval 5 seconds
[   25.496486] EXT3-fs: mounted filesystem with ordered data mode.
[   25.652569] ohci_hcd 0000:00:13.0: wakeup
[   26.036157] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   26.148342] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[573f02000d074179]
[   26.236145] usb 1-1: configuration #1 chosen from 1 choice
[   39.258008] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.267901] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.058629] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 201
[   40.170872] MC'97 0 converters and GPIO not ready (0x1)
[   40.172416] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 201
[   40.368458] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   40.368465] sdhci: Copyright(c) Pierre Ossman
[   40.368526] sdhci: SDHCI controller found at 0000:03:04.4 [104c:8034] (rev 0)
[   40.368558] GSI 20 sharing vector 0xE1 and IRQ 20
[   40.368564] ACPI: PCI Interrupt 0000:03:04.4[D] -> GSI 23 (level, low) -> IRQ 225
[   40.368943] mmc0: SDHCI at 0xb020a000 irq 225 DMA
[   40.369240] mmc1: SDHCI at 0xb0208c00 irq 225 DMA
[   40.369516] mmc2: SDHCI at 0xb0208800 irq 225 DMA
[   40.408378] input: PC Speaker as /class/input/input1
[   40.684357] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 177
[   40.684378] Yenta: CardBus bridge found at 0000:03:04.0 [103c:3085]
[   40.684400] Yenta: Enabling burst memory read transactions
[   40.684407] Yenta: Using INTVAL to route CSC interrupts to PCI
[   40.684411] Yenta: Routing CardBus interrupts to ISA
[   40.684420] Yenta TI: socket 0000:03:04.0, mfunc 0x00aa1b22, devctl 0x64
[   40.785200] 8139too Fast Ethernet driver 0.9.27
[   40.808167] usbcore: registered new driver hiddev
[   40.816479] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /class/input/input2
[   40.816592] input: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:13.0-1
[   40.816619] usbcore: registered new driver usbhid
[   40.816626] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   40.918964] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[   40.918972] Socket status: 30000006
[   40.918978] Yenta: Raising subordinate bus# of parent bus (#03) from #04 to #07
[   40.918988] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   40.918995] pcmcia: parent PCI bridge Memory window: 0xb0200000 - 0xb02fffff
[   40.919001] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x51ffffff
[   40.926375] GSI 21 sharing vector 0xA9 and IRQ 21
[   40.926383] ACPI: PCI Interrupt 0000:03:04.3[B] -> GSI 21 (level, low) -> IRQ 169
[   40.928285] GSI 22 sharing vector 0xE9 and IRQ 22
[   40.928293] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 22 (level, low) -> IRQ 233
[   40.930323] eth0: RealTek RTL8139 at 0xffffc200100aa400, 00:0f:b0:74:6c:fc, IRQ 233
[   40.930332] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   40.964655] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x23a0b1, caps: 0xa04713/0x200000
[   40.982366] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[   40.999905] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   41.202993] eth0: link down
[   41.232332] ts: Compaq touchscreen protocol output
[   41.326542] irq 169: nobody cared (try booting with the "irqpoll" option)
[   41.326550] 
[   41.326552] Call Trace: <IRQ> <ffffffff802b68a5>{__report_bad_irq+53}
[   41.326581]        <ffffffff802b6b20>{note_interrupt+544} <ffffffff8021051a>{handle_IRQ_event+26}
[   41.326604]        <ffffffff802b6190>{__do_IRQ+224} <ffffffff802737e2>{do_IRQ+66}
[   41.326624]        <ffffffff80265d08>{ret_from_intr+0} <EOI>
[   41.326652] handlers:
[   41.326656] [<ffffffff882551e0>] (tifm_7xx1_isr+0x0/0x140 [tifm_7xx1])
[   41.326669] Disabling IRQ #169
[   41.913417] lp: driver loaded but no devices found
[   42.009551] SCSI subsystem initialized
[   42.027114] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   42.027121] ieee1394: sbp2: Try serialize_io=0 for better performance
[   42.082502] Adding 1052248k swap on /dev/disk/by-uuid/cf147909-94a4-44f3-9157-d75b5f881f8c.  Priority:-1 extents:1 across:1052248k
[   42.194972] EXT3 FS on hda2, internal journal
[   42.313248] NET: Registered protocol family 17
[   42.504909] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   42.559330] NTFS volume version 3.1.
[   45.241011] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[   45.347830] ndiswrapper (link_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[   45.350360] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[   45.350670] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 21 (level, low) -> IRQ 169
[   45.355521] ndiswrapper: using IRQ 169
[   46.145387] wlan0: ethernet device 00:90:4b:f4:0b:33 using NDIS driver: bcmwl5, version: 0x4281300, NDIS version: 0x501, vendor: '', 14E4:4320.5.conf
[   46.145443] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   46.146282] usbcore: registered new driver ndiswrapper
[  110.213497] ACPI: AC Adapter [ACAD] (on-line)
[  111.296606] ACPI: Battery Slot [BAT1] (battery present)
[  111.320534] ACPI: Power Button (FF) [PWRF]
[  111.320556] ACPI: Lid Switch [LID]
[  111.320565] ACPI: Power Button (CM) [PWRB]
[  111.667144] ibm_acpi: ec object not found
[  111.702134] pcc_acpi: loading...
[  111.850208] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  112.143070] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[  112.351507] powernow-k8:    0 : fid 0x10 (2400 MHz), vid 0x2 (1500 mV)
[  112.351514] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0x6 (1400 mV)
[  112.351520] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe (1200 mV)
[  112.351525] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x10 (1150 mV)
[  112.351533] cpu_init done, current fid 0x2, vid 0x10
[  137.931568] Bluetooth: Core ver 2.8
[  137.931580] NET: Registered protocol family 31
[  137.931585] Bluetooth: HCI device and connection manager initialized
[  137.931624] Bluetooth: HCI socket layer initialized
[  138.274968] Bluetooth: L2CAP ver 2.8
[  138.274978] Bluetooth: L2CAP socket layer initialized
[  138.581328] Bluetooth: RFCOMM socket layer initialized
[  138.581375] Bluetooth: RFCOMM TTY layer initialized
[  138.581380] Bluetooth: RFCOMM ver 1.7
[  142.082800] NET: Registered protocol family 10
[  142.082947] lo: Disabled Privacy Extensions
[  142.083042] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  142.083048] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  142.083091] IPv6 over IPv4 tunneling driver
[  169.996235] usb 3-3: new high speed USB device using ehci_hcd and address 3
[  170.136783] usb 3-3: configuration #1 chosen from 1 choice
[  170.306655] usbcore: registered new driver libusual
[  170.377691] Initializing USB Mass Storage driver...
[  170.377825] scsi0 : SCSI emulation for USB Mass Storage devices
[  170.377909] usb-storage: device found at 3
[  170.377913] usb-storage: waiting for device to settle before scanning
[  170.377928] usbcore: registered new driver usb-storage
[  170.377933] USB Mass Storage support registered.
[  175.375375] usb-storage: device scan complete
[  175.379246]   Vendor: VBTM      Model: Store 'n' Go      Rev: 5.00
[  175.379262]   Type:   Direct-Access                      ANSI SCSI revision: 00
[  176.099192] SCSI device sda: 502784 512-byte hdwr sectors (257 MB)
[  176.099942] sda: Write Protect is off
[  176.099948] sda: Mode Sense: 23 00 00 00
[  176.099952] sda: assuming drive cache: write through
[  176.102563] SCSI device sda: 502784 512-byte hdwr sectors (257 MB)
[  176.103312] sda: Write Protect is off
[  176.103318] sda: Mode Sense: 23 00 00 00
[  176.103321] sda: assuming drive cache: write through
[  176.103627]  sda: sda1
[  176.105411] sd 0:0:0:0: Attached scsi removable disk sda
[  176.120036] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  176.811520] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  260.079018] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  260.079028] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  260.079034] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.
[  260.198972] hdc: tray open
[  260.198980] end_request: I/O error, dev hdc, sector 0
[  260.198988] Buffer I/O error on device hdc, logical block 0
[  260.200368] hdc: tray open
[  260.200373] end_request: I/O error, dev hdc, sector 4
[  260.200378] Buffer I/O error on device hdc, logical block 1
[  260.201757] hdc: tray open
[  260.201761] end_request: I/O error, dev hdc, sector 8
[  260.201766] Buffer I/O error on device hdc, logical block 2
[  260.203146] hdc: tray open
[  260.203150] end_request: I/O error, dev hdc, sector 12
[  260.203155] Buffer I/O error on device hdc, logical block 3
[  260.204536] hdc: tray open
[  260.204541] end_request: I/O error, dev hdc, sector 16
[  260.204546] Buffer I/O error on device hdc, logical block 4
[  260.205925] hdc: tray open
[  260.205929] end_request: I/O error, dev hdc, sector 20
[  260.205934] Buffer I/O error on device hdc, logical block 5
[  260.207314] hdc: tray open
[  260.207319] end_request: I/O error, dev hdc, sector 24
[  260.207323] Buffer I/O error on device hdc, logical block 6
[  260.208704] hdc: tray open
[  260.208708] end_request: I/O error, dev hdc, sector 28
[  260.208713] Buffer I/O error on device hdc, logical block 7
[  260.210093] hdc: tray open
[  260.210097] end_request: I/O error, dev hdc, sector 0
[  260.210102] Buffer I/O error on device hdc, logical block 0
[  260.211482] hdc: tray open
[  260.211487] end_request: I/O error, dev hdc, sector 4
[  260.211491] Buffer I/O error on device hdc, logical block 1
[  260.212871] hdc: tray open
[  260.212876] end_request: I/O error, dev hdc, sector 0
[  260.214260] hdc: tray open
[  260.214264] end_request: I/O error, dev hdc, sector 4
[  260.215649] hdc: tray open
[  260.215653] end_request: I/O error, dev hdc, sector 0
[  260.217037] hdc: tray open
[  260.217041] end_request: I/O error, dev hdc, sector 4
```

---

### Post by spd106 on 2007-02-10
Can you run iwlist scan again only as root. i.e. ```
sudo iwlist wlan0 scan
```

---

### Post by renegade1029 on 2007-02-10
Same thing, no scanning results

---

### Post by spd106 on 2007-02-10
Sorry, I'm almost out of ideas.

Does your laptop have a hardware wifi switch? Sometimes the card doesn't work properly when it's not switched on during boot. Maybe have a look around for issues with your specific network card or laptop.

---

### Post by renegade1029 on 2007-02-10
My switch is always on, so this must not be the problem.

I'm going to look around for my laptop model, an HP Pavilion zv6170ca.

Thanks for the help anyways.

---

### Post by renegade1029 on 2007-02-10
I just thought of something.

Does the fact that I am on amd64 have an effect? Having an Athlon64 3800+, I downloaded the amd64 version. Does ndiswrapper still work under this version?

---

### Post by zeddock on 2007-02-10
```
sudo tar –xvzf ndiswrapper-1.34.tar.gz
```

maclenin!  I had to use your guide again since I did an update and am guessing that since "linux-2.6.17-10-generic" is now "linux-2.6.17-11-generic" it broke the wireless.

Anyway... I figured out what the real problem with your listed code is...
the -xvzf, ends up with 2 dashes or one long dash.  Please look and see if you understand what I am saying.

If I cut/paste it does not work.  If I just type it, it does.

zeddock

---

### Post by carrie.peary on 2007-02-10
I got all the way to installing my divers with 'sudo ndiswrapper -i bcmwl5.inf' but it says that it is already installed, use -e to remove. I tried using -e to remove it but it won't let me

Also, when i type ndiswrapper -l is lists bcmwl5 as a driver but that is invalid next to it....

any way to fix this? or anything? cause i can't move the .conf files since they are not there...thanks!

---

### Post by georgetruong on 2007-02-10
does anybody get this error when trying to install drivers?...

```
sudo ndiswrapper -i bcmwl5.inf
forcing paramater IBSSGMode from 0 to 2
```

trying to figure out how to get my friend's laptop up. it's an AMD64 HP Pavilion zv6170us. everything seems to be fine from installation other then the forcing parameter thing. the lights for the wireless seem to be on, but when i run iwlist wlan0 scan it immediately returns 0 results.

eth1 is not found in iwconfig. bcm43xx has been removed with modprobe -r and blacklisted. my essid is defined in /etc/network/interfaces with the proper key, but it refuses to connect to it or acknowledge that the access point is there.

also, i don't seem to have a  /etc/ndiswrapper/bcmwl5/.conf file. 

running out of ideas...

---

### Post by renegade1029 on 2007-02-10
Well, turns out I was right, but it didn't fix my problem. I instaled the i386 version of Ubuntu, re-ran this guide, and now there's a slight improvement.

Here's the output of iwconfig :
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

And now, when I scan the networks :
```
renegade@renegade-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:ED:7D:EC
                    ESSID:"Maison"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

I have everything configured right in interfaces :
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Maison
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0
```

But I still can't connect! What should I do next?

---

### Post by maclenin on 2007-02-10
**renegae1029:**

Try forcing the association with "Maison"....

```
sudo iwconfig wlan0 essid Maison
```

...then...

```
iwconfig
```

...to see whether wlan0 has associated.

**georgetruong:**

Can you post the output from:

```
sudo lshw -C network
```

I am not familiar with the error message you've received....

**carrie.peary**

Take a swing back to page 7 of the thread you're in - and read a bit before and a bit after [**this post**]("http://www.ubuntuforums.org/showpost.php?p=2114608&postcount=74") - these might help you solve your riddle....

**zeddock:**

Good snipe! That's, exactly correct - I edited/proofed the early version of the guide using a word-processor - off-line and the long dash was auto-generated! Again, nice catch!

---

### Post by renegade1029 on 2007-02-10
**maclenin**

I did, many times, and still the essid in iwconfig shows off/any. However, wifi-radar sees the network without any problems, but can't connect to it.

I tried installing Network Manager, but it killed ndiswrapper and I had to uninstall network manager and reinstall ndiswrapper.

---

### Post by maclenin on 2007-02-10
You might want to try modifying la Maison's security settings to see whether you can, indeed, connect to the router - if so, you might be able hone in on the issue, more accurately. Do you have a MAC filter on that might be preventing your wireless card / router from associating?

---

### Post by renegade1029 on 2007-02-11
Well right now is not a good time to test this, since I am at my girlfriend's house, and I don't know the security encryption she's using.

Still, it would be fun to have WPA and WEP working, but that can wait. When I get home tonight, I'll be able to play with the security settings and see what I can do from there.

---

### Post by maclenin on 2007-02-11
My suggestions re: modifying security settings are purely ad hoc - just to test your ability to connect and to more specifically identify whether:

1. It's a wireless card configuration / ndiswrapper / bcmwl5 issue

or

2. It's a security settings alone issue....

Just helps focus trouble-shooting efforts....

Once you've tested - you can re-engage the security settings - and work from there.

(By the way, if your not at home, you should not be reading this - enjoy the time with your lady friend....)

---

### Post by zeddock on 2007-02-11
> zeddock:
Good snipe! That's, exactly correct - I edited/proofed the early version of the guide using a word-processor - off-line and the long dash was auto-generated! Again, nice catch!

Actually, I am thinking I am pretty lame since many other had no problem and I am the only one to think this was a stumbling block!

BTW, will I continue to have to re-do your guide every time an update comes in?

Thanx!

zeddock

---

### Post by renegade1029 on 2007-02-11
**zeddock**
You're not the only one. First time I followed the guide I copied/pasted everything, and I got the error. I guess the people who got no error typed everything...


**maclenin**

Tough luck. I turned off any security on my home network, and I still can't connect. I tried using Wifi-radar, and it didnt work. Here's what I tried to do:

I started by trying to connect via Wifi-radar. I got a "Could not get ip address" message. So I decided to try it the console way.

First thing I did was scan the networks :

```
renegade@renegade-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:7A:7B:2D
                    ESSID:"Powers"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:18:39:49:61:5A
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
```

My home network's essid is "Powers". OK. So my card can see it. I try to set the essid to "Powers", and see the result :

```
renegade@renegade-laptop:~$ sudo iwconfig wlan0 essid Powers
renegade@renegade-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"Powers"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

The ESSID didn't change. But I remarked that I am not on the right channel, so I changed my card's channel to match my network's :

```
renegade@renegade-laptop:~$ sudo iwconfig wlan0 channel 6
renegade@renegade-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"Powers"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Good. So now I am on the same frequency. Next thing I see is that Wifi-radar didn't change the essid, but it gave a nickname to my card. Thinking this might interfere, I removed it :

```
renegade@renegade-laptop:~$ sudo iwconfig wlan0 nick ""
renegade@renegade-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

So the nick is gone. Time to retry to change the essid :

```
renegade@renegade-laptop:~$ sudo iwconfig wlan0 essid "Powers"
renegade@renegade-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

So my problem is that whatever I try, I cannot change my card's essid. It stays on off/any and won't budge. I'll try to do some research on my side to see if this is about something else, but any help wil be appreciated ;)

---

### Post by iam_foo on 2007-02-12
what is the benefit of switching from fwcutter?

---

### Post by maclenin on 2007-02-12
**iam_foo:**

For me, the benefits (of ndiswrapper over fwcutter) were (and continue to be) ENORMOUS! In terms of the speed increase, stability and reliability, fwcutter can't hold a candle to ndiswrapper. I have had next to ZERO issues with ndiswrapper - other than that very rare need to re-associate the card with my ap (2 times in the past month - and one or both events came after I had been engaged in some tinkering of another kind that had locked up the system....) or (**zeddock**) the necessity to recompile ndiswrapper after upgrading the kernel. In short, non-events....

In my opinion, there is absolutely no contest - ndiswrapper is the champ.

**renegade1029**

Hmmm.... I feel like I've been down this road before (elsewhere).... Let me know if you find anything - I'll do a bit of scratching and searching, as well....

I can't place it - but I think I've read, in these forums, that folks have had issues with wifi-radar, when configuring their cards...ergo, I suggest you just terminal it - to troubleshoot and configure....

In the meantime, could you send me a latest and greatest...

```
cat /etc/network/interfaces
```

...to give me something to read....

**zeddock:**

No, you will not have to re-do the guide every time a new "update comes in" - which I assume means the kernel upgrade? If so, it's, actually, a pretty straight forward process:

Start with step 5 in the guide:

Id the kernel...

```
uname -r
```

...update the headers...

```
sudo aptitude install linux-headers-2.6.17-1**1**-generic 
sudo ln -s /usr/src/linux-2.6.17-1**1**-generic /lib/modules/2.6.17-1**1**-generic/build
```

...recompile / reinstall ndiswrapper...

```
cd ~/ndiswrapper/ndiswrapper-1.34
make distclean
make
sudo make install
```

...then:

sudo depmod -a
sudo modprobe ndiswrapper

That should do it!

Please note that I have - via additional gentle persuasion - "updated" the guide to enable a more "sudo free" install - i.e. ndiswrapper and bcm4306 directories are now made (in step 1) in the "~" directory - not in "/home". However, for you, zeddock, I believe you would still have to use "sudo" to...

```
make distclean
make
```

...given the permissions associated with "/home/ndiswrapper/ndiswrapper-1.34"....

---

### Post by renegade1029 on 2007-02-12
Well, I think there's nothing wrong with my interfaces :

```
renegade@renegade-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Powers
auto wlan0
```

I've done a bit of searching, and all I see is people having the same problem, but no solution :(

If nothing works, I will try the other method, involving fwcutter discussed [here]("http://www.ubuntuforums.org/showthread.php?t=267169&highlight=bcm43xx")

---

### Post by georgetruong on 2007-02-12
@maclenin:

sorry i've been away the past couple of days. here's the info from 

sudo lshw -C network

```
*-network:0

       description: Wireless interface

       product: BCM4306 802.11b/g Wireless LAN Controller

       vendor: Broadcom Corporation

       physical id: 2

       bus info: pci@03:02.0

       logical name: wlan0

       version: 03

       serial: 00:14:a5:10:47:b5

       width: 32 bits

       clock: 33MHz

       capabilities: bus_master ethernet physical wireless

       configuration: broadcast=yes driver=ndiswrapper driverversion=1.34 firmware=Broadcom,03/23/2006, 4.40.19.0 link=no multicast=yes wireless=IEEE 802.11g

       resources: iomemory:b0204000-b0205fff irq:225
```

---

### Post by hum525 on 2007-02-12
hello

First thank you for your post regarding the install of ndiswrapper.  I have been trying to do what you post as instructions for the wireless networking. 

After installing ubutu and running the 2.6.17-10-generic kernell I can see the wireless card in the networking pannel but when trying to enable it.  It will reset to disable. I ran all the commands but now the wireless card disappers from the networking pannel.  I donwloaded the drivers that you mention and followed all the steps but the wireles card is listed on the device manager but not under the networking panel

Any help please

---

### Post by nekofelin on 2007-02-14
hi, 

thanks for the tutorial but i have one question.  currently using a Compaq to get ubuntu (6.1)edgy working and i had the same wireless card.  i followed all the steps with no errors until #14 where my eth1/wlan0 are not there?  do you have any idea what that could have been? i'm pretty much a linux noobie so, any help would be appreciated!

---

### Post by josv on 2007-02-14
Hi maclenin,

THANKS THANKS THANKS!
I've been struggling with this thing only a full day, but I was starting to get annoyed :-)

Now, after following all your steps though, it still wasn't working though, but in my desperation I just went ahead and did something illogical (I guess, since I'm a newbie on Linux/Ubuntu).

Instead of just doing this:
alias wlan0 ndiswrapper

I added another line, making it:
alias wlan0 ndiswrapper
alias eth1 ndiswrapper

You know... what the heck, if it breaks, I can fix it.

Reboot... and guess what?   Everything works like a charm, and I'm sending this over my wifi connection.

You're the best (I've STFW and RTFM, tried all of them)!

ok. Flatter mode off.

Cheers,
Jos

---

### Post by iam_foo on 2007-02-14
I switched over..after working through some problems..everything is much better than with fwcutter.
thanks.

---

### Post by Codera on 2007-02-16
Hello!

I runned Ubuntu from the Livecd today, and configured everything by the guide. I was so surprised when it worked. Now i installed Ubuntu into hard drive and also did everything like the guide says (copy/paste) and it doesnt work. 
I noticed that, when i used livecd, then at the 13. step - sudo modprobe ndiswrapper command it gave that error, but when i did it from the hard drive it was error free. I tryd to Blacklist the bcm43xx wireless driver and comment out eth1, but it was no use. Iwconfig doesnt show wlan0.

nb! sorry for my bad english.

---

### Post by maclenin on 2007-02-16
**Codera:**

No worries - your English is far better than my Spanish(?)!!

As for your questions:

Can you be more explicit about it not working? Is the only issue that wlan0 is not appearing? The fact that step 13. was error free is a good sign.

Can you send along the output of:

```
iwconfig
```

**iam_foo:**

I felt the same way - congratulations! So the install worked for you, without errors?

**josv**

I guess, if it ain't broke, don't fix it - however, I have a feeling that you'll run into problems - at some point.... You might want to wander through the process, again, to make certain you didn't miss anything. I just fear the "dual-wielding" (in /etc/modprobe.d/ndiswrapper) may come back to haunt you! The flattery is appreciated - thanks - and I'm gald the guide (seems to have) served its purpose!

**nekofelin**

I would try the install process from the beginning - and this time (if you did it previously) do not sudo modprobe -r bcm43xx (step 3.) - just blacklist bcm43xx (step 3.a.). Let me know how it goes.

**hum525**

Can you send me the output of the following...

```
iwconfig
```

...and...

```
sudo lshw -C network
```

...and we'll go from there....

**georgetruong**

That looks like a clean "lshw" to me...how are things going? Are you making any progress?

**renegade1029**

Any progress?

---

### Post by renegade1029 on 2007-02-16
Nope, I'm still searching...

---

### Post by spd106 on 2007-02-16
I'm not sure whether this will be of any help, but I've spent the last hour trying to connect to an AP on channel 6 and getting nothing in return. Channel 1 and 11 both work perfectly.

Very strange:confused:

---

### Post by renegade1029 on 2007-02-19
Problem solved.

I changed the content of /etc/network/interfaces to this :
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

iface wlan0 inet dhcp
wireless-essid Powers
wireless-channel 11
wireless-mode managed
auto wlan0
```

And I can connect when my router is not protedted. I am going to try it when I have WEP encryption.

EDIT : Well, after trying, WEP doesn't work. But it has nothing to do with this thread.

EDIT of the EDIT : Everything works well now using Wifi-radar. Next step is to set up a VPN client for school.

---

### Post by maclenin on 2007-02-21
Congrats - it sounds like you're well on your way to a surmounting of the next hurdle!

---

### Post by maclenin on 2007-02-23
**renegade1029**

Keep us posted re: VPN progress....

---

### Post by renegade1029 on 2007-02-25
I haven't really had the time to look into it, but I have a new, really wierd, problem.

I can't connect to any network that is on channel 6! At home, it is not a problem, I just changed my channel. But when I am away, this becomes a nightmare. It's not a problem with my card, since I can connect just fine in Windows.

As for the VPN, I am looking foward to install pptp-config along with pptp-linux. My school, however, only provides connection instructions for windows, so I think I might be lacking some of the information I need. I am going to talk to someone in software engineering I know has Ubuntu working with the school network.

---

### Post by typost81 on 2007-02-25
Hello.

I've tried this guide (and many others ) with no success.  I think my main issue is that I've tried so many things that i've got a bunch of conflicting configurations and installations that I don't even know where to begin cleaning things up.  

I was expecting the wireless light to come on after rebooting, but it doesn't.  It flickers a couple of times during the boot up, then stays off.

What I do think might be causing the problem is my attempt to run the following command:

sudo ndiswrapper -i bcmwl5.inf

It says it is already installed.  This may be from a previous attempt following another guide.  I'm thinking I should go to Synaptic and completely remove anything that references ndiswrapper

Help a noob out.  The last thing I want to do is reinstall the OS because I just got World of Warcraft working on it perfectly and I don't want to have to go through that again!!!](*,) ](*,) ](*,)

---

### Post by leetcharmer on 2007-02-25
I followed this tutorial, but my wireless card still did not work right.  I get it to detect my broadcom 4306 internal wifi card on this laptop, but it can never receive information about access points.  I type in the ESSID and WEP information, but -- never can I get any signal after getting it all installed w/ ndiswrapper.  The card works fine when under windows, so it's not out of range.

What information do I need to give in order to receive help troubleshooting this hardware?

---

### Post by maclenin on 2007-02-26
**renegade1029:**

I don't know what to recommend as the "solve the problem forever" trick (though, if you've "hardwired" a particular channel into your interfaces file (as you mention, [_here_]("http://www.ubuntuforums.org/showpost.php?p=2181245&postcount=119")) that could be part of the problem - assuming the non-home ap is operating on a "non-11" channel)....

A manual workaround might be to, when you're out and about (assuming your card supports scanning)...

```
sudo iwlist wlan0 scanning
```

...to find out what frequency / channel / essid describes the non-home access point, then...

```
sudo nano /etc/network/interfaces
```

...to edit the wlan0 interface to swap in the non-home ap data (i.e. channel / essid)...

```
iface wlan0 inet dhcp
wireless-essid <whatever you find via iwlist>
wireless-channel <whatever you find via iwlist>
wireless-mode <whatever you find via iwlist>
auto wlan0
```

...then reboot.

Again, though not the most elegant "solution" - this might help you connect when you're on the fly....

NOTE: My wlan0 interface is set up in this way...

```
iface wlan0
wireless-essid <location_dependent>
auto wlan0
```

...so that all I have to do is change the essid - when I am out and about - assuming, of course, the ap I am trying to grab is not encrypted.... All other settings (as far as I understand) - e.g. frequency / channel - are handled automatically. You might also be able to play with the frequency settings - though I am less certain how to tweak this....

**typost81:**

Before you go and wipe everything out....

Can you post the results of...

```
ndiswrapper -l
```

...(where "l" is lower-case L) as well as...

```
ndiswrapper -v
```

...and:

```
iwconfig
```

Let's first see what these outputs show....

**leetcharmer:**

Let's start with output of...

```
iwconfig
```

...and...

```
cat /etc/network/interfaces
```

....

---

### Post by renegade1029 on 2007-03-04
> **spd106 said:**
> I'm not sure whether this will be of any help, but I've spent the last hour trying to connect to an AP on channel 6 and getting nothing in return. Channel 1 and 11 both work perfectly.

Very strange:confused:

Have you found anything new concerning this? I have the exact same problem, ie I can't connect to channel 6 while 11 works just fine...

---

### Post by spd106 on 2007-03-04
I saw a post about editing the driver .conf file to disable the Afterburner. Since this usually only works on channel 6 I thought it might be worth a try. I kinda forgot about it till just now and I can't really risk throwing off other users at the moment. Hopefully I'll try it out in the next few days when it's a little quieter.

---

### Post by maclenin on 2007-03-04
**spd106 and renegade1029:**

I believe the post that **spd106** is referring to is [_this one_]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show"), with specific reference to the latter portions of **Step 5**....

---

### Post by renegade1029 on 2007-03-04
I just turned AfterBurner off and nothing changed... this is really wierd, I can't find information anywhere regarding this bug...

---

### Post by aseedb on 2007-03-04
> **maclenin said:**
> Can you post the output of these commands...

lshw -C network

iwconfig

uname -r (which should be 2.6.19.2)

...and we'll see from there....

Hi, I also followed the procedure without any error. However, I cannot connect tu my wireless network. Here is the result of the 2 commands listed above. I hope someone can help me...

$lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:18:6a:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 ip=192.168.0.101 multicast=yes
       resources: iomemory:faffe000-faffffff irq:177
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:16:3c:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper multicast=yes wireless=IEEE 802.11g
       resources: iomemory:faffc000-faffdfff irq:193


$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by maclenin on 2007-03-04
Did you follow the instructions (to **jmrichky**) that came after the one you reference? Give them a whirl, if you haven't....

---

### Post by aseedb on 2007-03-05
> **maclenin said:**
> Did you follow the instructions (to **jmrichky**) that came after the one you reference? Give them a whirl, of you haven't....

no indeed, I'm a newbie and had not seen that... I'll have a lot to try before bothering you again. Thank you for your help.

---

### Post by maclenin on 2007-03-05
No bother! I just wanted to save you a bit of back and forth (as the instructions I was going to pass along had already been laid out).... Good luck!

---

### Post by 5hift on 2007-03-05
having gone through a lot of trouble with bcm4306, i commend you on this how to. it is, by far, the best guide i've seen.

this is why i love ubuntuforums.

kudos to you!

---

### Post by maclenin on 2007-03-06
**5hift:**

I appreciate the kind words and echo your sentiments regarding these forums!

Thanks, again!

---

### Post by Shadow503 on 2007-03-10
Thanks a TON!! I don't even have the exact same card, but your guide helped me troubleshoot my connection.

Step 3b was very, very helpful!

---

### Post by 2Sunny on 2007-03-11
Thanks for trying, but to me that's absurd.  

I'm reinstalling windows as we speak.

Atleast I can say I gave it a whirl.

Perhaps a machine with graphics cards etc. that were intended to run in a Linux environment would be o.k.  Converting a machine that has devices not automatically recognized by Linux is a disaster for your average home gamer.

Thanks again,

Joe

---

### Post by maclenin on 2007-03-11
**Shadow503:**

Glad it worked for you! And thanks for the weighty thanks, but that load needs to be distributed (among FrodoB, spd106, teaker1s, zeddock, renegade1029, MalVeauX, jmrichky...to name only a very few) - without them, this guide does not exist....

**2Sunny:**

I hear you.... The "problem" is, indeed, that you need to spend a bit more time learning and tinkering, to get ubuntu working with you - it's not yet the pure plug-n play.... 

Perhaps, it's the choice between stick-shift and automatic....

---

### Post by HWADIAGF on 2007-03-13
Hi there, all seemed to be going smoothly, but i must have made some trivial mistake as when i got to the point of doing iwconfig this was my output:

> lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

sudo      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Somehow instead of wlan0 i've ended up with sudo...

Any suggestions on getting this back on track?

Cheers, James.

---

### Post by renegade1029 on 2007-03-13
I used to have the same problem. I think you made a typo while folliwing the steps un the first post.

I don't know if this will satisfy you, but I fixed it by reinstalling Ubuntu and following the stps again with great caution, since I did not have anything important to keep. If you do not wish to reinstall, I have no idea how to fix this

---

### Post by HWADIAGF on 2007-03-13
OMG it works.

You literally saved my Ubuntu life.

I've spent the last 4 days under my desk (to reach the ethernet cable *sob*) trying every guide on the Internet to get my wireless to work.

Thank you so very much for this very effective guide.

This should be stickied.

Thanks again.

James.

---

### Post by astrosoup on 2007-03-14
Okay, me next...

I'm brand new to Linux, and found my way here from the beginner forums.

I'm Running a Compaq with a BCM4306 wireless card, and I'm getting hung up with the ndiswrapper business. 

It seemed to install just fine, but when I tried the "make distclean" command I received the following:

rm: cannot remove '(item name)': Permission denied

I got the same response when I went back to uninstall ndiswrapper.

I followed post 1 step by step, cut n paste. I've tried cut/paste and typing the make dist command and I've experimented with other codes from the associated guide and other threads, but I am just going around in circles, even after a couple of healthy restarts... so what did I miss?

---

### Post by zeddock on 2007-03-14
maclenin,

I have used your guide successfully several times for a bcm4309 inside of a Dell Latitude D800.  But that was for Edgy!

Will this work for Feisty Fawn?


Thanx!

zeddock

---

### Post by maclenin on 2007-03-14
**HWADIAGF:**

Glad you pulled through it - and thanks for the solid feedback!

**astrosoup:**

In my humble opinion, you ran into a permissions mine-field somewhere between step 1. and 8.... I would go back through the steps, again - to make certain you are doing everything as advertised. Perhaps you created/downloaded ndiswrapper into a directory outside your ~/ directory? The "Permission denied" error, to me, points to an inadventant use of a "root" ("/") directory (vs. "~/"), somewhere along the line.

Give it another walk-through - and ping, again - should you not find your way past number 8.

**zeddock:**

I might be able to give you a Feisty update after I've tested it, myself - for all I know Feisty might have figured it all out - and ndiswrapper (god forbid) will go the way of the dodo!

---

### Post by zeddock on 2007-03-14
> 
I might be able to give you a Feisty update after I've tested it, myself - for all I know Feisty might have figured it all out - and ndiswrapper (god forbid) will go the way of the dodo!


I look forward to that, Thanx!
I am starting to dip into Feisty now so if I get to the answer first, I will post.

zeddock

---

### Post by zeddock on 2007-03-14
I can confirm that your guide works on Feisty.  It did not seem that herd 5 had solved the problem.

The only changes I had to make had to do with repositories using feisty versus efty, and the kernel versions.

I do have a question about two things:
1. You call on bcm4306 but I know mine is a 4309.  Should I try changing that for better performance?
2. Is it important to use ndiswrapper 1.34 versus a newer version?

Thanx!

zeddock

PS. Dell Latitude D800 now on Feisty Fawn herd 5

---

### Post by spd106 on 2007-03-15
1) The 43xx refers to the Broadcom chipset where the xx are different depending on which version you have. They can all use the same driver as different firmware will be loaded automatically. So basically you don't need to do anything different.

2) Generally, the newer the better, however it is often a good idea to go with a stable version that has been reported by others to be known to work with your card. I'm on 1.37, but I didn't see any major improvement over 1.34. It's also worth checking the changelog for major changes.

As far as Feisty is concerned things are still in flux, the new mac80211 stack may be available for some cards, others will fall back to the old softmac. Regardless of that, you will still need to download firmware to use the bcm43xx driver. From the little testing I have done bcm43xx is far better than it was, though it still defaults to 11Mbps depending on your card. 

If you still want to use ndiswrapper, little will have changed (save a version bump). 

You can blame Broadcom for the lack of "out of the box" support.

---

### Post by maclenin on 2007-03-23
**zeddock and spd106:**

As you folks wrestle further with Feisty feel free to send along any additional observations regarding the continuing applicability of the guide (beyond the other different suggestions you both have already sent my way) - thanks....

---

### Post by macnod on 2007-03-24
I have a Dell Inspiron 8500. WiFi didn't work when I installed Ubuntu Edgy and I had heard that getting the internal card to work was very difficult. But I followed your guide without any problems and the WiFi now works perfectly.

---

### Post by maclenin on 2007-03-27
**macnod:**

Good to hear your good news! Thanks for the post!

---

### Post by ggumas on 2007-03-30
when I get to step 12 which is the code
sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf

The file "14E4:4324.5 " conf is not in the directory   /etc/ndiswrapper/bcmwl5
However the files 
"14E4:4301:103C:12F3.5.conf," , :\" 14E4:4320:0E11:00E7.5.conf " and
"14E4:4320:103C:12F4.5.conf  "  are

can you tell me what if anything went wrong


George

---

### Post by maclenin on 2007-03-30
**ggumas:**

At first glance, I am afraid I can't tell you anything specific - my suggestion is to give the install process another go - and pay meticulous attention to the details of each step. Post another word, should the problem continue. Good luck!

P.S. In any event, could you tell me the version number of ndiswrapper (e.g. 1.34), as well as the release (e.g. Edgy Eft) of ubuntu you are using?

---

### Post by ZakSmith on 2007-03-31
excellent guide. Thank you.

---

### Post by maclenin on 2007-04-01
Thanks and you're welcome! Glad it worked for you!

---

### Post by maclenin on 2007-04-04
Again, should anyone have any Feisty comments related to the efficacy of this guide (or other issues, for that matter) - pleasse feel free to post them here....

---

### Post by notsteve on 2007-04-04
could this work with a boardcom 4318?

---

### Post by maclenin on 2007-04-04
It, certianly, should.... Take a peek at this  "_[howto]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?action=show")_" link to see the various cards for which the guide has worked (mine is essentially, a revised version of the "howto" guide).... Good luck!

---

### Post by maclenin on 2007-04-07
Ping!

---

### Post by Firesky on 2007-04-07
Is there a way to do this without ethernet connection.
SYSTEM - HP pavilion 7940 desktop with added motorolla wireless card there is no other ethernet connects but i do have access to another computer with cd writer on internet
              ubuntu 6.06 live cd installed on hard disk
wil@wil-desktop: - $ lshw -class network
*-network:0 DISABLED
[INDENT]description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN contraller
vendor: Broadcom Corporation
physical id: 8
bus info: pci @01:08.0
logical name: eth1
version: 03
serial 00:0f:66:le:01:29
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE802.11b/g[/INDENT]

how do i enable this device
can i download to a cd and upload to linux computer and install and how

---

### Post by Firesky on 2007-04-07
Is there a way to do this without ethernet connection.
SYSTEM - HP pavilion 7940 desktop with added motorolla wireless card there is no other ethernet connects but i do have access to another computer with cd writer on internet
              ubuntu 6.06 live cd installed on hard disk
wil@wil-desktop: - $ lshw -class network
*-network:0 DISABLED
[INDENT]description: Wireless interface
product: BCM4306 802.11b/g Wireless LAN contraller
vendor: Broadcom Corporation
physical id: 8
bus info: pci @01:08.0
logical name: eth1
version: 03
serial 00:0f:66:le:01:29
width: 32 bits
clock: 33MHz
capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE802.11b/g[/INDENT]

how do i enable this device
can i download to a cd and upload to linux computer and install and how

---

### Post by chamberlain2006 on 2007-04-07
Well I use a different card, (a Trendnet TEW-424UB, using the SiS163u chipset).  About Feisty, I haven't seen any real differences with wireless.  Its actually worse, in some respects.  In Edgy and Dapper I was able to use the packages in the repositories, but on Feisty I had no choice but to compile from source.  It was kind of good that I did so, though.  It made me use the latest version, 1.41, which was an improvement from earlier versions.  It fixed issues with Signal Strength being reported wrong.  The one better thing in Feisty was roaming mode.  It automatically connects to any network, without knowing the ESSID!  It's fantastic.  Hopefully wireless will continue to improve though, maybe even get more native drivers!  Great guide though, very well done!

---

### Post by maclenin on 2007-04-07
chamberlain2006:

Thanks for the Feisty insights and guide feedback - I appreciate it!

---

### Post by dustrho on 2007-04-08
I have two words for the author of this thread... THANK YOU!

I have an HP Pavilion zd7020 laptop with the big 17" widescreen display, and I've been desperately trying to get the wireless networking/internet working on this for well over a week. That was, until I discovered this particular thread. I had tried several different Broadcom suggestions, and none of them worked. I tried this one and it worked right off the bat! Amazing!!!

I can't begin to tell you how excited this has made me, knowing that I can remove the 25 foot ethernet cable from the back of this laptop, and go wireless like it once was when Windows XP plagued this computer.

So, thank you again for the awesome guide, and thanks for sharing the knowledge in this great forum.

---

### Post by bg1256 on 2007-04-10
First off, thanks for the thorough guide.

I am running Kubuntu Edgy, and everything worked just fine while following the thread.

However, I am unsure how to activate the card in KDE.  I used to have Gnome installed, and network tools worked for me.

Does anyone know of something similar for KDE that would allow me to enable the card?

I have a wifi button on my keyboard, but that has not worked, at least as of yet.

---

### Post by bg1256 on 2007-04-10
Another update:

When I restarted my computer and booted into the kernel I was trying to install the driver on, it froze up twice in a row.

When I booted into an older kernel, everything worked fine... but obviously no wireless.

Again, I'm using Kubuntu 6.10 and I'm booting into the 2.6.17-11-generic.  I've seen a few threads about this kernel causing problems... but I'm apprehensive about trying this in the earlier kernel, as I'm currently locked out of the newest kernel after following this guide.

Edit:

I unplugged my wired connection and attempted to boot into the 2.6.17-11 kernel, and my wifi light came on, which had not been happening before, but it still hung at the same place.

Edit 2:

I should also mention that this notebook uses both wired and wireless connections often... Does this guide configure it to be wireless only? Or wireless by default?  The only reason I ask is because I keep freezing when booting into the 2.6.17-11 kernel.

Thanks again!

---

### Post by bg1256 on 2007-04-10
Oddly enough, this morning when I booted up, everything worked!

I've booted and rebooted several times now, and all seems well.

Thanks for the great howto!  I literally could not have gotten wireless working without it!

---

### Post by Firesky on 2007-04-10
Dears peep and geeks how do i install headers or what ever it is i need to get to get ndiswrapper i have no connection to internet to update without my wireless i have friends computer to make cds and copy to linux system.
:)

---

### Post by teaker1s on 2007-04-11
Are you sure that this isn't supported by native driver? lets check
```
iwconfig
``` post output

we would also possibly be best installing using alternate.iso which has more packages as a source to install ndiswrapper
[http://ubuntuforums.org/showthread.php?p=2190707#post2190707]("http://ubuntuforums.org/showthread.php?p=2190707#post2190707")

---

### Post by Firesky on 2007-04-12
OK i was able  to get headers installed ndis and ndis-util  able to get new driver to load on boot 

    sudo iwlist scanning    wlan:  no scan results

Fallowing back through guild once more i notice that when i get to line/step 13 i do not get the the error code list in 13 a.
my computer show me a 
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with ' 
is this ware my problem is how can i ajust this i believe step 13 is traceible back to 3.a. 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by maclenin on 2007-04-13
**dustrho:**

NO PROBLEM! Glad that I could help you out! And, I share your sentiments re: "this great forum"!

**bg1256: bg12156'': bg1256: **

Good to hear that all seems to be working - if first you don't succeed.... This is how I got my wireless up and running.... Thanks, as well, for the thanks!

---

### Post by maclenin on 2007-04-13
**Firesky:**

What's the latest?

---

### Post by Firesky on 2007-04-15
> **Firesky said:**
> 
Fallowing back through guide once more i notice that when i get to line/step 13 i do not get the the error code list in 13 a.
my computer show me a 
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with ' 
is this ware my problem is how can i ajust this i believe step 13 is traceible back to 3.a. 
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

i have not found where < ' > my bad start is at still playing post any advice i'm looking

---

### Post by maclenin on 2007-04-16
If you first don't succeed....

---

### Post by bg1256 on 2007-04-16
I'm curious about how this is (or is not) working on Feisty.

Searching the thread showed one success... Has anyone else tried it yet?

---

### Post by maclenin on 2007-04-18
I hope to be installing Feisty, soon. I'll post my results....

---

### Post by dustrho on 2007-04-21
So after upgrading to Ubuntu Feisty, my wireless crapped out and so did my screen resolution. I tried fixing it for almost two hours to no avail. So, I wiped my computer clean and actually did an install of Kubuntu Feisty. Very slick interface and so far things are working well... for the most part anyway.

I got the video resolution working fine, and same with the wireless of my Broadcom 4306 card. I shut down when I was for the day. Came back a few hours later, started the laptop up via a cold boot, and now my wireless card is GONE! I did exactly the steps in the original post of this thread, when it worked flawlessly for me, but after a cold boot I don't seem to have a wireless card anymore. Here's what it says when I do a sudo ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:2D:2B:BD
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe2d:2bbd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:492754 (481.2 KiB)  TX bytes:59983 (58.5 KiB)
          Interrupt:21 Base address:0xc800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:542 (542.0 b)  TX bytes:542 (542.0 b)
```

If I do an iwconfig I get the following:

```
lo        no wireless extensions.

eth0      no wireless extensions
```

WTF?!? :(

---

### Post by maclenin on 2007-04-21
**dustrho:**

I would recommend going back through the steps, once again - paying particular attention to steps 13. through 17. where you bring up the wireless driver (ndiswrapper) and cause ndiswrapper to load at start-up (step 16.).... Good luck.

**[anyone]:**

I have not been able to test my guide with Feisty, however, for those who have (and succeeded or failed), please feel free to post comments / suggestions....

---

### Post by elcu on 2007-04-22
No go for me in Feisty.  The network manager applet just spins and eventually gives up when I try to connect to a network.  Details of my setup: [http://paste.ubuntu-nl.org/16990/](http://paste.ubuntu-nl.org/16990/)

---

### Post by spd106 on 2007-04-22
Works for me :)

Both with static and eventually with roaming mode on, though I had to restart dbus.

---

### Post by elcu on 2007-04-23
> **spd106 said:**
> Works for me :)

Both with static and eventually with roaming mode on, though I had to restart dbus.

Worked it out.  Serves me right for not following the guide!

I used ndiswrapper packaged with Feisty ( 1.38 ) instead of compiling from source.  That version has a known bug: [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/85468)

Compiled the latest 1.42 and all is good.

---

### Post by maclenin on 2007-04-23
**elcu:**

Glad you worked it out  and thanks for the info. on the bug....

---

### Post by hitoshura85 on 2007-04-24
I just registered to this forum today, mainly to reply to the post about this wonderful howto. Another reason is to confirm that this guide does seem to work, at least for me, in Feisty as well. The light for my card is lit and I am able to scan for networks. One problem I seem to be having is that I can't seem to connect to one of the access points i found. However, this may not necessarily be an issue since I might just be located too far away.. the strength was low. I'll have to try to connect to some spots I know work.

Also, I'm actually using kubuntu and knetworkmanager never displays any networks when I right-click on the icon in the system tray. Does anyone else have this issue with the NetworkManager in gnome and if there is, is it cuz of the card?

Thanks again for helping and this great howto.

---

### Post by abhisheksen on 2007-04-24
Amazing work!! Thanks a million for the guide!

---

### Post by clarkNerd on 2007-04-24
Firstly, thanks for the great guide here.  I have two computers that I am trying to get this to work on.  One I have had great success on but the other will not seem to budge.  The computer that is not working is an AMD64 running feisty.  The card is the Linksys WMP300N PCI card.  I have tried everything I can think of and am hoping that somebody else looking/commenting might help.

My card seems to be visible and I can use iwlist to see my router, but I can not connect to it.  I tried what renegade1029 suggested (specifying my channel number), but that didn't seem to help.  I tried hard setting it with "iwconfig wlan0 essid linksys" with no success.

I have noticed a trend of code snippets you look for so i will do my best to include it all.  Any help here would be greatly appreciated.

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid linksys
wireless-channel 4
wireless-mode managed
auto wlan0
```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist wlan0 scanning:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:F8:C5:50:51
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:57/100  Signal level:-59 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

ndiswrapper -l:
```
bcmwl5 : driver installed
        device (14E4:4329) present
```

lshw -C network:
```
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: wlan0
       version: 01
       serial: 00:18:f8:a6:29:86
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.42 firmware=Linksys, A Division of Cisco Sy latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:fe9f8000-fe9fbfff irq:16
```

---

### Post by bg1256 on 2007-04-24
> **hitoshura85 said:**
> I just registered to this forum today, mainly to reply to the post about this wonderful howto. Another reason is to confirm that this guide does seem to work, at least for me, in Feisty as well. The light for my card is lit and I am able to scan for networks. One problem I seem to be having is that I can't seem to connect to one of the access points i found. However, this may not necessarily be an issue since I might just be located too far away.. the strength was low. I'll have to try to connect to some spots I know work.

Also, I'm actually using kubuntu and knetworkmanager never displays any networks when I right-click on the icon in the system tray. Does anyone else have this issue with the NetworkManager in gnome and if there is, is it cuz of the card?

Thanks again for helping and this great howto.

I too use KDE, but I don't have that particular problem.

I do use wireless assistant, however, which I'm not sure is installed by default.  It's in the repo's for install though.

---

### Post by clarkNerd on 2007-04-25
Update: I changed the router channel to channel 11 and then everything worked just fine.  Apparently my AMD64 fiesty machine couldn't attach to the router when it was on channel 4.  It was pretty odd though, because my other computer (32 bit, edgy) worked on both. Well thanks again for your guide.

---

### Post by memezaa on 2007-04-25
tutorial worked great. Finally installed kubuntu on my sibling's box which until yesterday ran XP. The wireless was my only hurdle(WMP54G PCI). Followed everything step by step and it worked flawlessly. Now I dont have to deal with anymore headaches dealing with their virus/adware infesting machine. Thanks!

---

### Post by maclenin on 2007-04-29
**hitoshura:**

I cannot speak to the network manager issue, as I do not use either it or KDE (or Feisty, yet - for that matter).... I am glad, though, that you got your wireless card working!

**abhisheksen:**

You are welcome - thanks for the thanks!

**clarkNerd:**

I have heard / read about the channel issue - check either this thread or do a search for that issue in the forum - I seem to recall that spd106 had some thoughts on that matter....

**memezaa:**

Glad to hear it - I am enjoying my "freedom" with equal enthusiasm!

---

### Post by maclenin on 2007-05-02
Any more wireless Feisty feedback or suggestions?

---

### Post by bg1256 on 2007-05-02
I will be installing Feisty in less than two weeks... seems like it's a safe bet?

The only problem I've had is that it increases my boot time by about double... not a huge deal, but I don't think it's a problem with the guide.  It's just ndiswrapper and broadcom chipsets.  Don't think there's a workaround for it.

---

### Post by maclenin on 2007-05-02
The boot time increase happens at what point? Post-ndiswrapper install? Post-Feisty install (but you haven't yet installed Feisty). Can you clarify? At what point was the boot time faster?

---

### Post by maclenin on 2007-05-06
Still fishing for Feisty feedback....

---

### Post by bg1256 on 2007-05-07
> **maclenin said:**
> The boot time increase happens at what point? Post-ndiswrapper install? Post-Feisty install (but you haven't yet installed Feisty). Can you clarify? At what point was the boot time faster?

My boot time increased dramatically after I inrsalled ndiswrapper while running Edgy. 

When running Dapper, ndiswrapper did not seem to affect the boot time at all.  I also have a friend who experienced the same problem when upgrading to Edgy.

I am convinced it is not the fault of this guide, but simply a glitch in the system somewhere that may remain unexplainable :) 

I will be upgrading to Feisty next week, as soon as final exams are over... until then, I can't afford any issues with my computer.

After I've done that, I'll have some Feisty feedback as well.

---

### Post by maclenin on 2007-05-07
Look forward to it - thanks for the detail....

---

### Post by subliminal727 on 2007-05-09
having a bit of trouble with this .  any help would be appreciated.  
installing this on a laptop with feisty. 
 when i iwconfig i my essid is only showing the first letter of any essid i type in.also says access point:invalid  everything in the guide seemed to go okay without any errors or anything. was able to get my wireless card to wlan0.

---

### Post by subliminal727 on 2007-05-09
Nevermind i'm a moron i guess.  i went back through the guide and its working now.  must have typed something wrong.  But this worked great for feisty btw.

---

### Post by maclenin on 2007-05-09
**subliminal727:**

Glad to hear it (and re: Feisty)! Were your early problems the result of you typing the commands (perhaps improperly) - or did you first copy and paste the commands into the terminal (which means some of my material might have errant spaces or some such)? Anyway, most importantly - you found a way to make it work!

---

### Post by helpdeskdan on 2007-05-12
If you get the "FATAL" error message, try a make uninstal.  I tried it and then got a "FATAL: Could not open '/lib/modules/2.6.17-11-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory" at which point I thought I was really in trouble.  However, after another "make install" the message went away and all worked well.  I also uninstalled and reinstalled ndiswrapper-comon and utils, but I don't think that did anything seeing as how ndiswrapper.ko is in neither.  

ndiswrapper -v
utils version: 1.9
driver filename:       /lib/modules/2.6.17-11-generic/misc/ndiswrapper.ko
version:        1.43
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1

---

### Post by bg1256 on 2007-05-12
Reporting a succesful upgrade to Kubuntu Feisty, and the subsequent success of this guide.

Everything works well, but boot time is still extremely slow... I'm still convincned it's not the fault of this guide. however.

---

### Post by maclenin on 2007-05-15
**helpdeskdan:**

Glad your second time 'round was error-free - and thanks for the procedural detail.

**bg1256:**

Thanks for the additional Feisty feedback - I am interested re: slower boot times - I think I've read elsewhere (in these forums) that this may be a Feisty issue.... We'll all stay tuned.

---

### Post by bg1256 on 2007-05-16
> **maclenin said:**
> 

**bg1256:**

Thanks for the additional Feisty feedback - I am interested re: slower boot times - I think I've read elsewhere (in these forums) that this may be a Feisty issue.... We'll all stay tuned.

Yes, I think I remember reading the same thing. I hope it gets updated... but if not, I'll just deal with a slow boot time :)

---

### Post by maclenin on 2007-05-17
> **bg1256 said:**
> Yes, I think I remember reading the same thing. I hope it gets updated... but if not, I'll just deal with a slow boot time :)

Re: updates - maybe I'll have to soon post fb requests re: the guide and Gusty!

---

### Post by maclenin on 2007-05-20
Onward!

---

### Post by maclenin on 2007-05-24
Any additional Feisty finds or wireless observations?

---

### Post by bg1256 on 2007-05-24
My boot time has suddenly gotten a lot faster.  I had been having trouble with very slow boot times, but it's sped up in the past week or so.  I don't think it has been any updates.

I'm also running KDE.

---

### Post by zeddock on 2007-05-25
Is there something I should change in the guide since I have a 4309 chipset?

zeddock

---

### Post by maclenin on 2007-05-26
**bg1256:**

If you stumble on the reason you were experiencing slow boot times - send it along....

**zeddock:**

I believe the guide should work for most (if not all flavors) of the bcm43xx chipset.... Are you having difficulty with the guide?

---

### Post by zeddock on 2007-05-27
No problems. Just want to get the beat possible solutions.

Thanx!

zeddock

---

### Post by maclenin on 2007-05-28
I hear you.... I seek out the same and more often than not find the best solution to be: "If it ain't broke don't fix it...." Thx for the Thanx.

---

### Post by maclenin on 2007-06-05
Any thoughts re: the continuing need for such driver installation guides in future ubuntu releases?

---

### Post by kevdog on 2007-06-05
Im running Kubunty Feisty 7.04 and wish I would have found this guide this weekend when I converted from bcm43xx to ndiswrapper.  Just a couple of interesting observations, some kind of some up the other posts in the file:

1. I never installed the headers for the kernel -- Im not sure if this is necessary
2. I never copied the conf file as suggested in your guide

Are these necessary steps??

I also installed ndiswrapper from svn.  I would suggest that everyone after compiling installing ndiswrapper run the command ndiswrapper -v to make sure that the utils version is compatible with the ndiswrapper program.

I ddnt use the driver mentioned in the guide.  I actually went to the ndiswrapper sourceforge website, looked for my card, and then downloaded the driver that was recommended.  I dont know if this is a necessary step, but there are a lot of different drivers present.  Adding this step would make the guide more applicable to cards other than broadcom.

Again conflicts in interface names eth0, wlan0, etc.  As you pointed out ndiswrapper assumes wlan0.  In order to make everything work with whatever interface name, the interface names in /etc/network/interfaces, /etc/iftab, and /etc/modprobe.d/ndiswrapper need to be all the same.

Sorry I dont remember but did you the instruction ndiswrapper -m to make the wrapper start at startup.

Other than that the guide was great -- although I never used -- I came to the exact same conclusions albeit after many more hours.

---

### Post by bg1256 on 2007-06-05
It seems to me such guides will be needed until broadcom chips work out of the box... at least that's my two cents worth.

If this works in Gutsy, no need to remake it,  I suppose...:D

---

### Post by zeddock on 2007-06-05
What do you mean?

zeddock

---

### Post by spd106 on 2007-06-05
> **kevdog said:**
> Im running Kubunty Feisty 7.04 and wish I would have found this guide this weekend when I converted from bcm43xx to ndiswrapper.  Just a couple of interesting observations, some kind of some up the other posts in the file:

1. I never installed the headers for the kernel -- Im not sure if this is necessary
2. I never copied the conf file as suggested in your guide

Are these necessary steps??


1. You need the kernel headers to build a kernel module, which is the main part of ndiswrapper. There is one included in the default kernel image, but this should be replaced when you build the newer version.
2. This step isn't necessary, I've never needed to do it, but it has helped others in the past.

>  I would suggest that everyone after compiling installing ndiswrapper run the command ndiswrapper -v to make sure that the utils version is compatible with the ndiswrapper program.

Good advice.

> **maclenin said:**
> Any thoughts re: the continuing need for such driver installation guides in future ubuntu releases?
Hopefully we will be able to focus on the efforts of the bcm43xx team, rather than ndiswrapper. Unfortunately, as has been said many times before, it's up to Broadcom to help develop a FOSS driver or at least allow distribution of their firmware, like Atheros.

You might want to check out Fedora 7 for the inclusion of new bcm43xx-mac80211 driver. It should allow faster data rates and adhoc mode among other things. It's a shame it wasn't ready for Feisty, but I expect it's already in Gutsy. Incidentally, the first alpha (tribe) release is scheduled to be on Thursday. [https://wiki.ubuntu.com/GutsyReleaseSchedule](https://wiki.ubuntu.com/GutsyReleaseSchedule)

---

### Post by mrsempai on 2007-06-05
i followed this guide

[http://ubuntuforums.org/showthread.php?t=201902&page=1](http://ubuntuforums.org/showthread.php?t=201902&page=1)

was having problems with the wireless card not showing so i used  this guide

[http://ubuntuforums.org/showthread.php?t=340689&page=5](http://ubuntuforums.org/showthread.php?t=340689&page=5)

and changed ndiswapper version for 1.44 where needed... now i can se my wireless card again, but cant rename it from eth0 to wlan0

here's some information... can someone help? i know im almost done!

```
mrsempai@lp2p:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:90:4b:cb:84:2a arp 1
#eth1 mac 00:03:25:20:3a:d0 arp 1


```


```
mrsempai@lp2p:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface


#iface eth1 inet dhcp

#auto eth1

#iface eth1 inet dhcp

#auto eth1

```

```
mrsempai@lp2p:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

im running ubuntu feisty fawn

---

### Post by spd106 on 2007-06-05
> **mrsempai said:**
> 
here's some information... can someone help? i know im almost done!

```
mrsempai@lp2p:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:90:4b:cb:84:2a arp 1 
[COLOR="Red"]#[/COLOR]eth1 mac 00:03:25:20:3a:d0 arp 1


```

```
mrsempai@lp2p:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



Looks like you commented out the wrong interface, no matter, just comment out eth0 instead and you should be good to go.

---

### Post by mrsempai on 2007-06-05
thanks :) that worked perfect... gonna keep reading now


when someone activates wireless in ubuntu and angel gets his wings :D

---

### Post by kevdog on 2007-06-05
The bcm43xx driver is far easier to install than ndiswrapper, however it currently only allows for 11 Mb/s.  Possibly this has been fixed with the fedora release.  It would be great if Broadcom would release an adequate driver.  

Thanks for the information about the headers, I didnt know this.

It would be great if both the bcm43xx driver and ndiswrapper were installed or at least part of the installation by default.  All of these guides, when stating get this package and that package, assume you either have a working internet connection, another computer with internet connection, or the installation CD.  Why however put this stuff on the CD, and not at least copy it to a directory during the installation?  Possibly the developers wanted to make the installation "as lean as possible", however I cant believe installing the ndiswrapper source code and bcm43xx driver and cutter package would be more than a few Kbs.  I love responding to the users in this forum about their problems with ndiswrapper or failed internet connection, but face it, the same question is asked over 90% of the time.  Trying to guide many beginners to install the ndiswrapper package, build-essentials package from Cd, then compile and install the package is very problematic for most.

I'll get off my soap box, however just feel the developers could make at least part of the installation of wireless drivers far more easy than it is at present.

---

### Post by maclenin on 2007-06-13
Thanks, all, for the continued comments, suggestions and insights.

---

### Post by maclenin on 2007-06-19
More, anon.

---

### Post by zeddock on 2007-06-21
> **maclenin said:**
> Thanks, all, for the continued comments, suggestions and insights.

I had thought that we had gotten past the need for this guide when I did a firmware update or one of the other many attempts to fix this ongoing issue, but alas, I was wrong.

My wireless is working, but just barely.  The throughput as shown from my DLink wireless router shows the same 4309 brought to life through your guide as having a 12 throughput. (I guess this means 12 Mbps?... but the other brought to life with [this]("http://ubuntuforums.org/showthread.php?t=201902"), I believe, shows a whoppn' 2Mbps.

zeddock

---

### Post by maclenin on 2007-06-25
Thanks? I am trying to get back to making a few additional revisions to the guide based on "user" comments.... In addition to those that might have already been suggested in these pages, are there others that folks think might enhance the effectiveness of this "howto"? I appreciate all the feed-back...as just one of the many pleasurable side-effects of using this terrific forum.

---

### Post by zeddock on 2007-06-26
Is it important to get 1.34 of NDISWRAPPER?

I have noticed newer versions.

Also,
How difficult is it to turn this into a script of some kind?  It really irritates me when I have to keep doing steps every time they release a new kernel.
Since your guide STILL is the only guide that is dependable for a good wireless connection on my Dell Latitude D800, it would be great if I could just run an update whenever the wireless stops working.

Scenario:
At work a new kernel update is applied through my wired connection.  
Get home and can't connect because wireless connection must be rebuilt using this guide.

It would be nice if, while not connected at home due to wireless not working due to wired kernel update, I could run the script and gain basic functionality.  Is this possible?

Thanx,

Zeddock.

---

### Post by t4thfavor on 2007-06-26
FYI there is decent native driver support for the bcm cards now. I have a buffalo cg54g card and it seems to work quite well without the ndiwrapper trick. Jus using the fwcutter tool to extract the firmware from the windows device driver, and copy it to /lib/firmware. Works in feisty fawn without a hitch.

My apologies if this has been covered in the thread already, I haven't got the bandwidth to read 23 pages of posts.

---

### Post by maclenin on 2007-06-26
**zeddock:**

You're correct, there are later versions of ndiswrapper (I think they're up to 1.47 now) - but 1.34 is the one I've tested and, therefore, the one I recommend - however, I think a note to the effect that there are other/later versions avail. - is not a bad idea....

As for the scripts - I have so many script plans - and, as **t4thfavor** mentions (differently) - if I had the "bandwidth" I would, certainly, put one together. Should time permit, I'll try to put one together. I imagine the process could be automated....

Thanks for the notes....

**t4thfavor:**

If you are referring to the fwcutter method - i.e. eviscerating the (bcmwl5) driver for the firmware - I have been down that road and found the ndiswrapper method far more effective (even with the added set-up time) - and continue to be thrilled with near-zero down-time and solid speeds....

No worries re: bandwidth and reviewing 23 pages of posts - thanks for the comments.

---

### Post by jpl80 on 2007-06-29
I did this and everything worked just fine! I even rebooted and it still worked. Great Success.

However, I rebooted a second time and I got the dreaded "can't access tty; job control turned off." 

Any idea what this could be? I'd rather not do a whole new Ubuntu installation. Especially if it's just going to happen again.

~Jeff

---

### Post by maclenin on 2007-06-29
**jpl80:**

I have not encountered your "tty" error, but I did a quick search in these forums, using the terms you've provided and found a wealth of potentially helpful threads! I suggest you do the same.

Good luck with your error resolution and I am pleased to hear that, at the very least, the guide worked for you!

---

### Post by maclenin on 2007-07-04
Thanks for the feedback....

---

### Post by The Judderman on 2007-07-08
I used this How To when I first upgraded to Edgy ages ago, and it worked a dream. In a couple of weeks when I have time, I'm hoping to upgrade to Feisty, which will be exciting, and will hopefully be like so many other people uneventful!!!

Thanks for your hard work Maclenin, and your continued interest in how people are doing. The great thing about Ubuntu is the way the community helps newbies like myself who don't have the knowledge to work everything out! It will be great if/when bcm cards work out of the box, but at the moment, thanks for people like you!!!

---

### Post by maclenin on 2007-07-11
**The Judderman:**

Thank you!

---

### Post by maclenin on 2007-07-14
...just checking in....

---

### Post by maclenin on 2007-07-17
...and doing so, again....

---

### Post by maclenin on 2007-07-23
...and again....

---

### Post by maclenin on 2007-07-26
...and, yet again....

---

### Post by zeddock on 2007-07-26
OK. OK!
Yer fillin' my inbox!<laughs>

I think the gusty version has dealt with the issues on my 4309. But I have been tricked before so I still subscribe to your tread of how-to.

Thanx for checkin' in though!

zeddock.

---

### Post by bg1256 on 2007-07-27
Not sure if anyone can help me here:

I followed this guide, and all has worked well.  I was using KDE at the time.

Yesterday, I switched to Gnome via apt-get, and that all went fine as well.  However, now I cannot connect to the wifi in my house.  The card is still working, as the wifi light is on, and I can turn it off and on, but I can't connect...

Ideas?

---

### Post by maclenin on 2007-07-27
**zeddock:**

Just stayin' in touch with the people....

**bg1256:**

Are you able to connect wirelessly, elsewhere? Or is your home the only trouble spot?

Can you send along the output of iwconfig?

In the meantime, you might want to give ndiswrapper a kick-start via...

```
sudo depmod -a
```

...and then...

```
sudo modprobe ndiswrapper
```

There have been times, after MAJOR upgrades - i.e. to the kernel headers, where I've needed to re-make and re-mod ndiswrapper. Perhaps you need to pay similar attention to ndiswrapper, post-Gnome install.... 

Give the modprobe a whirl and let me know what happens.

---

### Post by The Judderman on 2007-07-27
maclenin, once again you are a star...
As previously mentioned, I have just now upgraded to Feisty (need to change this on my profile), and I followed your HowTo, and I am now connected in less than 45 min via my wireless to the internet!!!!! 

Cheers!!!

Just to add, that I had to sudo the make distclean and make, to avoid errors, but that was easily sorted!

Again thanks for your hard work, and I will definitely come back to this if I have a problem.

I too had to re-make and re-mod ndiswrapper recently with some major upgrades.

A very happy Ubuntu user...

The Judderman

---

### Post by bg1256 on 2007-07-27
> **maclenin said:**
> 

**bg1256:**

Are you able to connect wirelessly, elsewhere? Or is your home the only trouble spot?

It's the only spot I've tried... as it's the only place I've been since switching to Gnome... I opened up wifi radar, and it says I'm connected to my network, but I can't connect to anything, gaim, synaptic, firefox, anything.  It also will not let me disconnect from the network either... 

I will post the outputs of those commands tonight when I get back home.

Thank you much for the help... I'd be a bit lost if it weren't for the people like you who make these kind of guides possible. 

> 
Can you send along the output of iwconfig?

In the meantime, you might want to give ndiswrapper a kick-start via...

```
sudo depmod -a
```

...and then...

```
sudo modprobe ndiswrapper
```

There have been times, after MAJOR upgrades - i.e. to the kernel headers, where I've needed to re-make and re-mod ndiswrapper. Perhaps you need to pay similar attention to ndiswrapper, post-Gnome install.... 

Give the modprobe a whirl and let me know what happens.

---

### Post by bg1256 on 2007-07-27
Okay, here are the results of the commands listed above:

iwconfig:

```
lo     no wireless extensions.

wlan0     IEE 802.11g  ESSID:"mywifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:38:BA:CC
          Bit Rate=54 Mb/s  Tx-Power:32 dBm
          RTS thr=2347 B  Fragment thr=2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-29 dBm  Noise level:-96dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0 Missed beacon:0

eth0     no wireless extensions     
```

To be clear, my wireless card seems to be working just fine.  I can detect my network, and wifi radar even says I'm connected, but I can't get online, no way, no how...

---

### Post by maclenin on 2007-07-27
**The Judderman:**

Thanks, once again, for the kind words.... Glad that the upgrade proved a smooth one. I am still Edgy, but will proceed with a little more confidence as I become Feisty - given your experience. 

**bg1256:**

I don't know what to tell you, for certain...all signs seem to point to operable connectivity.... Having said this, I've read mixed things about wifi-radar and network-manager and their tendency to get in the way. So, for the moment, I would suggest you try to "by-pass" wifi-radar and enter the following into the terminal...

```
sudo iwconfig wlan0 essid mywifi
```

...to re-associate your wireless card with your router and then ping your router using its ip address, which (if it's a linksys) is probably 192.168.1.1, with this command...

```
ping -c 4 192.168.1.1
```

...then try re-connecting to the web...

...let's see what happens.

---

### Post by bg1256 on 2007-07-27
Thanks for your help...

I did some tinkering in the networking options, and I got it working.

But thanks so much for taking the time to post what you did!

The first time I ever installed the wifi driver, it took me two weeks to find the right info... but with your guide, it took just a few minutes :guitar:

---

### Post by maclenin on 2007-07-28
Nice to hear you got it working - and thanks for the comments re: the guide (though mine is also heavily based on the input and sweat (and tears) of many many others)!

Just for curiosity's sake as well as posterity's - would you mind posting a brief summary of what you ended up doing to get yourself re-connected?

Good news!

---

### Post by bg1256 on 2007-07-28
> **maclenin said:**
> Nice to hear you got it working - and thanks for the comments re: the guide (though mine is also heavily based on the input and sweat (and tears) of many many others)!

Just for curiosity's sake as well as posterity's - would you mind posting a brief summary of what you ended up doing to get yourself re-connected?

Good news!

Sure, but I'm working from memory here, as I'm away from that machine right now.

I opened up system -> administration -> network

Then, I simply ensured it was connecting to my network.  I also disabled wifi-radar and network manager from sessions -> startup

And now it connects automatically on startup.

Once I get back to school in the fall, I'll be connecting to several other networks, and it may take some tinkering again... but I'm confident I'll get it working -- with some help :lolflag:

---

### Post by maclenin on 2007-07-31
Thanks for the detail and I am sure someone will be around to help out come fall....

---

### Post by gl0wst1ckn1nja on 2007-07-31
so i have a bcm4318 the airforce one card.  it sucks ... enough said. i used the ndiswrapper and it worked ... for 5 minutes then the kernel started to fluctuate the power that it supplied to the card so it became flaky with staying connected. i finally bought a new internal wireless card for my mPCI and im thinking of smashing the 4318 with an axe and then strapping the pieces to a bottle rocket and sending them skyward and then going boom.  :lolflag: im very excited for my new card its a DCMA-82 Atheros 6G: 802.11a/b/g High Power mPCI Card. anyone have one of those??

let me know

---

### Post by maclenin on 2007-08-01
Sorry, can't help with this particular card...google and/or these forums should provide the insight you require...good luck - and feel free to post any solutions you happen upon....

---

### Post by maclenin on 2007-08-05
Onward....

---

### Post by bg1256 on 2007-08-05
Well, I'm reporting a problem that I don't konw how to fix...

It seems that my notebook isn't properly loading the wifi driver on start up.  

I was visiting some family this weekend, and in the past (under KDE),  the driver loaded at startup, and knetworkmanager picked up the WPA encrypted network with no problems.

Now, after a fresh install - and switch back to Gnome - it only loaded about 1 out of 3 times...

I couldn't seem to figure out why, and I may not be able to reproduce the bug, as I am no longer around that network.

The only thing that I had configured differently than normal was that roaming mode was enabled in network manager, so that I could see the WPA encrypted network.

I think this is appropriate to post here, because the driver was not loading, rather than not being able to connect to the network.  When the driver did load, I connected fine.

I attempted the following after starting up without the driver working:

sudo depmod -a

and

sudo modprove ndiswrapper

Neither seeemed to work...

---

### Post by bg1256 on 2007-08-06
Here's an update to the previous post:

I have now returned home -- student living with parents for the summer -- and I followed this guide here.  All worked well, in that the driver loaded on startup, and I was able to view the wifi network here at home.

Now that I am home, the driver is not loading at startup, however.  I have returned the network settings to the way they should be, but the driver isn't loading. My wifi light does not come on, and I cannot view wireless networks...

Any ideas as to why this would be happening?

---

### Post by maclenin on 2007-08-07
Take a peek at this [_first post_]("http://ubuntuforums.org/showpost.php?p=3092835&postcount=241") to try and "reassociate" your wireless card. If this does not work - and given your recent move from KDE to Gnome, you might want to try a reset of the driver, with specific reference to comments for **zeddock** in this [_second post_]("http://ubuntuforums.org/showpost.php?p=2144218&postcount=108")....

Should these steps not work, I would re-install the driver....

Good luck!

---

### Post by maclenin on 2007-08-09
Any Gutsy reflections, yet?

---

### Post by KPatel on 2007-08-09
Hello there, I've been following your guide up til where it says to run "make", this is what I get when I put that in.
```
owner@Ubuntu:~/Desktop/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/owner/Desktop/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/owner/Desktop/ndiswrapper-1.47/driver'
make: *** [all] Error 2

```
what should I do?

Cheers for the help.

---

### Post by maclenin on 2007-08-09
Do you have a wired connection (ethernet) to the internet? At first blush it looks as though you need to install the build-essential tool set - a key component to being able to "make" ndiswrapper....

If you can connect (or are, already connected) via ethernet to the internet, return to this step...

4. Install the build-essential tool set:

...install the tool set and review the remaining steps 'till the end - and try to "make" ndiswrapper, once again....

---

### Post by KPatel on 2007-08-09
this is when I get when i put in sudo aptitude install build-essential```
owner@Ubuntu:~/Desktop/ndiswrapper-1.47$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint g++-4.0 gok gtk2-engines-clearlooks gtk2-engines-crux
  gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice ijsgutenprint libcompfaceg1 libgnutls12 libnetcdf3
  libstdc++6-4.0-dev libtasn1-2 pcmcia-cs python-gadfly python-htmltmpl python-kjbuckets python-netcdf python-parted
  python-pgsql python-soappy python-stats python-syck x-window-system-core
0 packages upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

---

### Post by maclenin on 2007-08-09
try this:

```
cd
```

```
sudo aptitude install build-essential
```

do you get the same output?

---

### Post by Asphyxiaphilia on 2007-08-10
So I'm sure this is a terrible way to introduce myself on this forum, particularly seeing as I've not spent the time to go through all 25 pages of this thread to find the answer I need (and am dumping a prodigious amount of useless text at all of you) but I'm at the end of my ******* rope.  I've been trying to install ndiswrapper for days.  I'm running 7.04 and whenever I attempt to execute MAKE or SUDO MAKE INSTALL in my ndiswrapper directory, it gives me this bullshit:


> aiwass@VALIS:~/temp/ndiswrapper-1.47$ make
make -C driver
make[1]: Entering directory `/home/aiwass/temp/ndiswrapper-1.47/driver'
make -C /lib/modules/2.6.20-16-generic/build SUBDIRS=/home/aiwass/temp/ndiswrapper-1.47/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  LD      /home/aiwass/temp/ndiswrapper-1.47/driver/built-in.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/crt.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/hal.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/iw_ndis.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/loader.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/ndis.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/ntoskernel.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/ntoskernel_io.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/pe_linker.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/pnp.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/proc.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/rtl.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/wrapmem.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/wrapndis.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/wrapper.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/usb.o
  CC [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/divdi3.o
  LD [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/aiwass/temp/ndiswrapper-1.47/driver/ndiswrapper.mod.o
  LD [M]  /home/aiwass/temp/ndiswrapper-1.47/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: Leaving directory `/home/aiwass/temp/ndiswrapper-1.47/driver'
make -C utils
make[1]: Entering directory `/home/aiwass/temp/ndiswrapper-1.47/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before ‘size_t’
loadndisdriver.c: In function ‘load_file’:
loadndisdriver.c:67: error: ‘size_t’ undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected ‘;’ before ‘size’
loadndisdriver.c:68: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:71: warning: implicit declaration of function ‘basename’
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function ‘open’
loadndisdriver.c:73: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘syslog’
loadndisdriver.c:75: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:75: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function ‘strerror’
loadndisdriver.c:75: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:76: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function ‘fstat’
loadndisdriver.c:81: warning: implicit declaration of function ‘close’
loadndisdriver.c:84: error: ‘size’ undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function ‘mmap’
loadndisdriver.c:86: error: ‘PROT_READ’ undeclared (first use in this function)
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: ‘MAP_FAILED’ undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function ‘strncpy’
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:95: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:96: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:69: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘parse_setting_line’:
loadndisdriver.c:109: warning: implicit declaration of function ‘isspace’
loadndisdriver.c:115: warning: implicit declaration of function ‘strchr’
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function ‘strchr’
loadndisdriver.c:115: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:117: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:118: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function ‘strlen’
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c: In function ‘read_conf_file’:
loadndisdriver.c:150: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:151: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:151: error: ‘config’ undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function ‘lstat’
loadndisdriver.c:158: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:158: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:160: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function ‘sscanf’
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:178: warning: implicit declaration of function ‘fopen’
loadndisdriver.c:178: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function ‘fgets’
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:205: warning: implicit declaration of function ‘fclose’
loadndisdriver.c:150: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_bin_file’:
loadndisdriver.c:217: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:217: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function ‘tolower’
loadndisdriver.c:221: warning: implicit declaration of function ‘chdir’
loadndisdriver.c:222: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:224: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:232: warning: implicit declaration of function ‘ioctl’
loadndisdriver.c:232: warning: implicit declaration of function ‘_IOW’
loadndisdriver.c:232: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘load_driver’:
loadndisdriver.c:249: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:249: error: ‘driver_dir’ undeclared (first use in this function)
loadndisdriver.c:251: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:255: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:257: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:259: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function ‘opendir’
loadndisdriver.c:267: warning: implicit declaration of function ‘malloc’
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function ‘malloc’
loadndisdriver.c:271: warning: implicit declaration of function ‘memset’
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:280: warning: implicit declaration of function ‘readdir’
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function ‘stat’
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function ‘S_ISREG’
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function ‘strlen’
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function ‘strcasecmp’
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function ‘strcpy’
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function ‘strcpy’
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:318: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable ‘statbuf’
loadndisdriver.c:344: error: expected expression before ‘struct’
loadndisdriver.c:346: warning: implicit declaration of function ‘closedir’
loadndisdriver.c:348: warning: implicit declaration of function ‘free’
loadndisdriver.c:355: warning: implicit declaration of function ‘munmap’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:355: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘data’
loadndisdriver.c:357: error: ‘struct load_driver_file’ has no member named ‘size’
loadndisdriver.c: In function ‘get_device’:
loadndisdriver.c:367: error: storage size of ‘statbuf’ isn’t known
loadndisdriver.c:370: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:370: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:373: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:374: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function ‘snprintf’
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function ‘snprintf’
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function ‘strncpy’
loadndisdriver.c:367: warning: unused variable ‘statbuf’
loadndisdriver.c: In function ‘load_device’:
loadndisdriver.c:419: error: ‘DIR’ undeclared (first use in this function)
loadndisdriver.c:419: error: ‘dir’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:423: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function ‘memset’
loadndisdriver.c:426: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:427: error: ‘EINVAL’ undeclared (first use in this function)
loadndisdriver.c:429: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before ‘struct’
loadndisdriver.c: In function ‘get_ioctl_device’:
loadndisdriver.c:464: error: ‘FILE’ undeclared (first use in this function)
loadndisdriver.c:464: error: ‘proc_misc’ undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function ‘strstr’
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function ‘strstr’
loadndisdriver.c:473: warning: implicit declaration of function ‘strtol’
loadndisdriver.c:473: error: ‘NULL’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:483: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function ‘unlink’
loadndisdriver.c:489: warning: implicit declaration of function ‘mknod’
loadndisdriver.c:489: error: ‘S_IFCHR’ undeclared (first use in this function)
loadndisdriver.c:489: error: ‘MISC_MAJOR’ undeclared (first use in this function)
loadndisdriver.c:490: error: ‘errno’ undeclared (first use in this function)
loadndisdriver.c:495: error: ‘O_RDONLY’ undeclared (first use in this function)
loadndisdriver.c: In function ‘main’:
loadndisdriver.c:511: warning: implicit declaration of function ‘openlog’
loadndisdriver.c:511: error: ‘LOG_PERROR’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_CONS’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_KERN’ undeclared (first use in this function)
loadndisdriver.c:511: error: ‘LOG_DEBUG’ undeclared (first use in this function)
loadndisdriver.c:513: error: ‘LOG_INFO’ undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function ‘strncmp’
loadndisdriver.c:517: warning: implicit declaration of function ‘printf’
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function ‘printf’
loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
loadndisdriver.c:549: warning: implicit declaration of function ‘strcmp’
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function ‘sscanf’
loadndisdriver.c:590: warning: implicit declaration of function ‘closelog’
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/aiwass/temp/ndiswrapper-1.47/utils'
make: *** [all] Error 2


What's going on??

---

### Post by maclenin on 2007-08-10
Have you installed the build-essential tool set (see step 4. in the guide)?

---

### Post by Asphyxiaphilia on 2007-08-10
I hadn't (dur)!  So now I've got ndiswrapper all installed, thank you.  I've now run into another snag in attempting to install my Netgear WG311v3 wireless pci card, however.  In attempting to install, I get the following output:
> 
aiwass@VALIS:~/temp/wg311v3$ sudo ndiswrapper -i  wg311v3.inf
installing wg311v3 ...
couldn't open wg311v3.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.

Out of frustration, I try it again, only to find...
> 
aiwass@VALIS:~/temp/wg311v3$ sudo ndiswrapper -i WG311v3.INF
driver wg311v3 is already installed

?  So it's installed, despite it not being able to find the install file?  And why is it looking for the INF in my ndiswrapper folder anyhow?  Just to be sure of what's going on, I had ndiswrapper list the installed drivers:
> 
aiwass@VALIS:~/temp/wg311v3$ ndiswrapper -l
wg311v3 : invalid driver!

Ugh.  So I figure I totally botched the install or perhaps am attempting to install the wrong file and ran sudo ndiswrapper -r wg311v3, successfully removing the little ****** (or so ndiswrapper -l tells me).  Just for kicks, I track down a 64 bit version of the driver produced by the chipset manufacturer, mrv8335x64.inf.  Exact same story, couldn't find it in the ndiswrapper folder and later told me it was actually installed just was an "invalid driver".  Yuck!

---

### Post by maclenin on 2007-08-11
I would recommed a "clean" re-install of ndiswrapper and your wireless driver of choice - paying particular attention to steps 6. 'till the end....

Also, be aware that names (files or directories etc.) are cAsE senSitive.... **THIS FILE** is not the same as **this file**.... Ergo, in your example - wg311v3.inf is a different file than WG311v3.INF.

So, pay attention to details - they AlL mATteR....

Anyway - give the process another whirl - substitute your specific variations, where applicable - and good luck.

I don't think your issues (at this point) are any more complicated than what I've described.

Also, have a look at [_**this link (and see [B]N** 3.)[/B]_]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/") for more info....

---

### Post by Genecks on 2007-08-12
This tutorial worked for me last night on a Live-CD of Feisty, but I think I did some things differently. However, I was tired, and I didn't really keep track of the stuff I did. I'm trying my best to replicate what I did last night, but I can't really do it.

I don't know what's wrong, though. I have a feeling it could be the version of ndiswrapper I am using, but I'm not sure. I'm using the most recent version.

Has anyone been able to do this in Feisty with a Live-CD?

Also, if the original thread creator would be so kind, I think this would be a nice thing to put under number 4:

> 
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

That's if someone is using the Live-CD for feisty without an Internet connection. Compiling ndiswrapper 1.47 works very well. Although, I advise using the apt-cdrom if you haven't used an Internet connection recently. I say that, because it tends to believe it can still access the ubuntu servers if you recently used Internet. Otherwise, without having hope that it can reach a server--and not having noticed a recent Internet connection--the process tends to go very quickly. It works if you just got done using the Internet and didn't reboot, but it will just take longer--maybe 10 minutes instead of 1 minute--not too sure anymore.

Also, could someone tell me how important permissions are? I remember just placing everything on the Desktop last night and having everything within the user ubuntu's home directory. At the moment, I'm trying to do it from a storage medium. It's not working too well, though. I keep getting some "user 1100" or UID error or something like that.

**Update:**

Ahh, that was my problem--not having everything within the home directory first. I think that would be an important thing to note in the manual, unless it's possible to do it without having the files inside of the home directory. I wonder why having it in /home/username/ matters at all... hmm.

Also, it is possible to create a script to do all of this. A person would have to use bash, sed, and perhaps awk for messing with certain files. The only things required would be the driver files, ndiswrapper, and build-essential. I'm not too sure if ndiswrapper is already on the Feisty Live-CD, though.

---

### Post by bg1256 on 2007-08-14
> **maclenin said:**
> Take a peek at this [_first post_]("http://ubuntuforums.org/showpost.php?p=3092835&postcount=241") to try and "reassociate" your wireless card. If this does not work - and given your recent move from KDE to Gnome, you might want to try a reset of the driver, with specific reference to comments for **zeddock** in this [_second post_]("http://ubuntuforums.org/showpost.php?p=2144218&postcount=108")....

Should these steps not work, I would re-install the driver....

Good luck!

Thank you for the post and links.

Here is what seems to be causing the problem, as best as I can figure.

When I am at home, the network here is not encrypted (wish it were, but it's my parents, not mine).  In order to connect to that network, I cannot use network manager.  It simply will not connect to it on its own.  In order to connect, I select the "manual configuration" option and enter my information.  Then, I restarted.  The driver loaded on startup, and it connected automatically.

However, when I select the "enable roaming mode" so that I can connect to a WPA encrypted network, it seems to be hit or miss.  About half the time the driver loads, and the other half it does not. I cannot seem to figure out why that would be the case, but it simply is.

If I do not enable manual configuration before I shut down again, the driver will not load at startup -- and then I cannot get it to load at all.

I hope that makes sense to someone... not even sure it makes sense to me.

But, when I get back to school, I would like to use network manager again, which makes connecting to the wifi hot spots at school quite easy.

so the question is, should I create a new post in the wireless forum for this purpose?  It may be out of the range of this particular howto thread.

Thanks!

---

### Post by maclenin on 2007-08-14
**bg1256:**

I would recommend starting a new thread - you'll get better visibility re: your issue.... If I could help, I would - I just haven't dabbled enough with WAP and the network manager to opine, constructively. I will follow your new thread!

---

### Post by spd106 on 2007-08-14
@ bg1256

I'm sure you could convince your parents to add a simple WEP key, if not WPA. There are loads of scare stories flying around about how evil people can pluck your passwords out of the air and steal your identity.

Getting back to the problem, it might be a good idea to run this command then try to connect via nm-applet (roaming mode), it will let you see what's going on behind the scenes.
```
tail -f /var/log/syslog
```


@ maclenin

I have noticed that driver you currently recommend in the guide,  (Broadcom,03/23/2006, 4.40.19.0) is slightly older than another one that's available, (Broadcom,10/12/2006, 4.100.15.5).
It was released late last year to fix a security issue on Windows, I'm not sure whether that makes any difference on Linux, but it couldn't hurt to give it a try and see if there are any improvements. Download from [ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)

---

### Post by maclenin on 2007-08-15
**spd106: **

Always nice to see you hangin' 'round - and thanks for the advice. I'll make the driver swap as soon as I've tested the driver - and will watch to see whether it lights up the forum.... Cheers!

P.S. Can you tell me where you found or how one stays abreast of info. re: driver updates, such as this?

---

### Post by maclenin on 2007-08-15
**Genecks:**

With reference to a couple of other posts here and in other threads (nods to **[_teaker1s_]("http://ubuntuforums.org/showpost.php?p=2194012&postcount=14")** and **[_LavaHot_]("http://ubuntuforums.org/showpost.php?p=2028732&postcount=3")**), I think your suggestions about retrieving build-essential from the livecd are solid - as are your suggestions re: scripting.

I will explore your suggestions and incorporate mods. into the guide, as I get them to work, for me.... Thanks for the input!

---

### Post by Genecks on 2007-08-16
Has anyone had problems with accessing certain administrative programs, such as "Services" and not being able to use them with this tutorial? I'm having a lot of system-wide problems because of this tutorial.

Inside of the Live-CD for Feisty, it works just fine. However, I didn't install and setup users. I didn't do all of that.

For the hard drive install, I did install it all. It could be that I have /home mounted to a different partition. It's just not working the same though. For anything to work, I've got to do this:

> sudo rmmod ndiswrapper
sudo modprobe ndiswrapper

That seems to get it working.

I did, however, delete the /etc/network/interfaces file. I didn't feel like commenting it. I don't know if that's too important or not. It might be.


When I use networkmanager, it connects. But I don't see why it's affecting the login process. When I login, GDM crashes. I don't get past the black background I have.

I've determined it has something to do with dhclient. I've messed with it multiple times, I tried different commands. I've narrowed the problem to dhclient. I don't know why dhclient is messing with it. It could be another bug with Ubuntu.

I'm getting pretty sick of the Ubuntu distro, to tell you the truth. I might just say f' it and move to RPM-types or straight Debian.

Sometimes I don't care for networkmanager, so I use dhclient.
If I use dhclient, I can access the Internet.
However, if I logout, I can't log back in.
I don't know why.

I'm stuck in the situation of rebooting the computer and not using Internet whenever I want to switch users.

Anyone know if there is a way to reverse the effects of dhclient?

**Update:**

I decided to take the clean etc/network/interfaces file from the Live-CD, save it to the HDD's /etc/network/interfaces. I altered the file and made changes.
All is well at this moment in time: It's working again.

---

### Post by Diseal3 on 2007-08-17
Hello,

     I am a long time experienced windows user and I have just installed ubuntu and followed your guide for ndiswrapper.. evreything installed fine.. I connected to my router, only thing is.. firefox wont load any websites?! The router is ok because im using my laptop on it just fine. I dont know what to do please help me out!

-Anthony

---

### Post by zeddock on 2007-08-17
> **maclenin said:**
> **Genecks:**

With reference to a couple of other posts here and in other threads (nods to **[_teaker1s_]("http://ubuntuforums.org/showpost.php?p=2194012&postcount=14")** and **[_LavaHot_]("http://ubuntuforums.org/showpost.php?p=2028732&postcount=3")**), I think your suggestions about retrieving build-essential from the livecd are solid - as are your suggestions re: scripting.

I will explore your suggestions and incorporate mods. into the guide, as I get them to work, for me.... Thanks for the input!

Maclenin,  please post when you have tested and changed things. I continue to subscribe to this thread as it is the ONLY reliable process for the 4306, and in my case, 4309, configuration.

You may remember that I commented on there being updated Ndiswrappers, and Dell drivers in the past... but in the end I have come to rely on the versions and process you suggest as they always work!

I am on the Gusty line now and your guide still holds water! I have seen my wireless work out of the box on Tribe 2 then get broken with an update around the 3rd of Aug, and it still will not work.  

I will wait and hope that Gusty finally gets it fixed before release. (Unlike Feisty.)  But in the end, i know I can just go through your guide.

The only issue is that I always seem to NOT have a wired connection when I need the wireless fixed.<sheepish grin>

Perhaps someone here could throw together a way to pack up the needed files usually DLed in your process and explain how to pull them from that local 'pack' versus the pull form the internet?

As always...

Thanx!


zeddock

---

### Post by bg1256 on 2007-08-17
> **maclenin said:**
> **bg1256:**

I would recommend starting a new thread - you'll get better visibility re: your issue.... If I could help, I would - I just haven't dabbled enough with WAP and the network manager to opine, constructively. I will follow your new thread!

Will do.  I'll try to remember to post the link of a new thread here, so others may benefit!

---

### Post by zeddock on 2007-08-17
I want to make others aware that there is an application called wicd, pronounced "wicked" that seems to be a good replacement for network-manager.  

Network-manager, on Fiesty and Gusty, just never seems to be "all there".  Here is a link:
[http://ubuntuforums.org/showpost.php?p=3206660&postcount=5](http://ubuntuforums.org/showpost.php?p=3206660&postcount=5)

I have started to use it. Although it does not solve the issues with bcm43xx, it sure is nice to get accurate reporting of the networking status.

zeddock

---

### Post by maclenin on 2007-08-18
Great zeddock! Thanks (as always) for your input!

---

### Post by asgardfleet on 2007-08-28
Hey,

Followed this guide as well as other quite  strictly - I am attempting to run a wg511 v2 
Which is :

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
```

When I attempt to scan for networks or connect to one the following is shown in system log

```
[  786.890842] ndiswrapper: driver mrv8335 (Marvell,02/22/2005,3.1.1.7) loaded
[  786.891892] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[  786.891904] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[  786.891921] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  786.894105] ndiswrapper: using IRQ 16
[  787.214918] wlan0: ethernet device 00:18:4d:76:00:f2 using NDIS driver: mrv8335, version: 0x3000036, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[  787.214937] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
**[  865.151040] ADDRCONF(NETDEV_UP): wlan0: link is not ready**
```

I was reading that this wlan0: link is not ready is a flaw with ubuntu?

And that compiling ndiswrapper from v1.47 should get around this.  

Well that is what I did and I am afraid I am still getting this.

Note I am also trying to use wicd to connect to networks as I also read that gnome network-manager had problems with the wg511.
Does anyone have any ideas that could help - any help would be appreciated

Thanks

---

### Post by bg1256 on 2007-09-09
I've posted about this before, but not really had an answer, so I'll give it another quick shot.

Whenever I boot up my computer, and there is no wireless network present, my wifi driver does not load.  My wifi light does not come on, and I can't seem to find a way to get it to load after I have booted up.

I also have this problem when I boot up my computer and there is a network my computer does not recognize. 

For example, at my in-laws, there is a WPA2 encrypted network, and when running network-manager, my wifi driver will not load.  I've tried wicd with the same result.

As another example, I am currently visiting friends at my former univeristy, and there is wireless router no more than ten feet from me.  In Windows (what I'm using now), it connects automatically, not asking for a password or anything.

Yet, in Ubuntu, my wifi driver doesn't load.  When booting up, I get stuck for about 1-2 minutes at the boot screen, and the little bar freezes.  This would be the point where it would normally load my wireless driver and the light would come on.

If anyone can point me in the right direction here, I would greatly appreciate it!

---

### Post by NullHead on 2007-09-09
> **bg1256 said:**
> I've posted about this before, but not really had an answer, so I'll give it another quick shot.

Whenever I boot up my computer, and there is no wireless network present, my wifi driver does not load.  My wifi light does not come on, and I can't seem to find a way to get it to load after I have booted up.

I also have this problem when I boot up my computer and there is a network my computer does not recognize. 

For example, at my in-laws, there is a WPA2 encrypted network, and when running network-manager, my wifi driver will not load.  I've tried wicd with the same result.

As another example, I am currently visiting friends at my former univeristy, and there is wireless router no more than ten feet from me.  In Windows (what I'm using now), it connects automatically, not asking for a password or anything.

Yet, in Ubuntu, my wifi driver doesn't load.  When booting up, I get stuck for about 1-2 minutes at the boot screen, and the little bar freezes.  This would be the point where it would normally load my wireless driver and the light would come on.

If anyone can point me in the right direction here, I would greatly appreciate it!

well sounds like you've got a problem ... but nothing we can't try to fix! try to disable the old bcm43xx driver ```
sudo rmmod bcm43xx
```
and to be shure we got it out of our way check the blacklist```
gksudo gedit /etc/modprobe.d/blacklist
```
after that text editor loads look for a "blacklist bcm43xx" line in that file that you just oped.
then make shure ndiswrapper is loaded ```
sudo modprobe ndiswrapper
```
and ```
sudo ndiswrapper -m
```
don't be scared by all of this  I'm just trying to be thorough!

---

### Post by bg1256 on 2007-09-09
Thanks much for your post, but I guess I must not have communicated my problem thoroughly enough... I was in a hurry when I wrote it.

Most of the time, the driver loads normally, and I can get connected to the internet just fine via wifi connection.  For example, when at home, my driver loads properly at start-up, and I can connect to my own wifi network without problems.

The steps that you just posted are steps I have taken -- during the initial install, and like I said, most of the time my driver loads.

For some reason, it is almost as if my computer recognizes that there is an unfamiliar network while it is booting up, and consequently, it will not load the driver.  I realize that sounds crazy, but it's the best I can come up with, since this only seems to happen when I am away from home and my own network (e.g., this network at school or networks at coffee shops).

I guess what I am looking for is a way to get the driver loaded manually if it does not load properly at start up.  It seems to me there must be some command or string of commands I could run in order to load the driver manually after I've booted up.

I will try what you have posted, but I am certain the native driver is blacklisted, as I blacklisted it when I followed the guide.

Am I making any sense?  I am once again in a hurry, so I hope so.

---

### Post by NullHead on 2007-09-10
> **bg1256 said:**
> Thanks much for your post, but I guess I must not have communicated my problem thoroughly enough... I was in a hurry when I wrote it.

Most of the time, the driver loads normally, and I can get connected to the internet just fine via wifi connection.  For example, when at home, my driver loads properly at start-up, and I can connect to my own wifi network without problems.

The steps that you just posted are steps I have taken -- during the initial install, and like I said, most of the time my driver loads.

For some reason, it is almost as if my computer recognizes that there is an unfamiliar network while it is booting up, and consequently, it will not load the driver.  I realize that sounds crazy, but it's the best I can come up with, since this only seems to happen when I am away from home and my own network (e.g., this network at school or networks at coffee shops).

I guess what I am looking for is a way to get the driver loaded manually if it does not load properly at start up.  It seems to me there must be some command or string of commands I could run in order to load the driver manually after I've booted up.

I will try what you have posted, but I am certain the native driver is blacklisted, as I blacklisted it when I followed the guide.

Am I making any sense?  I am once again in a hurry, so I hope so.

Don't worry you are making prefect sense! You might want to try reseting you network manager settings ... I don't know how but you could try making a new user.

---

### Post by maclenin on 2007-09-15
Will this guide still be necessary come gutsy?

---

### Post by NullHead on 2007-09-15
> **maclenin said:**
> WIll this guide still be necessary come gutsy?

No telling for sure, but yes I think it will be still necessary.

---

### Post by zeddock on 2007-09-16
> **maclenin said:**
> Will this guide still be necessary come gutsy?

It is likely to be still worthwhile.

zeddock
PS. For me this guide is the measuring stick.

---

### Post by bg1256 on 2007-09-16
I can't think of a reason it wouldn't be worthwhile...

---

### Post by spd106 on 2007-09-16
There have been improvements in the bcm43xx driver and 24mb/s is achievable for many of the 4306 cards. There are still issues with the later cards such as the 4318 though. That means some will want to use ndiswrapper instead, so this guide will still be useful. It might be worth considering that since ndiswrapper development appears to have slowed, there may not be any  need to swap out the version included in Ubuntu 7.10 for one downloaded from sourceforge.

In Ubuntu 7.10 configuration of the bcm43xx driver will be overseen by the restricted drivers manager just as the Atheros and Intel cards are at the moment. So I think the vast majority of users will stick with bcm43xx, but I thought that would be the case in Ubuntu 7.04. 

Of course there is still the issue of no firmware distribution, so it won't work out of the box either way.

---

### Post by maclenin on 2007-09-21
**zeddock:**

Thanks, as always, for your kind words....

**spd106:**

Thank you for keeping us posted re: developments. Your previous [_find_]("http://ubuntuforums.org/showpost.php?p=3189707&postcount=264") re: the broadcom driver upgrade proved instrumental (I believe) in my being able to get ndiswrapper working with my new wireless card (bcm4310/11) on an HP 6910p....

---

### Post by ShuaM75 on 2007-09-21
> **zeddock said:**
> maclenin,

I have used your guide successfully several times for a bcm4309 inside of a Dell Latitude D800.  But that was for Edgy!

Will this work for Feisty Fawn?


Thanx!

zeddock

Yes this works for Feisty Fawn version 7.02
Just got done with a fresh install, went through the update process, followed this guide to a "T", 
and all is well.

The last thing I'm working out is getting it to work each time I reboot.
Not woried though, there has been much discussion on this subject.

Feisty 7.04 kicks A@#!

Thanks Maclenin

---

### Post by maclenin on 2007-09-21
**ShuaM75:**

You are very welcome! Glad it works for you (as it does for me)! Agreed, these forums are loaded with substance re: your - and all matters....

Good luck!

---

### Post by maclenin on 2007-09-23
Not certain this has been asked - so I will ask it - has anyone tried this guide with gutsy?

---

### Post by maclenin on 2007-09-28
Have we tried the guide with gutsy?

---

### Post by NullHead on 2007-09-28
I would try but I have a bcm4318:( but it looks like it covers all of the things that need to be done when using ndiswrapper;) You should give it a try in 7.10 ... you have the correct card and all. I think I will install the Beta later today though.

---

### Post by maclenin on 2007-09-28
Let us know what happens....

---

### Post by cameronjcc on 2007-10-01
Using the bcm43xx driver (OEM.inf) with ndiswrapper worked better for me than this whole thing did.
I tried this, and it only seemed to work, and then only intermittently. Never got any connection, actually.

Then I did this:

1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines

# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"

Remove all comments ('#') that you see so that all devices arehandled by the default network manager.

I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper

Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.

You could also type "sudo apt-get install ndiswrapper-utils 
(IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"

Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"

Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit.

---

### Post by inthedryer on 2007-10-01
Wow what an awesome tutorial!
Been looking for something like this for months.
Worked perfectly on Kubuntu Feisty Fawn 7.04
For once my wireless is working correctly, goodbye bcm43xx-wrapper for once and for all.

Thank you.

---

### Post by NullHead on 2007-10-02
> **NullHead said:**
> I would try but I have a bcm4318:( but it looks like it covers all of the things that need to be done when using ndiswrapper;) You should give it a try in 7.10 ... you have the correct card and all. I think I will install the Beta later today though.

> **maclenin said:**
> Let us know what happens....

I've installed the Gutsy beta and there isn't such a big need for this guide in it though :( in the Restricted Drivers manager there is an automatic detection of my bcm4318 witch installs the bcm43xx firmware ... good for the average person who doesn't know better ... but I will allwase  use ndiswrapper witch is in on the disk by the way! :popcorn: Sorry but I didn't follow your guide by copying and pasting ... instead I did my own thing to get it working but it is still needed and I will still use ndiswrapper until there is a fully working firmware. You might want to give your guide a try in Gutsy maclenin. I've stopped using Gutsy because my Creative X-Fi doesn't work.

---

### Post by maclenin on 2007-10-06
**NullHead:**

Thanks (again) for the feedback - if you have any thoughts about bettering the guide/process - comments/suggestions are always welcome and encouraged....

---

### Post by mrmeyers99 on 2007-10-07
Just so you know that worked perfectly!  Thank you so much!!!

---

### Post by maclenin on 2007-10-08
**mrmeyers99**

You are very welcome! Glad to hear it worked for you!

---

### Post by maclenin on 2007-10-12
Any additional preliminary Gutsy reflections?

**Nulldead:**

As I understand it, from your latest post, ndiswrapper will no longer be needed in Gutsy - as the relevant wireless drivers are recognized and "installed" via the Restricted Drivers Manager? Does the Restricted Drivers Manager handle other chipsets - besides the bcm4318? You seem to imply that it does - but I just want to confirm. You also seem to imply that ndiswrapper performance may top those firmware options provided by the Restricted Drivers Manager.... Thanks for all the intel.

I have yet to test Gutsy, myself - will report - as I do. Using Feisty for work - so, little time for tinkering and Feisty's working just fine....

---

### Post by NullHead on 2007-10-12
> **maclenin said:**
> Any additional preliminary Gutsy reflections?

**Nulldead:**

As I understand it, from your latest post, ndiswrapper will no longer be needed in Gutsy - as the relevant wireless drivers are recognized and "installed" via the Restricted Drivers Manager? Does the Restricted Drivers Manager handle other chipsets - besides the bcm4318? You seem to imply that it does - but I just want to confirm. You also seem to imply that ndiswrapper performance may top those firmware options provided by the Restricted Drivers Manager.... Thanks for all the intel.

I have yet to test Gutsy, myself - will report - as I do. Using Feisty for work - so, little time for tinkering and Feisty's working just fine....

Well yes there is other support for the firmware check it out[ hear]("http://bcm43xx.berlios.de/?go=devices") as for your guide you're installing it on a bcm4306  am I correct? well if you check the link there is indeed a full driver version witch I believe is stable for your card bcm4306. 

Best not test on the main pc then! I would try[ Qemu ]("http://fabrice.bellard.free.fr/qemu/") or [virtual box]("http://www.virtualbox.org/").

---

### Post by Charles Girdlestone on 2007-10-12
Thanks, works with 7.04, on Compaq Presario M2000 laptop, Chas

---

### Post by bg1256 on 2007-10-12
> **maclenin said:**
> Any additional preliminary Gutsy reflections?

**Nulldead:**

As I understand it, from your latest post, ndiswrapper will no longer be needed in Gutsy - as the relevant wireless drivers are recognized and "installed" via the Restricted Drivers Manager? Does the Restricted Drivers Manager handle other chipsets - besides the bcm4318? You seem to imply that it does - but I just want to confirm. You also seem to imply that ndiswrapper performance may top those firmware options provided by the Restricted Drivers Manager.... Thanks for all the intel.

I have yet to test Gutsy, myself - will report - as I do. Using Feisty for work - so, little time for tinkering and Feisty's working just fine....

From what I have read, the firmware greatly reduces the speed of downloading.  For example, I have a friend running the Gutsy Beta, and running the firmware driver, he only gets half the speed as he does using ndiswrapper.

If that holds true for everyone, then this guide will still be quite relevant and important. 

I suppose we will all know more in a few days.

---

### Post by maclenin on 2007-10-12
Glad to hear it, folks. Will do my own Gutsy work - at some point. Until then - I'll keep checking in for stories....

---

### Post by maclenin on 2007-10-13
**inthedryer:**

Just wanted to say thanks for your kind words! I also took the path you took - and agree - ndiswrapper is the way!

---

### Post by maclenin on 2007-10-17
Onward!

---

### Post by bg1256 on 2007-10-17
maclenin:

I just wanted you to know that I am giving away the laptop (to my fiance) which required me to use this guide.  I am going to go with pure XP for her sake - since she lives 800 miles away, and I can't support the Ubuntu install -- but I wanted to say thanks again for this guide.

I amy end up referring to it again this summer when we get married... so see you then!

---

### Post by maclenin on 2007-10-18
Congratulations!

We'll still be here when you return! Thanks for the note!

Good luck!

---

### Post by zeddock on 2007-10-18
Congrats!
Hey, Just so I don't feel badly for not sharing this...

I have been supporting MS-Windows boxes for a lot of years and often support friends and family.

I have a new policy after Ubuntu Gusty (7.10)...and have worked up to it through Feisty...
All non-paying, friends/family/etc, that I support will have to agree to use Ubuntu.

I used to have to visit in-laws every 2 weeks or sooner, to support them.  (At 70 I do not expect the older dogs to learn new tricks like computers...)

Since I put them on the last Beta of Feisty.... months ago,  I have visited twice!

And those visits were for family time... not support.

Make sure you consider if XP is going to be easier for her!

Goodluck!

zeddock

---

### Post by cirorodrigues on 2007-10-21
It worked perfectly for me using a DWL-G510 Dlink wifi card, based on RT61 chipset, with WPA encryption. Just one remark about to use it with gnome network-manager: read carefully the detailed howto link pointed at begining of this one, and pay attention to the part regarding /etc/network/interfaces file. Maybe could be obvious for someone, but the fact this file should only contains data refering to interface "lo" BEFORE use network-manager was not clear for me (and I'm not a total noob on Ubuntu). After a clean install of Gutsy, I copied the old interfaces files and wifi networks just doesn't show up> After follow this howto, everything wents fine.
Thanks a lot!

---

### Post by maclenin on 2007-10-26
My pleasure!

---

### Post by mschap on 2007-10-27
Okay, after going through this:  Has anyone used this method with Gutsy and had it work?

---

### Post by NullHead on 2007-10-27
> **mschap said:**
> Okay, after going through this:  Has anyone used this method with Gutsy and had it work?

It will work with gutsy.

---

### Post by maclenin on 2007-10-31
Nice to hear....

---

### Post by maclenin on 2007-11-03
Again and again, Gutsy/ndiswrapper (or other) reflections are always welcome....

---

### Post by NullHead on 2007-11-03
> **maclenin said:**
> Again and again, Gutsy/ndiswrapper (or other) reflections are always welcome....

Nidswrapper preform beautifully in Gutsy ... hows that? although I haven't got a chance to go through your guide through and through, but I have configured ndiswrapper myself and it was easy! I'm reporting that I now have a bcm4306 and use ndiswrapper for it and my bcm4318 ... they both work as if they were installed with a native linux driver! All in all I will use ndiswrapper no matter what the firmware does for me ;)

As for Gutsy It is beautiful in all it's wondrous upgrades and updates It is positively the best version of Ubuntu I've found! [Hear]("https://blueprints.launchpad.net/sprints/uds-boston-2007/+roadmap") is a list of new updates to be added to he next Ubuntu release. 

I love Ubuntu so much I just have to show you all my desktop :D

---

### Post by maclenin on 2007-11-11
Thanks, NullHead!

---

### Post by maclenin on 2007-11-16
Any hardy heron / ndiswrapper prelim?

---

### Post by maclenin on 2007-11-20
Hardy Heron and ndiswrapper?

---

### Post by NullHead on 2007-11-20
I don't test new releases until the beta ... so I haven't tested it yet, but I'm sure it will work never the less.

---

### Post by maclenin on 2007-11-23
Thanks, NullHead, for the vote of confidence. Interesting to see what sorts of "advancements" Hardy brings!

---

### Post by scottvan on 2007-11-27
I can't figure out what is wrong.  I'm using a Compaq Presario 2200 with the BCM4306, and I followed the guide to step 11.  when I enter "sudo ndiswrapper -i bcml5.inf" I get the following:

```
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found

```

Can you help me, it must be something really silly, as everyone else here seems to be having success.

Thanks.

---

### Post by NullHead on 2007-11-27
> **scottvan said:**
> I can't figure out what is wrong.  I'm using a Compaq Presario 2200 with the BCM4306, and I followed the guide to step 11.  when I enter "sudo ndiswrapper -i bcml5.inf" I get the following:

```
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found

```

Can you help me, it must be something really silly, as everyone else here seems to be having success.

Thanks.

It looks like ndiswrapper isn't installedl.

Install it by ```
sudo apt-get install ndiswrapper
```

---

### Post by scottvan on 2007-11-27
I'm pretty sure it's installed.  It has a folder and files, I just can't run ndiswrapper.

---

### Post by NullHead on 2007-11-27
It doesn't hurt to try ;) 

If that doesn't work I would download the tarball from [hear]("http://ndiswrapper.sourceforge.net/") and make && make insall it.

---

### Post by maclenin on 2007-11-27
**scottvan**:

I would also consider making another pass through the guide - just to make certain you haven't missed a step.... Then give 11. another try!

Incidentally, what is the output of:

```
ndiswrapper -v
```

---

### Post by scottvan on 2007-11-28
```
wendy@wendy-laptop:~$ ndiswrapper -v
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

```

I guess it's NOT installed!  Ok, I'll try it again.

---

### Post by scottvan on 2007-11-28
I installed ndiswrapper and ndiswrapper utils from Synaptic Package Manager, and I get this:
```

wendy@wendy-laptop:~$ ndiswrapper -v
utils version: 1.9
driver modinfo: could not open ndiswrapper: No such device
```

---

### Post by NullHead on 2007-11-28
ok now continue from step 9

---

### Post by scottvan on 2007-11-28
If it's not one thing, it's another.  I started from step 9, and made to step 12:
```

wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
wendy@wendy-laptop:~/bcm4306$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
cp: cannot stat `/etc/ndiswrapper/bcmwl5/14E4:4324.5.conf': No such file or directory
```

---

### Post by NullHead on 2007-11-28
OK well do this then: 

Check the drivers installed and remove them all by doing the following ```
sudo ndiswrapper -l
``` Look at the output and uninstall them by ```
sudo ndiswrapper -e drivername
``` and THEN continue from step 9 ... This is proving to be a big pain ...

---

### Post by scottvan on 2007-11-29
I really appreciate your help in this.  I think I'm getting somewhere.  The wireless light came on during the last attempt, and the Wired Network Connection icon showed my ESSID (and my neighbor's) but there was no wireless connection.  I rebooted, but the wireless connection option disappeared.  I think the problem is in the WLAN0 portion of the instructions.  It shows my wireless connection as being lo instead.  Here is my attempt:

```
wendy@wendy-laptop:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
wendy@wendy-laptop:~$ sudo ndiswrapper -e bcmwl5
wendy@wendy-laptop:~$ sudo aptitude install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
wendy@wendy-laptop:~$ cd ~/bcm4306
wendy@wendy-laptop:~/bcm4306$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
wendy@wendy-laptop:~/bcm4306$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
wendy@wendy-laptop:~/bcm4306$ 
wendy@wendy-laptop:~/bcm4306$ sudo depmod -a
wendy@wendy-laptop:~/bcm4306$ sudo modprobe ndiswrapper
wendy@wendy-laptop:~/bcm4306$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wendy@wendy-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/iftab
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -m
module configuration already contains alias directive

wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/modprobe.d/ndiswrapper
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
wendy@wendy-laptop:~/bcm4306$ 
```

/etc/iftab is empty.
here is /etc/network/interfaces (with wireless key censored):

```
auto lo
iface lo inet loopback


#iface eth1 inet dhcp
wireless-key ****
wireless-essid Tatooine



#auto eth1

iface eth1 inet dhcp
wireless-key ****
wireless-essid Tatooine



auto eth1
```

I've noticed that the repeated lines beginning with iface eth1.... have been added by the process at some point, they weren't there before.

---

### Post by vcsp on 2007-11-29
Hi! I just installed Ubuntu on my laptop, and I have 2 problems. I was suggested to try to ask for some help on this forum. So my biggest problem is, my wifi doesnt work.
  for #lspci I got this:
 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
     Thanks for your help!!

---

### Post by NullHead on 2007-11-29
> **scottvan said:**
> I really appreciate your help in this.  I think I'm getting somewhere.  The wireless light came on during the last attempt, and the Wired Network Connection icon showed my ESSID (and my neighbor's) but there was no wireless connection.  I rebooted, but the wireless connection option disappeared.  I think the problem is in the WLAN0 portion of the instructions.  It shows my wireless connection as being lo instead.  Here is my attempt:

```
wendy@wendy-laptop:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
wendy@wendy-laptop:~$ sudo ndiswrapper -e bcmwl5
wendy@wendy-laptop:~$ sudo aptitude install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
wendy@wendy-laptop:~$ cd ~/bcm4306
wendy@wendy-laptop:~/bcm4306$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
wendy@wendy-laptop:~/bcm4306$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
wendy@wendy-laptop:~/bcm4306$ 
wendy@wendy-laptop:~/bcm4306$ sudo depmod -a
wendy@wendy-laptop:~/bcm4306$ sudo modprobe ndiswrapper
wendy@wendy-laptop:~/bcm4306$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wendy@wendy-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/iftab
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
wendy@wendy-laptop:~/bcm4306$ sudo ndiswrapper -m
module configuration already contains alias directive

wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/modprobe.d/ndiswrapper
wendy@wendy-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
wendy@wendy-laptop:~/bcm4306$ 
```

/etc/iftab is empty.
here is /etc/network/interfaces (with wireless key censored):

```
auto lo
iface lo inet loopback


#iface eth1 inet dhcp
wireless-key ****
wireless-essid Tatooine



#auto eth1

iface eth1 inet dhcp
wireless-key ****
wireless-essid Tatooine



auto eth1
```

I've noticed that the repeated lines beginning with iface eth1.... have been added by the process at some point, they weren't there before.

OK well for some odd reason all of my broadcom card are being switched to eth1 rather than wlan0 ... that looks like whats happening to you're card. It also looks like it's functioning correctly, but you're having trouble connecting to you're network? 

> **vcsp said:**
> Hi! I just installed Ubuntu on my laptop, and I have 2 problems. I was suggested to try to ask for some help on this forum. So my biggest problem is, my wifi doesnt work.
  for #lspci I got this:
 00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
     Thanks for your help!!

If you look at this > 02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) That is what you're lspci gave me from the output. 

You're at the right thread! This is just guide is for you're exact card! You might want to start by following the instructions on the 1st post and let us know after you're done with it. If you want an easier way though Ill point you to [hear]("http://ubuntuforums.org/showthread.php?t=405990") but I would try to use this guide the 1st post of this thread first ;)

---

### Post by vcsp on 2007-11-29
I did so fahr:

vcsp@vcsp-laptop:~/bcm4306$ cabextract sp33008.exe
sp33008.exe: No such file or directory

All done, errors in processing 1 file(s)

---

### Post by NullHead on 2007-11-29
You must download sp33008.exe and move it to you're home folder ;) You're terminal is looking at you're move folder. If you want to move where it's looking at rather than move you're file you can use the command "cd" to *change directories* do you're Desktop folder where you're .exe might be located.

---

### Post by josephbauer on 2007-11-29
I have a Broadcom 4318 wireless chipset. I tried this and it work but there are a few problems. First when I try to edit the /etc/iftab, well I can not find iftab! I am not sure then how to change my wireless form eth1 to wlan0. I also have to "sudo modprobe ndiswrapper" after every restart to get my wireless working; I am guessing that this is because my wireless is eth1 and not wlan0. Please help in fixing this.

Thank You

---

### Post by NullHead on 2007-11-29
> **josephbauer said:**
> I have a Broadcom 4318 wireless chipset. I tried this and it work but there are a few problems. First when I try to edit the /etc/iftab, well I can not find iftab! I am not sure then how to change my wireless form eth1 to wlan0. I also have to "sudo modprobe ndiswrapper" after every restart to get my wireless working; I am guessing that this is because my wireless is eth1 and not wlan0. Please help in fixing this.

Thank You

I'm not sure how to fix the wlan0, eth1 problem. I just live with it. As for the modprobe problem I add the line "sudo modprobe ndiswrapper" to my /etc/rc.local file right before the  [COLOR="Red"]exit[/COLOR] 0,  and it works as It should after that :)

---

### Post by vcsp on 2007-11-30
vcsp@vcsp-laptop:~/bcm4306$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
vcsp@vcsp-laptop:~/bcm4306$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
vcsp@vcsp-laptop:~/bcm4306$ sudo depmod -a
vcsp@vcsp-laptop:~/bcm4306$  sudo modprobe ndiswrapper
vcsp@vcsp-laptop:~/bcm4306$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist blacklistbcm43xx
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/iftab
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
vcsp@vcsp-laptop:~/bcm4306$ sudo ndiswrapper -m
module configuration already contains alias directive

vcsp@vcsp-laptop:~/bcm4306$ /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper: Permission denied
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/modprobe.d/ndiswrapper
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
   Everything went OK, but the contain of network/interfaces is sitll: iface lo inet loopback
and nothing else :( ...should I go back to windows? is there still any hope for me to use my wifi under ubuntu??

---

### Post by NullHead on 2007-11-30
> **vcsp said:**
> vcsp@vcsp-laptop:~/bcm4306$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
vcsp@vcsp-laptop:~/bcm4306$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4324.5.conf /etc/ndiswrapper/bcmwl5/.conf
vcsp@vcsp-laptop:~/bcm4306$ sudo depmod -a
vcsp@vcsp-laptop:~/bcm4306$  sudo modprobe ndiswrapper
vcsp@vcsp-laptop:~/bcm4306$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist blacklistbcm43xx
blacklist bcm43xx
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/iftab
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
vcsp@vcsp-laptop:~/bcm4306$ sudo ndiswrapper -m
module configuration already contains alias directive

vcsp@vcsp-laptop:~/bcm4306$ /etc/modprobe.d/ndiswrapper
bash: /etc/modprobe.d/ndiswrapper: Permission denied
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/modprobe.d/ndiswrapper
vcsp@vcsp-laptop:~/bcm4306$ sudo nano /etc/network/interfaces
   Everything went OK, but the contain of network/interfaces is sitll: iface lo inet loopback
and nothing else :( ...should I go back to windows? is there still any hope for me to use my wifi under ubuntu??

LOL if you miss windows you should have just set up dual booting.

If you look hear > vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist blacklistbcm43xx it should look like this ```
vcsp@vcsp-laptop:~/bcm4306$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist blacklist bcm43xx
``` and then you should restart and it should be working.

---

### Post by maclenin on 2007-12-01
**scottvan and josephbauer:**

I have a sneaking suspicion that an error (as minor as a typo) occurred while you folks were making your way through the guide. My recommendation is that you make certain you follow the directions exactly as written - giving particular attention to blacklisting the old wireless driver and commenting out eth1 (steps 3a. and 3b.) so that ndiswrapper has a chance to associate itself with the new driver and assign your wireless details to wlan0. In my experience, this is the only way ndiswrapper will work - properly....

Good luck!

---

### Post by scottvan on 2007-12-01
> **maclenin said:**
> **scottvan and josephbauer:**

I have a sneaking suspicion that an error (as minor as a typo) occurred while you folks were making your way through the guide. My recommendation is that you make certain you follow the directions exactly as written - giving particular attention to blacklisting the old wireless driver and commenting out eth1 (steps 3a. and 3b.) so that ndiswrapper has a chance to associate itself with the new driver and assign your wireless details to wlan0. In my experience, this is the only way ndiswrapper will work - properly....

Good luck!

Thanks for the suggestion.  I have been cut & pasting all of the commands, though, so I don't think that is what the problem is for me.

---

### Post by josephbauer on 2007-12-04
I wanted to let you know that I try to put "sudo modprobe ndiswrapper" in the rc.local file, but unfortunaly that did not help nor did it work. After some time I but "ndiswrapper" in the /etc/modules and now my wireless comes up every time, though it is still eth01 which I can live with. This really help and I have found it works with other distros beside Ubuntu. Thanks!

---

### Post by ambiance on 2007-12-06
At step 12...i run into the problem of the file or directory not existing.  

peter@DeafAmoeba:~$ sudo cp /etc/ndiswrapper/bcmwl5/14E4:4325.5.conf /etc/ndiswrapper/bcmwl5/.conf
cp: cannot stat `/etc/ndiswrapper/bcmwl5/14E4:4325.5.conf': No such file or directory


which is probably because the drivers ndiswrapper used are invalid, but I can't get rid of them.

peter@DeafAmoeba:~$ sudo ndiswrapper -i bcmwlf.inf
driver bcmwlf is already installed
peter@DeafAmoeba:~$ sudo ndiswrapper -e bcmwlf.inf
couldn't delete /etc/ndiswrapper/bcmwlf.inf: No such file or directory
peter@DeafAmoeba:~$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
peter@DeafAmoeba:~$ sudo ndiswrapper -e bcmwl5.inf
couldn't delete /etc/ndiswrapper/bcmwl5.inf: No such file or directory
peter@DeafAmoeba:~$ sudo ndiswrapper -l
bcmwl5 : invalid driver!
bcmwlf : invalid driver!

---

### Post by maclenin on 2007-12-08
**ambiance:**

I see a couple of potential issues, here:

1. The fact that you are getting the invalid driver error (as a result of ndiswrapper -l), indicates to me that you might have typed or even copied a command, improperly - somewhere along the way. Just be careful to make certain that you are entering commands exactly as the guide instructs. I have run into countless issues that looked to be something far more complex then they really were - i.e. a typo....

2. Should the installation go smoothly - and you get valid output from ndiswrapper -l, namely, something similar to...

```
bcmwl5 : driver installed
        device (14E4:43xx) present (alternate driver: bcm43xx)
```


 ...I would suggest you post the contents of your /etc/ndiswrapper/bcmwl5 directory, here, should you still encounter problems with Step 12....

Let's see what happens!

Good luck!

P.S. Step 12. of the guide asks that you copy /etc/ndiswrapper/bcmwl5/14E4:432***4***.5.conf, rather than /etc/ndiswrapper/bcmwl5/14E4:432***5***.5.conf, as you indicate in your question....

---

### Post by LIMEZ on 2007-12-08
hi guys i have a problem with the wireless pls look here
[http://ubuntuforums.org/showthread.php?t=634901](http://ubuntuforums.org/showthread.php?t=634901)
 i am trying to make it work with ndiswrapper
:(

---

### Post by maclenin on 2007-12-08
Try following the guide on the first page of this thread - should you still have issues (or success), feel free to report back....

---

### Post by maclenin on 2007-12-11
Any other hardy reflections?

---

### Post by NullHead on 2007-12-11
If you look over the list I posted earlier you will see the features to be in HH. If you look at [distro watch there will be an alpha2 ]("http://distrowatch.com/weekly.php?issue=20071210#upcoming")I'm planing on testing for no apparent reason. I'll let you know my thoughts on it when I'm done testing.

---

### Post by maclenin on 2007-12-13
Thanks, NullHead....

---

### Post by maclenin on 2007-12-19
Any Hardy news (with a wireless bent...)?

---

### Post by maclenin on 2007-12-28
Hardy news?

---

### Post by maclenin on 2008-01-02
Anyone Hardy, yet?

---

### Post by NullHead on 2008-01-02
Sorry I haven't had time to try it out yet, but I might here in a couple of weeks 8)

---

### Post by maclenin on 2008-01-07
No rush....

---

### Post by NullHead on 2008-01-13
OK I installed the alpha 3 and there seems to be no difference to the actual gnome GUI. So at first it looks just like gutsy, but then I noticed there is no .deb for ndiswraper on the 8,04  cd! witch is a very bad thing for me. I need that .deb to be able to connect in any way.

Anyways when I used my gutsy cd to install ndiswrapper I discovered that when you "ndiswrapper -i /path/to/.inf it doesn't seem to work. I rmmoded bcm43xx and I blacklisted bcm43xx and I added ndiswrapper to /etc/modules and it still doesn't seem to work. Also at this time there is no real reason to use 8.04 unless you're one of those people that need the biggest and the best.

Over all there seems to be no good reason to use 8,04 at this time. I will continue to test ndiswrapper and various ways of getting it to function, but other than that just don't switch.

---

### Post by ubunyou on 2008-01-20
worked perfectly im using wireless to make this post.
Thanks a bunch!

---

### Post by rosegarden78 on 2008-01-20
:popcorn:

---

### Post by maclenin on 2008-01-23
**Nullhead:**

Thanks for the intel. I will remain Feisty and fine (at least for the next little while)....

**ubunyou and rosegarden78:**

Glad to hear (see) that you're up and running! Thanks for the feedback!

---

### Post by maclenin on 2008-01-30
Any more Hardy/ndis news?

---

### Post by maclenin on 2008-02-06
Hardy news?

---

### Post by maclenin on 2008-02-11
Hardy news?

---

### Post by maclenin on 2008-02-18
Any Hardy news or comments on the efficacy of this guide?

Thanks, All!

---

### Post by maclenin on 2008-02-21
Thanks!

---

### Post by zeddock on 2008-02-22
Howdy again!

I am not able to play with Hardy yet. (Started new job, so busy.)

I also have moved to a different laptop computer which does not have the issuses that the broadcomm does.

So, I guess this post is just to say thank you.

Thank you for all of your efforts, help, guidance, and persistance of this forum.

I will now unsubscribe, but will check in from time to time.

Thanx!

Zeddock

---

### Post by maclenin on 2008-02-22
**zeddock!**

Thank you, as well, for the same! Good luck with the new job and laptop!

I'll still be here when you check back....

Ciao!

---

### Post by maclenin on 2008-02-28
Any more Hardy news?

---

### Post by maclenin on 2008-03-05
Just checking in....

---

### Post by NullHead on 2008-03-06
I'm hoping to get my hands on a 8.06 alpha6 (is released today) and test it out. I'll report back here when I get it all setup.

---

### Post by maclenin on 2008-03-12
Looking forward to the findings.

---

### Post by NullHead on 2008-03-12
Mid thoughts on 8.04

The wifi is a [SIZE="5"]***HUGE***[/SIZE] pain to get working for offline users ... and after you ***do*** get it working, it only runs at 1mb/s .vs the 54mb/s ndiswrapper offers ... 

What I'm talking about is the built in b43 driver that is now in the kernel ... I might just write a guide on how to get it working off-line ... 

As for ndiswrapper I haven't given it an effort yet ... it's not on the CD and I mistakenly installed the i386 version of Ubuntu where as I usually install the x86_64 version .. so my .inf and .sys are for a 64but OS .. so I need to dig up some of my older i386 drivers ... so when I get ndiswrapper installed and working I'll report again ;)

---

### Post by maclenin on 2008-03-19
Thanks (again) NullHead for the intel. It seems then this guide can continue to serve its purpose....

---

### Post by maclenin on 2008-03-26
Any beta dish?

---

### Post by NullHead on 2008-03-26
Well I eventually got ndiswrapper working  (I forgot to announce) after much trial and error. What it seems I ended up doing is downloading the debs from packages.ubuntu.com and installing those and then installing build-essential and making ndiswrapper from source. It runs so good I forget I'm on wifi :) 

The beta offers huge bonuses over gutsy ... for example you can now edit the connections you make when you connect to a network with network-manager, there is new artwork, updated apps (e.g rhthmbox) and the list goes on. One of the most most noticeable things about the bets is faster startup speeds and the new artwork. 

I've been using the beta quite often now (I dual boot) and it's very stable. It still has some bugs with some programs but for the most part it all runs good :D

Hope I've enlightened you all a little, 

Nullhead

EDIT: you might think about updating the how-to a little bit. It's still talking about edgy ... and now we're moving on to hardy ;)

---

### Post by maclenin on 2008-03-31
Thanks for the wink-wink, nudge-nudge - and the enlightenment, as always.... When I make my leap to Hardy - I'll slip some changes into the text...!

---

### Post by pigSTI04 on 2008-04-01
Anymore news regarding Hardy Beta and NDISWrapper?

I had NDISWrapper working well with my broadcom 4306 wireless card a couple days ago. That was when I was running Ubuntu 7.10 thanks to this guide. It's an old laptop so I decided to scratch Gutsy and install Xubuntu 8.04 Beta, since then I've been unable to get the wireless care working. 

Anyone know any tricks I can try?

---

### Post by NullHead on 2008-04-03
> **pigSTI04 said:**
> Anymore news regarding Hardy Beta and NDISWrapper?

I had NDISWrapper working well with my broadcom 4306 wireless card a couple days ago. That was when I was running Ubuntu 7.10 thanks to this guide. It's an old laptop so I decided to scratch Gutsy and install Xubuntu 8.04 Beta, since then I've been unable to get the wireless care working. 

Anyone know any tricks I can try?

Well I just re-installed ubuntu and upgraded to the beta on my laptop and what I did goes as follows. 

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
blacklist b43
blacklist b44
blacklist ssb
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
ndiswrapper -l
sudo modprobe ndiswrapper

Use nm-applet to connect to wireless router and it's all working great :D 

Hope this helps, NullHead

---

### Post by maclenin on 2008-04-14
Thanks, as always, for filling in....

---

### Post by maclenin on 2008-04-22
Any 8.04 LTS vis a vis ndiswrapper news?

---

### Post by maclenin on 2008-04-27
How Hardy is the Heron?

---

### Post by NullHead on 2008-04-28
It's nice and updated and stable :)

---

### Post by maclenin on 2008-05-04
I hope to make my Hardy move, soon! Thanks for keeping us posted!

---

### Post by maclenin on 2008-05-14
Any comments on what might need to be added/changed in this guide to bring it up to date? Mulling a move to Hardy and would like to make certain all is current (without leaving others behind, of course)....

---

### Post by NullHead on 2008-05-14
Well for starters I'd get rid of the whole repository thing. I'd also recommend not building ndiswrapper from source. You should download the binary from here before you upgrade [http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=ndiswrapper&searchon=names&suite=hardy&section=all) and when you get done installing make sure to rmmod b43 and ssb before you modprobe ndiswrapper. Ndiswrapper -m is depreciated and does not need to be ran anymore; so don't. 

From that stand point I'd probably re-write the guide for more simplicity using the .deb from packages.ubuntu.com.

---

### Post by maclenin on 2008-05-20
Thanks for the suggestions. I'll reflect more completely - as I rebuild!

---

### Post by jfreak53 on 2008-06-01
Well I have read all through your forum and I still don't know what it is that I'm doing wrong here.  I have done it three times with no errors and nothing still, could I get some help by chance please.

When I do iwconfig I get this:

lo        no wireless extensions.

eth0      no wireless extensions.

This is lshw -C network:

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4b:36:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.122 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:18
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: iomemory:e0104000-e0105fff irq:11

uname -r:

2.6.20-15-generic

I just don't know why it won't give me wlan0. I have it blacklisted too.

This is ndiswrapper -l:

bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

Thanks for any help.  I would really like to switch over to using ubuntu but I can't until I get the wireless working correctly.

---

### Post by NullHead on 2008-06-01
Well I think you've come to the right place! 

I'd like to know what version of ubuntu you're running. This can make a difference on the instructions that I/OP gives you.

---

### Post by jfreak53 on 2008-06-01
My kernel version is: 2.6.20-15-generic

Ubuntu is: 7.04 - the Feisty Fawn

---

### Post by jfreak53 on 2008-06-01
I forgot to state, I am using 64bit ubuntu on an AMD64 HP Pavilion

---

### Post by NullHead on 2008-06-01
> **jfreak53 said:**
> My kernel version is: 2.6.20-15-generic

Ubuntu is: 7.04 - the Feisty Fawn

> **jfreak53 said:**
> I forgot to state, I am using 64bit ubuntu on an AMD64 HP Pavilion

OK not to worry. I've used my bcm4318 a whole lot in 7.04. Here is what I would do:

[CENTER]**Step #1**[/CENTER]

Download and install ndiswrapper *note that the debs in (either 7.04 or 6.10 had broken debs... [can't remember])*

Save [this]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz?modtime=1211931005&big_mirror=0") file into your home directory. 

Now lets open a terminal window and unpack it and install the needed packages to configure/install ndiswrapper. ```
sudo apt-get purge ndiswrapper-utils-1.9 ndiswrapper-common && sudo apt-get install build-essential
```Now you're ready to unpack the file. ```
tar -xvf ndiswrapper-1.5*
```Move to the ndiswrapper directory:```
cd ndiswrapper*
```Make and install ndiswrapper: ```
make && sudo make install
```Assuming all goes well lets disable the built in (bad) driver: ```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
``` Restart the computer and install [these]("http://ubuntuforums.org/attachment.php?attachmentid=30521&d=1177299363") drivers for 64bit broadcom cards: ```
sudo ndiswrapper -i bcmwl5.inf
``` Start ndiswrapper and make it load on bootup: ```
sudo modprobe ndiswrapper
```and to make ndiswrapper load on boot: ```
echo 'ndiswrapper' | sudo tee -a /etc/modules
``` 

You might have to restart again, but you should have it working after that :popcorn:

---

### Post by foxy123 on 2008-06-01
I have tried a number of howtos but without any luck. I have a 4306 rev2 Belkin card on Hardy and I cannot make it work with ndiswrapper. The problem is that it does not handle WPA. If I switch it off in the router it connects fine but as soon as I switch it back on I have no connection. It used to work fine on Feisty.

---

### Post by NullHead on 2008-06-01
> **foxy123 said:**
> I have tried a number of howtos but without any luck. I have a 4306 rev2 Belkin card on Hardy and I cannot make it work with ndiswrapper. The problem is that it does not handle WPA. If I switch it off in the router it connects fine but as soon as I switch it back on I have no connection. It used to work fine on Feisty.

You should try using [wicd]("http://wicd.sourceforge.net/").

---

### Post by foxy123 on 2008-06-02
> **NullHead said:**
> You should try using [wicd]("http://wicd.sourceforge.net/").

Thanks, but it is what I am using.

---

### Post by NullHead on 2008-06-02
> **foxy123 said:**
> Thanks, but it is what I am using.

Does your card actually support any of the higher encryptions? For my card I can type into the terminal "lwlist scan" and it'll report back the encryption information and the speed/rates that the router/NIC support. The only thing I can think of is your network card doesn't support wpa/wep :confused:

---

### Post by foxy123 on 2008-06-02
> **NullHead said:**
> Does your card actually support any of the higher encryptions? For my card I can type into the terminal "lwlist scan" and it'll report back the encryption information and the speed/rates that the router/NIC support. The only thing I can think of is your network card doesn't support wpa/wep :confused:

Yes, it does support WPA. I used bcm43xx driver as well as ndiswrapper before and it worked fine.

```
~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:6C:02:C1:0F:4F
                    ESSID:"MYROUTE"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-19 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:14:6C:E0:F5:4F
                    ESSID:"SAXEWAY"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:34/100  Signal level:-74 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:1D:68:0A:B3:0B
                    ESSID:"O2wirelessDD5531"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


```

---

### Post by NullHead on 2008-06-02
One thing I notice from your output you posted is that all of your access points are 802.11b only .. where as mine says 802.11**g** ... I'm not sure why its acting like that, but I'd try building ndiswrapper from source. I'd make sure to purge the debs first (if you have those installed).

---

### Post by foxy123 on 2008-06-08
> **NullHead said:**
> One thing I notice from your output you posted is that all of your access points are 802.11b only .. where as mine says 802.11**g** ... I'm not sure why its acting like that, but I'd try building ndiswrapper from source. I'd make sure to purge the debs first (if you have those installed).

Yes, it is kind of strange. I think there is something wrong with ndiswrapper. I have manage to make my wifi work with the b43 driver but is only gives me 1 Mb/s speed while ndiswrapper used to give me 54 Mb/s. I have tried to build it from source but it had the same problem :(

---

### Post by NullHead on 2008-06-09
> **foxy123 said:**
> Yes, it is kind of strange. I think there is something wrong with ndiswrapper. I have manage to make my wifi work with the b43 driver but is only gives me 1 Mb/s speed while ndiswrapper used to give me 54 Mb/s. I have tried to build it from source but it had the same problem :(

The b43 driver does not work as well as ndiswrapper. Ndiswrapper's top speed **is** 54mbps. If you're getting 54mbps then you're doing something correct!

---

### Post by foxy123 on 2008-06-09
> **NullHead said:**
> The b43 driver does not work as well as ndiswrapper. Ndiswrapper's top speed **is** 54mbps. If you're getting 54mbps then you're doing something correct!

the trouble is that now ndiswrapper cannot handle WPA security :(

---

### Post by NullHead on 2008-06-09
I did some searching and I found this on the ndiswrapper website: > #
Card: HP 54g W450

    *
      Chipset: Broadcom BCM4306
    *
      pciid: 14e4:4320 (rev 02)
    *
      Driver: bcmwl5.sys and oem6.inf (got it off working windows install)
    *
      Other: HP Pavilion ze5400 came with WinXP home. Took drivers off of that.

Now I do understand it's a Belkin card, but this oen6.inf might work. I'd do some searching for that driver and see if you can't find a place to download it. When/if you get it downloaded put it with a bcmwl5.sys and install the oen6.inf and see if it goes through.

---

### Post by dmizer on 2008-06-19
hello,

just out of curiosity, is there a reason why it's necessary to compile ndiswrapper from source?  this creates a real headache for users who regularly update kernels, as they will have to recompile against each new kernel.

if it's possible to use the ndiswrapper version from the repositories, this would be far more preferable.

i'm asking because i see people having problems with 4306 card quite frequently, but i hesitate to point them to this howto because it involves compiling ndiswrapper from source.

---

### Post by NullHead on 2008-06-19
> **dmizer said:**
> hello,

just out of curiosity, is there a reason why it's necessary to compile ndiswrapper from source?  this creates a real headache for users who regularly update kernels, as they will have to recompile against each new kernel.

if it's possible to use the ndiswrapper version from the repositories, this would be far more preferable.

i'm asking because i see people having problems with 4306 card quite frequently, but i hesitate to point them to this howto because it involves compiling ndiswrapper from source.

A valid point you have there. Yes I think it would be acceptable if you used the package from the repositories. The problem is that this how-to is written for ubuntu 6.10,Edgy, witch is very old and no longer supported.

---

### Post by maclenin on 2008-06-29
**dmizer and NullHead:**

Valid points, all.

Re: the "very old" 6.10 ("EE") angle - I think the general flow of the guide still works - even for the most current releases. I've used it (successfully) with FF and it seems you've (**NullHead**) been able to use it with [_GG_]("http://ubuntuforums.org/showpost.php?p=3647159&postcount=309") and [_HH_]("http://ubuntuforums.org/showpost.php?p=4644002&postcount=373") - to similar effect.

As far as the repository/source question - if you folks can suggest a revised step (or steps) that addresses this issue (or any other), I'd be happy to test it for a guide that I will re-issue (into the new updated forum framework) when I finally make my leap to HH.

Incidentally, I have not found the [_re-compile_]("http://ubuntuforums.org/showpost.php?p=2144218&postcount=108") of ndiswrapper that big a challenge when I've had to update my kernel - perhaps I am missing your point, **dmizer**? 

Thanks for the comments.

---

### Post by dmizer on 2008-06-29
> **maclenin said:**
> Incidentally, I have not found the [_re-compile_]("http://ubuntuforums.org/showpost.php?p=2144218&postcount=108") of ndiswrapper that big a challenge when I've had to update my kernel - perhaps I am missing your point, **dmizer**? 

Thanks for the comments.

no, it wouldn't be a challenge if you know it needs to be done.

but, if someone blindly follows your howto (which is quite possible because it's well written), there's no way to know that ndiswrapper needs to be recompiled after a kernel update unless you're familiar with linux and what compiling is.

it's also easy enough if the person who followed your howto had the forethought to bookmark it for future reference.  but this is obviously not always the case.

usually what happens is that they spend a few frustrating hours trying to hunt down the howto they used before, end up trying a bunch of different things they run into along the way, and ultimately end up breaking things more.

so what they see is, "blast it all, the update broke my wireless!" then in a last bid for a fix, they post in the networking & wireless forum and make a new post entitled, "Hardy update breaks wirless!!!!" or "goodbye ubuntu: wireless AGAIN."

of course i'm exaggerating ... but only a little.

---

