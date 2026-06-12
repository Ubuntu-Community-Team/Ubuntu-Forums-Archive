---
title: "Configuring linux as a router using a pci adsl card"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by wp.rauchholz on 2016-11-19
I want to setup my Linux home server as the modem / router of my network.
Would somebody please recommend me a pci card for a fiber-optic internet connection.
Can't find anything in google and/or forum here

THis is basically what I intend to do:

[IMG]C:\Users\103000514\Downloads\Capture.JPG[/IMG]


Thanks, Wolfgang

---

### Post by ian-weisser on 2016-11-19
I did something similar a few years ago.
After a few months, I separated server and modem/router into separate boxes.
Partly security, partly for uptime and reliability: A server crash kills the network, which makes restarting the network much harder! (And you cannot go online to look up a solution while your network is down)

---

### Post by wp.rauchholz on 2016-11-19
I understand you propose to use the modem in bridged mode. I'll think about it.

But still if I was to go the the initial idea, are there PCI cards available for fiber optic?

---

### Post by SeijiSensei on 2016-11-19
To me, this looks like a better solution if your cable run is less than a third of a mile.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833114041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833114041)

It takes up to a 1Gbit fiber and converts it to Gigabit Ethernet.  I don't know whether the 550m distance limit poses a problem in your application.

More pertinent to your request is [http://www.newegg.com/Product/Product.aspx?Item=N82E16833114083](http://www.newegg.com/Product/Product.aspx?Item=N82E16833114083)

It appears to have [Linux support]("https://www.startech.com/Networking-IO/Adapter-Cards/PCI-Express-10-100-Mbps-Ethernet-Fiber-SFP-PCIe-Network-Card~PEX100SFP"), but it's only 100 Mbit if that matters.  I couldn't tell whether the driver comes with the Ubuntu kernel or whether you need to install it.

---

### Post by wp.rauchholz on 2016-11-25
Thank you SeijiSensei
Is there somebody in this community, living in Spain who can confirm that it works to create the PPPoE with Telefonica/Spain?

---

