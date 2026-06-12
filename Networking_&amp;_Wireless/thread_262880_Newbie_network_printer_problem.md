---
title: "Newbie: network printer problem"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by wolfbreath on 2006-09-22
I'm trying to get my Ubuntu 6.06 box to talk to a Windows Network printer and I just can't get it to work. I am sure I am doing something wrong, but can't figure out what. I have an IP number for the printer and a share name.

I've picked the Network Printer button and selected "Windows Printer (SMB)".
Then I've tried entering the IP number where it says "Host" and the share name where it says "Printer". I've tried entering my network ID and password and clicked on "Print a Test Page", but get no result.

Can someone tell this poor clueless newbie just what I am doing wrong?

---

### Post by wolfbreath on 2006-09-24
Still no success. Can anyne point me in the right direction, please?

---

### Post by handy on 2006-09-26
You call it a **network printer**?

Does this printer connect directly to a network hub/switch via cable, or is it connected directly to the windoze box via usb or parallel cable?

This information is needed to know how to set it up...

Also, make & model of printer please?

---

### Post by wolfbreath on 2006-09-26
The printer is connected directly to a windows xp computer but it is also connected to a network, since it is possible to print to it when the windows computer is not turned on.

It is an HP Laserjet 2100.

---

### Post by handy on 2006-09-27
Why is it connected both ways to the windoze machine & not just through the LAN?

---

### Post by Iowan on 2006-09-27
> **wolfbreath said:**
> ...but it is also connected to a network...

It is an HP Laserjet 2100.Would it be connecting to the network via a JetDirect card?  Rather than selecting SMB, you should have an option for JetDirect (Sure wish I were looking at my system at home...).  On my LJ5M, I needed to use the IP address instead of the printer name.

---

### Post by hellmet on 2006-09-27
well, same problem here..
But the printer ain't connected to the network tho..
any idea on how I can get the printer working??
I have no idea wat to enter i the "username" and "password" fields tho..

The moment I hit Windows SMB...i am shown upto n login pages
to various computers on my LAN..where n = no. of computers..

---

### Post by handy on 2006-09-27
**@Wolfbreath**

I use an HP Laserjet 5 on my home network.  It plugs into the network switch (hub), & is accessed by 3 Dapper boxes & a Mac Powerbook on OSX. The LAN used to carry a windoze box which used the printer too.

You have the IP address, that's great!

***DO NOT choose SMB, that is what is confusing the situation.*** 

So, I'll try to walk you through & see how we go:-

***Menu* / System / Administration / Printing**

You could try the:

***Menu* / Global Settings / Detect LAN Printers**

You never know your luck!

If that did you no good then we carry on manualy:-

Double click on the **New Printer** icon, which will start the wizard.

***Printer Type:*** = **Network Printer**

Then choose **HP JetDirect** from the drop down menu to the right of **Network Printer**

Enter the printers IP address beside **Host:** <mine is 192.168.0.99>

Leave **Port** at **9100**

Now you should be able to select the **Forward** button at the lower right hand corner.

On the **Printer Driver** dialogue, select the **Manufacturer:** drop down menu, & choose **HP** then scroll down until you find the **LaserJet 2100** highlight it & then select the **Forward** button again.

In the **Printer Information** dialogue, fill in the 2 fields there with something meaningful to you & then select the **Apply** button.

In the **Printers** window on your desktop, you should now find an icon called **LaserJet-2100** with ***Ready*** written under it!

**Right** click on it & call **Properties** from the menu & try the **Print a Test Page** button at the bottom left of the dialogue, if it works great :D  if not have a look at the other settings in the **LaserJet-2100 Properties** tabs, if you have got this far without problems it should only be a paper source/size type of problem.

By the way I would disconect the 2nd cable going to the windoze box whilst doing this, & then I would set it up as a network printer under windoze too.  There should be no reason to have it connected both ways.

Let me know how you go?

---

### Post by handy on 2006-09-27
> **hellmet said:**
> well, same problem here..
But the printer ain't connected to the network tho..
any idea on how I can get the printer working??
I have no idea wat to enter i the "username" and "password" fields tho..

The moment I hit Windows SMB...i am shown upto n login pages
to various computers on my LAN..where n = no. of computers..

Do you have an HP LaserJet-2100 too?

If you have a printer that connects directly to your network via a network switch/hub, then ***do NOT use SMB...***  

Choosing SMB is causing your problem.

---

