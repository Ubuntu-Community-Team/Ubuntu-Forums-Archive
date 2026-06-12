---
title: "HOWTO: Ralink success guide"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by 4lc0h0l1c on 2008-08-08
Hi everyone.  As a new Linux/Ubuntu user, I had a LOT of trouble getting my wireless Ralink chipset device to work.  Eventually I figured it out.  I followed all the guides I could find but they did not each have each piece of information I needed.  This is from my post on Linuxquestions ( [http://www.linuxquestions.org/questions/linux-networking-3/ralink-wireless-unable-to-connect-660355/#post3238037](http://www.linuxquestions.org/questions/linux-networking-3/ralink-wireless-unable-to-connect-660355/#post3238037) ) when I got everything working.  I am right now using Wicd and a wireless static IP with WPA2.

I have: Zonet ZEW2500P USB Wireless Adapater, which I read uses the Ralink chipset, which I read uses the RT73 driver.

The guide:

Ok. I've got it working now. This is a detailed description of all the steps I followed to success, because by the end I was convinced it wasn't going to happen.

For future headachers: there are THREE THINGS you need to know to get this working:

1) KEVDOG KEVDOG KEVDOG
kevdog is a user who posts on the Ubuntuforums. I would say that 95% of everything I read that contained useful or helpful information were posts where he was responding on threads trying to help people. I think I'm going to send him a thank you card. In 99% of cases I bet you could get this working just by reading all his posts.

2) You need to use the correct driver! Although they are no doubt very similar only ONE of all the Ralink drivers actually works for me!

3) wpa_supplicant needs to be up and running!! (Note that I could not connect even to non-authenticated networks before this, probably due to configuration problems beyond my understanding) The other programs I used to try to connect were supposed to running wpa_supplicant but they did not!
This command ended an entire week's worth of headache:

wpa_supplicant -D wext -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -dd

sudo dhclient wlan0


Detailed steps:

1)
Getting the correct drivers:

For others with this card (which btw aside from the Ubuntu problems I do recommend), be aware that the disk contains a windows installer which must be run before you have access to the drivers on the disk, so you must have access to a Windows installation or emulator. I ran the installer in Wine and it crashed out halfway through, looked like it kept installing, but didn't actually copy the driver files anywhere. I used Sun's VirtualBox to complete an actual installation, and the driver files went in C:\Program Files\RALINK\RT7x Wireless LAN Card\Installer\WINXP\. I copied the whole Ralink folder to my Ubuntu installation using smb networking (I never got the VirtualBox shared folders working for some reason but I can network Ubuntu to the virtual XP) and used a nifty utility called ndisgtk to make a driver for ndiswrapper out of the windows driver. Be aware that ndisgtk is just a front-end for ndiswrapper tools; when I had my wireless working before I used CLI (command line interface) to create drivers with ndiswrapper, so if you want to go that route read some documentation on ndiswrapper.


2)
My hardware and required driver:

I have a Zonet ZEW2500P external USB adapter, which uses the Ralink chipset. The driver that works for me is rt73, which is widely available I believe from the serialmonkey site or Ralink support. Also I have my manufacturer's disk from buying that card, which as rt2500usb and rt73 on it (possibly others). When I had wireless working before, I thought I had used rt2500usb, but when I load the rt73 modules it recognizes my USB card and it doesn't with any other driver. I will explain more about this below.


3)
Blacklist modules

I blacklisted all of my rtxx drivers in /etc/modprobe.d/blacklist:

blacklist ipv6
blacklist rt2400
blacklist rt2400pci
blacklist rt2570
blacklist rt2500
blacklist rt2500usb
blacklist rt2500pci
blacklist rt2x00
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt73usb
blacklist rt73
blacklist b43legacy
blacklist bcm43xx
blacklist b44
blacklist ssb

