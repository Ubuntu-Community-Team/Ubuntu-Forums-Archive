---
title: "dlink printserver dp-300u"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by pinelands on 2005-05-27
Trying to map to this server which has a hp photosmart 1100. printer is supported but unshure of config to access it 

thankyou
john

---

### Post by DawgSoldier on 2006-01-12
I also have a DP-300U print hub but I have a HP Officejet V40 hooked up to it.  I have tried several different things to make it work.  I tried to use the HP Jetdirect setting and I did a port search on that IP address and it said that the printer was on 515 so I changed the default 9100 to 515 but it still didn't work.  Any suggestions would be appreciated.  Besides the printer issue I love the OS.

Tom

---

### Post by killhup on 2006-10-22
Hi there!

I also had some problems with printing through my D-link 824VUP+. This is how a managed it.

First choose UNIX Printer = lpd and then your printservers adress ex. 192.168.1.1 as host and then on queue you should print lp. 

This worked for me and I'll hope it will work for you to.

regards

/Killhup

---

### Post by calvmari on 2006-12-01
Killhup, thank you VERY much :D 

I remember setting up the printserver for linksys a few years ago and I literally had to hack the printserver so it would even talk to linux.

With your little tip I was done in 1 minute. Much thanks!! Linux sure has come a long way.

---

### Post by iml2860 on 2008-01-04
I have just configured my DLink DP-300U on Ubuntu 7.1 (Gutsy) and I thought I would share the info with you:  

First thing to do is to use a web browser to go to your DP-300U (simply type in the IP 192.168.x.x within Firefox).  Once there, look down the Printer Status section and write down the Printer Name for the USB, LPT1 & LPT2 printer ports.  Now that you've everything readied let's:

1/. Go back to your desktop and press SYSTEM, ADMINISTRATION, PRINTING.
2/. Followed by "New Printer", "LPD/LPR Host or Printer".
3/. Type in the IP to your DP-300U as Hostname and the Printer Name you've previously written down as Printername and press the Forward buton.
4/. Choose the Make & Model of your Printer and press Forward.
5/. Fill in the Name, Desc & Location and press Apply.
6/. Press the "Print Test Page" button and everything should be good.

I hope this help.

---

### Post by tanapon on 2008-07-01
> **iml2860 said:**
> I have just configured my DLink DP-300U on Ubuntu 7.1 (Gutsy) and I thought I would share the info with you:  

First thing to do is to use a web browser to go to your DP-300U (simply type in the IP 192.168.x.x within Firefox).  Once there, look down the Printer Status section and write down the Printer Name for the USB, LPT1 & LPT2 printer ports.  Now that you've everything readied let's:

1/. Go back to your desktop and press SYSTEM, ADMINISTRATION, PRINTING.
2/. Followed by "New Printer", "LPD/LPR Host or Printer".
3/. Type in the IP to your DP-300U as Hostname and the Printer Name you've previously written down as Printername and press the Forward buton.
4/. Choose the Make & Model of your Printer and press Forward.
5/. Fill in the Name, Desc & Location and press Apply.
6/. Press the "Print Test Page" button and everything should be good.

I hope this help.

Thank you! I never thought it's as easy as that.

---

