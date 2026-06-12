---
title: "Ubuntu Gnome Wi-Fi Hardware disabled"
date: 2014-01-02
forum: Networking &amp; Wireless
---

### Post by blaz.kvas on 2014-01-02
I just bought a new laptop (Asus X551CA) and installed Ubuntu Gnome 13.10.
There is a problem with my wifi. Wired connection works fine but for the Wi-Fi it's saying " Hardware disabled".
I tried to go to the network settings and turning it on manualy but it just jumps back to off state imidiately.

Oh and if someone knows how to get drivers for the touchpad I would also apreciate it :grin:.

My network controller is qualcomm atheros ar9485

---

### Post by praseodym on 2014-01-02
```
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf 
```
and rebooting should do the trick. Check the keys afterwards.

---

### Post by grahammechanical on 2014-01-02
It could be that the WiFi (wireless) card in the machine is turned off. I have heard that with some laptops it is possible to turn off wireless to save battery power by a keyboard key combination or that if wireless is turned off in Windows it will also be turned off in Ubuntu and Ubuntu cannot turn it on again.

When you click the Network icon do you see a list of wireless access points in range? Is Networking and Wireless enabled? You may also need a driver for your wireless adapter. Run the command

```
rfkill list
```

You should see this

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


If you have even one "yes" then wireless will not work. When software is blocked it could indicate that we have not turned networking on or enabled wireless. It could also indicate that the wireless card needs a driver. When the hardware is blocked it will indicate that the wireless card is turned off, usually by a keyboard combination.

To install a driver go to System Settings>Software and Updates>Additional Drivers tab and see if a driver for wireless is offered to you.

Regards.

---

### Post by blaz.kvas on 2014-01-02
[COLOR=#000000][grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")

Code:
echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf[/COLOR]
[COLOR=#000000]and rebooting should do the trick. Check the keys afterwards.[/COLOR]


Thank you. This did it.
I will report if I have any issues with it. :D

---

### Post by DJArty on 2014-04-19
Yes, modprobe string is work.
But found one more trick(bug) for simple users (X551 + Ubuntu 14.04 ).

If you close/up laptop screen (sleep mode)  - WiFi start to work :)

---

