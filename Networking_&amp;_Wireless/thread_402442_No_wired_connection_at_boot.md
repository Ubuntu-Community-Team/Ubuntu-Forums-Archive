---
title: "No wired connection at boot"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by BobK on 2007-04-05
Complete noob discovering the wonderful world of Ubuntu!  When I boot Feisty my wired ethernet connection is not connected. I have to click on the network icon next to the volume control, a drop down box appears and I have to click the button labeled Wired Network to get the connection started.  Can that connection start automatically at boot?

Worked through an annoying monitor resolution/refresh issue today!  This is fun.  :)

---

### Post by dannyboy79 on 2007-04-05
post the output these commands, just copy and paste the output after you enter the command in a terminal. terminal is located under the "start" menu, then accessories.

sudo ifconfig -a

cat /etc/dhcp3/dhclient.conf

cat /etc/network/interfaces

cat /etc/resolv.conf

ls -la /etc/init.d/ | grep networking

NOTE: if any of the commands won't let you do it, then use sudo in the front of the command. ie: sudo cat /etc/network/interfaces


also, when you first boot up, I also would like o know what this outputs from the command line also. so you'll need to shutdown, then restart, and don't do anything else but open a terminal and do this:

dmesg | grep eth

and 

dmesg | grep Eth

when you post back please make sure you provide all the info I have asked for.

---

### Post by BobK on 2007-04-06
THANKS for the help.  I followed your instructions to the letter.  Note:  this is an ancient machine I use just for kicks and to learn Ubuntu.  It's a PIII 450MHz w/ 384Meg ram...but it works great with Ubuntu (and PCLinuxOS too).  Below is what I have assembled from your questions.  Please let me know if you need anything else...and thanks again.

With a live network connection first:

sudo ifconfig -a
**********************Results**************************************
eth0      Link encap:Ethernet  HWaddr 00:20:78:E0:84:DB  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::220:78ff:fee0:84db/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:16510 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12424 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:1782 txqueuelen:1000 
          RX bytes:21440878 (20.4 MiB)  TX bytes:3669718 (3.4 MiB) 
          Interrupt:5 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:50937 (49.7 KiB)  TX bytes:50937 (49.7 KiB) 
******************************************************************************

cat /etc/dhcp3/dhclient.conf
******************************Results***************************
# Configuration file for /sbin/dhclient, which is included in Debian's 
#       dhcp3-client package. 
# 
# This is a sample configuration file for dhclient. See dhclient.conf's 
#       man page for more information about the syntax of this file 
#       and a more comprehensive list of the parameters understood by 
#       dhclient. 
# 
# Normally, if the DHCP server provides reasonable information and does 
#       not leave anything out (like the domain name, for example), then 
#       few changes must be made to this file, if any. 
# 

send host-name "<hostname>"; 
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c; 
#send dhcp-lease-time 3600; 
#supersede domain-name "fugue.com home.vix.com"; 
#prepend domain-name-servers 127.0.0.1; 
request subnet-mask, broadcast-address, time-offset, routers, 
        domain-name, domain-name-servers, host-name, 
        netbios-name-servers, netbios-scope; 
#require subnet-mask, domain-name-servers; 
timeout 30; 
#retry 60; 
#reboot 10; 
#select-timeout 5; 
#initial-interval 2; 
#script "/etc/dhcp3/dhclient-script"; 
#media "-link0 -link1 -link2", "link0 link1"; 
#reject 192.33.137.209; 

#alias { 
#  interface "eth0"; 
#  fixed-address 192.5.5.213; 
#  option subnet-mask 255.255.255.255; 
#} 

#lease { 
#  interface "eth0"; 
#  fixed-address 192.33.137.200; 
#  medium "link0 link1"; 
#  option host-name "andare.swiftmedia.com"; 
#  option subnet-mask 255.255.255.0; 
#  option broadcast-address 192.33.137.255; 
#  option routers 192.33.137.250; 
#  option domain-name-servers 127.0.0.1; 
#  renew 2 2000/1/12 00:00:01; 
#  rebind 2 2000/1/12 00:00:01; 
#  expire 2 2000/1/12 00:00:01; 
#} 

