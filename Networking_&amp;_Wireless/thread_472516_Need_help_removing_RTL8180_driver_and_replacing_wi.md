---
title: "Need help removing RTL8180 driver and replacing with ndiswrapper for WPA [Dapper]"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by monomaniacpat on 2007-06-13
Hey guys,

I am using RTL818x drivers that came with Dapper, but in order to use WPA encryption, I'm going to need to use the windows drivers.

How can I stop R818x being loaded at boot and switch to ndiwrapper?

Thanks for any help.

mono.

---

### Post by monomaniacpat on 2007-06-13
I'm having trouble installing the deb package I made from the tarball from sourceforge.

Here's the error:

```
patrick@inspiron-8200:~/downloads/ndiswrapper-1.47$ sudo dpkg -i ndiswrapper_1.47-1_i386.deb
(Reading database ... 124695 files and directories currently installed.)
Unpacking ndiswrapper (from ndiswrapper_1.47-1_i386.deb) ...
dpkg: error processing ndiswrapper_1.47-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.15-27-386/modules.alias', which is also i n package linux-image-2.6.15-27-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ndiswrapper_1.47-1_i386.deb

```

I originally got the error with checkinstall, but it happens with dpkg, as you can see. Little help?

---

### Post by wieman01 on 2007-06-13
What about installing it via Synaptic? Did you check there? Don't install from source.

---

### Post by bollix47 on 2007-06-13
I know you said you are using Dapper but I was wondering if you have tried to manually setup WPA.

The following is for Feisty and did work on my RTL8187.

[http://ubuntuforums.org/showpost.php?p=2490388&postcount=9](http://ubuntuforums.org/showpost.php?p=2490388&postcount=9)

Doesn't use wrapper or network manager.

---

### Post by wieman01 on 2007-06-13
> **bollix47 said:**
> I know you said you are using Dapper but I was wondering if you have tried to manually setup WPA.

The following is for Feisty and did work on my RTL8187.

[http://ubuntuforums.org/showpost.php?p=2490388&postcount=9](http://ubuntuforums.org/showpost.php?p=2490388&postcount=9)

Doesn't use wrapper or network manager.
It may be that they have improved the driver in Feisty. Dapper does not seem to support WPA.

---

### Post by monomaniacpat on 2007-06-13
> **wieman01 said:**
> What about installing it via Synaptic? Did you check there? Don't install from source.

Yeah, I can use the one in the repos, but I wasn't sure if it was the latest version. I'll check in a mo.

---

### Post by monomaniacpat on 2007-06-13
Well, I'm not sure of the version of ndiswrapper from the repos, but it's installed. The driver and hardware are "present".

Now I need to remove the open source drivers, so I can use ndiswrapper - how do I do that?

---

### Post by wieman01 on 2007-06-13
Have you got the latest Windows driver at hand? Please unzip the driver file... even if it is an .EXE file doing this:
> sudo unzip your_driver_file.exe /opt/RTL8180
Does the archive contain any files e.g. one that ends with .INF?

---

### Post by monomaniacpat on 2007-06-13
Yes I have the driver and I have installed it with ndiswrapper.

```
patrick@inspiron-8200:~$ ndiswrapper -l
Installed ndis drivers:
net8180         driver present, hardware present

```

The problem is that wlan0 is set to use rt818x. Ubuntu doesn't like it if I have both devices (eth0 and wlan0) on when I boot my computer and I am having to change /etc/network/interfaces and reset my computer every time I want to use the other device. Therefore I need to stop rt818x being inserted and have ndiswrapper inserted at boot instead.

---

### Post by wieman01 on 2007-06-13
Ok, now try this:
> sudo gedit /etc/modprobe.d/blacklist
Then add these 2 lines:
> blacklist r818x
blacklist r8187
Now modprobe "ndiswrapper":
> sudo modprobe ndiswrapper
Does this make a difference now? Please do this:
> iwlist scan

---

### Post by monomaniacpat on 2007-06-13
> **wieman01 said:**
> 

Now modprobe "ndiswrapper":


I get an error trying to insert ndiswrapper, that it has no module to insert. It's almost like it's not installed... :(

```
patrick@inspiron-8200:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory

```

On closer inspection, the file is in the following directory - the wrong kernel:

/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/

I tried giving the full path, but it gives the same error, albeit with the path above in it.

---

### Post by wieman01 on 2007-06-13
Alright, I am not in front of my Linux machine, but here is what you could try:
> sudo ln -s /lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko /lib/modules/2.6.15-27-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
The symb-link now points to the correct path where the "ndiswrapper" module is located. We are tricking the system.

---

### Post by monomaniacpat on 2007-06-13
You're a clever one! ;)

Here's the output:

```
patrick@inspiron-8200:~$ sudo modprobe ndiswrapper 
patrick@inspiron-8200:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:E9:27:09:5E
                    ESSID:"PolyandorUS"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-74 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f20 2


```

---

### Post by wieman01 on 2007-06-13
I guess you have blacklisted the old driver? The new one is ready for use then. 

If you are now able to connect to any unsecured network, you can continue & give my WPA HOWTO another go.

---

### Post by wieman01 on 2007-06-14
@monomaniacpat:

Any success as far as WPA is concerned? Don't hesitate to post your problems either here or there. It is really important that you check the change-log for your driver if WPA support has been implemented.

---

### Post by monomaniacpat on 2007-06-14
Hi again,

I've posted in the howto - don't know if you noticed.

I basically uncommented the interfaces file. Now it just hangs on boot-up. I can only get it to boot if I comment out wlan0 and it's settings or pull the card out of the machine. 

Once when I did this I re-inserted the card and it listed it's attempts at connecting. So it looks like something's not right.

Here's my /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.5
gateway 192.168.1.1
netmask 255.255.255.0
wpa-driver wext
wpa-ssid PolyandorUS
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <64 character key>

auto eth0
iface eth0 inet dhcp

```

And my custom written /etc/wpa_supplicant/wpa_supplicant.conf

```

network={

	ssid="PolyandorUS"

	key_mgmt=WPA-PSK

	psk=<64-character key>

}


```

If I have my wlan0 commented out, I get scan data, if I have it uncommented, but obviously after pulling out the card and inserting it after boot up, I get "resource temporarily unavailable".

What are the various commands for setting up networking after boot and do they work with the interface commented out? Any ideas?

---

### Post by panurge77 on 2007-06-27
I used to have a 8180... the trick with it was you had to set the password before the essid name on the interfaces file, but that was for wep... I never used wpa. You can still try anyway.

---

