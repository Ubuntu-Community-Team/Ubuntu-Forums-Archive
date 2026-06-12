---
title: "How to set up WiFi hotspot in 18.04, similar to mobile hotspot in Windows 10?"
date: 2019-04-04
forum: Networking &amp; Wireless
---

### Post by rahul3555 on 2019-04-04
Hello all,

I'm new to the forum here. I've searched for the exact query already and didn't seem to find suitable answers, thus posting this. Windows 10 has nifty trick called Mobile Hotspot which shares the computer's internet (Wired or Wireless) with upto 8 devices by creating a Wifi hotspot. Searching for its equivalent in Ubuntu, I found answers for creating a hotspot (which disconnects from the connected network, thus a hotspot without internet) and for routing Ethernet to Wifi hotspot, but not for this. Any suggestions are welcome.

To clarify, I already use mobile hotspot in Windows 10, so I'm confident my laptop's hardware supports this feature: simultaneously connected to a Wifi and routing its internet through a hotspot. If it is a case of lack of driver support in Ubuntu, then there's not much that can be done. However, if there is some option to enable this feature or if its already present that I've blindly overlooked, please enlighten.

---

### Post by jtremblaymclellan on 2019-04-04
**Simple steps: 
Create wifi hotspot in ubuntu**


 1. Disable Wifi (Uncheck Enable Wi-Fi)
 2. Go to network connection (Edit Connections...)
 3. Click "Add"
 4. Choose "Wi-Fi" and click "Create"
 5. Type in Connection name like "wifi-hotspot"
 6. Type in SSID as you wish
 7. Choose Device MAC Address from the dropdown (wlan0)
 8. Wifi Security select "WPA & WPA2 Personal" and set a *password*.
 9. Go to IPv4 Settings tab, from Method drop-down box select Shared to other computers.
 10. Then save and close.
>  11. Open Terminal (Ctrl+Alt+T) and type in the following command with your connection name used in step 5.


        sudo gedit /etc/NetworkManager/system-connections/wifi-hotspot


If you have issues provide the following 
> ls /etc/NetworkManager/system-connections/
> cat /etc/NetworkManager/system-connections/*



 12. Find `mode=infrastructure` and change it to `mode=ap`


 13. Now check the network section where wi-fi will be connected to the created hotspot automatically. If you can not find it, go to *Connect to Hidden Network...* Find the connection and connect to it.
[/QUOTE]



*Source: [http://ubuntuhandbook.org/index.php/2014/09/3-ways-create-wifi-hotspot-ubuntu/*](http://ubuntuhandbook.org/index.php/2014/09/3-ways-create-wifi-hotspot-ubuntu/*)

---

### Post by coffeecat on 2019-04-04
Support, not chat.

*Thread moved to **Networking & Wireless**.*

@rahul3555, the poster after you advises you to run a command that commences *sudo gedit*. If you value the integrity of your operating system, **do not do this**. Please consult the [Community RootSudo](https://help.ubuntu.com/community/RootSudo) page for important information about opening a graphical application as root. Although that page is currently being revised, the caveat about not running a graphical application with bare sudo is sound.  

@jtremblaymclellan, please take to heart this quote from the RootSudo page:

> You should **never** use normal sudo to start graphical applications as root. Using sudo with graphical apps has the potential to corrupt your environment by allowing root to take ownership of and/or change permissions on critical files that you must own. The forums frequently see panicked requests for help from users who can no longer log in after running graphical applications under sudo.

---

### Post by afflospark on 2019-04-16
Hello,
You can use your Ubuntu system as a wireless hotspot. Wireless hotspot allows to create a separate network and it shares internet connection also 
To create a wireless connection you have to follow these points

[LIST=1]
[*]you have to open the system menu
[*]You have to disconnect all the wireless network which you already connected
[*]Then click WiFi settings and click the button of” use as a WiFi hotspot”
[*] Then your system creates you a single connection if you want to share internet just click Turn on there and your hotspot will be created via the system.
[/LIST]
And your network name (ssid) automatically generated via your system.
Thanks and Regards
Afflospark

---

