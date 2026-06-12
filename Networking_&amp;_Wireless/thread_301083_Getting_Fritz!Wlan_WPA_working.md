---
title: "Getting Fritz!Wlan WPA working"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by hulluPeruna on 2006-11-16
This is step by step how I got my fritz!wlan usb stick to work.
before installing ndiswrapper make sure the following packages are on your system :
1  	gcc
2  	debhelper
3  	linux-headers-2.6.15-26-386
4  	built-essentials
5  	fakeroot
6  	make

First download the latest ndiswrapper from
[http://www.kubuntu.de/forum/forum.php?req=derefer&url=http%3A%2F%2Fprdownloads.sourceforge.net%2Fndiswrapper%2Fndiswrapper-1.23.tar.gz%3Fdownload](http://www.kubuntu.de/forum/forum.php?req=derefer&url=http%3A%2F%2Fprdownloads.sourceforge.net%2Fndiswrapper%2Fndiswrapper-1.23.tar.gz%3Fdownload)
to /tmp
switch to /tmp
> #cd tmp

extract the ndiswrapper
> # sudo tar -xvf ndiswrapper-1.23.tar.gz

switch to ndiswrapper via
> #cd ndiswrapper-1.23

build the ndiswrapper
> 
# sudo	make
# sudo 	make install

now install the fritz driver from the cd. Best Copy the fwlan.inf to your home 

> #sudo ndiswrapper -i /"PATH TO THE DRIVER"/fwlan.inf

the system should tell you now that the driver where loaded
now check if hardware is present 

> # sudo 	ndiswrapper -l

now finish by adding ndiswrapper to the modules
> # sudo 	ndiswrapper -m
# sudo	modprobe ndiswrapper

to ensure that the NDISWRAPPER gets loaded on every system start edit the 	/etc/modules as root

> #sudo vi /etc/modules

add "ndiswrapper" to the bottom of the file and save

now get the wpasupplicant package 
> # sudo apt-get install wpasupplicant

create the psk key by 
> # wpa_passphrase "YOUR SSID"
and than type the key you should get something like this

> $ wpa_passphrase SSID
# reading passphrase from stdin
myssidkeyislong
network={
        ssid="SSID"
        #psk="myssidkeyislong"
        psk=35964d141dc2640e53e002948eda16e577e386e8ef71b526d4bdafaed0866f42
}

create a config file for the wpasupplicant 
> #sudo vi /etc/wpa_supplicant/wpa_supplicant.conf

add following lines to the /etc/wpa_supplicant/wpa_supplicant.conf file:

> ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
    ssid="SSID"
    scan_ssid=1
    proto=WPA
    key_mgmt=WPA-PSK
    pairwise=TKIP
    #psk="myssidkeyislong"
    psk=35964d141dc2640e53e002948eda16e577e386e8ef71b526d4bdafaed0866f42
}

You should probably test this now - here's a good command 

> # sudo ifconfig wlan0 up && wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf && dhclient wlan0

If that doesn't get you to the point where you can ping other hosts on your network, something is most likely wrong with wpa_supplicant. To figure out what went wrong here are the debug commands.
kill the client
> # sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
and fire it up in debug mode
> # sudo ifconfig wlan0 up && wpa_supplicant -w -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -dd

This will give you a bunch of debugging output.

if everything is working smoth kill the client again
> # sudo dhclient -r wlan0 && ifconfig wlan0 down && killall wpa_supplicant
Now we ensure that the usb stick integrates in our system and is available on bootup! So we edit /etc/network/interfaces:

> # sudo vi /etc/network/interfaces

and add the following lines:
> auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Save and exit.

We're all done! Remember though to unplug the network cable!!! Otherwise the system will not be able to get a ip address from the router.
once that is done reboot and TATAA it should work.8) 

Thanks to notzac and his great [tutorial]("http://ubuntuforums.org/showthread.php?t=31418&highlight=wpa_supplicant+usb") !!! That helped me to make the final step and get this up and running

---

### Post by graysnake on 2006-11-19
Thank you very much....I got my wireless working great with WPA-TKIP encryption thanks to this post!!!!!

Thanks again.

Greetings

---

### Post by StephaneLenclud on 2008-02-20
On 7.10 I had no need to do all of that to get that WLAN Fritz USB stick working.
I just installed the ndiswrapper packages I found in Synaptic (not even sure that was needed).
Then I rebooted and plug-in the device.
I was notified that Ubuntu needed to use some proprietary drivers to get my hardware working.
Then I configured the Network interface using the Network administration UI. (using WEP ascii key)
I could see the wlan0 entry in ifconfig and everything looked ok but could not ping my WLAN router.
I rebooted.
After reboot everything was working fine. My WLAN USB stick worked perfectly.
I'm looking forward to see how stable that driver is.

Ubuntu rules! ;)

P.S:
was done on a AOpen MZ915-M

---

