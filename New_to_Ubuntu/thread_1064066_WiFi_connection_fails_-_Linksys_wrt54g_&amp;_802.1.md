---
title: "WiFi connection fails - Linksys wrt54g &amp; 802.11b"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by algonquin96 on 2009-02-08
I'm trying to connect my 802.11b wireless NIC to a Linksys WRT54G router (unsecure/open for now). Ubuntu v8.04 loads the Wi-Fi card fine using the default drivers and can browser to the SSID. When I try to connect to the router, I get message "Attempting to join wireless network" then an error, and an entry is made in Network Configuration/Wireless tab.

Also other open AP are viewable and Ubuntu can't connect to them either.

note:  the only thing that seems odd is the NIC is listed with only IPv6 and not IPv4 in Network Tools.

Thanks!

---

### Post by houstonbofh on 2009-02-08
Whatever you do, don't tell us what wireless card you are trying to use! ;)  I bet a quick search on your wireless card will show that you need a special driver, or a BIOS installed.  You can also try running the "Restricted Drivers" applet.

---

### Post by Kevbert on 2009-02-08
Welcome to Ubuntu.
You probably need to install a wireless firmware driver. Please go to Applications-Accessories-Terminal and type one of the following commands and then post back the output:
```
lspci
lsusb
```
which are list pci bus devices and list usb devices.
Also please post the output of
```
iwconfig
```
which tells us the wireless configuration and whether there are any set-up problems.
You can copy the output from terminal by highlighting the text with the mouse and pressing Ctrl-Shift-C to copy and Ctrl-V to paste here. If you need to transfer the output from another machine then you can use a pipe to a file, for example
```
lspci > file1.txt
```
This will save the output of lspci to a file called file1.txt in your home directory.

---

### Post by algonquin96 on 2009-02-08
Thanks for the replies. 

The USB wireless is an older ezonics 802.11b, which isn't listed on the compatibility issue. Thought the default driver might work since Ubuntu saw the SSID.

When I tried to run terminal but the terminal window is blank. The blsnk window issue also happens on a few other applets. I was hoping to resolve this Intel Direct AGP 3D video card issue later. Also I'm not seeing this card listed on compatibility list. 

Maybe I picked the wrong hardware platform to try Ubuntu?

---

### Post by Kevbert on 2009-02-09
Did you burn your own CD ? It may be that either the downloaded file is corrupt or you burnt the CD at too higher speed (x2 best).  It may be worth running the CD and checking the CD integrity from the CD start menu.
There's a very good chance that you'll be able to run Ubuntu (I'm running it on a PC that must be at least 10 years old).

---

### Post by houstonbofh on 2009-02-09
Boy, there just isn't much on your card out there.  Hopefully is it an OEM of something else.  As to the black screen, try turning off 3D for now.  System --> Preferences --> Appearance Under the "Visual Effects" tab select "none" and see if it gets better.  Then you can try listing things.  Also, run the Restricted Driver Applet under System --> Administration --> Restricted Drivers Manager and see if you have some stuff there.

---

