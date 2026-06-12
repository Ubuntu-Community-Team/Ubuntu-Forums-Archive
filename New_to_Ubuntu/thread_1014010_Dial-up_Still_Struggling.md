---
title: "Dial-up: Still Struggling"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by drneals on 2008-12-17
I am still struggling to get my new Dell Mini 9 running Ubuntu 8.04 connected to the internet using a new US Robotics USB Modem USR5637. The earlier recommendations lead nowhere. By exploring I found that Network Manager should do the job. I have been unable to locate any good instructions. For example: I have the Domain Name Servers but it is not clear to me what format they should be entered into the table. I have a recollection that it should be xxx.xxx.xxx.xxx where the x's stand for a digit. Is that correct? Also, there is no provision for a Primary and Secondary DNS address as in Windows. Also there was a 10.0.1.1 in the table. I deleted it. Why was it there?

Also, in Windows one has to connect to the internet via clicking on buttons. I have not found such an option in Ubuntu. Can someone comment on the exact procedure to initiate the dial-up?

---

### Post by billgoldberg on 2008-12-17
> **drneals said:**
> I am still struggling to get my new Dell Mini 9 running Ubuntu 8.04 connected to the internet using a new US Robotics USB Modem USR5637. The earlier recommendations lead nowhere. By exploring I found that Network Manager should do the job. I have been unable to locate any good instructions. For example: I have the Domain Name Servers but it is not clear to me what format they should be entered into the table. I have a recollection that it should be xxx.xxx.xxx.xxx where the x's stand for a digit. Is that correct? Also, there is no provision for a Primary and Secondary DNS address as in Windows. Also there was a 10.0.1.1 in the table. I deleted it. Why was it there?

Also, in Windows one has to connect to the internet via clicking on buttons. I have not found such an option in Ubuntu. Can someone comment on the exact procedure to initiate the dial-up?

> You need a USB modem driver (CDC ACM) compiled into a Linux ker-
nel 2.4.20 or higher or as a loadable module for your kernel. Installation
of the modem under these kernels is fully automatic provided your kernel


from the usr website.

--

Try this command from the terminal:

sudo /sbin/modprobe cdc-acm

And then plug in the modem.

---

### Post by Flimm on 2008-12-17
> **drneals said:**
> For example: I have the Domain Name Servers but it is not clear to me what format they should be entered into the table. I have a recollection that it should be xxx.xxx.xxx.xxx where the x's stand for a digit. Is that correct? Also, there is no provision for a Primary and Secondary DNS address as in Windows. Also there was a 10.0.1.1 in the table. I deleted it. Why was it there?Yes, use the xxx.xxx.xxx.xxx format, that's standard for IP addresses.
To add primary and secondary DNS servers, open Network Manager, click on Unlock, (enter password), then click on the DNS tab. Click Add and type the address of the primary DNS server, then click add and type the address of the secondary server.

---

### Post by cek on 2008-12-17
Let's start with the basics -- what is the actual problem?

Are you connected to your ISP but cannot connect to websites?  That could potentially be a DNS issue, however, if you still haven't got connected in the first place, we need to start there first.

So, first step, explain the problem in its entirety.  Have you connected to your ISP with wvdial/gnome-ppp/kppp?

I have this same modem, and was able to get online very easily with it.


The modem is usually detected as /dev/ttyUSBACM0, running this command in a terminal should setup a /etc/wvdial.conf file template for you to edit:

sudo wvdialconf

From there, edit the /etc/wvdial.conf file changing your username, password and phone number:

sudo gedit /etc/wvdial.conf

Then, run this command to physically connect:

sudo wvdial

That should connect to your ISP and eventually show an IP address for ppp0, and primary and secondary DNS addresses (the default behavior is to get this information from your ISP).

At that point, you are physically "connected" -- you may still have problems connecting through Firefox because the Network Manager in 8.04 (and 8.10, btw) doesn't properly handle dailup connections for ppp0.  IF you got this far, check to see if Firefox is in "Offline Mode" -- if it is take it out of "Offline Mode" and try again.

---

