---
title: "WEP woes"
date: 2005-12-01
forum: Networking &amp; Wireless
---

### Post by dc2447 on 2005-12-01
I am having some issues getting WEP with 128bit Keys to work.

Here is my interfaces:
> 
auto lo
iface lo inet loopback

mapping hotplug
   script grep
   map eth0

iface eth0 inet dhcp
auto eth0

iface wlan0 inet dhcp
wireless-essid dr44l
wireless-mode Managed
wireless-key 1nsufnhs7yerg
wireless-keymode restricted
auto wlan0


This works great with WEP disables on the router but as soon as I enabled wep with a 128bit key it fails.

I have tried iwpriv wlan0 authmode 1/2/3

But no luck.  

I know I'm missing something obvious but what?

---

### Post by daller on 2005-12-02
If it is restricted (not open) WEP, it looks great!

Are you sure your card has linux-supported WEP?

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

---

### Post by Lambert on 2005-12-02
what card and driver are you using? (ndiswrapper)

post the output of this command here

iwpriv wlan0

One thing to try. Add a - after every 4 letters in the key

Have you been able to connect with out wep enabled?

If you want to use wep, shared/restricted key doesn't really offer any greater security over open key. You should consider using open.

other things you can do to improve security is not broadcast your signal and if router allows it, add mac filtering

---

### Post by mpvano on 2005-12-02
Here's something I noticed about your wireless key entry - it's NOT a Hexadecimal key!

According to the man page for iwconfig, the syntax you used is for a Hexadecimal key - that command line is probably silently failing (as most iwconfig do when run by ifup scripts from the "interfaces" file).

To enter an ascii string as a WEP key, you need to prefix it with "s:", like the following example from the man page:
 
    iwconfig eth0 key s:whateverpassword

I don't know if this is your problem, but it could certainly be ONE of your problems.

I have also noticed great inconsistency in the ways wireless drivers derive keys from ascii strings. I've never had much luck with them myself unless all the equipment and drivers were from the same vendor.

I suggest trying hex keys - just make sure you properly enter them. In some drivers and router configuration dialogs that have relaxed rules for the key length entry,  It's possible to accidently enter a hex key AS AN ASCII STRING, which of course results in a completely different key after it's converted to hex.

good luck...

Mario

---

### Post by tonyw50 on 2005-12-02
Are you sure both the access point and the card support high level encryption?  I have a newer access point capable of high level encryption but must use it on lower level encryption in order that one computer with an older card can connect to it.

---

### Post by Lemmikkipuu on 2005-12-10
I have read all the messages here, but no luck. I have WL54PC card by A-link.
It use to work with ubuntu 5.04 after compling the drivers and RaConfig ... untill few days ago an uppdate destroy my driver (smart uppgrade!). Now I have Ubuntu 5.10 and it founds the card OK. but it will not communicate with my access point. There is nothing wrong with the accesspoint, because it talks fine with my win2k pc laptop (siemens 11g). 

*Here is some data*
```
root@Data:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"pihkala"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:7065-7472-692E-7069-686B-616C-61   Security mode:open
          Link Quality=0/100  Signal level=-63 dBm  Noise level:-201 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

*and more*
```
root@Data:~# iwlist ra0 scanning
ra0       Scan completed :
          Cell 01 - Address: 00:90:4B:7A:CE:47
                    Mode:Managed
                    ESSID:"pihkala"
                    Encryption key:on
                    Channel:1
                    Quality:0/100  Signal level:-59 dBm  Noise level:-203 dBm
```
[I]
and my interfacesfile looks like this[/I]
```
# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script echo
	map ra0

iface ra0 inet dhcp
wireless-essid pihkala
wireless-key s:petri.pihkala

iface eth0 inet dhcp

auto eth0

