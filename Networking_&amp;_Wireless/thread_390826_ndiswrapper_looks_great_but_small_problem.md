---
title: "ndiswrapper looks great but small problem"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by bugler on 2007-03-22
Howdy all,

Having a problem with ndiswrapper current stable.  I have followed the [wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29") for broadcom 4311 rev01 and ndiswrapper and I AM VERY CLOSE!  Below is my scenario.

I have dv6113us laptop with broadcom 4311 rev 01 amd64 x2 ubuntu edgy 2.6.17-11-generic.

No errors following all instructions in wiki. Wifi light comes on and turns off by switch. 
iwlist shows AP's.  system networking applet shows essid and wep hex.
/etc/networking/interfaces shows correct text.

Problem is iwconfig shows wlan0 with NO essid even though it is in /etc/network/interfaces.
when I ifdown and ifup wlan0 I get dhcpdiscover 255.255.255.255 and no resolution. 

HOW do I fix this?  Any ideas are welcome.  I am on day number 2 and I am so close I can taste it.

Thanks in advance,

Bugler.

---

### Post by chili555 on 2007-03-22
> /etc/networking/interfaces shows correct text.
Including the ESSID? For eample:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91
```Also did you try with the word 'restricted' or the word 'open' after the key:```
auto wlan0
iface wlan0 inet dhcp
wireless-essid chili
wireless-key 93c8530b2df51711bad5596f91 open
```Does sudo iwlist wlan0 scan confirm the ESSID? chili is not the same as Chili is not the same as CHILI.

After each experimental change, you needn't reboot, just restart networking:```
sudo /etc/init.d/networking restart
```Let us know.

---

### Post by bugler on 2007-03-22
Chili thanks for the reply!

/etc/network/interfaces - I have masked some
```
iface wlan0 inet dhcp
wireless-essid normal
wireless-key 7065616b37207665XXXXXXXXXX
auto wlan0

iface eth0 inet dhcp
```

iwlist clip for wlan0

```
          Cell 01 - Address: 00:19:5B:06:7D:82
                    ESSID:"normal"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-32 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

Lastly, I did not try restricted or open.  In my router I have OPEN set up as the authentication, WEP 128 HEX.

I will try the open in my setting and let you know.

Thanks again.

---

### Post by bugler on 2007-03-23
Ok Ndiswrapper works with open at the end of the line.  Thanks.  

As always with linux and laptops, I have another issue.  I will briefly explain it here for reference and post it in another category.

Gnome settings daemon errors and hangs login efforts.  Ubuntu does come up after about 1min and 30sec and I just have to hit themes and all theming works.  However, Gedit and some others hang when opening.  When I ifdown wlan0 all works ok.

If I shut down X and shut down wlan0 from terminal and start X, I don't get problem of hanging login.  Obviously it is conflict somewhere on boot between wlan0 and X.  

Question is: can I delay wlan0 from coming up until after gdm comes up?  or is this a bad way to look at it?

Thanks Chili,

Bugler

---

### Post by chili555 on 2007-03-23
I think it's a bad way, because you are just masking a deeper problem. Gedit is an excellent start to diagnosing the problem. You can start it in a terminal and watch the output. Here is what my terminal output looks like when I open and close gedit:```
chili@LAPTOP:~$ gedit
chili@LAPTOP:~$ 
```No errors. You may see errors or warnings that some files are not found and you can google up the missing file along with ubuntu and start to figure out who is gone AWOL.

I will further look for you on the other thread.

---

### Post by bugler on 2007-03-24
FULLY OPERATIONAL DV6000 hp laptop.
Chili,

Found the error!  After searching ubuntuforums i found a solution.  

After following the wiki, the /etc/network/interfaces did not have the auto lo (the local loopback interface) which I believe (I'm a newb) is needed for the gnome-settings daemon to communicate with dbus messenger.  Could be wrong on that statement.  Anyway, after putting lo in interfaces, error was removed and gedit and login boot normally.  

NVidia 9755 1280x800, ndiswrapper at 54g ubuntu edgy on dv6000 (dv6113us)  FULLY OPERATIONAL!  I am loving this.  Gnome network-manager for wireless and wep is working.

Chili, thanks for your help!

Bugler

---

