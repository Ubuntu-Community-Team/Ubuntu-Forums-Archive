---
title: "Belkin F5D8010 wireless card"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by zaidee on 2007-06-02
I am new to all this and am trying to install a wireless network.

My pc has a pci card that takes a Belkin F5D8010 notebook network card. I foolowed a couple of links on here that took me to a list of supported cards and although it said this particular card was NOT supported it did suggest that come 2005/2006 it would be?

Can anybody help me?

Also in the help menu it suggest I use System - Administration - Networking, I do not appear to have a "Networking" option. Am I just being really thick

Thanks

---

### Post by spd106 on 2007-06-03
Your best bet would be to try ndiswrapper with the windows driver. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

For some reason the menu entry was changed in Gnome 2.18. So Feisty has Network, rather than Networking. But you'll probably want to use Network Manager via nm-applet.

---

### Post by zaidee on 2007-06-05
Thanks for that.

The next prob I had was when the card was still in the pc, obviously not installed properly, I switched my pc off and when I tried putting back on I had an error of "Failed to start the X server (your graphical interface). It is likely that it is not set up properly.........................................
When i removed the card it all was ok?
Could this have been because the correct drivers or whatever where no there or could there have been another reason?

Thanks

---

### Post by technotika on 2008-02-29
Hi Mate  - hope this helps

I have  desktop card but i has the same model no. so should be the same.

I have done this proceedure  about 4 times now and it works fine for me.

First of all unzip the relevant drivers to your desktop ( and for some reason it has to be desktop, I tried loading the drivers from a different area and nothing happened).

get the drivers here [http://http://www.netgear.com/Produc...s.aspx?for=All](http://http://www.netgear.com/Produc...s.aspx?for=All).

Ok gonna run through setting through from scatch as if new install of ubuntu.

1.) With WIRED connection (assuming you have one ^%$!) go to synaptic and search "NDISWRAPPER".
Install all 3 components (if you select ngdisk it will highlight them all anyway).

2.) REMOVE Wired connectin from PC  - then RESEAT the wireless card (or leave it out till this point and insert)

3.) Then go to the NDIS WRAPPER GUI (administration  - WIRELESS DRIVERS) and Install new DRIVER.

4.) Browse to the "desktop" where you have unzipped the drivers and navigate to the drivers folder
you will see 2 *.inf files. Install 1 and then the other. One is called netani.inf I forget the other but there are only 2. 

With any luck the hardware will be detected and the window will show the 2 files as one saying hardware present yes! and the other no! ( this is what we want). 

If nothing happens at this point check above about driver folder unzip location and connection of wired removal. Perhaps even reboot. Its a tad flakey so persist along these lines but it should be ok.

Once your drivers are loaded you are nearly there. 

5.) From the same GUI go to network set up. With a bit of luck you should now see WIRELESS connection. Open it and take off "roaming" at the top then fill in the details for the wireless network.
I use wep with mac address control so dont know about WPA. Then set the card for DHCP and then
in the list of network connections make sure you have wireless TICKED - wait a few seconds and a message saying "changing interface connectio" ( or something). OPen firefox and make sure you can open a webpage.

6.) From my readings I have heard people have a lot of issues with losing network at reboot and also issues with DHCP.

7.) I got round it by changing to static IP, making sure internet worked after changes then did this..
sudo gedit  /etc/rc.local file

just before line exit=0

add

/etc/init.d/networking restart.

8.) Reboot and hopefully thats it . Its dependant on you using STATIC and various things but in terms of getting this fast card working  - it's all good.

The reaon I managed to get it working this way is from reading loads about it and using a combination of the easiest parts.

Good LUCK.

---

### Post by justinmiller87 on 2008-03-02
If you're still having trouble, check the link in my signature. It's a step-by-step guide for either an online or offline installation mode for the card you have.

---

### Post by technotika on 2008-03-05
justinmiller87  

you LEGEND - i have spent weeks tinkering around with wireless for this card and got it working in a real hashed up way  - see posts - I tried your method and it just rocked (its now printed out and "skewered" into  the wall next to the bunt box for future emergencies")- no hassles after reboot or anything.
You REALLY helped me there  - THANKS alot fella!!!!!!!!!!!!

---

### Post by justinmiller87 on 2008-03-05
Glad I could be of service. :)

---

### Post by technotika on 2008-03-07
Actually I did notice one thing  - it's no biggy really but hey.

I now have ubuntu on my laptop aswell as my desktop where the pre-n card is.

I have got HELLANZB running like no bodies business on the laptop connected wirelessly. I have an up to 20 m/b connection and on the laptop it rocks to full speed. 

I want it on the desktop really coz more storage and its seems like there is a struggle , the speed is very erratic and jumps about all over the place. 

I have run the laptop next to the desktop in the same room and its the same; strong laptop performance,  poor dekstop pre-n card peformance...... so its not the location of the desktop or the signal. 

I know the desktop card was capable of full speed on windows before. I wonder if its driver or something specific to the hardware within ubuntu.

Like I said though I got it pretty good so dont really need that but it would be special to have it running to full ability.

Thanks in advance.

J

---

### Post by justinmiller87 on 2008-03-07
I think it's an Ubuntu thing. I have a different laptop now than the one that I was actually using the Belkin on, and it has built-in wifi that uses the Broadcom drivers. Well, needless to say, it's not as fast as when I'm under Windows. Either way, it's still no reason for me to throw in the towel and swear off Linux forever. I've heard there's better Wifi support in Hardy, but I can't actually confirm that.

---

### Post by technotika on 2008-03-15
hi mate just for your info I have done something that seems to have cured the previous problem of the connection speed. 

I downloaded the NDISWRAPPER front end and from there proceeded to uninstall all netani.inf that was loaded there.

I reinstalled the driver from the "CD" that came with the PRE-N desktop card and suddenly 
everything is coming down at full pelt just about.

Thanks again. looking forward to Hardy though, got a good feeling on that!!!

---

