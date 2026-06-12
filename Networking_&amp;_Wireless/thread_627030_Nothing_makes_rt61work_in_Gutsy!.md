---
title: "Nothing makes rt61work in Gutsy!"
date: 2007-11-29
forum: Networking &amp; Wireless
---

### Post by salviablue on 2007-11-29
Hi, I am a bit of a noob.
I (well, gutsy) have (has) this problem with connecting to the internet via wifi. I have tried all the different steps could find to make this work and I just can`t! Gutsy can see my wireless network, but just doesnt connect. 
I would like to point out here that the wifi works in Windows.
If I open Wireshark whilst trying to connect, the connection seems to get stuck at the `obtaining IP address` stage at which point the router does something to do with flush cache, fury (my laptop) and then boots me off and I have to try connecting again for another go.
*** Now the really stupid thing is that whilst at my inlaws I did something to break Gutsy (again, my fault though, I went mad installing random repositories that I thpught may be usefull!) and did a fresh install. After the fresh install I somehow managed to connect to their wifi router using network manager and by placing my MAC on their routers whitelist.  I did not alter anything to do with network, or wifi or owt like that (that I was aware of anyway) since the fresh install.****
 When I got back home I though I still had not internet. This may force me to try a different distro (although I like this one) although I have tried a few and my wifi doesnt seem to work with any of them!
I have tried all the network progs i can find with the different drivers compiled in different ways and non seem to work!
I have even tried setting my router to no firewall and no security key to no joy!
Can someone please try and help me!?

This cheap laptop doent help either!



P.S. I had always thought in the past that linux systems where made for networking. So I cant understand why one of the main functions of linux hasnt been worked on enough to ensure its compatability and flexability with everything network (especially considering how its virtually impossible to reasonably run linux w/out an internet connection)!?!?

Advent7201, Celeron M, rt61, Ubuntu 7.10 Gutsy.
Ive tried Network Manager, KWiFi Manager, RutilT, Network Selector, SWScanner, Wicd and another one I cant remember that kept crashing.
Trying to connect to an open, broadcasting and discoverable, WEP activated, no white or black list, Orange Broadband router.
Have tried various combinations with drivers aswell. I only havent tried wrapping the win drivers yet since I would like to wifi audit and the win drivers disable the monitor mode.

If any more info is needed I will try and provide. I will post the output of several methods tried (the breaking point) tomorrow as I am knackered now! TIA

---

### Post by toes22 on 2007-11-30
Hi there salviablue

  I had exactly the same problem and after a lot of scouting arround Ive managed to work out that the 
official ubuntu howto 
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61") 
for this driver is somewhat deprecated. After following the howto for the rt71 driver 
[http://ubuntuforums.org/showthread.php?t=400236]("http://ubuntuforums.org/showthread.php?t=400236") 
but changing every instance of 71 to 61 I managed to get it working really well. The main source of 
problems is leaving the old driver rt61pci working on the system this driver has to be blacklisted and the 
rt61 used instead. Ill try to put a small howto together here for anyone who needs it. These instructions 
are based on the preceding urls but with a few changes.

[LIST=3][*]Open a Terminal[*]Go to the directory where the source code will be kept
```
cd /usr/src
```
[*]Download the source code. (NOTE: because /usr/src is a privileged directory, prefix all commands with 
sudo from here on. Type "man sudo_root" for more information.)
```
sudo wget http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz -O 
/usr/src/rt61-cvs-daily.tar.gz
```
[*]Extract the archive you just downloaded.
```
sudo tar -xvzf rt61-cvs-daily.tar.gz
```
[*]If you do not have the Linux Kernel Headers and essential build tools install them with this command.
```
sudo aptitude install linux-headers-`uname -r` build-essential
```
[*]Change to the build directory and compile the sources. note: yyyymmddhh corresponds to the numbers 
found on the extracted directory.
```
cd /usr/src/rt61-cvs-yyyymmddhh/Module
sudo make
```
[*]If the module is too big, strip unnecessary stuff from it.

On some systems, the rt61 kernel module compiles to a file that is unnecessarily large. If this happens 
you will receive a warning like this:
```
!!! WARNING: Module file much too big (>1MB)
!!! Check your kernel settings or use 'strip'
```

If you want to make doubly sure, you can check the file's size by typing
```
ls -alh rt61.ko
```
If the file's size is in the megabytes, you are affected by this issue (it's not really a bug).

Luckily this is easily fixed, just type
```
sudo strip -S rt61.ko
```
[*]Install the module.
```
sudo make install
```
[*]Make sure neither the Ubuntu, nor the RaLink modules are loaded (the former doesn't work, while the 
latter causes conflicts). Some other modules need to be removed as well. Don't worry if your computer 
complains about these modules not being found - that's a good thing.
```
sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt61pci
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib
```
[*]Blacklist these modules, so that they aren't loaded on startup.
```
gksu gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
kdesu kate /etc/modprobe.d/blacklist (if you are using Kubuntu)
sudo nano /etc/modprobe.d/blaclist (if you know how to use the nano editor)
```
Add the following lines to the text file:  Note: not all these modules have to be blacklisted because they 
reffer to the rt73usb driver the most important is the rt61pci, this must go in the blacklist file.
```
# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 
module.
blacklist rt73usb
#Blacklist the Broken rt6pci driver
blacklist rt61pci
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib
```
[*]As root add the rt61 module to the /etc/modules file.
```
echo rt61 >>/etc/modules
```
[*] Load the new module.
```
sudo modprobe -v rt61
```
[*]Check whether your hardware is being detected.
```
ifconfig -a
```
[*]This command lists all networking devices on your PC. You'll probably find several entries here, "lo" will always be present, "eth0" will be present on most modern computers. Look for the entry "wlan0" or "wlan1". If you have a new entry that starts with "wlan", the kernel is now detecting your RT61 device and you can proceed to configure it. Note that from here on out, I assume that the interface name is "wlan0". If yours is "wlan1" or similiar, substitute that in place of "wlan0" below.
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0
```
Note insert your network essid where it says YOUR_NETWORK_NAME_HERE and your WEP key where it says YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY. Type "off" instead if you don't have a WEP key to secure your network. All this should be typed without quotation marks.
[/LIST]
The interface should now acquire an IP address now remains the job of setting up the network for boot time.
[LIST=1]
[*]Edit the /etc/network/interfaces file
```
gksu gedit /etc/network/interfaces (if you are using Ubuntu)
kdesu kate /etc/network/interfaces (if you are using Kubuntu)
sudo nano /etc/network/interfaces
```
[*]Look for a section containing "wlan0", if there is no such section, add the following to the bottom of the file:
```
auto wlan0
iface wlan0 inet dhcp

 pre-up ifconfig wlan0 up
 pre-up iwconfig wlan0 essid YOUR_ESSID
 pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE
```
[*] If you have it installed (you will if you are using dapper), remove network manager (!)
```
sudo aptitude purge network-manager
```
If you had a problem of the Internett dropping out intermintantly before this was because of the buggy rt61pci driver that created a dummy network device wmaster0 you should now notice after running ifconfig that this no longer exists. To manage the network you can now install wicd.or something similar.

