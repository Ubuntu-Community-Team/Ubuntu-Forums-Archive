---
title: "New RT73 Wireless Driver Installer Script"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by zszafran on 2008-07-03
**Notice: This script was written and tested on Ubuntu Hardy 8.04 and was later tested on a clean/fresh install of the same version.**

This is a simple bash script that will automatically install drivers for any wireless device using the RT73 chipset from RALINK.

This script was based off the one posted here: [http://ubuntuforums.org/showthread.php?t=757607]("http://ubuntuforums.org/showthread.php?t=757607") by Kiefer Rodriguez. This script was completely rewritten with some bug fixes and new features.

**Script Name:** RT73 Wireless Driver Installer
**Language:** Bash
**Distro:** [U/Ku/Edu]buntu 8.04
**Script Version:** 1.0
**Script Author:** Zach Szafran
**Last Update:** July 03, 2008

**Instructions:**
Download the attached .tar.gx and extract the contents of the archive to any directory. Open terminal and navigate to the directory that contains the install-rt73.sh script. Run the command:	
```
sudo sh install-rt73.sh
```

Answer the five prompts that the script displays and then sit back and let the script do the rest.
[COLOR="Red"]
**NOTE:** You may notice that the section "Checking for module source" fails. This is nothing to worry about, it just means that the script was unable to find a pre-downloaded tar.gz archive of the drivers and the next step will attempt to download the archive.[/COLOR]

If you answered yes ("y") in regards to having an active internet connection, then this script will attempt to download the latest version of the drivers. If you do not have an internet connection then go to [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) and download the .tar.gz into the same directory as this script. 

This script also attempts to download and install the packages "build-essential" and "linux-headers...", and without an active internet connection you will need to insert your ubuntu cd. This script will prompt you for the correct time to put the cd in and will automatically detect it and add it to your package manager sources.

**Supported Devices:**
The following is a list of devices that are supported by the rt73 driver. There are probably other devices that are not listed here. 
[LIST]
[*] Asus WL-167g
[*] Sitecom WL113 v1-002
[*] GW-US54HP
[*] D-Link DWL-G122
[*] Digitus DN-7003GR (VPR 1.0)
[*] Belkin F5D7050 Ver 3
[*] Hawking HWUG1
[*] Linksys WUSB54GR
[/LIST]

**Screenshot:**
[IMG]http://i26.tinypic.com/2a4qtxj.png[/IMG]

---

### Post by heinorr on 2008-07-09
Thanks for the good work. Before I had to do these steps by hand for gutsy. 
There remains one problem: Your script does not seem to work with WPA encryption. So I added some lines to the interfaces file. 
More precisely, open a terminal and enter:
```

sudo gedit /etc/network/interfaces

```
If you haven't done anything, but have a ethernet card in your PC, it might look like this:

```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp
```

Then enter the following lines (assuming you entered "wlan0" for the device name when running zszafran's script) and change the arguments with a '$' sign to suit your needs.
```


auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 mode managed 
	#pre-up iwconfig wlan0 channel $CHANNEL_NUMBER
	pre-up iwconfig wlan0 essid "$NETWORK_NAME"
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK="$PASSWORD"
	dhclient wlan0

```
Note: Specifying the channel number is not required but may help sometimes.
You can test if things work by running
```
sudo /etc/init.d/networking restart

```
If this connects, then it should also work after  a reboot.

---

### Post by zszafran on 2008-07-09
Thats something that I completely forgot about. Thanks for pointing this out and thanks for the examples. The next version of this script will probably have some advanced option for configuring this or something.

---

### Post by samwisgg on 2008-07-13
Heinorr (& zszafran),
thank you for this script and the appropriate update !

It took me quite a while to get my wireless lan (via D-link DWL G122 rev. C1 dongle) working but thanks to you guys it does. I hope that some day this would all be compiled into one comprehensible HOW-TO since there are countless threads out there related to wireless subjects for all kinds of versions of Ubuntu.

There is one little problem I still have that I would like to be solved. When I boot my computer my wireless does not start up. I have each time to execute 'sudo /etc/init.d/networking restart' after startup and then my wireless works. This is kind of annoying. This problem only occurs under Ubuntu since my dual boot PC does not have the issue with XP. 

After looking into syslogd I noticed my router (D-LINK DI-524) does not get its IP address via DHCP at startup. It states 'DHCPDISCOVER' a couple of times and then gives up. If I do a restart of the network, I can see the same DHCPDISCOVER appear but it finally gets its IP address via a DHCPOFFER (although sometimes it doesn't neither and then I again have to do a restart of the network).

Looking on other threads I found no solution and tried all kinds of combinations by shutting down services at boot up (such as AVAHI).

Any suggestions ?

Thanks

---

### Post by jtbalt on 2008-07-20
Any ideas anyone...?

 Checking for module source                                             [done]
* Copying rt73 module .tar to /usr/src                                   [done]
* Changing directory to /usr/src                                         [done]
* Unpacking rt73 module in /usr/src                                      [done]
* Changing directory to /usr/src/rt73-cvs-2008072021/Module              [done]
* Installing headers                                                     [done]
* Building module                                                        /usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutDataPacketComplete’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:107: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:107: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:121: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:121: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutMLMEPacketComplete’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:322: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:322: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutDataPacket’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:569: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:569: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:570: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:570: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutNullFrame’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:683: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:683: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutRTSFrame’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:753: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:753: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutMLMEPacket’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:812: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:812: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c: In function ‘RTUSBBulkOutPsPoll’:
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:872: error: incompatible type for argument 1 of ‘_spin_lock_irqsave’
/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.c:872: error: incompatible type for argument 1 of ‘_spin_unlock_irqrestore’
make[2]: *** [/usr/src/rt73-cvs-2008072021/Module/rtusb_bulk.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2008072021/Module] Error 2
make: *** [module] Error 1
[fail]
* Installing module                                                      make: *** [modules_install] Error 1
[done]
* Removing obsolete modules                                              [done]
* Making a backup of modprobe blacklist                                  [done]
* Writing to modprobe blacklist                                          [done]
* Verifying rt73 driver                                                  FATAL: Module rt73 not found.
[done]

---

### Post by heinorr on 2008-07-23
@ samwisgg

sometimes I also encounter this problem, when there hasn't been
sufficiently much time between turning on the wireless router and
booting ubuntu. So then the router appears to be not ready yet.
Do you have your wifi network turned on all the time?
In that case, it also happens on say 5% of the days that I can't get an
IP, so I try

sudo /etc/init.d/networking restart

a handful of times until it works. There are a lot of networks around at
my place, don't know if that has something to do with it.

If your rt73 never connects during bootup, but always after you are
logged in, why not try to run an automatic startup script that does the job?

Let us know if you have problems setting that up.


@ jtbalt:

my quick idea would be to try again today, maybe the latest driver that was downloaded by the script contained a bug. If it fails again, I attached the serialmonkey driver that worked for me from about two weeks ago.You could run zszafran's script again and tell it you are offline, using the attached file.
A bug appearing on the latest version is not uncommon, happened to me last time with  gutsy as well. 

Good luck

---

### Post by escipio on 2008-07-26
Hello:

I have the same problem as samwisgg. And the problem persists even if a reinit the computer with the router switched on hours ago.
Probably the script would work, but I would prefer knowing why it does not connect. I tried also giving static ip to avoid the problem of the response from the router, but still no ip, and then no net.

Any idea of what the problem could be?

Thank you in advance.

---

### Post by heinorr on 2008-07-27
hey escipio,

do I understand correctly: You *can* connect to your wireless network, but only by hand after booting?
If so, I have no idea why, but I can only repeat my advice to include 
sudo /etc/init.d/networking restart
in your personal startup script. As an alternative, using the programm rutilt might help. This also gives you a graphical output of connection quality etc.

---

### Post by jtbalt on 2008-07-27
Woooo Hoooooooooooo!

I got it working.  The script (for whatever reason) finally ran and gave me good results all the way down.  I'm using WPA encryption on my router and Hardy 8.04 as my OS.  I had to put all the following in my interfaces file as follows:

sudo gedit /etc/network/interfaces

Then add the following (without removing anything that was already there):

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EnrypType=TKIP
pre-up iwpriv wlan0 set NetworkType=Managed
pre-up iwconfig wlan0 essid my_ssid_was_put_here
pre-up iwpriv wlan0 set WPAPSK=my_key_was_put_here

I restarted networking using:

sudo /etc/init.d/networking restart

and I'm in business.  I also created a file on my desktop and placed the restart command above into it, so if/when the wireless connection dropped out I could simply double-click the restart icon and reconnect it.

Thanks guys:)

---

### Post by escipio on 2008-07-28
Hi heinorr,

thank you, very much, for your help. The problem is that sometimes, when I switch on the computer, it is connected to the net, and sometimes not. If it is not connected, I solve the problem with "sudo /etc/init.d/networking restart".

I tested to put it in "system-> preferences-> sessions", in order to restart allways the net, but even so, sometimes it is connected and sometimes not.

In any case, I would like to know where is the problem.

Thnak you.

---

### Post by Gene_s on 2008-08-01
Can someone translate this into English please? I have a Hawking HUWG1 but cannot understand all the commands.

thanks, Gene

---

### Post by samwisgg on 2008-08-03
All,

I finally got things working ... After tree weeks (not continously but during all of my limited spare time) of trial & error, searching and sweating :) my D-link DWL-G122 (rev. C1) connects automatically at boot time using WPAPSK security in Ubuntu Hardy Heron. Since this might be helpful to others I'll try to put what I did in a logical order (I'm no complete linux newbie but I'm not a guru either so comments are always welcome). 

1) First check your chipset : this post only handles the rev. C1 of DWL-G122 which uses the rt73 ralink chipset. If you type 'lsusb' in terminal window, you should have a line containing 'ID 07d1:3c03'. I think that for other revisions (A,B,D) you should use the windows driver and the ndiswrapper linux utility but I have (luckily) no experience with this.

