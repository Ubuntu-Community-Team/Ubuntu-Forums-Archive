---
title: "Wifi problems - Atheros AR5007EG"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by Jesuses Left Leg on 2008-03-01
Ok so I am having problems with my Acer Aspire 5315 and its wireless.  Up until now it was working perfectly fine using ndiswrapper and I as happy with that but it has suddenly stopped working for seemingly no reason.

What happens is I can see all the networks near me but Ubuntu will either connect to the network telling me it will have like 70% strength then tell me it is now 0% and give me no internet or it won't connect at all.  This has been tried with various network managers.  It seems to have a problem aquiring the IP of the router for some reason, but I can connect with my desktop wirelessly and with another computer through a cable so the router is fine.

The bizzare thing is I dual boot and windows is doing the exact same thing and started at the exact same time.
By the way I have searched already.
Help would be MUCH appreciated.

Here are some outputs too if they help
iwconfig output:
```

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"Livebox-DE60"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci output:
```

06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)

```

ndiswrapper output:
```

matt@matt-laptop:~$ ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

```

---

### Post by calraith on 2008-03-01
I have wifi working without ndiswrapper using madwifi.  Hey, try something for me, o guinea pig.  If this doesn't work, I'll post an alternative that I'm sure will work.

Unload your ndiswrapper driver.  Save this to get_madwifi.sh, chmod it 744, and run it:
```
#!/bin/bash

# Try this:
if [ "`whoami`" != "root" ]; then {
        echo "Please use sudo or launch this as root."
        exit 1
}; fi
WICD=`grep 'http://apt.wicd.net' /etc/apt/sources.list`
if [ ! "$WICD" ]; then {
        echo 'deb http://apt.wicd.net/ gutsy extras' | tee -a /etc/apt/sources.list
        apt-get update
}; fi
apt-get install madwifi-tools hostapd wpasupplicant wicd -y --force-yes
exit 0
```Then add /opt/wicd/tray.py to your session startup list.

After you reboot, click the wicd tray icon and go to the Preferences tab.  Change the WPA Supplicant driver to madwifi, and the wireless interface to ath0.  Hit OK, then configure your wireless connection for the AP to which you want to connect.

If it works, it'll simplify things for a lot of people.  Like I say, if not, I'll post something that I know will work.  I bet all this will be a moot point when Hardy hits final release, though.

---

### Post by Jesuses Left Leg on 2008-03-02
Thanks for the help but it seems madwifi is not recognising my card as iwconfig shows no wireless devices and wcid shows no wireless networks, only my wired connection.
I did actually try madwifi previously with a patch but i believe I did it wrong that time because I was pretty tired but it does not seem to work even now I have done it properly.
Thanks a lot for the help, what is your 2nd solution? :KS

---

### Post by calraith on 2008-03-02
Keep wicd, just because I know it works and it's nicer than Gnome's nm-applet, in my humble opinion.

Anyway, yeah, the patched madwifi is how mine works.  Do the following:
```
sudo apt-get install build-essential linux-headers-`uname -r`
cd /usr/src
wget 'http://headcandy.org/rojo/madwifi-ng-r2756+ar5007.tar.gz'
tar -xvzf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
sudo make install
```Reboot, and see whether wicd will now recognize the madwifi driver and ath0.

If not, you might also need "acer_acpi,"  It's easily Googlable, and I believe has already been replaced by something more up-to-date in Hardy (although not quite working for me yet with the current Hardy alpha kernel).  If you install acer_acpi, be sure to modify /etc/modprobe.d/blacklist and comment out its blacklist entry, as well as add acer_acpi to /etc/modules.  The acer_acpi module is how I got sound and some of my keyboard hotkeys working.

If you need to install acer_acpi, I believe it'll also mess with your network interfaces, treating your firewire port as eth0.  If it does, you can modify /etc/udev/rules.d/70-persistent-net.rules, switching eth0 and eth1 on whichever devices have eth? assigned.

---

### Post by Jesuses Left Leg on 2008-03-02
I appreciate the help you're giving me but I still cant see my device with madwifi. It is not in iwconfig nor are there any networks in wicd.
I have installed acer_acpi as well but there was no blacklist entry for it to delete. Also I dont have a firewire port so I dont think that will be a problem.

Any suggestions as to what is going wrong/what I am doing wrong.

---

### Post by scottro on 2008-03-02
I think you might need to do a couple of other things.  I'm assuming this is a 32 bit machine--if it's running 64 bit, then ignore the rest of this.
Go back into the untarred madwifi directory.
```

cd madwifi-ng-r2756+ar5007
sudo make uninstall
sudo make clean
sudo make
sudo make install
sudo rmmod ath5k
sudo modprobe ath_pci

