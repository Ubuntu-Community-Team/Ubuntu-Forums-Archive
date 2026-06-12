---
title: "Acer Aspire Timeling 5810TG Wireless problems (modem-manager)"
date: 2013-10-06
forum: Networking &amp; Wireless
---

### Post by airplanesimen on 2013-10-06
[COLOR=#333333][FONT=UbuntuRegular]When booting my computer, my modem-manager wont connect to any networks, because it's failing to load properly upon booting.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When i tried to enable networking when in **safemode**, i got this output, and it stayed like that for over 5 min:

[IMG]http://i.stack.imgur.com/jxozC.jpg[/IMG]





When i am in Unity, **without safemode**, i can see the icon for the networking on the bar flickering. It stays there for like 5-10 seconds, and dissapears, and then comes back. The popup is appearing all the time that i am not connected to any networks.
And when i click the icon in order to watch the dropdown-menu, nothing happens.

[/FONT][/COLOR] if I am entering the system tool called "Networking", it tells me this:
"The Networking-service on this system is not compatible with this version".


[COLOR=#333333][FONT=UbuntuRegular][B][U]BUT 
[/U][/B]Sometimes, when i reboot my computer, the network is working all fine, nothing wrong. But, that is extremely rare, so i am most often expereiencing that it doesn't work.


I am Running ubuntu 13.04 with Unity on an Acer Aspire 5810TG with the [COLOR=#000000][FONT=Helvetica]Intel WiFi Link 5100 / [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]Bluetooth 2.0 EDR, [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]802.11 a/b/g/n (draft).



Thanks for any help i might get. Can provide more info if needed.

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by airplanesimen on 2013-10-06
Uhm well,
If i do:

```

sudo killall modem-manager
```

and then

```

sudo modem-manager 
```

It says 

> could not acquire the org.freedesktop.modemmanager service as it is already taken

---

### Post by varunendra on 2013-10-06
> **airplanesimen said:**
> When booting my computer, my modem-manager wont connect to **[COLOR="#FF0000"]any networks[/COLOR]**
Any networks?? Is this a modem or a Wireless card/adapter? Modem and wifi are different things and are managed differently too (although the same GUI application - NetworkManager usually handles them just fine).

>  if I am entering the system tool called "Networking", it tells me this:
"The Networking-service on this system is not compatible with this version".
This most probably indicates an incompatible entry in /etc/network/interfaces file. Please post the outputs of -
```
cat /etc/network/interfaces
nm-tool
```

And if it is a USB modem/wifi adapter, the output of -
```
lsusb
```

If it is an internal PCI one, then the output of -
```
lspci -nnk | grep -iA2 net
```

---

### Post by airplanesimen on 2013-10-06
_**cat /etc/network/interfaces**_
```
simen@acer-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```



_**nm-tool**_
```
simen@acer-ubuntu:~$ nm-tool
** (process:2726): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Message did not receive a reply (timeout by message bus)
NetworkManager Tool
State: unknown

** (process:2726): WARNING **: error: could not connect to NetworkManager
```




**lspci -nnk | grep -iA2 net**

```
simen@acer-ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022b]
    Kernel driver in use: atl1c
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1301]
    Kernel driver in use: iwlwifi
```

---

### Post by varunendra on 2013-10-06
> **airplanesimen said:**
> ```
simen@acer-ubuntu:~$ nm-tool
** (process:2726): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Message did not receive a reply (timeout by message bus)
NetworkManager Tool
State: unknown

** (process:2726): WARNING **: error: could not connect to NetworkManager
```

Hmm.. please try -
```
sudo service network-manager stop
sudo service network-manager start
```

Does it enable the Network Manager icon on the top right of the screen? Can you connect after this?

If connected, please do -
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall network-manager network-manager gnome
```
..and reboot. Does Network Manager start automatically after this?

---

### Post by airplanesimen on 2013-10-06
Nope, that's my problem:

I started the service again, and the icon appears (blank, when it's not connected). The dialog that tells me : "Disconnected - You are now offline" shows, and i can't click the icon either, because nothing happens at all.

No networks connected either.

---

### Post by varunendra on 2013-10-06
When the icon appears, does "nm-tool" start returning normal outputs? If yes, please post -
```
nm-tool
nmcli con
```

Does your wireless connection show up in the last command's output? If yes, you may try -
```
nmcli con up id <your connection's NAME>
```
where NAME is the connection name that appears in the output of "nmcli con".

However, if your connection is not saved (so does not appear in "nmcli con"), you may try this method to manually connect : [http://askubuntu.com/a/55832](http://askubuntu.com/a/55832) - just to be able to do the updates and re-install NM. I hope it should be fixed itself after an update --> reinstall.

Oh, and to try making the nm-applet (the NM icon on the top right) clickable, you may try this -
```
killall nm-applet
```
Then press Alt-F2 --> type "nm-applet" --> press "Enter". The above command will remove nm-applet, and this will bring it back, functioning properly this time if the background services are fine.

---

### Post by airplanesimen on 2013-10-06
**NM-TOOL**
```
simen@acer-ubuntu:~$ nm-tool
 
** (process:14556): WARNING **: Error in get_property: Message did not receive a reply (timeout by message bus)
 
 
(process:14556): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
 
(process:14556): GLib-GObject-CRITICAL **: g_value_get_uint: assertion 'G_VALUE_HOLDS_UINT (value)' failed
 
** (process:14556): WARNING **: Unknown device type 0
 
** (process:14556): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/0: unknown object type
 
** (process:14556): WARNING **: Error in get_property: The name org.freedesktop.NetworkManager was not provided by any .service files
 
 
(process:14556): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
 
(process:14556): GLib-GObject-CRITICAL **: g_value_get_uint: assertion 'G_VALUE_HOLDS_UINT (value)' failed
 
** (process:14556): WARNING **: Unknown device type 0
 
** (process:14556): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/1: unknown object type
 
NetworkManager Tool
 
State: disconnected
```
 
 **nmcli con**
```
simen@acer-ubuntu:~$ nmcli con
 
** (process:15588): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
Error: nmcli (0.9.8.0) and NetworkManager (unknown) versions don't match. Force execution using --nocheck, but the results are unpredictable.
```

Well, there was some difference in the nm-tool output, but i did the same cmd many times, and it changed from that output and the first one i posted earllier. Btw, the icon is flickering (it dissapears and appears constantly, looks like network-manager is having a rough time.)


BTW: the icon is still not clickable, but the others are. 
And as i said, it keeps dissapearing.

---

### Post by varunendra on 2013-10-06
Yup, because the package network-manager is clearly broken. Please try this alternate method to re-install it -

```
apt-get install --print-uris network-manager network-manager-gnome
```
This will give you the download URIs of the required packages. Copy-past these URIs and use them to download the packages on another system where you are posting from.

Once downloaded, copy them back to your Ubuntu desktop, in a new folder named "nm" (just to avoid confusion), then open a terminal and do -
```
sudo apt-get purge network-manager network-manager-gnome
cd Desktop/nm
sudo dpkg -i *.deb
```
Let me know if there are still errors. If not, you should have a working nm-applet icon (may require you a reboot or logout re-login)

---

### Post by airplanesimen on 2013-10-07
No errors setting up the packages now. 

But still, the same error as earlier when doing nm-tool, and the icon is long gone. 

I am kinda stuck here.

AND the icon is flickering even faster now than before. Weird.

---

### Post by airplanesimen on 2013-10-07
AHHH!

Anyone, please help:

When trying with my hardware-switch to turn_** off **_the internet, it turns **_automatically on_** again if Network-Manager is running. Why is this happening? I think there might be some kind of a software-conflict going on here.

---

### Post by varunendra on 2013-10-08
Sorry for a late response, but now I see you've marked it 'solved'? So is the Network manager working now? Does "nm-tool" show some sensible output now?

> **airplanesimen said:**
> When trying with my hardware-switch to turn_** off **_the internet, it turns **_automatically on_** again if Network-Manager is running. Why is this happening? I think there might be some kind of a software-conflict going on here.

Make sure "Connect Automatically" option is unchecked for your connection settings in Network Manager.

---

### Post by airplanesimen on 2013-10-09
Yep i got it solved by rage-reinstalling ubuntu x)

I tried to remove the configuration-files for my network, so it didn't connect to the network automatically, but it was still conflicting hardware-wise.
Took a fast backup of my documents on another partition and reinstalled, back to 12.10 (where the computer worked fine)- as long as i can use it as a SSH-server, i am satisfied :)
Anyways, i couldn't get it solved by myself, so i gave up and did downgrade to 12.10. Everything is fine now ^^

So Thanks for trying to help ;)

---

### Post by varunendra on 2013-10-09
No problem. Hope the upcoming versions treat you better. :)

---

