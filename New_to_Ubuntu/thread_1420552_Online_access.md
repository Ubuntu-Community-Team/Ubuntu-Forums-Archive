---
title: "Online access"
date: 2010-03-03
forum: New to Ubuntu
---

### Post by unrepentant on 2010-03-03
Hi

A couple of months ago I found a publication called Linux - The Complete Manual in W H Smiths. Intrigued, I had a flick through it. It came with a Ubuntu 9.10 CD for installation.

I have a Dell Inspiron 1520 laptop loaded with Dell Media Direct and running Windows Media (32 bit). I also have a desktop with a wireless router that talks quite happily with a Nintendo WII in another room in the house.

I bought the manual, loaded the CD into the Laptop and told it to use the whole disk for installing Ubuntu; which it did. Everything seemed ok.

I tried to connect to the Internet via my wireless router. I entered my details at System/Preferences/Network Connections/Wireless - filling the SSID box and the security on the next tab. I then clicked on the connection symbol at the top right of the screen. In the drop down box it said that wireless was disabled. I turned on the switch at the side of the laptop. The drop down box then read Wireless Networks disconnected. This is as far as I have managed to get.

I also bought a Vodaphone mobile broadband "Top up and go" USB stick. When I plugged this in and went to Network Connections/mobile broadband Ubuntu had correctly identified the device and I was able to complete the wizard.

After rebooting, I clicked on the connection symbol on the desk top and it listed the top up and go device as one of the options. I clicked on it to connect and got a message telling me that I was connected. The signal box, top left of the screen, showed full bars for a maximum signal. However, when I tried to use Firefox I got a welcome to Ubuntu page but then the  message said that the server was not found when I tried to surf the web.

One more thing. Update Manager says that my system was updated 3 days ago (last time I tried connecting with USB stick).

Why can I not connect to the Internet or Ubuntu Software Centre and what can I do about it.

Sorry for the length of the post but I would appreciate any comments/help.

Regards

---

### Post by beegary on 2010-03-03
> **unrepentant said:**
> 
After rebooting, I clicked on the connection symbol on the desk top and it listed the top up and go device as one of the options. I clicked on it to connect and got a message telling me that I was connected. The signal box, top left of the screen, showed full bars for a maximum signal. However, when I tried to use Firefox I got a welcome to Ubuntu page but then the message said that the server was not found when I tried to surf the web.
 
 
Check the connection settings in your web browser (?Firefox). Ensure that it is set to Autodetect an internet connection

---

### Post by 3rdalbum on 2010-03-03
On Ubuntu 9.10 it might take a couple of tries to get a reliable mobile broadband connection. Sorry to say it, but 9.10 has this problem and it's not likely to be fixed at all in 9.10.

As for your wireless card, try shutting down completely and then left-click in the Network Manager applet (one of the icons to the left of the clock) to see if any networks are listed. You might want to get the model number of the wireless card or the chipset and do a Google search.

For instance, if I put the 'lsusb' command into the terminal:

```
~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1532:010b Razer USA, Ltd 
Bus 008 Device 003: ID 1532:0016 Razer USA, Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I would do a Google search for "RTL8187 ubuntu 9.10".

The 'lspci' command might help too.

---

### Post by unrepentant on 2010-03-04
Thanks for the replies but no luck yet.

I'm gonna try to contact the local Linux User Group to see if they can help - though their website (Mansfield LUG) says that their next meeting is November of last year so not overly optimistic.

Thanks again.

---

