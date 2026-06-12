---
title: "how to set up a wireless printer"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by DarinB on 2011-06-25
Hi Folks. 
I have never set up a wireless printer. I have it working with the cable fine. but I have no idea what my first step is. 

it is an hp p1102w it does have a button to transmit something but beyond that, I got nothing! 
any help?

---

### Post by candtalan on 2011-06-25
I also have never set up a wireless printer, however, thinking about it, the wireless point being connected to - is I guess - the wireless router? So the printer will need to tell the router what the wireless password is, so that the router knows it is your printer and not your neighbour's printer.

You might be able to input this information from the printer itself, or it might be necessary to input from the (printer) tools shown on your PC display.

I might be useful in a help discussion to know the model and type of your printer.

---

### Post by DarinB on 2011-06-26
Its an HP P1102W. 
Of course anything I have found on it is for a windows set up. 
I don't even know what the first step is???

---

### Post by walt.smith1960 on 2011-06-26
Have you enabled wireless networking on the printer?  I have a Photosmart 746x (I think) and there's a touch screen. You have to give it your Network I.D. or name (ESSID) and passphrase or key.  The printer should then recognize your network.  At that point go to Printers (how to find that depends on your distro) and click on "add" "printer" "network printer" and click "find".  There's a good chance your HP printer will be found. Then simply install.  There is an HP utility call "HP-Lip"which may be helpful but I've never used it, my networked HP printer is found and I use the suggested software. No problems.

---

### Post by candtalan on 2011-06-26
> **walt.smith1960 said:**
>  There is an HP utility call "HP-Lip"which may be helpful but I've never used it
it is 
hplip
and is usually included in a normal (ubuntu ) installation. However I have often found the included version is not the latest version. My own approach has been to unistall the installed one and manually install the hplip deb downloaded version. I am not an expert so I would suggest to get better advise in detail than from me, if you go this route. However, hplip once installed correctly, works brilliantly.

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by DarinB on 2011-06-29
I have the latest version I did that last week. 
[HTML]You have to give it your Network I.D. or name (ESSID) and passphrase or key.[/HTML]
I am not sure about the above, I have a linksys router wrt54g
my laptop is connected to it... the printer is connected to my laptop via usb. does the printer have to be connected to the router? 
I know my wep key and passphrase to the router. 
the printer P1102w has a button on the top that causes the printer to activate the wireless a blue light flashes. when i add printer in my os i try find network printer but nothing comes up. 
I don't know how to make the printer a network printer or what that means. does it have anything to do with my router? 
See!!! i don't know anything about this, and I have been googling how to's and can't find a basic explanation how this thing works....
or a step by step. 
thank for everyones help.

---

### Post by owiknowi on 2011-06-29
based on candtalan's info-links an excerpt from [https://help.ubuntu.com/community/HpAllInOne:](https://help.ubuntu.com/community/HpAllInOne:)

"To connect by wireless connection, press the printer Setup button and use the arrow keys to highlight the Network (sometimes Wireless) menu and press OK. Select Wireless Setup Wizard under the Network and press OK again. Follow the prompts and enter a WEP or WPA security key if prompted."

and does your router broadcasts its essid? if not broadcasted it's sometimes hard to connect to.

---

### Post by walt.smith1960 on 2011-06-30
> **DarinB said:**
> I have the latest version I did that last week. 
[HTML]You have to give it your Network I.D. or name (ESSID) and passphrase or key.[/HTML]I am not sure about the above, I have a linksys router wrt54g
my laptop is connected to it... the printer is connected to my laptop via usb. does the printer have to be connected to the router? 
I know my wep key and passphrase to the router. 
the printer P1102w has a button on the top that causes the printer to activate the wireless a blue light flashes. when i add printer in my os i try find network printer but nothing comes up. 
I don't know how to make the printer a network printer or what that means. does it have anything to do with my router? 
See!!! i don't know anything about this, and I have been googling how to's and can't find a basic explanation how this thing works....
or a step by step. 
thank for everyones help.

My choice would be to connect it to the router via either cable or wireless network connection.  That way no computer is required to be powered up except the one you're using. Your blue light is flashing which I think says the printer sees your wireless network.   An HP network-enabled printer should be very simple to install but the network connection won't be there until you unplug any USB cables.  I'm using an XFCE DE right now so can't give step by step instructions. If you go to "printing" it should be fairly intuitive to install your HP.

---