The b43legacy and below is from before, when I decided it was a good idea to install Broadcom wireless chipset stuff also, because Ubuntu seems to detect that I have onboard Broadcom wireless even though I don't, so I installed to see if I did and didn't know it or something. All that did was confuse things and when I had my actual Wireless adapter plugged in it would recognize two copies of each wireless network, one from my actual adapter and one from the Broadcom adapter it thought it had.

Blacklisting ipv6 makes your internet connection run much faster unless you actually use ipv6  Google this for more info

IMORTANT Note I am 99% sure the actual rt73 module would work for me just as well as the one I load with ndiswrapper. A process of elimination helped me determine which drive I actually needed, although there are other ways to obtain this information, and I got identical results using the rt73 module as with the ndiswrapper rt73, I just didn't figure out how to get the rest of it working until I had already blacklisted rt73 and used ndiswrapper.

You will see reports that you need to reboot after modifying the blacklist file; that is sort of true. The blacklist file controls what modules are loaded on startup. You can still add and remove modules just fine while running. I just updated my blacklist file every time I added or removed modules to test stuff out, so that blacklist was in sync with what I was actually doing, so I wouldn't get confused if I did reboot.

4)
Unload all other modules that might affect things!!
Look at the list of drivers you have blacklisted and remove them all:

sudo modprobe -r moduleName

I believe you can also insert and remove modules with insmdo and rmmod. I have no idea what the difference is between that and modprobe.
To know if you have modules loaded that you need to unload, run

lsmod | grep moduleName

If you are using ndiswrapper, you do NOT want any rtxx modules loaded because ndiswrapper has them. So do: lsmod | grep rt and if there are any other ralink related modules, remove them. Note that modules have dependencies so you may have to remove other modules first, for example, when I had rt2500usb loaded, it would also load rt2x00lib and I think one other one. I couldn't remove rt2x00 lib because rt2500usb was running and depended on it (although when I removed rt2500usb it automatically removed rt2x00lib). Newbie note: removing modules doesn't take them off your system, it just unloads them.

If you really can't get all the modules unloaded, make sure they're blacklisted and reboot your system. I found that modules I had blacklisted WOULD still load if I had not blacklisted another module that loaded & depended on it, hence all the b43, b44 stuff being blacklisted.

Also, to see what a module actually depends on, run
modprobe --show-depends moduleName (it will list itself there too)


5)
Make sure that ndiswrapper has the correct drivers loaded:


$ ndiswrapper -l
rt73 : driver installed
device (148F:2573) present (alternate driver: rt2500usb)

I see that it says rt2500usb is an alternative driver (it is still loaded on my system). This is the driver I thought I had gotten working before. I know that rt73 is the correct driver for my device because running lsusb, which lists usb devices connected my computer, shows:
$ lsusb
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp.
Bus 001 Device 001: ID 0000:0000

See the 2573? I think that indicates I need to rt73 driver. Als, I bet if I were to google 148f I may find lists of device IDs and drivers that would indicate the same.

On my computer I also have the modules usbcore and ohci_hcd loaded. I don't know what these are for but I think this is standard, so if you are having problems and don't have these it may be a cause. Check:
$ lsmod | grep ndis
ndiswrapper 192920 0
usbcore 146028 3 ndiswrapper,ohci_hcd

If you had any other rt modules loaded while ndiswrapper was loaded, you probably need to unload ndiswrapper after unloading the others, then load it back up. I say this because I assume if there are multiple conflicting drivers present, when ndiswrapper loads and the driver attempts to connect to your card, it probably won't succeed.

Run dmesg to see if your wireless card it recognized correctly:
$dmesg
-----------a lot of other stuff, just look at the bottom of the output--------
[ 132.515635] eth0: Setting full-duplex based on negotiated link capability.
[ 2396.406193] usb 1-2: new full speed USB device using ohci_hcd and address 2
[ 2396.754903] usb 1-2: configuration #1 chosen from 1 choice
[ 2397.245039] usb 1-2: reset full speed USB device using ohci_hcd and address 2
[ 2397.554008] ndiswrapper: driver rt73 (Ralink,03/08/2006, 1.00.05.0000) loaded
[ 2399.789134] wlan0: ethernet device 00:e0:4c:18:cc:ee using NDIS driver: rt73, version: 0x0, NDIS version: 0x500, vendor: 'IEEE 802.11g Wireless Card.', 148F:2573.F.conf
[ 2399.795708] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

