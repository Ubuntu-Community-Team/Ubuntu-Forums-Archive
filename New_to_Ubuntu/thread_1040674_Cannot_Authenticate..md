---
title: "Cannot Authenticate."
date: 2009-01-15
forum: New to Ubuntu
---

### Post by k3lt01 on 2009-01-15
I have come across a small problem with my laptop. Whenever I try to change a setting such as the User Settings or Manually Configure my network where I have to Unlock the UI to make adjustments I get a "Cannot Authenticate" message without even getting an opportunity to use my password. I'm hoping there is a simple way to fix this so I can change 1 Network Setting at least.

A little info is probably very appropriate. I reinstalled Ubuntu using the Minimum Install Disk and have FluxBox and GnomeCore along with a few programs.

---

### Post by aesis05401 on 2009-01-15
> **k3lt01 said:**
> I have come across a small problem with my laptop. Whenever I try to change a setting such as the User Settings or Manually Configure my network where I have to Unlock the UI to make adjustments I get a "Cannot Authenticate" message without even getting an opportunity to use my password... 

Where are you initiating from?  CLI?  

Edit:  And tell us what network settings you are doing manually.  Most are very easily set from CLI.

---

### Post by k3lt01 on 2009-01-15
> **aesis05401 said:**
> Where are you initiating from?  CLI?  

Edit:  And tell us what network settings you are doing manually.  Most are very easily set from CLI.The answer to your question is in my OP and highlighted in the quote below.
> **k3lt01 said:**
>  Whenever I try to change a setting such as the ***_User Settings_*** or ***_Manually Configure_*** my network where I have to Unlock the UI to make adjustments I get a "Cannot Authenticate" message without even getting an opportunity to use my password.

---

### Post by aesis05401 on 2009-01-15
Ah.. I see we are not speaking with the same definitions :)

These terms you highlighted are menu items inside your GUI?

sudo ifconfig etc... 
sudo dhclient etc...
sudo route etc...
sudo brctl etc..
sudo tunctl etc...

These CLI commands will allow you complete control over your network configuration.  Unfortunately I do not know what you were accessing through the menu items you reference.

If you can tell me what part of the user settings or network settings you want to modify I may be able to tell you the terminal commands.

Edit: or easier yet, figure out the name of the app that launches when you clicked those menu items and launch from a terminal using sudo or better, gksudo if you have the right packages installed.

---

### Post by k3lt01 on 2009-01-15
> **aesis05401 said:**
> Edit: or easier yet, figure out the name of the app that launches when you clicked those menu items and launch from a terminal using sudo or better, gksudo if you have the right packages installed.Network settings is the one I really want to modify. My Wireless is set Roaming mode so I have to sign in, I want it set to DHCP so it signs in automatically.

I checked the User Settings dialog so I can see if it was an isolated problem or one that was more global. It seems its a global problem and that is why I would ideally like to fix it as a global problem but would be happy to at least fix my Network Settings.

---

### Post by aesis05401 on 2009-01-15
Okay.  When your OS boots it runs a process called 'ifup' where it brings up your networking interfaces and sets their properties.  To do this it reads the following very simple file: /etc/network/interfaces.

This will open the interfaces file with root privileges for you to examine:
```

sudo nano /etc/network/interfaces

```

You are using wireless, so you should see an entry for a device name 'wlan0' which I believe is the Linux default for wireless single NIC setups.  You can check the name of your wireless device by doing an 'ifconfig' from command line or 'sudo lshw' for a complete list of hardware.

to set up for dhcp the entry you need is something along the lines of:

auto wlan0 
iface wlan0 inet dhcp

Here is a link with a fairly good description of how to set up the interfaces files in general: _[LINK!]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")_

Your interfaces entry for wlan0 should match the second example on the linked site except your device is wlan0, not eth0.

If you check this out to no avail then we can check out your make of card and figure out whether there are issues with it.  Some people need to use NDISwrapper to solve the roaming issue.

Edit: I think 'iwconfig' is the terminal command for setting things like network name etc.. so you can type 'man iwconfig' at a terminal for info on how to examine those things as well.

Here is documentation  on running wifi that does not play well with Linux: [LINK!]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by k3lt01 on 2009-01-15
> **aesis05401 said:**
> Okay.  When your OS boots it runs a process called 'ifup' where it brings up your networking interfaces and sets their properties.  To do this it reads the following very simple file: /etc/network/interfaces.

This will open the interfaces file with root privileges for you to examine:
```

sudo nano /etc/network/interfaces

```Here is the output for that code

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

> **aesis05401 said:**
> You are using wireless, so you should see an entry for a device name 'wlan0' which I believe is the Linux default for wireless single NIC setups.  You can check the name of your wireless device by doing an 'ifconfig' from command line or 'sudo lshw' for a complete list of hardware.

to set up for dhcp the entry you need is something along the lines of:

auto wlan0 
iface wlan0 inet dhcp

Here is a link with a fairly good description of how to set up the interfaces files in general: _[LINK!]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")_

Your interfaces entry for wlan0 should match the second example on the linked site except your device is wlan0, not eth0.

