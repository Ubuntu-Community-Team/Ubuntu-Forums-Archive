---
title: "Network printer setup issues."
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by Stibily on 2007-10-07
Hi.

I am trying to set up my Canon iP4200 printer to work with Ubuntu 7.04. It is a network printer connected to a wireless print server (Netgear WGPS606) via usb and currently works fine with all Windows versions in the house. I tried a few configurations with LPD and IPP however was unsuccessful. I could not find someone with the same setup as me so have no resources to look at. The IP address of the print server is 192.168.1.208 and is connected to Port2. I can ping the IP successfully.

Could someone guide me through the process for this specific situation?
Should I be using LPD or IPP or other?

Many thanks.
:: Tom

---

### Post by linuxwizard on 2007-10-07
Check over these mightbe something that will help you.

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)

---

### Post by Stibily on 2007-10-21
Sorry, none of those links seemed to be of much help in terms of solving the issue.

Any other ideas?

Regards.
::Tom

---

### Post by manemannen on 2007-10-29
Did you solve this issue? I'm about to go pure Ubuntu and this is the only problem I have left to solve so if you figured out how to fix this I'd appreciate if you'd post it here.

---

### Post by mtennant on 2007-11-11
lpd://192.168.1.109/L1

Using the new 7.10 printer setup, I specified LPD and the above format after much experimentation. Replace my IP address with your fixed IP address on your print server.

My printer, an HL-2040 Brother Laser (setup as an HL-1250) is connected to USB Port 1 on the Netgear WGPS606 wireless print server.

In previous versions of Ubuntu, I had to specify a queue name when setting up an LPD printer using this Netgear device.  I don't know if the L1 designation above takes care of that, or if it specifies the USB port number.  P1 does not work.

I tried printing some graphics using the Gnome image viewer.  I got funny results, with partially duplicated images.  Finally, I got a good print using Gimp to view and print.

I've never tried setting up a second printer using this wireless printer server device.  Not sure how you would go about that.  Maybe someone else can explain that.

---

### Post by SeanHodges on 2008-04-30
mtennent, brilliant your post helped me to get my printer working.

I was using the name I gave the printer on the Netgear print server instead of "L1".

So to clarify for anyone with a similar problem (and for me later on :)):

1. Go to System -> Administration -> Printing
2. "New Printer" button
3. Select "LPD/LPR Host or Printer"
4. Type the print server IP address in the Hostname field. e.g. "10.0.0.48"
5. Set the Printer Name to "L1"
6. Click Forward, and continue selecting the model and make of your printer
7. Test the configuration with "Print Test Page"

(If it still hangs try changing the device URI from "lpd://10.0.0.48/L1" to "lpd://10.0.0.48/L2")


I think this is a bug in Gutsy (haven't tried it in Hardy yet). Feisty used to list the "Printer Name" list correctly (probably providing "L1" as an option).

Thanks!

---

### Post by cap'n leaky on 2008-04-30
Just to add to this,

I had been printing to an ancient Canon BJ-200 ink jet that was attached to my SMC Barricade router.  You use the same string, but put lpt1 at the end since it is a parallel port on the router:

lpd://192.168.xxx.xxx/lpt1

I just hooked up my Brother HL-2040 laser and got it working the same way after I downloaded the drivers from Brothers site.  I purchased this printer because they do support linux.

mtennant, Is there a reason you have your HL-2040 set up as a 1250? I just got this printer today, but it seems to work great.

---

### Post by Vule on 2008-05-09
Hi,

I have an old HP Deskjet 895Cxi connected to the Wireless Network via Dlink DP311P Print Server. It works in the Windows XP world (my system is dual boot with the XP and, recently, Ubuntu 8.04) well.

Since I installed Ubuntu I had difficulty making this printer to work. Print server has default setting for the port name "lp1" which I tried and, of course, it failed. I tried everything that came to my mind until I read cap'n leaky's advice. My print server is directly connected to the parallel port, so it is logical to use "Lpt1" as a port name, but it did not come to my mind to try. 

**Thank you, cap'n leaky.**

It worked right away.

I just followed your advice to the letter. Excellent.

Vule.:)

---