******************************************************************************

cat /etc/network/interfaces
***************************Results*********************************
auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

auto eth1 
iface eth1 inet dhcp 

auto eth2 
iface eth2 inet dhcp 

auto ath0 
iface ath0 inet dhcp 

auto wlan0 
iface wlan0 inet dhcp 

********************************************************************************

cat /etc/resolv.conf
**************************Results**********************************
# generated by NetworkManager, do not edit! 

search cable.bardstowncable.net 


nameserver 209.215.186.2 
nameserver 209.215.186.20 

***************************************************************************
ls -la /etc/init.d/ | grep networking
********************************Results**************************
-rwxr-xr-x   1 root root 1725 2006-11-27 08:32 networking 



NOTE: if any of the commands won't let you do it, then use sudo in the front of the command. ie: sudo cat /etc/network/interfaces


also, when you first boot up, I also would like o know what this outputs from the command line also. so you'll need to shutdown, then restart, and don't do anything else but open a terminal and do this:

On a fresh boot without touching the network connection:

dmesg | grep eth
**************************Results********************************
[   39.684483] eth0: Macronix 98715 PMAC rev 37 at Port 0xec00, 00:20:78:E0:84:DB, IRQ 5.

[   84.549256] eth0: no IPv6 routers present


and 

dmesg | grep Eth
**********************************Results**********************
didn't return anything, just went back to my login line &#8220;bob@PenguinBox:~$&#8221;
*************************************************************************

when you post back please make sure you provide all the info I have asked for.

---

### Post by BobK on 2007-04-06
OK, how that smiley got in there is a mystery!!!  That line really says:

eth0      Link encap:Ethernet  HWaddr 00:20:78:E0:84:DB

---

### Post by BobK on 2007-04-06
That's maddening.  manually entered:

00:20:78:E0:84:DB

Let's see if that evokes a smiley.

---

### Post by BobK on 2007-04-06
last two characters in that MAC address are D and B.

---

### Post by dannyboy79 on 2007-04-09
ok, sorry took so long. i would like you to first back up your /etc/network/interfaces file:

**sudo cp /etc/network/interfaces /etc/network/interfaces-backup**