If you check this out to no avail then we can check out your make of card and figure out whether there are issues with it.  Some people need to use NDIS wrapper to solve the roaming issue.Ndiswrapper is installed so my wireless will work, check my signature for my laptops specs which include my wireless card.

---

### Post by aesis05401 on 2009-01-15
Can you post output from iwconfig and ifconfig? Thanks.

---

### Post by k3lt01 on 2009-01-15
sure

```
michael@michael-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"*******"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:9D:FA:28   
          Bit Rate=54 Mb/s   
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

michael@michael-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:73:9f:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:6 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66900 (65.3 KB)  TX bytes:66900 (65.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:9b:81:62:76  
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::20e:9bff:fe81:6276/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82711716 (78.8 MB)  TX bytes:5717281 (5.4 MB)
          Interrupt:10 Memory:e0203000-e0203800 

michael@michael-laptop:~$ 
```

---

### Post by albinootje on 2009-01-15
> **k3lt01 said:**
> I have come across a small problem with my laptop. Whenever I try to change a setting such as the User Settings or Manually Configure my network where I have to Unlock the UI to make adjustments I get a "Cannot Authenticate" message without even getting an opportunity to use my password. I'm hoping there is a simple way to fix this so I can change 1 Network Setting at least.

A little info is probably very appropriate. I reinstalled Ubuntu using the Minimum Install Disk and have FluxBox and GnomeCore along with a few programs.

Is your user in the admin group ? And are policykit and apparmor installed ?

Check with the commands :
```

groups
dpkg -i|grep policy
dpkg -i|grep armor

```

---

### Post by aesis05401 on 2009-01-15
K. 

It should just be the interfaces entries. 

```

# Set dhcp on wifi interface
auto wlan0
iface wlan0 inet dhcp

```

After saving this return to your terminal and try:
```

sudo dhclient wlan0

```

This will force wlan0 to apply for credentials. 

If this does not work, return to your terminal and type:
```

sudo ifdown -a
sudo ifup -a

```

This will force a reinitialization of all networking interfaces.  

BTW, as I do not use ndiswrapper I did a quick search and this appears to wrok for others with your card.  If this does not work we will try something else.

---

### Post by k3lt01 on 2009-01-15
> **albinootje said:**
> Is your user in the admin group ? And are policykit and apparmor installed ?

Check with the commands :
```

groups
dpkg -i|grep policy
dpkg -i|grep armor

```

```
michael@michael-laptop:~$ groups
michael adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
```

```
michael@michael-laptop:~$ sudo dpkg -i|grep policy
dpkg: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
```

```
michael@michael-laptop:~$ sudo dpkg -i|grep armor
dpkg: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
michael@michael-laptop:~$ 
```

---

### Post by albinootje on 2009-01-15
> **k3lt01 said:**
> ```

[code]michael@michael-laptop:~$ sudo dpkg -i|grep policy
dpkg: --install needs at least one package archive file argument


My bad :( 
Should be :
[code]
dpkg -l|grep policy
dpkg -l|grep armor

```

---

### Post by k3lt01 on 2009-01-15
> **albinootje said:**
> My bad :( 
Should be :
```

dpkg -l|grep policy
dpkg -l|grep armor

```lol, its ok

```
michael@michael-laptop:~$ dpkg -l|grep policy
ii  libselinux1                                2.0.55-0ubuntu4                                            SELinux policy enforcement, run-time librari
ii  libsepol1                                  2.0.20-0ubuntu3                                            SELinux binary policy, run-time library
ii  policykit                                  0.7-2ubuntu7                                               framework for managing administrative polici
```
```
michael@michael-laptop:~$ dpkg -l|grep armor
ii  apparmor                                   2.1+1075-0ubuntu9.1                                        User-space parser utility for AppArmor
ii  apparmor-utils                             2.1+1075-0ubuntu9.1                                        Utilities for controlling AppArmor
michael@michael-laptop:~$ 
```

---

### Post by k3lt01 on 2009-01-15
> **aesis05401 said:**
> K. 

It should just be the interfaces entries. 

This will force a reinitialization of all networking interfaces.  

BTW, as I do not use ndiswrapper I did a quick search and this appears to wrok for others with your card.  If this does not work we will try something else.
All that happened was I totally lost my connection and it jammed my laptop I had to force a reboot and then change it back to what is was.

---

### Post by albinootje on 2009-01-16
> **k3lt01 said:**
>  Whenever I try to change a setting such as the User Settings or Manually
Configure my network where I have to Unlock the UI to make adjustments I get a "Cannot Authenticate" message without even getting an opportunity to use my password.


Here's a possible solution :
[http://ubuntuforums.org/showthread.php?t=903813](http://ubuntuforums.org/showthread.php?t=903813)

Here's a bug report which could be relevant :
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/205037](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/205037)

See also :
[http://ubuntuforums.org/archive/index.php/t-788538.html](http://ubuntuforums.org/archive/index.php/t-788538.html)
the comment by "maninsitu October 24th, 2008, 09:36 PM".

---

### Post by k3lt01 on 2009-01-16
Thanks albinootje. I am able to authenticate now, but being able to do that has highlighted a few other issues. I will take a look at the links you posted to see if they are relevant to the new issues.

---