For refference here is the /etc/network/interfaces file on my machine

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid default
pre-up iwconfig wlan0 key off
[/LIST]

There are many other options for the configuration of your network device, ie if you wish to use encryption etc. The best refference for the configuration is in the driver documentation itself.
```
kate /usr/share/doc/module/README
```
Go to the section "Wireless Station Configuration" about halfway down the page.

---

### Post by salviablue on 2007-12-01
Hi, thankyou very much for the reply. I thought I was the only one that had these extended problems.
I have followed the post up to step 11 where I get a `permission denied`, even if I sudo the command. Is this to do with permissions?

Also on the sudo make install I get a No such file or directory. Is this normal output for the make install?

jascas@FURY:/usr/src/rt61-cvs-2007113009/Module$ sudo make install
*** Install module in /lib/modules/2.6.22-14-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /usr/src/rt61-cvs-2007113009/Module/rt61.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
*** Update /etc/modprobe.conf alias for wlan*
grep: /etc/modprobe.conf: No such file or directory
*** Install firmware in /lib/firmware ...
*** Check old config ...

Again thankyou very much for taking the time to print this how to.

---

### Post by salviablue on 2007-12-01
I figured out the do from root thing. It means run a term as root i.e. 'gksudo xterm' doesnt it? Well it worked anyway (that bit).
 What I am stuck at now is that when requesting an IP address from the dhc whatsit, it seems to be asking on 255.255.255.255 but I think the dhc is on 255.255.255.0. How could I change this?
how does the dhcpdiscover decide on what address and port to request ip address 

jascas@FURY:/$ sudo dhclient wlan0
[sudo] password for jascas:
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)

Listening on LPF/wlan0/00:0d:f0:39:ed:2f
Sending on   LPF/wlan0/00:0d:f0:39:ed:2f
Sending on   Socket/fallback/fallback-net
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database.

