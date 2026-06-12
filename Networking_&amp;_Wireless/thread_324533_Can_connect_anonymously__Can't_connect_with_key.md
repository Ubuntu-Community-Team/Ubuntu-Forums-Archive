---
title: "Can connect anonymously / Can't connect with key"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by Morbett on 2006-12-23
Hi,

I am using Edgy on a Dell laptop with a broadcom chip.  My wireless works fine for connecting anonymously to free connections all over the city, but for some reason I can't connect to a network that requires a password.  

I have the right password and I try to enter it with the NetworkManager (which recognizes the connection, btw) but I have no luck.  

When I do System-Adm-Networking and go to the wireless configuration, the network does not appear for some reason.

It's getting annoying, anybody know what to do?

Thanks

---

### Post by dbott67 on 2006-12-23
A few things to look at:

1. Which encryption are the APs using: WEP or WPA?
2. Are the APs using any other type of security (MAC filtering, static IPs, limited DHCP, etc.)?
3. Do you have administrative access to the AP to verify settings?

-Dave

---

### Post by jerryl on 2006-12-24
Hello,
Sorry to jump in on this thread but I think I am having a similar problem.  I am new to Ubuntu and reasonably new to Linux.  I have been trying for days to get my wireless network going.
I have an IBM Thinkpad (have been poring over the Stinkpad thread and many others) and a D-link G630 wireless card.  The laptop is dual boot with Windows and the wireless network works fine in Windows.  
I originally had 128 bit encryption enabled but suspected maybe that was the problem so I took encryption off the router and it worked ok.  However, I can't really leave the network open so tried adding 64 bit encryption (WEP).  
Using Network Monitor I can't see the wireless network.  I installed Wifi Radar and can see the network.  It was using this that I could connect when encryption was disabled.  I am sorry to jump in on this thread and hate to add to all the other threads on wireless problems but I have been at this for days.  Not sure what other information to provide.
Any help would be really appreciated.

Jerry

---

### Post by jerryl on 2006-12-24
following on from a suggestion in another thread, here is the output from iwconfig, ifconfig and netstat -rn

jerry@eragon:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"jalapeno"  Nickname:"Jalapeno"
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:4196  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

irda0     no wireless extensions.

sit0      no wireless extensions.

jerry@eragon:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:92:96:BD  
          inet6 addr: fe80::211:95ff:fe92:96bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0      Link encap:Ethernet  HWaddr 00:03:47:B9:D7:1F  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-92-96-BD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20878 errors:0 dropped:0 overruns:0 frame:14667
          TX packets:52310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1329820 (1.2 MiB)  TX bytes:2615500 (2.4 MiB)
          Interrupt:11 Memory:d0b60000-d0b70000 

jerry@eragon:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
jerry@eragon:~$

---

### Post by jerryl on 2006-12-26
still struggling with this several days later.  What hurts even more is how simple it was to get two other Windows laptops connected to the network (visitors) and a Nintendo Wii!
Any help would be appreciated - even if it is simply helping me find a solution already posted with this problem (that would be great in fact).

Cheers.

---

### Post by dbott67 on 2006-12-26
Hi Jerry,

Sorry, I would have been able to help you out earlier but family get-togethers have curtailed my time online.

Seeing that the computer connects without WEP is a good sign.  Can you post the output of the following command:
```
cat /etc/network/interfaces
```

If it looks similar to mine, then we could try using the ASCII WEP key in the file instead of the HEX key.