Also, viewing the system log file at /var/log/syslog can be helpful. I would recommend loading this in a GUI text editor (I use kate), not command line like nano, because it's HUGE. The bottom of the file contains newest entries. Among all the "warning: not loaded blacklisted module..." entries it says: 
[ 2397.245039] usb 1-2: reset full speed USB device using ohci_hcd and address 2
[ 2397.554008] ndiswrapper: driver rt73 (Ralink,03/08/2006, 1.00.05.0000) loaded


I think that I have programs on my system that are still trying to load all the rt modules I blacklisted, and that is why I have about a hundred "not loading blacklisted module rt73" and "not loading blacklisted module rt2500usb" lines. I assume it would be more efficient to stop the system from trying to load those, so if anyone knows how to find out what programs are doing that and turn them off, let me know.

[Edit: I fixed this. Skip to the bottom of this edit for the fix; I am going to explain it here. Open the /etc/udev/rules.d/ directory. In here should be a a file ending in "modprobe.rules". On mine it is /etc/udev/rules.d/90-modprobe.rules. Towards the end is a section that says "load drivers that match kernel-supplied alias." I don't know anything about aliasing, but I remembered that at some point during this whole process some program made aliases for my wireless connection, such as rausb0 or ra0 instead of wlan0. This was in the file /etc/modprobe.d/ralink. This file contained: 

alias wlan* rt2500usb
alias ra0 rt2500
alias rausb0 rt2570

which are the modules the system log said it kept trying to load. I simply (backed up this file and) erased the contents of it. I rebooted my machine to see if it still tried to load those modules and bingo, it did not. Note the first time I rebooted after this the system froze after it finished loading everything, before it entered the login manager. I rebooted again and have not had this problem since. I think you could probably safely just delete the ralink file. I recommend always making backups when messing with config / system files.
END EDIT]

At this point you should be able to run
iwlist wlan0 scan
and see wireless networks even if you cannot connect to them. (If you can, lucky you). All the wireless utilities I tried would show wireless networks but would fail to connect with WPA on. If WPA is off, they would report a successful connection but still wouldn't be able to connect. Running sudo dhclient wlan0 now would time out waiting for DHCPOFFER.


6)
Setting up /etc/network/interfaces and /etc/wpa_supplicant/wpa_supplicant.conf

I believe at the time I got this working my /etc/network/interfaces contained only:

auto lo
iface lo inet loopback
iface wlan0 inet dhcp
auto eth0
auto wlan0
wireless-mode managed
wireless-essid any

I don't think the last two lines are necessary for this to work.

/etc/wpa_supplicant/wpa_supplicant.conf contains:

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=myGroup
ap_scan=1
network={
ssid="mySSid"
key_mgmt=WPA-PSK
psk="myAsciiPSK"
}

# associate with any access point
network={
key_mgmt=NONE
}

I recommend setting a group so that wpa_supplicant doesn't need root / admin privileges every time it wants to do something. I haven't actually tested this yet but it should work. In KDE I have a user manager, Kuser (I think). It is in my Systems list off the menu, from my KDE4 installation (I switched back to KDE3 cuz 4 blows).
I have my network info tabbed over for spacing (which I can't enter in here) but I don't think that affects the config file in any way.

You probably need to restart your networking to reload /etc/networking/information. I don't know exactly how to do this other than restarting your computer, but I think one or both of these commands might do it:

/etc/init.d/networking restart
/etc/init.d/dbus restart

You probably need to sudo those. A lot of system services use dbus, so I don't think it's a good thing to do. You could probably google and find the exact command to reload interfaces.


7)
Load wpa_supplicant:

wpa_supplicant -D wext -i wlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -dd

sudo dhclient wlan0

