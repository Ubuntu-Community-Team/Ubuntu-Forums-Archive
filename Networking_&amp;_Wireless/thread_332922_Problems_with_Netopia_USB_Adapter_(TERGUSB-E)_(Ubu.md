---
title: "Problems with Netopia USB Adapter (TER/GUSB-E) (Ubuntu 6.06)"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by instantnoodle on 2007-01-06
Hi there,
I'm new to linux and tried to install a wireless connection, but failed miserably.. 
I already posted my problem in the german community a week ago, but no one answered my post. I decided to post it in this forum, or should I've posted it in the beginners forum?
I'm using Dapper Drake (Ubuntu 6.06) with GNOME and following USB adapter:
Brand: Netopia
Model: TER/GUSB-E
The wireless network works fine on my laptop (using windows).
After I plugged the adapter in the leds do not blink at all. When i go to the Wireless Configuration and try to set up my connection. My whole system freezes at the time I try to activiate the connection. And I have to restart my machine.
I don't know what to do..:-k 

I'm thankful for every hint!
Cheers



Here are some of my configuration I which may be useful to you.
What is this Ralink driver? Does it suit to my adapter after all?

```

lsusb: 
Bus 001 Device 002: ID 148f: Ralink Technology, Corp. 802.11g WiFi 
Bus 001 Device 001: ID 0000:0000 


will@will-desktop:~$ egrep -v "^$|^#" /etc/network/interfaces 
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


will@will-desktop:~$ egrep -v "^$|^#" /etc/resolv.conf 
grep: /etc/resolv.conf: No such file or directory 


will@will-desktop:~$ egrep -v "^$|^#" /etc/hosts 
127.0.0.1       localhost 
127.0.1.1       will-desktop 
::1     ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 


will@will-desktop:~$ cat /etc/network/interfaces 
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


will@will-desktop:~$ cat /etc/resolv.conf 
cat: /etc/resolv.conf: No such file or directory 


will@will-desktop:~$ cat /etc/hosts 
127.0.0.1       localhost 
127.0.1.1       will-desktop 

# The following lines are desirable for IPv6 capable hosts 
::1     ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 


will@will-desktop:~$ iconfig 
bash: iconfig: command not found 


will@will-desktop:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 


will@will-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

sit0      no wireless extensions. 

```

---

### Post by teaker1s on 2007-01-06
look here your wireless has this chipset maker and it would appear they support linux directly
[http://www.ralinktech.com/ralink/Home/Support/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")

---

### Post by chrisjpb on 2007-01-16
I have the TER/GUSB-N usb stick and when i plug it in i also get no lights and im VERY new to Ubuntu/Linux, been using it for all of 4 hours haha.  Anyway i HAVE to have this working to use this OS, i went to the website above and downloaded the usb driver from ralink but i have no clue where to go from here as far as compiling and what not. I do have the build-essential package installed. Any help would be GREATLY appreciated. Thanks in advance

---

### Post by teaker1s on 2007-01-16
okay I'm not great at compiling and someone will know a lot more than me,but golden rule read all documentation before starting
then in terminal 

[COLOR="Red"]sudo apt-get build-essential [/COLOR]
 [COLOR="Red"]sudo apt-get install linux-headers-`uname -r` 
 sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
[/COLOR]

cd into source directory example
[COLOR="Red"]cd /home/teaker1s/driver[/COLOR]
[COLOR="Red"]make distclean[/COLOR]  (only sometimes required if you get error then not required)
[COLOR="Red"]./configure
make
sudo make install[/COLOR]

if it comes back with errors then you will need to read through and see what packages are missing-these are dependencies which will need installing before you can build and install source. synaptic is easier to install dependencies

[COLOR="Red"]gksudo synaptic[/COLOR]

;)

---

### Post by chrisjpb on 2007-01-16
ok, i may be looking at something wrong here but thought the directions here and in the readme etc. in the files didnt work properly probably due to me messing something up i noticed the output file is rt2570.ko. This file already exists in the kernel>drivers>usb>net folder so why is all of this telling me to re-create a file i already have. Is there a way to diagnose why the original isnt working to make it work

---

### Post by teaker1s on 2007-01-16
I wasn't aware it's there by default, you could terminal

[COLOR="Red"]iwconfig[/COLOR]

post the output and we'll see what's happening

---

### Post by chrisjpb on 2007-01-16
I cant copy it all over since that computer still has no internet access or no way of transferring information to this computer since it cant write to my NTFS usb hard drive. I did notice the SSID on our building has changed to start with a capital letter and I didnt notice that, but when i tried to change it thinking it would fix something my computer locked up, and had to be rebooted so i cnat change it.

---

### Post by teaker1s on 2007-01-16
if you burn alternate.iso there is network manager that makes it a lot easier
network-manager-gnome

using synaptic you can add packages from cd

see a copy of my iwconfig now you may see two eth rather than wlan on yours-generally it's a minor config issue 

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"ghetto"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:14:BF:6C:6F:2C   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:111  Invalid misc:1683   Missed beacon:0

sit0      no wireless extensions.

---

### Post by chrisjpb on 2007-01-16
where do i fnd alternate.iso?

---

### Post by chrisjpb on 2007-01-16
UPDATE: I just got it all to change and am now online so it FINALLY worked, thanks a lot for your guidance and input, now i jsut need to find where to look for new software

---

### Post by teaker1s on 2007-01-17
terminal

[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR]  uncomment any commented out repositories by removing [COLOR="Red"]#[/COLOR]

[COLOR="Red"]gksudo synaptic[/COLOR]

hit reload tab and you can search and install software

---