auto ra0
```

I have tried just about anything I can think of. I even tried to put RaConfig in the system, but with no luck. From the "https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo" 
[LIST=1]
[*]First of all "sudo apt-get install kdebase" could not find "kdebase"... and 
[*]"sudo apt-get install libgtk2.0-dev" could not find "ibgtk2.0-dev" and finally 
[*]"sudo apt-get install gcc-3.4" could not find "gcc-3.4".
[/LIST]

Then I even tried to install **Mandriva-Linux**, but that could not even get me to gnome, but only the linux-terminal... so I gave that up. Now I am here back to try to get this ubuntu 5.10 talk with my acces point. Please help me!

I know my spellign is poor, but hope You will understand...

--Lemmikkipuu

---

### Post by reddeljb on 2005-12-10
I'm having the same problem with a different card. my acer laptop with an ipn2220 inbuild wireless doesn't seem to be able to connect with wep enabled. Is this a wep problem only or does it also apply to other security modes of the router? wpa for example.

---

### Post by Lambert on 2005-12-10
post the output of 

sudo iwpriv ra0

This may take a couple posts but there may be a driver setting that needs to be tweaked. posting the output of iwpriv will show which ones are available for your driver.

---

### Post by Lemmikkipuu on 2005-12-10
I found at least one problem:
becouse 
```
root@Data:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"pihkala"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:7065-7472-692E-7069-686B-616C-61   Security mode:**open**
```
Security mode is "**open**" and it should be "**shared**". How could I change that? 
Now when I have no WEP on, this works fine.

--Lemmikkipuu

---

### Post by Lambert on 2005-12-10
Not 100% sure with out seeing the output of iwpriv but try this command

sudo iwpriv ra0 set authmode=shared

---

### Post by Lemmikkipuu on 2005-12-11
[I]You were right
that command gave me just this[/I]
```
root@Data:~# iwpriv ra0 set authmode=shared
Interface doesn't accept private ioctl...
set (8BE2): Invalid argument
root@Data:~#
```

*Here is some data You needed*
```

root@Data:~# iwpriv ra0
ra0       Available private ioctls :
          set              (8BE2) : set 1024 char  & get   0
          bbp              (8BE3) : set 1024 char  & get 1024 char
          mac              (8BE5) : set 1024 char  & get 1024 char
          e2p              (8BE7) : set 1024 char  & get 1024 char

```

so what I could do next?
--Lemmikkipuu

ps.
I have a feeling that we are near the solution of my problem... Thank you!

---

### Post by Lemmikkipuu on 2005-12-11
It seems that nothing works here....

I tried to start using "open" in my AP, but it did not like that idea!

---

### Post by fog on 2005-12-11
Try to add this line in your /etc/network/interfaces:
> pre-up iwpriv ra0 authmode 2
or 
> pre-up iwpriv wlan0 authmode 2
whatever your network is...

---

### Post by Lambert on 2005-12-11
1. shared/restricted mode doesn't offer any extra security over open wep setting. I would consider going to open or at least trying that to see if you can connect with wep there.
2. If you stay with shared restricted, there is some driver setting that needs to be changed probably which is done through the iwpriv command. Do a google search for "iwpriv ra0" authmode and other variations you find while searching. You might find some help through that.

---

### Post by Lemmikkipuu on 2005-12-11
I added pre-up iwpriv ra0 authmode 2, and now my interfaces look like this...
 ```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script echo
	map ra0
pre-up iwpriv ra0 authmode 2
iface ra0 inet dhcp
wireless-essid pihkala
wireless-key s:petri.pihkala

iface eth0 inet dhcp

auto eth0

