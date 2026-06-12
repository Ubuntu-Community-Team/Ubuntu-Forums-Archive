---
title: "WPA WiFi with ipw3945"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by irober02 on 2007-01-11
I've just upgraded my Dell Insprion 6400 to Edgy (to get my ATI graphics working properly -now I can watch videos etc v. nicely! :-)) but am having some trouble finalising the init scripts.

As I use my laptop at home almost exclusively, I don't really want to use the knetworkmanager and would rather manually configure the interface (/etc/network/interface). I am using WPA.

I tested Edgy with a workstation and that is working the way I want it (but it has an Atheros-chipped WiFi card).

When I boot my laptop the WiFi it takes a long time to boot -pausing on the 'Configuring network interfaces...' step and then fails to connect. However, once I log in, all I need to do is "sudo /etc/init.d/networking restart" and it connects promptly and perfectly (using wpa_supplicant) -seems very stable. :-)

The /etc/network/interface files for both my test workstation and my laptop are identical as are their /etc/wpa_supplicant.conf, /etc/wpa_supplicant/ifupdown.sh and /etc/init.d/networking.

I can't see any differences in the init scripts.

The invocation of wpa_supplicant on both machines is identical except the workstation uses the madwifi driver and the laptop wext.

Any suggestions how to make the laptop connect properly at boot time?

Are there significant difference between the madwifi and wext "drivers"?

Is there a config change I can make to get the laptop to connect quickly at boot? Reorder init scripts perhaps? Missing packages?

---

### Post by x64Jimbo on 2007-01-11
Your wireless interface(s) shouldn't be connecting during boot-up because you never know what network you might be getting on. The best policy with wireless interfaces is to activate the kernel module on boot, but wait until you can manage them from within the GUI to actually connect. That way you get all the help from the GUI tools that you need (they're much better at managing security than their boot-time counterparts). I know you said that you only use that one wireless network, but if you let knetworkmanager manage your connection, your boot will be much faster.

---

### Post by irober02 on 2007-01-15
I don't understand what you mean. If I supply the ESSID and encryption details then, I think, I've got pretty good control over the connection.

I've experimented with knetworkmanager and I'm finding it a bit flakey. My access point doesn't broadcast its ESSID and requires WPA encryption. I've succeeded in connecting but it's slow and unreliable.

I'd really prefer to configure my ipw3945 manually using /etc/network/interfaces. This works perfectly provided I restart the network after logging in to me laptop. There must be a simple problem with my init scripts that is preventing the connection being established at boot time.

Another benefit of the manual approach (for my situation) is that I can manually assign an IP number and mount some network shares via /etc/fstab. I don't know how to do either of those with the knetworkmanager.

Suggestions?

bye

ian

---

### Post by andrey_bakhmet on 2007-01-22
I have this problem on Dell 6400 ( ubuntu edgy) +  ipw3945. 


But can't find any solution ](*,) 

This is WPA encryption + ubuntu edgy  problem only. I try to use generic kernel, latest kernel from kernel.org, recompile ieee801, install new ipw3945 drivers, etc...

I use wext driver.

After startup wireless connection up, but without WPA. But after /etc/init.d/networking restart all works fine.

On win32 and other OS it works fine after startup:mad:

---

### Post by x64Jimbo on 2007-01-22
I have had infinite problems with WPA networks that have hidden SSIDs. Try un-hiding it. WPA is secure enough that you don't need to hide your SSID if you have a strong passphrase.

---

### Post by andrey_bakhmet on 2007-01-23
I don't use hidden SSID.


But this bug already known. See HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. Post #2   :(

---

### Post by irober02 on 2007-01-23
In one sense it's good to hear that others are having the same problem -at least I'm not imagining it nor have I done something really stupid.

It does seem strange that my connection method works perfectly as soon as I've logged in and restart the network (sudo /etc/init.d/networking restart). What is different at boot time?

I do notice that the wpa_supplicant daemon has not been invoked during boot but is as soon as I restart the network.

---

### Post by irober02 on 2007-01-23
It's also weird that my 3 computers fitted with Atheros-chipped, madwifi-driven WiFi NICs all connected perfectly via the settings in /etc/network/interfaces and /etc/wpa_supplicant.conf (expurgated contents follow).

Perhaps there are changes that I could make in one of these files to help the situation:

/etc/network/interfaces 

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
# auto eth0
# iface eth0 inet dhcp

iface ath0 inet static
address 192.168.0.##
netmask 255.255.255.0
gateway 192.168.0.#
wireless-essid XXXXXXXXX
wpa-driver madwifi # for atheros-chipped wifi
# wpa-driver wext # for ipw3945
wpa-conf /etc/wpa_supplicant.conf
auto ath0

/etc/wpa_supplicant.conf

ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1
update_config=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli

network={
        ssid="XXXXXXXX"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA2
        key_mgmt=WPA-PSK
        psk=##############################################
}

---

### Post by irober02 on 2007-01-23
I've created a networking restart init script as described in HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. That's a definite improvement as it doesn't require a manual network restart (or right to do so) for users (other users of this machine wouldn't know how to do that) but booting still takes a llllooonnnngggg time while the first attempt fails. Let's hope those un-paid volunteers who keep the whole Linux project going can fix this sometime.

---

### Post by wieman01 on 2007-01-25
> **irober02 said:**
> I've created a networking restart init script as described in HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc. That's a definite improvement as it doesn't require a manual network restart (or right to do so) for users (other users of this machine wouldn't know how to do that) but booting still takes a llllooonnnngggg time while the first attempt fails. Let's hope those un-paid volunteers who keep the whole Linux project going can fix this sometime.
This is not solution, but also a bug fix, however, all you have to do is press "crtl + c" to skip your computer's the first attempt to connect to the network.

Let's hope this will be fixed by the developers soon.

---

### Post by hippo31 on 2007-03-04
I have bought recently the same Inspiron 6400 laptop.
With my old PC (which was not a laptop) I was connecting at home using NIS, NFS and autofs through a physical ethernet link to a small home made server acting as a firewall, file server, etc...
When I switched to the laptop and by idleness I also used ethernet connection for a while. Of course all was running like a charme, nis login authentication, /home automounting
Then I said to myself that it should be fine to go on and try wifi connection. After having resolved all the difficulties that the wifi chipset (with wpa) configuration brought me up, I have been extremly disappointed to not be able to start the network connection at boot. I have to login with a local user, restart network, nis, nfs, autofs, logout and then login with an nis user.
Of course when using wifi we never know which network  we connect to, but can't we imagine that if the ESSID supplied for a default connection reaches the connection point ; then it is used in addition to all the encryption details ; else the boot process continues and the network connection is managed later ; fi ?

---

### Post by hippo31 on 2007-03-23
Isn't there here anyone with an idea on how to make wifi connection up at boot ?

---

### Post by irober02 on 2007-04-28
After updating to Feisty, I find the improved functionality of NetworkManager and smb4k obviates the need to fiddle with hard-coded interface and ftsab files. 

The Feisty support for WPA and my ipw3945 was seamless -Great work. :-)

I did have problems with my ATI adapter not working with the live CD but postings here helped me sort those out.

I swapped to kubuntu from Fedora a while ago and have progressed through Dapper, Edgy & Feisty. Even Dapper was pretty good but each successive upgrade delivered major advances in easy installability. :-)

bye

ian

---

