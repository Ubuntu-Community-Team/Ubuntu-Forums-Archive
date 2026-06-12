---
title: "How can i network from xp to ubuntu and share internet?"
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by tdelphous on 2008-03-16
This is the reason why I want to network my laptop(ubuntu os) to my desktop (xp sp2):  I don't have regular internet, nor do i have access to wifi, or anything else that is close to me.  I have a sprint broadband card.  It works fine on my desktop, and if i network other computers to it(both have xp os), they can share the same source of internet from the main computer.    This is all connected via the ethernet cable as well.

Reason why I want to network them:  So i can connect to the internet on my laptop(ubuntu os)  to get the necessary update and programs needed so I can use the USB aircard directly pluged into it. I have a novatel u727, and i followed all the directions, but i need to be connected to the internet to get all the updates and programs i need to run it.   

does any one know how to network a xp computer to an unbuntu computer , and be able to share internet from one source?  This would be very helpful.  of if there was a site where I could download unbuntu programs and updates on my xp computer same them to a cd or flash drive and install them on my laptop. Thanks!!!!!

---

### Post by nsche on 2008-04-01
I cannot give you a complete tested step by step procedure but I would suggest:
Start off in the XP computer as if you were doing ics using another XP computer.  The wizard will generate a script that it will put on a floppy (what is that?) or flash drive.  The script it creates sets up a the things needed for setting up an internet connection including the ip address to use and gateway address to use.  These things are the same in Linux as in XP they are just set up by different commands.  I think you could then use the data in that script to set up a network connection using  whatever method you are familiar with.

This is a broad map of what to do.  Exact steps are something you need to figure out.

---

### Post by ryanhaigh on 2008-04-01
Actually if you have configured ICS (internet connection sharing) on your XP machine, all you should need to do is connect your ubuntu laptop to that the same way you do with your other xp computers. 

When ICS is enabled the host (your main desktop) uses DHCP to assign IP addresses to the other computers it is connected to. You should just be able to plug the laptop in and go.

---

### Post by unicynic on 2008-04-26
Well... it's not as easy as described. Sometimes it works, sometimes it doesn't.
I use XP SP2 connected to DSL. I added a wifi USB to it so it can share using ad-hoc. Make sure you let Windows manage the wireless connection instead of the program that comes with the USB driver.
Then, on the network card connected to the DSL (not the wireless), enable connection sharing. You might have some problems with Windows saying the address is in use or that sort of things. If that happens, set the property of the wireless connection to DHCP or let it use other IP rather than 192.168.0.1. Restart after changing all these if Windows still complain.
Once the connection sharing is successfully enabled, now open the properties of the wireless connection and go to the wireless tab. In there, add a wireless network and select that it's ad-hoc (at the bottom there). Deselect "The key is provided...". Give it a sensible SSID, select an authentication method, and type a network key. If you use Open and WEP, the network key must 5 or 13 ascii characters, or 10 or 26 hex characters. Now, it's for 40bits (5/13) or 104bits (10/26) encryption. So, remember the one you used as that will be asked in Ubuntu and that's where it's confusing.
Save it and let it be.
Now, go to Ubuntu, and click the nm-applet in the panel. If wireless is on, you'd see a list and the SSID you gave just now in XP will be shown. If not, wait a bit while Ubuntu detects it. If it's there, click it. Ubuntu will ask for the network key.
Select the same as in XP (Open and WEP if that's what you use). The confusing part is the selection of what type of WEP. XP computers automatically recognize but not Ubuntu. Anyway, in Ubuntu, it says 64 bit or 128 bit and that's not what it says in XP (40/104). Now, it depends on the number of characters you use.
If you use 5 characters, it's the 64bit ASCII. If 13 characters, it's the 128bit ASCII. If 10 characters, 64bit hex and 26 characters for the 128bit hex. The passphrase one.. hmm, I'm just confused with that because last time it works but now I don't know how XP handles the connection.
Try.
Mine used to work but now doesn't work anymore unless I specify a static IP for Ubuntu. So, anyone know why? Is there problem with the DHCP client in Ubuntu? A firewall port needs to be opened?
I used Mint before this and it was always easy to connect.

---

### Post by d400e on 2008-05-01
Same problem here.
Past days i have been reading a lot about ad-hoc in linux. Some guys have succeded while others have reported total failure. Things dont seem quite clear and its not a simple matter for sure. I realised that(if i am not mistaken) it depends on whether ad hoc is supported(by device driver) for the specific kind of each wireless adapter. 

I am trying to conect to ad-hoc xp sp2 desktop with my laptop(ubuntu8.04) but no luck what so ever-same with 7.10-.(when the same laptop is set up with xp internet sharing works fine so its not a matter of hardware).
Desktop uses usb wireless adapter.
It is set with windows zero configuration.
It is set to share internet and has static IP adress.
(tested and works fine i.e. laptops with either xp or vista OS can access the internet through ad-hoc).

My laptop wireless pcmcia card netgear wpn 511 conects excellent to all access points but no luck with ad-hoc.
I have tried dhcp or static adress but my laptop cannot even conect to ad-hoc network.So i think it is not a problem with internet sharing but a "simple" conection problem.I have set up many xp desktops to share internet(xp to xp) with wireless usb adapters succesfully but i seem to be stuck with this.

---

### Post by d400e on 2008-05-02
As said in the Madwifi v0.9.4 readme file:


*********************************************************************
Known Problems [All these problems are to be fixed in future revisions.]
--------------
1. Ad-hoc mode is broken; symptoms are intermittent operation.
*********************************************************************

---

