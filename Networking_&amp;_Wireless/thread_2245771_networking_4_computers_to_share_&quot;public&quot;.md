---
title: "networking 4 computers to share &quot;public&quot; and printers?"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by pauls2 on 2014-09-26
I have four computers - two desktops; one running Ubuntu14.04 LTS and one running Lubuntu 14.04 with wired connections to the router, and two laptops; one running Xubuntu 14.04 and the other running Windows 7 that are connected to the router with WiFi.

We have cofigured the printers on the two desktop units for sharing but the Lubuntu computer cannot find the other printer and cannot find the other computers . The main desktop can find and use the Lubuntu computers printer but it cannot find the computer or the other two laptops. The laptops can't see any other computers and or the two printers.

How do I go about setting up a LAN with the four computers?  I am new to Ubuntu and know very little about LANs. I know it is possible but I am just clueless and have a very low confidence level.

I am 64 but am not new to computing. I have been using personal computers since 1972. How about a helping hand?

Paul

---

### Post by Hamburgian on 2014-09-26
Hi Pauls,

I had a similar problem using bot lan and wlan (WiFi) on a single desktop. Have a look at the seetings suggested here:

[http://aleksz-programming.blogspot.de/2013/01/using-wifi-and-network-cable-at-same.html](http://aleksz-programming.blogspot.de/2013/01/using-wifi-and-network-cable-at-same.html)

Although it's a German blog, it's written in plain English. 
The only thing I had to change in this was to keep my Wifi fully open - that is unclick the "use this connection only for it's resources on the network" option.
I think you'll also need Samba installed and configured, but there are lots of tips in these pages to get you set up quickly with that.

---

### Post by pauls2 on 2014-09-27
I have no problem accessing the internet with any of the computers - I just can't access the printers from the other computers.

Maybe I am not literate enough to grasp the blog but it seems to be dealing with internet connectivity and not the local network (which doesn't exist, apparently).

---

### Post by ian-weisser on 2014-09-28
> **pauls2 said:**
> We have cofigured the printers on the two desktop units for sharing

Let's check that.

Go to one of the systems attached to a local printer.
Open a web browser.
Open [http://localhost:631/admin/](http://localhost:631/admin/)
Look for the checkbox "Share printers connected to this system"
Is it checked?

---