```
dbott@dapper:~$ cat /etc/network/interfaces 
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
wireless-essid bott
wireless-key s:mysecretwepkey
```
If yours interfaces file displays the HEX WEP key, copy the HEX key from the router and convert it to ASCII (use this link: [http://www.dolcevie.com/js/converter.html)](http://www.dolcevie.com/js/converter.html)).

Then modify your **/etc/network/interfaces** file:
```
dbott@dapper:~$ sudo gedit /etc/network/interfaces 

auto ath0
iface ath0 inet dhcp
wireless-essid jalapeno
wireless-key [COLOR="Red"]**s:**[/COLOR][COLOR="Blue"]ascii-wep-key[/COLOR]
```

Notice the **[COLOR="Red"]s:[/COLOR]** in front of the key.  The 128-bit HEX key is 26 characters, while the ASCII version is 13 characters.

-Dave

---

### Post by jerryl on 2006-12-27
Hi Dave,
Thanks for replying - it is a busy time of year for this.
The output of that command was as follows:

jerry@eragon:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ath0 inet dhcp
wireless-essid jalapeno
wireless-key s:

auto eth0
jerry@eragon:~$ 

I tried entering the password in ascii and also in hex but couldn't get it to work.  My WEP key is 64 bits - is that a problem?  I changed it from 128 because I read somewhere that Ubuntu had some difficulty handling 128 bit keys with some cards.

Cheers,
Jerry.

---

### Post by dbott67 on 2006-12-27
64-bit shouldn't be a problem.  I haven't heard that 128-bit wep is a problem either (although I haven't ever looked, so it may be true).

Just to be clear, the s: is used in front of the WEP key when you're using ASCII.  Drop the s: prefix if you're using HEX.

Try using simple ASCII keys (**abcdefghijklm** or **1234567890abc**) in your interfaces file.  Use the converter above to convert to HEX and insert the HEX values in your router.  If it works, then we can change the key to something a little more challenging.

-Dave

---

### Post by jerryl on 2006-12-28
Hi Dave,
I am nearly there - I had a bit of success but then lost it.  My wireless router is a Netgear ME 102 and I read  that for 64 bit keys you only enter five ascii characters.
This generated a 10 character hex key.
I tried the ascii code (jerry) in /etc/network/interfaces but it didn't work.  Then I tried the hex key using the s: in front of it but that didn't work either.  Then I went to the link you mentioned and converted 'jerry' to hex and tried that but it too didn't work.  Since I was using a key generated from 5 ascii characters I tried reconfiguring the network using the wifi radar utility and used the 10 character hex key from the router and it worked.  Wifi Radar was able to get an ip address.
I browsed a couple of web pages and rebooted the machine but couldn't connect.  I went back into wifi radar and re-entered the WEP key and all was ok again - I had to re-enter the key though and it was able to get an ip address.  Just to be sure I rebooted again but no matter what I do now I can't obtain an ip address using wifi radar.  wifi radar is able to see the network and says 'Connected to jalapeno ip(none).  The standard Network Monitor doesn't seem to see it.  
I think I am nearly there but suspect I have some sort of conflict - no changes I make in the wifi radar utility seem to appear in /etc/network/interfaces so I am not sure where this information is being stored.

Cheers,
Jerry.

---

### Post by dbott67 on 2006-12-28
In another thread, I saw that someone had installed and removed "network manager" and was having all sorts of problems until they "purged" it (which removes all configuration files as well as the program).  Network manager does not use the interfaces file, so it may be related to that (I think).  Read this thread if you did install it:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)


Did you install network manager at any time?  If so, you may need to re-install it & then remove it using this command:
```
sudo apt-get --purge remove <app>
```

You might also want to uninstall (& purge) the other wifi managers while we test this out.

-Dave

---

### Post by jerryl on 2006-12-28
Hi Dave,
after reading that post you recommended and since I have probably got myself pretty messed up by now I decided to do a clean install so have reinstalled Ubuntu 6.10.
After completing this I tried editing /etc/network/interfaces to match the example you gave.  For a simple ascii key I used 'jerry'.  In the hex converter this translated to 6a65727279.  I entered the hex value into my wireless router however I couldn't then connect using my Windows (work) laptop.  I don't think it likes the lower case 'a'. so I checked the converter whether upper case 'A' (ie 6A65727279) translated to 'jerry' which it did.  I re-entered the hex key into the router using the upper case 'A' and the windows laptop was now happy and could connect to the network.

I then went about trying the Ubuntu laptop using the changes in your example and tried both the following wireless keys in the interfaces file without any luck:

wireless-key s:jerry
wireless-key 6A65727279

On the status bar on the laptop there is an icon called Network Connection which, when I look at the propertys only recognises eth0 and l0.  

So, at this point, the /etc/network/interfaces file was I think pretty identical to the sample one except using my ESSID and wireless-key.  

I then decided to go to System-->Administration-->Networking and see if that recognised anything.  There were no details for the network so I entered them in (ESSID = jalapeno and the hexadecimal key 6A65727279).

This still didn't solve it but when I checked the /etc/network/interfaces file I noticed some changes.  It had put in the network details under the ath0 section so now I have the wlan0 section and the ath0 section both showing the network details.



Cheers,
Jerry.

---

### Post by jerryl on 2006-12-28
Hi Dave,
In the end I reinstalled Ubuntu 6.10 completely as I had probably messed a few things up.
I then followed this thread from scratch and made the /etc/network/interfaces file the same as the example but with my ESSID and key.

I used a simple key (jerry) and the hex converter showed that to be 6a65727279 which I updated in the router.  However, it seems my work (Windows) laptop doesn't like lowercase so I changed it to 6A65727279 and that kept the Windows laptop happy. 
I rechecked the new key in the ascii converter and it still came out as 'jerry' so I figured that was ok.
Unfortunately I still can't get wireless working in Ubuntu.
The Network Connection icon in the status bar only recognises eth0 and l0.  
I ended up going to System-->Administration-->networking and adding the details of the wireless network there but with no luck.  The Network Connection icon still doesn't see the wireless network but the /etc/network/interfaces file has changed.
It now has the following two lines in two places:

wireless-essid jalapeno
wireless-key 6A65727279

They are under the **iface ath0 inet dhc**p line and the **iface wlan0 inet dhcp** line.

I have tried both the ascii and hex keys.  Also, following a suggestion in the [wireless networking wiki,]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") I changed the wep key to open instead of shared (I have no idea what difference that makes).

Cheers,
Jerry.

---

### Post by jerryl on 2006-12-28
Hi Dave,
Also, following a suggestion in the [wireless networking wiki,]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") I changed the wep key to open instead of shared (I have no idea what difference that makes).

Cheers,
Jerry.

---

### Post by dbott67 on 2006-12-29
> **jerryl said:**
> Hi Dave,
Also, following a suggestion in the [wireless networking wiki,]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") I changed the wep key to open instead of shared (I have no idea what difference that makes).

Cheers,
Jerry.

I think open means not encrypted.  It's funny, while looking for other hints as to your troubles, I stumbled across the same link ([https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)), but you beat me to it.

Normally when I'm troubleshooting, I try to remove all of the variables and only deal with one issue at a time.  In this case, it appears as the the driver is loaded and we are able to scan for access points, but are unable to connect to it.

From you earlier posts, we know that you can connect without encryption which means both the card and router work properly.  Now it's just a question of what part of the encryption equation is causing the problem (the router, the card, Ubuntu, the wep key, ascii, hex, etc.)

We will get it sorted out.  You can IM me in my profile if you need to.

-Dave

---

### Post by jamesstansell on 2006-12-30
Hi Jerry,

You mentioned both ath0 and wlan0 at the same time, which may be a problem, assuming you're working with just one wireless card.  There are other reports in this forum that suggest to either use the 'native Ubuntu' driver and not have ndiswrapper installed, or to install and use ndiswrapper but blacklist the native driver.

I assume you've looked at the sticky thread about wireless security in this forum?

I'm having a similar problem to you, but with a WUSB54G (Ralink 2570) device.  I tried to go straight to wpa2 using the rt2570 driver, but I may try wep soon.  And if that doesn't work I'll try ndiswrapper.

Here's a recent, well-written article, although it's examples don't apply directly to Ubuntu:

[http://www.troubleshooters.com/lpm/200612/200612.htm](http://www.troubleshooters.com/lpm/200612/200612.htm)

Regards,

-james.

---

### Post by jerryl on 2007-01-08
Hi James,
Thanks for that - I have just got back from holidays and am about to start troubleshooting again so will look into that thread.

Cheers,
Jerry.

---

### Post by randoker on 2007-01-16
Morbett / Jerry / All

I had the exact same symptoms that you are describing.
IBM T41
Internal mini-PCI Cisco Aironet 350
D-Link WBR-1310 Wireless Router

The system would authenticate and obtain an IP address on open networks.
The system would authenticate but WOULD NOT obtain an IP address on networks with WEP.

All of the following revealed the expected results:
sudo lsmod | grep airo
sudo iwlist eth1 scan
sudo iwconfig eth1
sudo lshw -businfo
sudo lshw -C network

After tinkering for hours, all I had to do was paste the WEP key into all 4 fields on the router, instead of having it just in the first one.

This is how it was to start with:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 0000000000000000000000000
WEP Key 3: 0000000000000000000000000
WEP Key 4: 0000000000000000000000000

This is what I changed it to:
WEP Key 1: 613c5e6645787166627e7a395f
WEP Key 2: 613c5e6645787166627e7a395f
WEP Key 3: 613c5e6645787166627e7a395f
WEP Key 4: 613c5e6645787166627e7a395f

Doubtless this is just something screwy on my Router, but just throwing it out there in case it puts anyone on track to find an answer.

thanks,
Kerry

---