then I want you to edit it. (NOTE: if you use gnome this will work, Xubutnu should use mousepad and kubuntu i think it's Kate you should use. all it is a text editor.

**gksudo gedit /etc/network/interfaces**

now please delete all the interfaces that you don't need. so all your interfaces file should look like is this:

auto lo 
iface lo inet loopback 

auto eth0 
iface eth0 inet dhcp 

DONT forget to save before you close. Are those dns server's in resolve.conf correct, the 209.... numbers???? Also, when you look inside the /etc/init.d/ folder, what numbers does networking have?? OR do you use Network Manager????  If you don't use Network Manager (i say this because I am told that network manager starts your networking for you and you don't need to use the networking script within init.d) than I would like to try to remove the networking from booting and then re-add it. This should make sure that networking starts up during first bootup. copy and paste it exactly:

**sudo update-rc.d -f networking remove**

and then do this otherwise it won't work.

**sudo update-rc.d networking defaults**

If that doesn't work than sometimes setting a static IP address has cleared up similar situations. Just don't chose the same ones that a dhcp computer might get. let me know how it goes. if this doesn't work, I am not sure why, but there is one more thing we can do. we can have a script run right after the system is up. we'd make it shutdown your eth0 interface with ifdown and then start it back up with ifup. this is basically the same thing you do thru the gui by disabling eth0 and enabling it which you stated ends up making your internet work.

---

### Post by BobK on 2007-04-09
No problem on the reply!  This is not my main computer today so it's NO problem at all.  Thanks for the help!!!

I did the backup as you suggested and opened the interfaces file and deleted all the other interfaces except as you showed in your instructions. I saved the file and rebooted at that point to see it just that would solve anything.  No joy.  Ubuntu still came up with showing no connection.  I checked the dns numbers you asked about...they are exactly the same on my Windows machine.  I think that might have something to do with the ISP/cable company relationship.  I get my signal from the local cable company "Bardstown Cable Internet" who owns the wires BUT my actual service comes through another ISP, "Bardstown Internet Service", in town who "rent" the cable ISP wires.  I started off with Bardstown Internet Service when I only had dialup available so I kept that option when they became available via the cable TV system here.  Maybe that 209 number is some kind of handshake between the two ISP's?  Not sure.

Being too much of a noob I'm not sure how to look into the init.d folder.  Can you help with some instructions?  I tried a few ways, gedit tells me init.d is a directory.

If I right click and go to "About" on the network icon in the tray in the upper right hand corner of my screen I can see this is indeed NetworkManager Applet version 0.6.4 running there.  If I left click on the icon it allows me to click a button either connecting or disconnecting the connection.

To your last comment on the ifdown, ifup idea.  When Ubuntu finally loads the Network Manager icon in the tray shows the two computers with an exclamation point next to them.  I simply left click in the icon and a drop down box appears with an open circle next to "Wired Network". I simply click in the circle to "mark" the button and the connection starts itself.  I don't have to take it down then up.  It is down to begin with and with one click I can bring it up.

This connection issue is not a deal breaker for me, I already love Ubuntu.  THANK YOU for the help!!

I see you are in Milwaukee, I end up staying in a hotel on Lovers Lane when I go to Oshkosh during the fly-in and I used to call on Midwest Airlines at the airport years ago!!!  Nice town!

---

### Post by dannyboy79 on 2007-04-09
ok, so you're using networkmanager applet. also, if you ever want to learn any basic linux command, just gogle. basic linux commands. or basic terminal commands. and you'll find plenty of them. here's a good start: [http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)
so to look at the contents of a folder you use "ls" stands for listing. so it would be

**ls /etc/init.d/**

then you can also add options, like ls -la, this would show you the studd within that folder but with tons of info, like owners:groups, permissions, times, date etc etc.\

next, if those are the dns server from windows and windows internet works than your dns is fine on ubuntu. 

ok, so how do we get the network manager to enable that interface from the start?? huh, I don't use it so I am not sure. Let me look into it for ya and I'll get back to ya.

I am very close to General Mitchel airport and I know what you're talking about when you say Lovers Lane. It's also referred to as Hwy 100 and also 108th street. Very confusing. Anyway good luck and I'll get back to you.

---

### Post by BobK on 2007-04-09
Thanks!!  I WILL be studying the Linux command stuff.  The link you gave me is a good start.  DOS is not a problem haha.

Just for reference, below is the contents of init.d

acpid              hotkey-setup                     readahead-desktop
acpi-support       hplip                            README
alsa-utils         hwclock.sh                       reboot
anacron            keyboard-setup                   rmnologin
apmd               killprocs                        rsync
apport             klogd                            screen
atd                laptop-mode                      sendsigs
avahi-daemon       linux-restricted-modules-common  setserial
binfmt-support     loopback                         single
bluetooth          makedev                          skeleton
bootclean          module-init-tools                stop-bootlogd
bootlogd           mountall-bootclean.sh            stop-bootlogd-single
bootmisc.sh        mountall.sh                      stop-readahead
brltty             mountdevsubfs.sh                 sysklogd
checkfs.sh         mountkernfs.sh                   udev
checkroot.sh       mountnfs-bootclean.sh            umountfs
console-screen.sh  mtab.sh                          umountnfs.sh
console-setup      networking                       umountroot
cron               nvidia-kernel                    urandom
cupsys             pcmciautils                      usplash
dbus               powernowd                        vbesave
dns-clean          powernowd.early                  wacom-tools
etc-setserial      pppd-dns                         waitnfs.sh
gdm                procps.sh                        wpa-ifupdown
glibc.sh           rc                               x11-common
halt               rc.local                         xserver-xorg-input-wacom
hdparm             rcS
hostname.sh        readahead


When I look at the -la suffix I can see the following line for networking:

-rwxr-xr-x 1 root root 1725 2006-11-27 08:32 /etc/init.d/networking

---

### Post by dannyboy79 on 2007-04-09
you already showed me that. remember when I asked for this?

ls -la /etc/init.d/ | grep networking
this was to make sure that networking was in /etc/init.d/. init is what starts various processes during bootup.

i am still looking into network-manager but you can also look. there are tons of threads relating to this. just look within the wireless section and then click the "search this forum" on the right side and type in network-manager or nm applet. good lcuk

---

### Post by BobK on 2007-04-11
Just found another thread with at least one post exactly the same as my issue.  Apparently this is an official bug.

[http://ubuntuforums.org/showthread.php?t=405971](http://ubuntuforums.org/showthread.php?t=405971)

I'm going to follow that thread for the solution.  Thanks for the help!!

---

### Post by dannyboy79 on 2007-04-12
well after reading a few of the posts within that thread, I don't think this is the same issue. They are using Fiesty for 1 thing and also, some are saying that their internet works but the applet states that they aren't connected. I thought your problem was just that it's not starting upon boot up. This has to do with the startup script that is running.  hopefully you do figure it out though as I am fresh out of ideas since I don't use the network-manger applet.

---

### Post by BobK on 2007-04-13
OK, guess we had a disconnect.  Per my first post I am using Feisty too!  Hope that didn't cause too much heartburn for you.  You have been a great help (and teacher) and I appreciate the effort you made.  As I said before, this little issue is NOT a dealbreaker for me, I love Ubuntu and will continue to use it even if this issue is permanent.  THANKS!

I found two other posts in that other thread that were "similar" sounding to mine.   

The first one starts off with the same problem I have today and then changes:
"On the 32-bit, I would have to manually click on the NM applet and select "wired network" to be able to connect to the network. With the latest update, I'm now automatically connected--but the applet says I'm not! Sheesh."

The second one _follows_ my post to the other thread (my post first, follow up after):
My post:  "My issue is straightforward. When I boot Feisty I do not have a network connection. I have to left click on NM and check off the "Wired Network" choice. After that action, everything works fine...until the next reboot when I have to do it all over again. At least it is consistent. I'm only on a wired connnection so I do not have any wireless experience to add.  I first reported this on http://ubuntuforums.org/showthread.php?t=402442."
 
And the follow up to my post:
"Indeed... same here. An annoyance but at least it didn't cripple our ability to use the net.  I tinkered around a bit with purging and reinstalling, but got nowhere.
BH"

---

### Post by gonzalov on 2007-04-15
Boy! More people with the same problem!

Your description exactly fits my "problem": no network at startup, click on network manager and it connects ok.

My setup: Feisty with all updates, desktop with wired network (no wireless, no moving laptop), I would like it to login connected to the network as I have thunderbird in the "Session-startup" section and it always starts with an error, as there is no net.

I've tried:
1. /etc/network/interfaces: eth0 is on "auto" (I do have more interfaces since I run VMPlayer with a Win98 OS there).
2. Disable NetworkManager from the "Sessions-Startup" (probably reactivated immedately by an update, will try again). I got this from one of the numerous threads on wireless net problems.

I haven't tried:
1. Assigning a static IP to my box, instead of allowing it to do DHCP.
2. Removing NetworkManager and ensuring the init scripts connect the network.

What I would truly like is NetworkManager having an option that says something like "Connect to this interface by default".

Any suggestions? Thanks!

---