-D is for the driver to load. For some reason I had to use wext even though I am using ndiswrapper to load rt73. -i is the interface I use for my wireless, wlan0. A lot of people have their wireless on eth1 so you may need to change this. -c is the wpa supplicant config file, usually at /etc/wpa_supplicant/wpa_supplicant.conf. The -dd is for extended debugging information.

This command is usually run by other programs. From what I've read wpa_supplicant is supposed to have front-end programs that do all these things for you. One of the main problems I had is that this did not occur; that is why I was able to connect on the command line by using iwconfig and iwpriv to set my essid and psk and everything, but I still couldn't connect with any wireless manager utility.

After running the command in a shell I had to enter

sudo dhclient wlan0

to get a DHCP lease from the router. As for static IPs in this situation...I have no idea, other than that after I entered the wpa_supplicant command, my utilities were able to manage my connection, and wicd (among others) has options for static IP, so I guess that would do it. I'll find out anyway because I have to connect to a non-broadcast static IP network soon. I'll post here if I get it working. You could probably enter in your static IP information into /etc/networking/interfaces also. Google for how to do that.

Also note: during the process of doing all this, I uninstalled network managers and my wired connection no longer auto connected. To connect to your wired (assuming you're like me and have that luxury while trying to get wireless to work), do: (eth0 is my wired interfaces)

sudo ifconfig eth0 up
sudo dhclient eth0

8)
Now what?

I don't want to have to connect manually to wireless every time I want to get online. Why can't it be like windows, where all I have to do is turn my computer on, and if there's a wired connection, use that, otherwise connected to the fastest wireless network that's available? Well, there are a few options for this. One would be to write a startup script that automatically tries to connect to wired, and if that fails, runs an iwlist wlan0 scan and then tries to connect to all of those. I don't know how to do that.

I read that putting
wpa-driver wext
in /etc/network/interfaces should make it automatically use wpa_supplicant. I put that line in mine after "iface wlan0 inet dhcp".

I read about (and installed but haven't used) a utility called ifplugd, a daemon that is supposed to do exactly what I'm asking for. I followed this guide
[http://ubuntuforums.org/showthread.php?t=43766](http://ubuntuforums.org/showthread.php?t=43766)
and also installed the latest wicd that is supposed to be able to do the same thing, stable wicd-1.5.1 from [http://www.wicd.net/latest](http://www.wicd.net/latest) (I read the latest is a lot better than repo version).
I also read [http://wicd.net/punbb/viewtopic.php?pid=373](http://wicd.net/punbb/viewtopic.php?pid=373)
and ran
sudo update-rc.d wicd start 80 2 3 4 5 . stop 20 0 1 6 .
which is supposed to make wicd not ask for your password every time the computer boots up.

I have not tested most of the stuff in Section 8 here. I have just done it and I will see how it works. Wicd did automatically connect to my wired when I booted, although I didn't have my Wireless plugged in, but any number of network managers do that. I think a lot of them can probably automate this process and there's probably other scripts that can be run. The important part is that I got wireless with WPA working finally, after a week's worth of hassle. The main problem is that wpa_supplicant was not automatically started by other programs when I think it was supposed to be. I don't know why this was, and I don't know why I still couldn't connect to unsecure networks when wpa_supplicant wasn't loaded.

Good luck.

[EDIT: The above configuration does seem to work. The system automatically connects to my wired network, and is able to connect wirelessly without me explicitly loading wpa_supplicant. It is not automatically connecting to wireless networks if there isn't a wired connection present, which I think may be due to something with wicd. I am researching that now.]
[The most likely reason I have found is that the system may take longer to register the wireless adapter than wicd takes to run its autoconnect logic on startup. However that is too far beyond the scope of my original topic for me to cover here.]

---

### Post by lbharti on 2009-03-13
Now this is what I needed. I would try this when I get home. Thanks for sharing.

---

### Post by 55Phils on 2011-11-17
This is exactly what I was looking for. Thanks a bunch.

---