2) The network manager under gnome (and thus in Ubuntu) is known not to support the rt73 chipset (as stated on the gnome/network manager website) and, even worse, it is best to just remove the package all together :
```
sudo aptitude purge network-manager
``` or remove it via the GUI (synaptic pakage manager)

3) Download the script provided in this thread and run it

4) Alter the interfaces file via 'sudo gedit /etc/network/interfaces'. Here you have two options:
4a) Bring up your network interface (in my case wlan0) specifying the following syntax :
```
auto wlan0
iface wlan0 inet dhcp
	pre-up iwconfig wlan0 mode managed 
	pre-up iwconfig wlan0 channel 6
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK="Enter your key here"
	pre-up iwconfig wlan0 essid "Enter your essid here"

```
4b) Bring up the wlan0 interface via RutilT, a cool utility (thanks to Romain) you can download on the [http://rt2x00.serialmonkey.com]("http://rt2x00.serialmonkey.com") website and used to configure the rt73 (both also others). You should first run the utility to make a "profile" file "RutilT_profiles.xml" and copy this file (as root) from ~/.config/rutilt to /root/.config/rutilt.
After that you should specify the following section in /etc/network/interfaces :
```
iface wlan0 inet manual
	pre-down dhclient -r wlan0
	up HOME=/root rutilt wlan0 -dep "Enter name of your profile here"

```

5) Type the following in a terminal window :
```
sudo /etc/init.d/networking restart

```**You should be in business now !**
But ... next time you reboot you will probably notice your wireless connection doesn't work :confused:. When you call again the networking script with the restart option ... it works again ! So you proceed to the next step :)

