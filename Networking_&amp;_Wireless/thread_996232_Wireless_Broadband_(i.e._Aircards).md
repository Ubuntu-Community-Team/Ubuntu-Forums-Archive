---
title: "Wireless Broadband (i.e. Aircards)"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by DWade on 2008-11-28
**[COLOR="Red"][SIZE="6"]I liked to let everyone who uses an aircard know, that there is now semi-automatic set up for them in Ubuntu and Kubuntu.[/SIZE][/COLOR]** version 8.10

Aircards are know as CDMA devices.

In Ubuntu select the network Icon on top panel and right click on it. Insure that networking is enabled and enable wireless.

Then click on edit connections and select Mobile Broadband.  with the wireless enabled the Auto Mobile Broadband should be listed.

If not add a new one.  Like Verizon.  If you have AT&T or T Mobile the base setup is already their.

My aircard is verizon.
The user name for verizon is your air cards phone number  Like [email]this-9991235678@vzw3g.com[/email]
and password is vzw.

At this point I do not know if creating a new connection in wizard which only had AT&T or TMobile turned networking on and wireless enabled.
or my creating The AT&T connection and editing it an renaming it to Verizon and changing the dial and setup.

Any way Auto Mobile broadband connection appeared and I edited it and put my log on and password.

So when you want to connect right click on the network icon select auto connect. you be up and running.

No more wvdial or GPPP or in Kubuntu KPPP.  Or that is unless you have snail speed dialup land line..

Thanks
DWADE

I hope this gets placed sticky and the moderator has my permission to correct this and ensure all people using aircards knows of this change.

And can you tell me if this was in 8.04

---

### Post by cigtoxdoc on 2008-12-01
I had my AT&T USBConnect 881 working under 8.04 LTS with kppp by following the Sierra Wireless instructions exactly includng removal of the existing Sierra driver and installing the updated one and filling in the blanks in kppp per instructions and then "messing" with the network connect icon until things started working. When I attempted an upgrade to 8.10, device would not connect anymore.  Problem seemed to be in the network connect dialog.

I took another PC already running 8.10 (with latest updates).  I stuck the 881 in one of the USB ports, and a device was recognized.  However, could not get it to connect.  I tried to configure kppp, but modem section of dialog said device could not be found where it should be found.

Any ideas?

John

---

### Post by DWade on 2008-12-08
The new version 8.10 recognizes the aircard a CDMA device under airprime.

You may have to remove your blacklisted airprime. Or rather comment it out.

Also uninstall KPPP it is not needed for the aircard. It may also be causing the problems

In Kubuntu there is a world icon in the right hand corner.  right click on it and setup the wireless broadband.  When you right click on it it should have wired eth0 and wireless eth2 or something and ttyACMO. Let me know.

If the ttyacmo isn't there it won't connect.

---

### Post by DWade on 2009-04-20
[COLOR="Red"][SIZE="5"]Please Note[/SIZE][/COLOR]:

Kernel 2.6.27.11 causes the aircard CDMA device to be removed and not recognized.   Blacklisting as in 8.04 does not work.


The Good news....  Kernel 2.6.27.14 fixes the problem.

The Bad news ....  Its not a regular update but, a proposed update.

---

