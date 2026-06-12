---
title: "[SOLVED] Want to Share a Printer on a Mixed Network"
date: 2006-12-03
forum: Networking &amp; Wireless
---

### Post by shaft350x on 2006-12-03
I would like to share the printer that I have connected to my desktop with my wife's laptop.  We have a Linksys WRT54G wireless router.

Desktop is running Ubuntu Edgy Eft 6.10
Laptop is running Win XP sp2

Printer HP1510 PSC is connected via USB to the desktop

Laptop connects to router wirelessly
Desktop is wired directly to router.
Router is hardwired to other end of apartment complex to neighbors router which is connected to the internet which we share.

Net --> WiFi Router 1 --> Wifi Router 2 --> laptop & Desktop -- printer

I had tried to get this to work while the computer was running XP and couldn't get the laptop to see the printer.

So how do I get the laptop to be able to use the printer across the network?

---

### Post by shaft350x on 2006-12-04
I tried the How-To here [http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)
to no avail.

Anyone got any ideas on how I can do this?

---

### Post by mitch.c on 2006-12-04
> **shaft350x said:**
> I tried the How-To here [http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1561331&postcount=2)
to no avail.

Anyone got any ideas on how I can do this?
You say you can't get printing configured using the information in this post, but you don't say exactly what behavior you are experiencing.

There was a change to where the Listen directives are placed with Edgy, and the post has been recently updated to reflect that. Could that be the problem?

I notice in your previous post, that you are going through 2 routers. I don't know exactly how you have those wired, but could it be that port 631 is not being forwarded to the desktop computer? This will definitly keep this from working.

Here are some things you can check:

The Listen directives need exist in /etc/cups/cupsd.conf (not /etc/cups/cups.d/ports.conf as for Dapper):
```
Listen *:631
Listen /var/run/cups/cups.sock
```
Restart cupsys:
```
$ sudo /etc/init.d/cupsys restart
```
From the Windows machine, open a Command Prompt and type (change 'desktop' to the hostname or ip address for PC):
```
C:> telnet desktop 631
```
If you get a black screen with blinking curser but *do not* get "Could not open connection to host, on port 631", then you are able to communicate with the cups server. If not, you need to consider that your router may not be forwarding port 631.

If your telnet connection appears to be successfule, try browsing from your Windows machine (change 'desktop' to the hostname or ip address for PC) to: [http://desktop:631/printers](http://desktop:631/printers)

Let me know where this leads, and I'll try to help you troubleshoot.

---

### Post by shaft350x on 2006-12-04
Thanks for your help!

Basically the problem seems to be that the laptop cannot "see" the desktop (which is where the printer is connected).  I had the same sort of problem when I was using XP sp2 on both machines.

When I tried the suggested how-to, I still got the same lack of response.  Also I think that when I changed the cupsd.conf file according to the How-to from the other page, I was no longer able to toggle the option of sharing the printer, it was grayed out.  I just realized as I was typing this that what is shown here is different so  I will give that a shot.

However, I did try the telnet prompt from the windows laptop and got the "Could not open connection to host, on port 631" message.  So this may be more of a problem to do with the network setup than the printer setup.  Although I don't know how to fix that either.

---

### Post by eriefisher on 2006-12-04
Can you ping?

---

### Post by shaft350x on 2006-12-04
Ping from where to where?

---

### Post by mitch.c on 2006-12-04
> **shaft350x said:**
> Ping from where to where?
ping the ubuntu box from the windows box.

---

### Post by shaft350x on 2006-12-04
I guess I just don't know how to do that.  I went to the cmd in the Win Box and tried to ping the hostname of my Ubu box and it couldn't see it.

Even when I was running win on both systems in the same work group I couldn't get the win laptop to view the shared stuff on the desktop.

---

### Post by mitch.c on 2006-12-05
> **shaft350x said:**
> I guess I just don't know how to do that.  I went to the cmd in the Win Box and tried to ping the hostname of my Ubu box and it couldn't see it.

Even when I was running win on both systems in the same work group I couldn't get the win laptop to view the shared stuff on the desktop.
Can you ping the ip address?

---

### Post by Buickman on 2006-12-23
I just had the same problem. Turned out to be firestarter. I created a policy to allow the ip of the windows system, and it finally worked.

---

### Post by Leigemax on 2007-01-19
I've an interesting variation on this problem.

I've followed all above instructions, but when I get to editing the cups, it says I can't save it because the destination is not a folder and that I also do not have the proper permissions.
Do I have to create a root user or am I aotmatically set to one?
If I do have to make a root login, how do I go about it, having only used Freespire before this.

Thankyou muchly

---

### Post by shaft350x on 2007-01-26
Well I am happy to report that now my computer can be seen by the WinXP Laptop.  However it is asking for a User ID and Password to login to my desktop.  I have tried my wife's login and my own, and neither have been successful.  How do I set up an account for logging in or what not?

---

### Post by shaft350x on 2007-01-28
All right, well new twist old game... Windows can now see my machined (I added some drivers in windows) and I also added a user and password to Samba, so I was able to get into the Ubuntu machine and see the printer.  I click on the printer and it asks me to install printer drivers and then it tells me that it has the wrong drivers (from the Windows Machine).  The printer is an HP PSC 1510, and I am using the Ubuntu recommended Hpijs driver.  Any advice here?

---

### Post by shaft350x on 2007-01-29
**[SIZE="5"]RESOLVED!!![/SIZE]**

I got it to work finally!  I went ahead and had Windows install a driver that was on its list, that was close (HP PSC 950).  Since I had already had the printer connected to the laptop the driver was there (just wouldn't show up on the list).  So once I got Windows to accept this I went into the properties of the printer and changed it to the proper driver (HP PSC 1500 series).  Then it worked properly (I had attempted to print twice on the other driver and it locked up the printer).

---