6) We will now add the restart script to the scripts run at boot time. Without going into detail, I can tell you a script '/etc/rc.local' exists that is run by default as the last script on start-up. The script file only contains the command 'exit 0'. You can add the following line _before_ this command :
```
/etc/init.d/networking restart

```
To be sure the rc.local script is executable, type :
```
sudo chmod +x /etc/rc.local
```So now everything should work at start-up. If you want a visual in gnome on the state of your wireless connection you can optionally execute step 7 (you'll need the rutilt utility for this).

7) Under System-> Preferences -> Settings add a new program to start using the command 'rutilt -t'. 

Some (more advanced) side remarks :
- Theoretically the command '/etc/init.d/networking start' should work but in practice it doesn't. Why you first have to bring down the interface (ifdown) and then up again (ifup) via the restart option is still a mystery to me.
- I've seen people code 'pre-up iwconfig wlan0 up/down' sequences. I understand this is to simulate the up/down cycle you also have with restart. I find this very confusing : why do you want to bring up an interface BEFORE you bring up the interface (=meaning of the pre-up command) ?
- In my system I found out that the networking script was never called during start-up sequence (no wonder my connection wasn't up at boot time). You only find it in single user run level (S) and since ubuntu (at least in my case) boots in run level 2 ...

Hope this is helpful to some folks,

Regards,

Samwisgg

---

### Post by TheTank on 2008-08-05
Hi all.
I have been having some problems getting my system set up and after trying this script (worked well from what I could tell) I am still having problems.

We want to replace lan with wlan in our appartment.
I have a Speedport W 500V router/modem set up with a static ip, dhcp and the wlan is also set up with ssid 'TeletubbieLand', 'WPA / WPA2 with Pre-shared key' and channel 11.

I still have both the lan and the wlan attacked because I kinda need the net to read the forums for help.

I was able to get the connection running as far as I can tell:
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:"TeletubbieLand"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 01:23:45:67:98:10   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=79/100  Signal level:-60 dBm  Noise level:-99 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ifconfig:
```

eth0      Link encap:Ethernet  Hardware Adresse 00:11:22:33:44:55  
          inet Adresse:192.168.0.13  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::204:61ff:fe43:6bf9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:33742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31105 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:27949572 (26.6 MB)  TX bytes:4168749 (3.9 MB)
          Interrupt:10 Basisadresse:0xe000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2469 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:138536 (135.2 KB)  TX bytes:138536 (135.2 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 01:23:45:67:98:10  
          inet6-Adresse: fe80::21e:58ff:fea1:ef99/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5767 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:820660 (801.4 KB)  TX bytes:1202 (1.1 KB)

wlan0:avahi Link encap:Ethernet  Hardware Adresse 01:23:45:67:98:10  
          inet Adresse:169.254.9.107  Bcast:169.254.255.255  Maske:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.0.13
netmask 255.255.255.0
gateway 192.168.0.3

auto eth0

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up iwconfig wlan0 mode managed 
	pre-up iwconfig wlan0 channel 11
	pre-up iwconfig wlan0 essid "TeletubbieLand"
	pre-up iwpriv wlan0 set AuthMode=WPAPSK
	pre-up iwpriv wlan0 set EncrypType=TKIP
	pre-up iwpriv wlan0 set WPAPSK="**************************"
	dhclient wlan0

```

but when the dhclient runs I only get:
```

Listening on LPF/wlan0/01:23:45:67:98:10
Sending on   LPF/wlan0/01:23:45:67:98:10
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Can anyone help me out?

Also, if I wanted to configure a static ip for the wlan, how would I do that?

Thanks!

---

### Post by samwisgg on 2008-08-06
TheTank,

which version of Ubuntu you're on ?

After you've booted, try the following :

sudo /etc/init.d/networking restart

Tell me if dhcp still times out.

Regards,

---

### Post by Les Ped on 2008-08-08
I am having difficulty making the script work.  I'm a newby.
Here are the particulars.  Please point me in the right direction.
"System: IBM 2139 SE7, Intel 440BX, Pentium II 450; ASUS wl-167g, 1723; Ubuntu  2.6.24-19-generic #1 (sole OS, no win)

 
"First attempt that partially completed 08/08/2008, used Heron iso CD when directed by script"

lester@lester-aptivadt:~/Usbwldrv$ sudo sh install-rt73.sh
[sudo] password for lester: 

Ralink rt73: Driver Installer - by Zach Szafran

Please enter your intended AP name (e.g. 'netgear' or 'HomeConnection') : layzaypere

Please enter the WEP key for layzaypere (or type 'off' if there isnt one) : -------------------------7

Please enter your package manager (e.g. 'apt-get' or 'aptitude') : apt-get

Do you currently have an active internet connection? [y/n] : n

Enter the interface name for the device to activate (e.g. 'wlan0' or 'wlan1') : wlan0


* Checking for module source                                             [done]
* Copying rt73 module .tar to /usr/src                                   [done]
* Changing directory to /usr/src                                         [done]
* Unpacking rt73 module in /usr/src                                      
gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
[done]
* Changing directory to /usr/src/rt73-cvs-2008080813/Module              [done]
* Waiting for Ubuntu CD in CDROM                                         [done]
* Adding Ubuntu CD as source to package manager                          [done]
* Updating package manager's sources                                     W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntu-rocks.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[done]
* Installing headers                                                     E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[done]
* Building module                                                        make: *** No targets specified and no makefile found.  Stop.
[fail]
* Installing module                                                      make: *** No rule to make target `install'.  Stop.
[done]
* Bringing down wireless device                                          [done]
* Removing obsolete modules                                              [done]
* Making a backup of modprobe blacklist                                  [done]
* Writing to modprobe blacklist                                          [done]
* Verifying rt73 driver                                                  FATAL: Module rt73 not found.
[done]

---

### Post by TheTank on 2008-08-09
> **samwisgg said:**
> TheTank,

which version of Ubuntu you're on ?

After you've booted, try the following :

sudo /etc/init.d/networking restart

Tell me if dhcp still times out.

Regards,
Sorry for forgetting to mention it. I am using 8.04

As soon as I hook up my WLAN again I will try that.

Thanks!

---

### Post by TheTank on 2008-08-11
Hello again.

Well I got it working with dhcp.

But what I would also like is a static ip because the DHCP server on my wlan router does not seem to have the possiblity of reserving special ips.

thanks for all the help sofar!

---

### Post by TheTank on 2008-08-12
Slight correction:
If I leave my USB dongle plugged in and restart, it gets mapped to wlan1 and then DHCP does not work, regardless of how many networking restarts.

If I unplug it and then plug it back in, it gets mapped to wlan0 (and I change the interfaces) and a networking restart gets me a DHCP.

Can anyone help me out?

---

### Post by Kiefer Rodriguez on 2008-08-16
Zach,
Looks like good work, I never managed to get around to updating the script as I had some dramas in my life that took precedence. I am more than happy to link my current RT73-Ins. Script to this post.
Though I do have one quarrel, You will notice that my work is under a license, that license states that you are free to re-distribute, copy, edit, whatever to my work, on the condition that my name remains. I noticed you snipped some stuff from my post/readme -- so I am going to have to ask you to place my name AND "diepruis" (who wrote the original guide that this script is based on) in either a AUTHORS file, or along yours in the README.
Other than that, great work, keep it up mate.

Kiefer Rodriguez.

---

### Post by TheTank on 2008-08-17
Hello again.

I figured out why my wlan was always being mapped to wlan1 and not wlan0.

As I had previously tried wlan with a different usb dongle it was mapped to wlan0 and the second one was mapped to wlan1.

This topic helped me fix it:
[http://fixunix.com/ubuntu/508804-make-wlan1-wlan0.html](http://fixunix.com/ubuntu/508804-make-wlan1-wlan0.html)

I hope it will help others as well.

---

### Post by TheTank on 2008-08-25
Only current problem is that my wlan dongle stops working after some time.
Possibly due to idleing?

---

### Post by Faggotry on 2008-08-30
I tried this script on a fresh install of ubuntu server 8.04, I didn't configure the network/dhcp on install.

I start the script, select name (the internet), wep key (off),( apt-get).
When I select "n" when it ask for active internet connection i get:
"read: 47: INTE}***P**]**T*X*: bad variable name
install-rt73.sh: 48: *: not fount
install-rt73.sh: 49: T*TT**: not found
install-rt73.sh: 4: Syntax error: Unterminated quoted string"
* = strange diamond-shaped character

What does this mean?

---

### Post by TheTank on 2008-09-03
Me again.
I bought a new computer and installed hardy on it. As I can now only use wlan I copied the two files as directed to my usb drive and then to my new pc.

I'm using the same USB dongle as before and have also copied my interface file.

When I run the script it mostly work (sometimes problems are declared but it still works).
This seems to work fine and I have to reconnect my USB dongle and then to a networking restart and I am off and running.

Problem is when I reboot, everything is gone again.
And in the restricted drivers window I can see that it is available but not used. If I want to use it I need to reboot and then it is gone again.

I also tried using the way above and then once I have I-net connection to redo it and then use the remote files.
Also did not work but actually failed because it claims rt73.do (or something like that) was not a correct module.

Question:
Does the rt73 have to be in the /etc/modules? Because it was missing in mine.

Also one suggestion:
Every time I run the script it wants either an INet connection or the CD, even though I have already installed all the required features.
Maybe you can add this as an option?

---

### Post by TheTank on 2008-09-03
Fixed:
Seems as though due to some strangeness in my console (special chars were getting printed as their values like \233) the entries in blacklist were not being written in correctly. i.e. the \n were in plain text form.

---

### Post by Kiefer Rodriguez on 2008-09-18
Okay, so I actually have gotten round to updating my original script, so anyone who isnt comfordable with the terminal should head over and check out the [**[COLOR="Blue"]RT73 Driver GUI Installer[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=923387").

Seeing as the newcomers love a GUI :P

-Kiefer

---

### Post by gnusci on 2008-09-18
Thanks zszafran work just great.... I writing you from my new Ubuntu Hardy connected via rt73 wlan.... Wow... Ubuntu Rocks....

---

### Post by chitek on 2008-11-12
Hi 
I tried running the script and this is what I got
* Checking for module source                                                          [fail]
* Attempting to download source                                                       [done]
* Copying rt73 module .tar to /usr/src                                                [done]
* Changing directory to /usr/src                                                      [done]
* Unpacking rt73 module in /usr/src                                                   [done]
* Changing directory to /usr/src/rt73-cvs-2008111211/Module                           [done]
* Installing headers                                                                  [done]
* Building module                                                                     WARNING: "there_is_no_init_MUTEX_LOCKED_for_RT_semaphores" [/usr/src/rt73-cvs-2008111211/Module/rt73.ko] undefined!
[done]
* Stripping driver file                                                               [done]
* Installing module                                                                   [done]
* Removing obsolete modules                                                           [done]
* Making a backup of modprobe blacklist                                               [done]
* Writing to modprobe blacklist                                                       [done]
* Verifying rt73 driver                                                               FATAL: Error inserting rt73 (/lib/modules/2.6.24-21-rt/extra/rt73.ko): Unknown symbol in module, or unknown parameter (see dmesg)
[done]

---

### Post by Gotit on 2008-11-15
Hi,
I see the first post says this scipt supports the Linksys WUSB54G**[COLOR="Red"]R[/COLOR]**, but by chance, has anyone tried this script with a Linksys WUSB54G**[COLOR="Red"]C[/COLOR]**? 
Thanks

---

### Post by weaver4 on 2008-11-17
Will this script work on 8.10 as well?  Or does 8.10 require the script at all?

---

### Post by weihaichao on 2009-07-06
[hello zszafran:]("http://ubuntuforums.org/member.php?u=236697")
ask for help please!
what is up with the below:

 Checking for module source                                             [fail]
* Attempting to download source                                          [fail]
* Copying rt73 module .tar to /usr/src                                   cp: cannot stat `rt73-cvs-daily.tar.gz': No such file or directory
[fail]

please! thank you!

---

### Post by grey1beard on 2011-01-03
> **weihaichao said:**
> [hello zszafran:]("http://ubuntuforums.org/member.php?u=236697")
ask for help please!
what is up with the below:

 Checking for module source                                             [fail]
* Attempting to download source                                          [fail]
* Copying rt73 module .tar to /usr/src                                   cp: cannot stat `rt73-cvs-daily.tar.gz': No such file or directory
[fail]

please! thank you!

Trying to install a TL-WN321G/RT73 driver with this method and get exactly the same result.

I've tried having the tar folder in the same directory as the Install RT73 or one directory higher, but it makes no difference.
I came here after trying Kiefer's GUI method, but getting stuck at the 65% mark, like other people.

John

---

### Post by grey1beard on 2011-01-03
Breakthrough - it's the compressed file that needs to be in the same directory as the script, NOT the uncompressed files. Doh !
Eight attempts at doing it before the penny dropped.
John

---

### Post by grey1beard on 2011-01-04
> **TheTank said:**
> Hello again.

I figured out why my wlan was always being mapped to wlan1 and not wlan0.

As I had previously tried wlan with a different usb dongle it was mapped to wlan0 and the second one was mapped to wlan1.

This topic helped me fix it:
[http://fixunix.com/ubuntu/508804-make-wlan1-wlan0.html](http://fixunix.com/ubuntu/508804-make-wlan1-wlan0.html)

I hope it will help others as well.

I've just tried this method, but permission is denied when I try to save either a re-named copy as a back-up, or, more usefully, when I try to save an edited version.
I'm running 8.04, and have got the usb dongle responding, but the conflict from an older attempt is, I think, preventing me getting a wireless connection.

Very grateful if anyone could advise this elderly newbie.
John

---