Sleeping.

this is what I get on trying to obtain an ip address

---

### Post by salviablue on 2007-12-01
Sorry everyone and thanks for your help. But it just seems I have one problem after another and each time it seems to take me days to find out some one else has the same problem (well, its never quite the same) and they usually seem to find a fix. I try their fix to no avail, it usually seems as though it going to work until around the last step when my computer just doesnt do what everyone elses does! To me Gutsy just isnt compatible with the Advent 7201 laptop which runs the rt61wifi chipset and the Ati SB450 HDA sound chip set (the two things I just cannot get working no matter what I try) which works brilliantly in Vista. I think I may wait for a further reply on this before completely removing ubuntu and starting from scrath with someother distro. But what to try?

If anyone has any suggestions. Ive tried Fedora and cant get my wifi working, but then again i didnt try too hard on that. Free/Lin spire just doesnt even load on my laptop. Suse is slower than Vista, and BT2 cant even access my HDD for an install! So anything that uses gnome or a gnome like interface, can be used as a regular desktop, is quicker than windows and can have some nice eye candy like compiz (with which I have had no probs with whatsoever! Been running cubed desktops, blur, reflection, water effects, windows wobble etc since install)

Personaly I loved my time with Gutsy and I wish I didnt have to remove it, maybe I shall return when it works, but I really do not beleive that Ubuntu Gutsy is a distro to turn Window$ users. It looks great, works faster and is generally more flexible and less restrictive. BUT certain important essential things are too much of a pain to get working, or just dont work, especially the things where linux is so much better than Window$, ie networking (window$ disallows monitor mode in wireless for  a start). If the basic linux advantages where properly worked on then I think Ubuntu would be a serious contender for Vista but until then....

---

### Post by toes22 on 2007-12-03
hello again

  it seems to me youve managed to compile the drivers without a problem, the best thing to do is to do it all as root, ie
```
su root
insert your root password
```
the files created in the source directory should be installed as follows.
> 
/lib/firmware/rt2561s.bin
/lib/firmware/rt2661.bin
/lib/firmware/rt2561.bin
/lib/modules/2.6.22-14-generic
/lib/modules/2.6.22-14-generic/extra
/lib/modules/2.6.22-14-generic/extra/rt61.ko
/usr/share/doc/module/README

If you dont have those make the directories and place the files from the source into each directory.

It sounds to me like you are still using the old driver on your system if you run the command iwconfig and see a device there named wmaster0 you are not using rt61. if this is the case you have to isolate the driver that you are using and blacklist it so it doesnt work. This old driver is most probably rt61pci or rt61usb or some other flavour. when you have found the driver that Gutsy is trying to connect to wireless with blacklist it. bring the network down and unload the module.
```
ifconfig wlan0 down
modprobe -r rt61pci    <-(or whatever module you are using)
```
to blacklist the driver do the following.
```
echo "blacklist rt61pci" >>/etc/modprobe.d/blacklist
```
Now load the new module.
```
modprobe -v rt61
```
Now if you run iwconfig you will see that wmaster0 has disapeared and you will have in the list possibly lo, eth0, and wlan0. If this is the case when you try to configure the network as usual the internett will come up.
```
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid default    <-(might be another name besides default)
sudo iwconfig wlan0 key off         <-( read /usr/share/doc/module/README for more info)
sudo dhclient wlan0
```
Now open a browser and see if you can reach the internett.

Once you have established you can connect to the internett edit the /etc/network/interfaces file as follows
> iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid default
pre-up iwconfig wlan0 key off


Note: this interfaces file is only very basic youll have to read up on configuring WEP and other things for yourself. If all went well you should have a connection.

---

### Post by salviablue on 2007-12-03
Hi, thankyou very much for the reply.
   I went to a party last night, in rather a grumble du to wifi problems, and to my fortune there was a linux geek there (self proclaimed). I picked his brains and he asked me to check the resolve.conf file for a dns. On getting home I did, and there where none. I promptly added the IP of the router, ran through the command line ; sudo dhclient wlan0, lo and behold upon trying firefox i had a connection!
Thankyou very much for your help though as I am sure that your little recompiled guide got me to the very last hurdle.

I was thinking of starting a new thread with your guide but including that if no dhcp offers have been received then to check the resolve.conf file for dns. If your router does not have dns then to find some from the intrenet and insert into resolve.conf . This resolve.conf file may need to be automated at startup because i was told it gets overwritten at every dhcp request? (Or maybe I misunderstood that bit?)
What do you think?:lolflag:

---

### Post by salviablue on 2007-12-03
This is really pssssssng me off now! When I had the wifi working was at a mates house. Now I get home again it doesnt work! Now its telling me 

jascas@FURY:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                       Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)

wlan0: unknown hardware address type 801
IF_METRIC=100: ERROR while getting interface flags: No such device
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/<null>
Sending on   LPF/wlan0/<null>
Bind socket to interface: No such device
exiting.
Failed to bring up wlan0.
                                 

If i iwconfig

jascas@FURY:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     RT61 Wireless  ESSID:"Chaos"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:19:7D:CA:CB:D3
          Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:029F-204F-EC28-E933-4F8E-EC15-50
          Link Quality=75/100  Signal level:-64 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

if i dhclient

jascas@FURY:~$ sudo dhclient wlan0
Internet Software Consortium DHCP Client 2.0pl5
Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
All rights reserved.

Please contribute if you find this software useful.
For info, please visit [http://www.isc.org/dhcp-contrib.html](http://www.isc.org/dhcp-contrib.html)

wlan0: unknown hardware address type 801
wlan0: unknown hardware address type 801
Listening on LPF/wlan0/<null>
Sending on   LPF/wlan0/<null>
Sending on   Socket/fallback/fallback-net
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
Trying recorded lease 192.168.1.27
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database.

Sleeping.


What the hell is going on???? Why can connect to my freinds wifi router, which is identical - in router and setup- to mine, and connect at my inlaws - different router and setup - but not my own?!?!?!


PLEASE PLEASE HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!:confused:

---

### Post by toes22 on 2007-12-04
salviablue It looks to me like your network device is working well but the problem might be with the network. Are the network details for each location the same ie is your inlaws essid "Chaos" and is the encryption key you are using the same as well. :guitar:

---

### Post by salviablue on 2007-12-08
Hi, thanks for the continued support everyone.

I had set the essid and key and mode etc to what they should be in each location.ie. when at inlaws i set iwconfig to their essid, key. 
The setup at my mates house is the same as mine as in the orange router is set up identically other than for the essid, key, router to phone line login, external IP, BESSID (or what ever its called, the MAC

I would like to try and restore all the networking stuff back to how it would have been after a fresh install and then start again with this tutorial (as it seems to have got me further than any other!)

What tends to happen is that wicd or rutilt see the router and says its connected. From the command line iwconfig tends to show its connected to the router, sometimes it shows a decent link quality ~87%??
But still I never seem to be able to connect to the www??????

Regards

---

### Post by salviablue on 2007-12-08
Sorry, I meant to say that I would like to restore the networking stuff of Ubuntu....

---

### Post by salviablue on 2008-02-25
Hi, I have just realised after coming here for another problem (although long time on see!) that I never updated this thread and say how things worked out. Well, it may help someone else?!?

I did the whole installing the correct driver and attatching it to the correct device etc, as per  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) and changing all instances of rt71 to rt61.

I removed all wifi managers in aptitude and disabled network manager from starting at boot time.

added my router IP to resolv.conf

updated iwconfig with the ap whatnots (essid, wepkey etc) and did "/~ sudo dhclient wlan0" and waited for a dhcpack and bound to ip blah blah. (upon pressing return after entering "sudo dhclient wlan0" it spews some lines about "listening on blah : sending on blah : dhcpdiscover on wlan0 blah etc. Just have to wait for it to finish spewing lines (shouldnt take longer than say 10 seconds. If it does take longer, ctrl+c and start again.
:guitar::guitar:
I found I had to give the essid and wep key wassit info on every boot so I wrote a little script to automate that for me at each boot;

#!/bin/sh
# This script will auto-connect the computer to the router wirelessly (WiFi)
# This will only work with WEP encryption. WPA_Supplicant has to be installed and then added to this script for WPA encryption to work (not quite got there yet!)
# Juan Stoneley 10/01/08

script_name="online.sh"

#script must be run as root
if [ $USER != "root" ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

sudo iwconfig wlan0 essid Chaos
sudo iwconfig wlan0 key <your wep key here>
sudo iwconfig wlan0 channel 1
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

save the script as "online" in /home/<user>/
After boot up just go into a terminal and type "sudo sh online" and cross your fingers!

The script is probably very bad and no doubt someone will correct it/make it better (hopefully!) but it is my first bash script (first script ever infact!).

Hoped this has helped

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

