---
title: "Lost internet connectivity on 2 machines"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by homegrown-holio on 2008-09-04
I'm a recent windows convert although I still have one XP system running... which is the only way I was able to make this post!  Please forgive any dumbness on my part, I've used nothing but winblows until about two months ago and now trying to sever the relationship completely.

So... Tuesday I lost the internet connection on my wife's pc running Kubuntu and my eee900 running Ubuntu-eee.
I've checked my wireless router (Netgear, 54mbps) and cable modem connections - all's fine.
The eee does not even see my wireless network (and I live in the boonies so there aren't any other networks for it to see or I would have tried to test the connection elsewhere).
On the desktop, I tried reactivating the connection (several times) and rebooting (also several desperate but futile times)... it goes through the motions of renewing the IP but still no connection.
All I get on both computers when I open a browser is 'Page Load Error' 'Address not found' 'Firefox cannot find the server at...'.

I wish I could provide more details but I really haven't got the slightest idea of what to do next other than reinstall and hope they both work again as they did a week ago!
Thanks very much in advance for any guidance!

---

### Post by mrsteveman1 on 2008-09-04
Ok so you can't even see the network in the networkmanager applet in the corner?

What happens when you open a terminal and type "sudo iwconfig" and "sudo iwlist scan"

---

### Post by homegrown-holio on 2008-09-06
Apologies for the delay!  Work work work...

This is what I got when I typed those commands:
Kubuntu desktop
sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

sudo iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

Knetworkmanger icon is the task panel (sorry for the windows reference) and it shows the ethernet 'device' as active... 

Ubuntueee Eee900 laptop
sudo iwconfig
lo        no wireless extensions.

sudo iwlist scan
lo        Interface doesn't support scanning.

The network manger icon is also visible on the eee but when clicked says 'no network devices have been found' and option for 'manual configuration'

I'm 'usually' pretty good with computers; this is the strangest thing that's ever happened to me!

---

