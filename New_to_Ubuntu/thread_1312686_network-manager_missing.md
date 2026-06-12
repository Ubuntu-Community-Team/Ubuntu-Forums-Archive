---
title: "network-manager missing"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Ginger The Cat on 2009-11-03
I am running 9.10 and was enjoying trying out things at random in the Ubuntu Software Centre on the Applications menu. (probably not a good idea)

I can't give you a list of all the things I tried, some I kept, some I immediately uninstalled.

At the end of it I noticed my network had gone and along with it the network-manager icon that usually displays my wireless network.

I suspect something I tried uninstalled it ?

I thought I could just reinstall it using the CD. I went to System, Admin, Software Sources and unchecked all the "Downloadable from the internet" items and checked the CD with Ubuntu9.10 Karmic Koala.
I got a warning my software was out of date and that I need to Reload. I need a working internet connection for this so I clicked Close.

When I go into Synaptic Package Manager I found that network-manager shows up with a white square and no text in the other columns 

In the new Software Centre, network-manager shows up as "Not available in the current data"

I tried typing sudo apt-get install network-manager-gnome
Reading package lists... done
Building dependency tree
Reading state information... done
Package network-manager-gnone is not available but is referred to by another package.
This may mean that the package is missing , has been obsoleted or is only available from another source.
E: Package network-manager-gnome has no installation candidate.

I also read somewhere you need to do sudo apt-cdrom add but this didn't help.

Any ideas how I can get this working again?

Thanks

Mike

---

### Post by MelDJ on 2009-11-03
right click the top panel and press add to panel. then add notification area

---

### Post by Ginger The Cat on 2009-11-03
That just adds 3 small horizontal lines. I already had one of those.

---

### Post by wrgb2 on 2009-11-03
Have you tried running Synaptic and then putting the CD in the drive?

---

### Post by danastasio on 2009-11-03
well to get your connection back, TEMPORARILY, in  a terminal run

first you need to find the type of wireless card you have and how your system recognizes it.

```
ifconfig
```

you should see a left hand coloumn and in that column, things like "eth0" "lo" "wlan0" or "ath0"

"eth0" your ethernet connection
"lo" is your loopback port, it is what the computer uses to talk to itself, and how programs communicate with each other.
"wlan0" and "ath0" are your wireless capabilities.

assuming that you know the name of the network that you want to join, and you have wlan0 and not ath0:

```
sudo iwconfig wlan0 essid NETWORKNAME
```

when that clears with no problems, run:

```
sudo dhclient
```

and wait for that to connect.

that will get you a working internet connection for the time being, i would try to install the network manager from there

```
sudo apt-get install network-manager
```

or the iconset

```
sudo apt-get install network-manager-gnome
```

and if that fails you can try installing wicd. it is a program that many people (myself included) use to connect to the internet, it will replace network-manager completly.

```
sudo apt-get install wicd
```

then run it under applications->internet->wicd network manager

hope that helps!

---

### Post by Ginger The Cat on 2009-11-03
I have now. Nothing happened.

There is a complete lack of networking on my computer.

My /etc/network/interfaces is
auto lo
iface lo inet loopback


Is there a manual way to get online without network-manager then when I am back online I can try loading it again the normal way?

Our posts crossed. I'll try your suggestion and get back to you

---

### Post by Ginger The Cat on 2009-11-03
All I get from ifconfig is lo

---

### Post by Ginger The Cat on 2009-11-03
I needed to do ifconfig -a to see all the interfaces

I followed your suggestion which looked good but failed in the end with "no DHCPOFFERS received"

I guess it needs the WPA key. How can I specify that?

Thanks

Mike

---

### Post by danastasio on 2009-11-03
hmmm give me a second for that

---

### Post by danastasio on 2009-11-03
> **Ginger The Cat said:**
> I needed to do ifconfig -a to see all the interfaces

I followed your suggestion which looked good but failed in the end with "no DHCPOFFERS received"

I guess it needs the WPA key. How can I specify that?

Thanks

Mike

What type of WPA is encrpting your network?

---

### Post by Ginger The Cat on 2009-11-03
Not WPA2. Just the original one.

---

### Post by Ginger The Cat on 2009-11-03
Wpa-psk

---

### Post by danastasio on 2009-11-03
alright my network isn't encrypted (so sue me) so i dont know the commands myself, but i'll quote you a section from [here]("http://ubuntuforums.org/showthread.php?t=571188")

> WPA-PSK - Covers WPA(1) and WPA(2)

1. Creation of /etc/wpa_supplicant.conf file

At command line:
Code:
gksu gedit /etc/wpa_supplicant.conf
Inside the file add the following for WPA(1):

Code:
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
}
For WPA(2) (see this thread: [http://ubuntuforums.org/showthread.php?t=607410):](http://ubuntuforums.org/showthread.php?t=607410):)
Code:
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="ESSID_IN_QUOTES"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
        group=CCMP TKIP
}
***Word of caution -- In some cases I have found WPA(2) to have different settings than the above. Some Broadcom cards use the pairwise/group TKIP cipher for WPA2 rather than CCMP. I would suggest all initially use WPA(1) and then later convert to WPA2 since some variations to the above may be needed

**WPA2 capabilities must also be built-into the driver set used with your hardware. If using ndiswrapper with an old windows driver, the driver may not contain code for wpa2. 

2. Connect via command line
Code:
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo wpa_supplicant -D<****see footer below***> -i<interface> -c/etc/wpa_supplicant.conf -dd 

***Note that starting with the -dd flag will create a lot of debuggin output.
If you choose to use the -dd flag to troubleshoot your connection, you must 
open up a separate terminal and type the rest of the commands listed below in a
separate terminal window.  You can also replace the -dd flag with the -B flag to
send the process to the background, avoiding the need to open up a separate
terminal window (however no debugging output will be generated) 

sudo dhclient <interface>
***footer
The value listed here is dependent on the driver you have installed. Typing man wpa_supplicant at command line will give you the full gamut of choices however most recent versions of wpa_supplicant only recognize wext as the appropriate value (Despite all the information on the internet). If you would like to verify what drivers besides wext your installed version of wpa_supplicant recognizes, type at the command line:
wpa_supplicant -l
And look specifically at the section called drivers:

Here is what my stock wpa_supplicant lists for its drivers:

drivers:
wext = Linux wireless extensions (generic)
atmel = ATMEL AT76C5XXx (USB, PCMCIA)
wired = wpa_supplicant wired Ethernet driver

Other drivers can be compiled into wpa_supplicant if you compile wpa_supplicant, however please not that in recent kernel versions this is unnecessary. wext will work for ndiswrapper, madwifi, intel, etc.

---

### Post by Ginger The Cat on 2009-11-03
Excellent.

Worked first time.

Thank you very much for your help.

Mike

---

### Post by danastasio on 2009-11-03
glad i could help, are you all set with your graphical manager as well?

---

### Post by Ginger The Cat on 2009-11-03
> **danastasio said:**
> glad i could help, are you all set with your graphical manager as well?

Yes it all seems as it was before. i.e. excellent. :D

---

### Post by ben2talk on 2012-02-13
This guide doesn't help - 

```
sudo apt-get install network-manager
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package network-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'network-manager' has no installation candidate
ben @Serenity 12:48 PM 
[/]  install wicd
Working...
E: Unable to locate package wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package wicd
-e 
Done! Verify that all packages were installed successfully. If errors are found, run apt-get clean as root and try again using apt-get directly.

```

---

