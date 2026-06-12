---
title: "cannot connect thru wpa-psk enable router"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by tyroach on 2008-11-21
I just installed ubuntu 8.10 on my Dell Vostro 1510 and I cannot connect thru my DLink 524 WPA-PSK enabled router.

I was able to connect thru a neighboring WiFi that had no security (so I know my card is working okay).

The closest option for me to configure thru NetworkManager seems to security settings of "WPA & WPA2 Personal", but that isn't working.  

when I do an iwconfig, I get
eth1  IEEE 802.11 Nickname: ""
Access Point: Not-Associated

I'm guessing that the best I can hope for is a command line script that I can run to set things up, but I'm not sure what to do.  I tried editing the /etc/network/interfaces as follows:

[INDENT]auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid <my_essid>
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <your_hex_key>

Next I did the following:
sudo /etc/init.d/networking restart

I get the following some text that says
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
.
.
.
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received
No working leases in persistent database - sleeping.
grep: /et/resolv.conf: No such file or directory[/INDENT]

Can anyone help?

Thanks in advance.

Oh yeah I have a Broadcom BCM4312 802.11b/g wireless interface

---

### Post by superprash2003 on 2008-11-21
have you treid WEP?

---

### Post by tyroach on 2008-11-21
no, but I did gain access through an unsecured wireless AP.

I don't want to change security to WEP as it is less secure + work to update other computers.

---

### Post by tyroach on 2008-11-21
Not sure if this is worth mentioning, but I have spaces in both my SSID and my passcode.

So my configuration looks like
wpa-ssid My Home Computer
wpa-psk <generated key>

I got the <generated key> from running the following:
wpa_passphrase "My Home Computer"
his to enjoys

I then took the generated key and copied it after wpa-psk.

I mention this because I was reading another thread where someone asked a question about spaces in the passcode so I thought I should mention that I have them, both in passcode and in SSID.

---

### Post by UtopiaTheory on 2008-11-21
Spaces are fine.  I have spaces in both my essid and my WPA2 key.  Try this from a command line:

```
iwlist eth1 scanning
```

Paste what it gives you in a reply.

---

### Post by tyroach on 2008-11-21
okay...will do.  Unit is at home and won't be there until late tonight.

in the mean time, any other ideas?

I'm should I try a different driver package (ie something other than wext)?

---

### Post by m_pourfathi on 2008-11-30
I've got the same issue with my Dell Vostro 1510 laptop. I had ubuntu 8.04 LTS and the wireless worked. I upgraded it and the exact thing happened. I just received an original CD from canonical containing Ubuntu 8.10. I tried that as well, but didn't do. But I could connect to unsecured networks. haven't tried WEP yet neither. Any ideas folks?

---

### Post by int2ag0n on 2008-12-14
Hi guys. I face the same problem with my Acer Aspire one. I was able to connect via WPA-PSK when i had the pre-installed linpus linux but after i installed ubuntu 8.10 connection always fails. Through wep it connects straight away. The acer aspire one  has an atheros like wireless card. i also forget to mention that i have installed the madwifi drivers for that card, i suspect that this may cause the problem. Any ideas?

---

### Post by james_xxx on 2008-12-14
I am in the same boat, using a brand new Dell Mini 9.

I really need to get this working in order to access the wireless network at the university that I attend.

Is there any chance that using ndiswrapper with this chipset would work better?

---

### Post by 0x1b on 2008-12-16
I can confirm the problem on my Dell Vostro 1510 w/ Ubuntu 8.10 Intrepid:

# lspci | grep Broadcom
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
# lspci -n | grep '14e4:43'
06:00.0 0280: 14e4:4315 (rev 01)
# uname -mr
2.6.27-9-generic x86_64
# no extra boot options in /boot/grub/menu.lst

I was able to see all wireless access points, but cannot able to connect with WPA key.

I've tried following instructions in comment #498 ( 27 april 2008 ) from kevdog in:
[http://ubuntuforums.org/showthread.php?t=475963&page=50](http://ubuntuforums.org/showthread.php?t=475963&page=50)

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

Downloaded BCM4312 driver (google "BCM4312 driver download") from some site, installed it (.exe) with wine:
# wine sp32158.exe
cd /path/to/drivers/install/dir/

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

Created /etc/modprobe.d/blacklist-broadcom with only this line:
blacklist b43 b43legacy ssb

Rebooted

# ndiswrapper -l
bcmwl5 : driver installed

But from "system > admin > windows wireless drivers" it says "no hardware found"... And now I can't see eth1 in ifconfig/iwconfig.

Shuold I forget to see WPA working ?

---

### Post by Ayuthia on 2008-12-16
> **0x1b said:**
> 
# ndiswrapper -l
bcmwl5 : driver installed

But from "system > admin > windows wireless drivers" it says "no hardware found"... And now I can't see eth1 in ifconfig/iwconfig.

Shuold I forget to see WPA working ?

This is showing that it did not like the driver that you used.  Since you have a Dell, you might try this Windows driver:
[ftp://ftp.us.dell.com/network/R174291.exe](ftp://ftp.us.dell.com/network/R174291.exe)
Since it is from Dell, you should be able to extract the file by using:
```
unzip R174291.exe
```This came from the no-fluff site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
You will need to remove the old driver first:
```
sudo ndiswrapper -r bcmwl5
```
Then you can load the new one.

---

### Post by 0x1b on 2008-12-17
Thank you Ayuthia,

I've rolled back undoing all I've written in my previous post,
and enabled "Broadcom STA wireless drivers" (the one suggested to me by the fresh install of ubuntu) from "system > admin > hardware drivers". This is the situation I had before.

Then I installed an ubuntu update of network manager and rebooted, but in the tray menu it says "devide not handled" on both eth0 and eth1.
But... surprise! In the "ifconfig" I see an IP in eth1!
Yes, I am connected to the wireless router! But network manager doesn't know (where does it put its configuration stuff?!? ...should I uninstall it?).

The only thing that changed in the meanwhile is the way I configure wireless: before I've tried (unsuccessfully) configuring network manager and then (unsuccessfully) adding to /etc/network/interfaces these lines:

auto eth1
iface eth1 inet dhcp
wireless-channel 11
wireless-essid myessid
wireless-key MYHEXKEY0143923094u2009...

But I did't receive any syntax error. 

I changed to this (successfully working) configuration taken somewhere in the net:

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-ssid myessid
wpa-ap-scan 2
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk MYHEXKEY.......

When I've restarted I've seen in ifconfig the right IP, as I was saying before.

The only problem now is how to say to use eth0 in my office and eth1 in my home, but I could disable "auto" and use a startup script.

I still don't understand what was my problem (interfaces config? network manager?)... any idea?

Maybe using the right driver (the one suggested by Ayuthia) using ndiswrapper I will finally see network manager working?

Thanks

---

### Post by djseto on 2009-01-05
I just did a fresh install of 8.10 on an old laptop I have with a Netgear 802.11g wireless card. When I selected WPA and WPA2 Personal, I could not connect to my wireless network either. I had to manually edit the interfaces file using what I read here. It works now, but I too would like to know why it didnt work before. I also no longer have network manager working now

---

