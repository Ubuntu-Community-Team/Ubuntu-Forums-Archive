---
title: "Roaming on ubuntu"
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Dooley on 2008-01-17
Hi there,

Im not sure if these are the entire steps for setting up roaming on ubuntu but for some reason this doesnt work. These are my config files.
##This is my /etc/network/interfacess
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

allow-hotplug eth1
iface eth1 inet manual
    wpa-driver wext
    wpa-roam /etc/wpa_supplicant.conf

iface network1 inet dhcp
iface network2 inet dhcp


##This is my /etc/wpa_supplicant.conf
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

network={
id_str="network1"
ssid="net1"
scan_ssid=1
key_mgmt=IEEE8021X
eap=LEAP
identity="username"
password="password"
phase2="MSCHAPV2"
priority=3
}

network={
id_str="network2"
ssid="net2"
scan_ssid=1
key_mgmt=IEEE8021X
eap=LEAP
identity="username"
password="password"
phase2="MSCHAPV2"
priority=2
}

This is all I have done. The wpa_supplicant config works grand 
when I connect to it manually via a script. 

I tried sudo ifconfig eth1 essid any
and all I get is cannot find hostname errors.

Can anyone point me to a decent guide for this or has spotted any problems I might have in my config files?

Thanks in advance for any help!

---

### Post by Dooley on 2008-01-17
Can anyone help? I don't think this is a hard problem to solve, it's quite specific.

Thanks.

---

### Post by Dooley on 2008-01-17
Bump, can anyone help. I really don't think this is  a big issue.
Seriously can anyone help??

---

### Post by ugm6hr on 2008-01-17
I just wanted to let you know someone is reading your post.

But I'm afraid I have no idea what you are trying to achieve.  My Ubuntu Gutsy has wifi roaming out-of-the-box with Gnome Network Manager.

I didn't think it was possible to roam from Command Line.

---

### Post by julian67 on 2008-01-17
your interfaces file should look like this ```
auto lo
iface lo inet loopback

``` and network manager applet and gnome-keyring will do the rest.  Any reason for wanting to do it by hand?  Different desktop environment or wireless card that doesn't work with nm?

---

### Post by Dooley on 2008-01-18
Im actually connecting to a college network and network manager doesnt seem to like the wireless networks, but ill give it another go.

---

### Post by ugm6hr on 2008-01-18
> **Dooley said:**
> Im actually connecting to a college network and network manager doesnt seem to like the wireless networks, but ill give it another go.

Wicd is another option if NM doesn't work.  See the wifi link below.

---

### Post by Dooley on 2008-01-18
I tried wicd its a nice looking GUI much better than network manger, but again no luck connecting. It only detected one of my two networks. And it wouln't get an ip from it. Network manager was a definite no go. 

Thanks anyway, though if you happen to know a command line way, that would be great.

---

### Post by ugm6hr on 2008-01-18
Why not start from the beginning.  It may be a problem with either your router's settings, or your wifi card.

Can you connect from Terminal at all?  Sounds like you can.

If yes, it is likely you have  a ra, realtek or prism chipset wifi.  Wicd has been trying to improve support for these, but the settings need to be appropriately modified.

```
lspci
lshw -C network
```

The output of these will tell you which chipset and driver you have.

---

### Post by Dooley on 2008-01-18
I have an Intel PRO/Wireless 2200BG Network Connection.
I can connect with no issues via a command line script using only the settings I have specified above

The script is
sudo ifconfig eth1 down
sudo ifconfig eth1 up
sleep 3
sudo killall ssh
sudo killall dhclient dhclient3
sudo killall wpa_supplicant
sleep 3
sudo wpa_supplicant -B -ieth1 -Dwext -c/etc/wpa_supplicant.conf
sleep 3
sudo iwconfig eth1 essid network1/2
sleep 3
sudo dhclient eth1

And I would simply like to circumvent this by automatically connecting to the wireless networks I can be authenticated to.
When I used wicd I entered in that Im using LEAP with WEP, my username and password and tried connecting with no luck.

---

### Post by ugm6hr on 2008-01-18
If you have an Intel chipset, Network Manager (or Wicd) should connect with roaming out-of-the-box, as long as you use DHCP (i.e. not a fixed IP), which it looks like you use.  Must be something to do with WEP/EAP maybe?  And is your SSID hidden?  That also causes problems with NM.

Wicd *should* work, but obviously doesn't for you :(  

If you have no luck with the CLI method, maybe try asking for help to get Wicd working on the Wicd forum.

Sorry, I don't know enough about networking to help any more.

---

### Post by Dooley on 2008-01-18
Yeah im using dhcp and yes the networks are hidden. 

Thanks anyway for all the help, I might just ask around on the wicd forum.

---

### Post by ugm6hr on 2008-01-18
Only other thing with Wicd is that sometimes you have to enter the passord in "" (i.e. include the " marks when you type it in).

Good luck with this.

---

### Post by Dooley on 2008-01-18
Cool,

I'll give that a go when I get back to college. My wireless network isnt configured yet.

Thanks again for the help.

---

### Post by Dooley on 2008-01-21
I gave WICD another go, with the password in ""'s no luc sadly.

It halts trying to obtain an ip.

The ssids are hidden, and wicd seems to see them one I add a new hidden ssid. Could this be where wicd fails?

---

