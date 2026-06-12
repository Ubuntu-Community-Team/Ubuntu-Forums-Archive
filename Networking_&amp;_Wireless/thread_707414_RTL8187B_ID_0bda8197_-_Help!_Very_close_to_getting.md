---
title: "RTL8187B ID: 0bda:8197 - Help! Very close to getting Wireless!"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Tom--d on 2008-02-25
Im using Ubuntu 7.10 - 32bit

I have a RTL8187B Wireless card in my Toshiba A200 Laptop. Everything else works, but not my wireless.

I've installed,

Ndiswrapper
ndisgtk 
ndiswrapper-utils-1.9 
ndiswrapper-common 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") I followed the steps. 

They all installed fine, no problem there. I've got the GUI of Ndisgtk. 

It says to install the Win98 driver to run the wireless. Done that. It installed fine, no problem. 

When I type in the Terminal..

```
ndiswrapper -l
```
This is what comes up
```
net8187b : driver installed
```
Thats the Windows 98 driver.

But its ment to come up with this...
```
  {name of driver} : driver installed
       device ({Chipset ID}) present

```
The device doesn't show on mine :/
I was told to use the Win98 driver. I've tried all the other drivers, XP, 2000, Vista and ME. But nothing. it says the hardware is not persent. Ther hardware is there as...

I type this in
```
lsusb
```
My wireless adapter is internal.

This is what is shown,
```
Bus 002 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.
```
Ubuntu knows its there but the Win98 driver doesn't :/

**I tried the modified RTL8187B driver from here [http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/"). It worked, but very poorly as I need WEP. WEP doesn't work with that modified driver. Well, it didn't for me. And the signal is messed but that wasn't a problem, just the WEP.**

I need help on getting my Win98 Driver to recgonise my 0bda:8197 card. Is there a modifed version which does this? Has anyone got the same problem as me?

Please please help me. Im stuck, really stuck!

THANKS, 
Tom

---