```

Their advice is to always do a make clean if there are previous installations.
The ath5k module (if present) can interfere, so we remove it.   (Sudo isn't necessary for all those commands, but won't hurt anything)
Also, I believe the modprobe ath_pci will be necessary. (You'll want to blacklist that ath5k module in the future).
Now, at least see if it's recognized, either as ath0 or wlan0, more likely ath0.

If not, add ath5k to /etc/modprobe.d/blacklist (if it's not there already) reboot and see if you have any luck.

---

### Post by Jesuses Left Leg on 2008-03-02
Thanks scottro I now have in iwconfig output a wifi0 which says no wireless extensions so I can ignore I assume and I also have wlan0 back and can see all my networks in wicd.  This is great so thanks but the problem I began with in Ubuntu and Windows still remains. That is I can see the networks but cannot connect using wicd (or anything else). It will just repeat obtaining IP address at the bottom and then return 'not conected' as its status.
I am not sure what the problem is as I can see the networks in both Ubuntu and Window XP but cannot connect in either :confused:.

EDIT: In fact in wicd I have just found that if I manually set the IP, gateway, DNS etc it will connect but i cannot access the internet or the router's config pages.
Also I cannot ping the router by its config page address but I can by its IP I gave to wicd.

---

### Post by scottro on 2008-03-02
I'm glad you got the card visible at least, that's a start.  
I don't use wicd.  In Ubuntu, I just NetworkManager without issue.  (I use other things in other distros, but that won't really help.)

Since you say the issue also occurs in Windows, I wonder if it's possible that the card is defective.  (Maybe you could get it replaced with a card that's supported out of the box.)  :)

You might try using the command line and seeing what sort of errors you get.   (The commands depend upon what sort of encryption is used on the network.)  
Hopefully, the fellow who first recommended wicd will have some ideas.  I've only experienced something similar with an abortive effort to use ndiswrapper on a 64 bit install.  (The mad wifi drivers don't work with 64 bit.)

---

### Post by Jesuses Left Leg on 2008-03-02
It would be nice to have an out of the box card. I wouldn't mind if this laptop wasn't new and the card wasn't integrated into the laptop so no funny sticky out cards.  If i run wicd from the terminal i just get 'connecting' it never tells you if you have connected even when you have so thats really of no help.  I may reinstall network-manager just to see if that makes any difference.

I dunno if this would help but I shall type it anyway. The problem only arose after I had to reinstall Ubuntu (wireless was working then) as it wasn't booting properly. I reinstalled and set up my wireless, sound and compiz effects (don't work out of the box).  I rebooted a few times and then wireless had suddenly stopped connecting the next day on windows. So i boot into ubuntu and the same problem is there.  This was when I was using ndiswrapper so I tried reinstalling all that and setting it up again to no avail.

I am tempted to just reinstall both Windows and Ubuntu to see if it fixes itself.:confused:

edit: from what I can understand teh card can see the network but it cannot acquire the IP etc from it and if I give it that information manually it just claims to be connected but I've tried giving it random IPs that aren't mine and it just tells me it is connnected but it can't be.

---

### Post by calraith on 2008-03-02
If your wireless device sees the wireless access point but can't associate with it or association is unstable, sometimes it helps to unplug the power from your wireless access point, leave it unplugged for about 10 seconds, then plug it back in.  If your problems are happening both in Windows and in Linux, and both started at the same time, I would imagine that means that the router / access point has lost its sanity for some reason.  It happens, from time to time.

If a reboot of the router fixes the problem, it wouldn't be a bad idea to check the device manufacturer's website to see whether a firmware update is available.

For what it's worth, I'm still convinced that Hardy will fix a lot of our Acer laptop woes.  In the current Hardy alpha kernel, I think there's at least half-assed support for acer_acpi (blacklisted in favor of acer_laptop, which doesn't quite seem to work yet, possibly because I'm running the hardy kernel with the gutsy c libraries and so forth); and I think I read somewhere that the ar5007 patch is being considered for inclusion in the Linux kernel.  Don't ask me to cite source, though ;)

---

### Post by Jesuses Left Leg on 2008-03-02
Well it's not the router because I had already tried resetting that assuming that was the problem and also I can connect to it from my desktop wirelessly and through a cable. All I can think is that the card itself is faulty because the same problem keeps coming up again and again. Luckily it is under guarantee still so I can just get a new one hopefully or at least get mine fixed.

Thanks for the help you've given me though, it will be useful when I get this problem fixed for making sure my wireless works well in the future. Inclusion in the kernel would be nice cos Hardy is looking very nice so far. Fingers crossed eh :)? 
Thanks a lot guys!

---

