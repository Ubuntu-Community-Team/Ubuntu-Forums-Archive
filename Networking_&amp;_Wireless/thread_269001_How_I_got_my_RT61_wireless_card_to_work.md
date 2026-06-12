---
title: "How I got my RT61 wireless card to work"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by blackdalek on 2006-10-01
I have a D-Link DWL-G510 rev C (Australian model) RT61 chipset wireless card. I had been trying for months without success to get this thing to work in Linux, first trying with Ubuntu and then with Mandriva. This morning I have finally got this card to work with some success. Below is a copy of a post I have made on the RaLink Tech Linux forum...

Well, I'm happy to report that I have now had some success with this damned RT61 chipset card.

Firstly, I dumped Madriva which was getting me nowhere and reinstalled Ubuntu 6.06.1 (using kernel 2.6.15-27-686 SMP PREEMPT)

Downloaded and installed again the build-essential, the make and linux-kernel-headers packages for my kernel.

Downloaded the RT61 drivers in the latest CVS (rt61-cvs-daily.tar.gz) from the serialmonkey project page and made the module according to the instructions in the included readme ("make" then "make install")

Now to get the thing to work with my WPAPSK network, this is what I have to do each time the computer starts up...

I open a terminal window then -

sudo -s
ifconfig eth0 down
ifconfig ra0 up
iwconfig ra0 mode managed
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwconfig ra0 essid "myAPname"
iwpriv ra0 set WPAPSK="myAP'sWPAPSK password"
iwconfig ra0 essid "myAPname" (I don't know why, but it doesn't seem to work unless I do this twice)
dhclient ra0
exit

Then I can ping the AP (ping 192.168.1.1 in my case). I like to just leave a terminal window open with it continually pinging the AP so that I can see that the connection is still working.

I l would ike to stick all the commands above into some sort of start up script so I don't have to type it all in every time, but I'm not sure how to go about doing that yet.

Using this method, I have so far been able to get the RT61 card up and running 5 times in a row without the connection dropping out or failing to get a response from the AP's DHCP service.

---

### Post by alecjw on 2006-10-01
Well, I'm having the same problem (have we talked on Ralink forums before?). I've found out that it works on the LiveCD, but not on the installed system. Can anyone help?

---