auto ra0
```
but still iwconfig shows open. 
> 
1. shared/restricted mode doesn't offer any extra security over open wep setting. I would consider going to open or at least trying that to see if you can connect with wep there

I know that, but I can not get my WLAN AP to give up shared settings and still keep some encryption. This is Motorola SBG900E and in the help it says:
> Open - Any client device is allowed to authenticate with the access point and transmit data to any other client devices on the wireless network. Open authentication does NOT provide any security for data transmitted on the wireless network.
So that is last option I would like use in middle of the city... and google... I have tried to google ralink 2500 iwpriv whole morning and today, but not very much luck jet...

> **I try again to go to Motorola SBG900E settings and changed to open and ... after savig it toggle open option back to shared... then I did it third time and this time it accepted option shared and encryption.... good this problem is solved**

---

### Post by reddeljb on 2005-12-11
Try MAC address filtering, then no computers would be able to negotiate with the router with out first being on the approved list, right?

---

### Post by fog on 2005-12-11
Not like this:
> pre-up iwpriv ra0 authmode 2
iface ra0 inet dhcp
wireless-essid pihkala
wireless-key s: petri.pihkala
but like this:
> iface ra0 inet dhcp
pre-up iwpriv ra0 authmode 2
wireless-essid pihkala
wireless-key s: petri.pihkala

---

### Post by roachk71 on 2005-12-11
[LEFT]Hi,

I have my own router set up with shared mode. Adding 'restricted' to the end of the key line usually helps:

wireless-key (wep key) restricted

I was so groggy this morning I had to edit this post several times...
[/LEFT]

---

### Post by fog on 2005-12-11
> auto lo
iface lo inet loopback

mapping hotplug
	script grep
	map ath0
	
# The primary network interface

iface ath0 inet static
pre-up iwpriv ath0 authmode 2
address 10.0.0.1
netmask 255.255.255.0
gateway 10.0.0.138
wireless-essid FOG
wireless-key xxxxxxxxxx

Here is my /etc/network/intefaces, I have WEP authentication in my network
and works fine.

---

### Post by Lemmikkipuu on 2005-12-11
This is maybe stupid question but after I have made changes to my Interfaces-file. How I can tell computer/card that new interfaces has changed and it should be used? I guess that I do not need to boot whole system, every time I make some changes?

---

### Post by fog on 2005-12-11
sudo ifconfig ra0 down
sudo ifconfig ra0 up

---

### Post by Lemmikkipuu on 2005-12-12
**I try again to go to Motorola SBG900E settings and changed to open and ... after savig it toggle open option back to shared... then I did it third time and this time it accepted option shared and encryption.... good this problem is solved**

Thank everybody for giving me a lot of information to solve this problem!

I have only minor detail to fix:
after booting I have to go settings and activate every time my wlan card.

---

### Post by fog on 2005-12-12
sudo gedit /etc/modules
and add in the end, the name of your wireless module
(mine was: ath_pci)

---

### Post by mpvano on 2005-12-12
I believe that the security mode should actually be "restricted", not shared.

You can try the following:

1. First of all, I assume you  are logging in as root (using sudo su) or preceding all the following commands with "sudo", and the configuration method you are trying to use is to directly edit /etc/network/interfaces. If you are using some other configuration tool or method, then disregard the rest of this post, it will just confuse things.

2. Before each edit, issue (again with root authority) the command "ifdown ra0" and wait for it to complete. After each edit issue the command "ifup ra0" and wait for it to complete. The "interfaces" file is ONLY read during the execution of these commands.

3. I'm assuming your "interfaces" file is the last one in this thread. Try changing the line 

wireless-key s:petri.pihkala

to add the rest of the optional arguments that some drivers may require. It will look like this then:

wireless-key restricted s:petri.pihkala [0]

I'm assuming that you ARE, in fact trying to use key 0? Some cards handle 4 keys and you have to pick the right key, as well as having the right value in that key slot. If you're actually trying to use a different key, plug the appropriate number into that line inside the square brackets.



If this doesn't make any difference, then I suggest that you may have a problem in getting your ascii key entry to agree with the router's idea of the ascii key entry. If there's a way to examine the router's key in HEX, you might compare it to the values in the iwconfig command.

hope this is getting you closer to an answer....

Mario

PS I hope you can see the lines properly, I get a smiley face displayed in the middle of your key line because of the way the forum works! Presumably you can ignore this if you see it that way....

---

### Post by Lemmikkipuu on 2005-12-13
**Yes** problem is solved! 
Thank you Mario for you comment anyway. 
Now I have wep 128 bit ecryption with open system. That is what 5.10 is willing to use. I could never change it to shared or restricted and since this is working, I probably never will. Here is few comments.

1) Yes I am logged in as root. (I am allways if I am willing to make changes to system, it is easier that way.)

2)What about
```
 ifconfig ra0 down
 ifconfig ra0 up
```
does it do same thing?
---
After I told 
```
 
dhclient ra0
ifup ra0
```
The problem of activating my wlan card every time after booting was fixed.
I just do not know really what those commands will do...

3) I keep that in my mind if I want to somehow change back to use shared/restricted coding. Now everything is working nice, so I think I do not make any changes....

Finally this is my interface file at the moment and it is working....
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script echo
	map ra0
iface ra0 inet dhcp
wireless-essid pihkala
wireless-key s:xxxxxxxxxxxxx

iface eth0 inet dhcp

auto ra0
auto eth0

```

***...and finally I want to thank everybody who helped me struggle my way throught this jungle.***

--Petri

---

