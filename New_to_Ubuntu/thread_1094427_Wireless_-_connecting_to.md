---
title: "Wireless - connecting to"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Eman1955 on 2009-03-12
I have a dual boot system, Windows XP and Ubuntu 8.10
My HD crashed and I installed a new one and have the system back to normal only I cannot get wireless to work.  I used the Windows driver previously, but been so long ago I cannot remember how I did it.  I read the documentation and nothing has worked.  I downloaded the ndisgtk file but cannot get it installed. The network icon states wireless is enabled but there is no option to manually set it like the documentation states. 
Any help would be greatly appreciated.

Thanks in advance

E
:(

---

### Post by sneeks on 2009-03-12
mnnn,you seem a bit vague in what you are trying to do,have u installed xp and ubuntu,and does one of them connect???
more info please..

---

### Post by Eman1955 on 2009-03-12
Windows connects wirelessly no problem.  I cannot get wireless to connect in Ubuntu.  From all I have read it should be simple to do.  Nothing I've read works to get wireless working.
I have a Dell Inspiron 1505

---

### Post by anewguy on 2009-03-12
Post back the output of both of these commands from a terminal window:

lspci

lsusb


We'll go from there.

dave :)

---

### Post by fly-by-night on 2009-03-12
When you say you downloaded ndisgtk, do you mean installed via Synaptic?  Because back in Dapper I had to use ndiswrapper and ndisgtk is the GUI for it.

---

### Post by novafluxx on 2009-03-12
Is the wireless network broadcasting its SSID? Theres some issue with it not being able to connect if the network isn't broadcasting its SSID.

I had the problem, and have sense just let my router broadcast its SSID, I'll try it again with 9.04 though!

---

### Post by anewguy on 2009-03-12
If network manager is showing wireless networks, then yes your adapter is working.  As mentioned in the previous post, if your router is not broadcasting the essid, then you have to do just a little more work, since it won't show as an available network:

click on network manager, then click on manual or new connection (I forget exactly what it says and right now I'm on a Windows machine).  When you have done that, you'll be able to enter the essid plus anything like WEP or WPA password or passphrase. 

If the your network DOES show, you should be able to just click on it for it to try to connect - if WEP or WPA password or passphrase is needed it will prompt you for it.

If network manager is not showing any wireless networks, then 2 things are possible:

1.  You need to enable roaming mode under system/administration/network after clicking on the wireless "box".

2.  You still need a driver for your adapter.

If you are unable to connect, please post the outputs I requested earlier:

lsusb

lspci

The lsusb may be needed as some laptops internal wireless are actually attached as usb devices.

Dave :)

---

### Post by Eman1955 on 2009-03-12
THANK YOU ONE AND ALL FOR ALL SUGGESTIONS!

Here is the solution - best I've found.

From this site:
[http://www.ubuntu1501.com/2008/11/ndiswrapper-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntu1501.com/2008/11/ndiswrapper-in-ubuntu-810-intrepid-ibex.html)


You do not need to use ndiswrapper. Plug computer into Ethernet, go to system>administrator>update manager and update your computer. Once it is done restart computer. Now go to system>administrator>Hardware drivers and activate all that's there, ie the Wireless card and the graphics card. 

The driver was created by Linux dudes.  Thanks!

E

---

### Post by Mickeyj4j on 2009-03-12
Y not check out Linux Mint distro its a Ubuntu offshoot. it auto detects everthing including modems. 

Its allot easier to set up than Ubuntu check it out here. 

[http://www.linuxmint.com](http://www.linuxmint.com)

---

