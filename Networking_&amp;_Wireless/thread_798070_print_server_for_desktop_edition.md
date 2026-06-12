---
title: "print server for desktop edition"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Clark76 on 2008-05-17
I'm using 8.04 desktop edition and wonder if it is possible to configure it to function as a print server?  Through all my googling and searching of this site every reference uses the server edition.  If I have to I will delete my current version and install the server edition but wanted to know if it is possible with what I already have.  

Thanks for any advice provided.

---

### Post by Thirtysixway on 2008-05-17
If you have the printer added already, go over to
```

System > Administration > Printing

```

Click on "Server Settings" and you should see the server options.  You can share printers, setup remote administration, and some other stuff.

---

### Post by Clark76 on 2008-05-17
I want this computer to act as a print router for my wifes laptop that has XP on it so I want to know if this holds true for a desktop edition of Ubuntu.

On the xp when I am setting it up to add a network printer and select [COLOR="Red"]Choose Connect to a printer on the internet[/COLOR] do I still type ```
http://SERVER_NAME:631/printers/PRINTER_NAME 
```only changing **SERVER_NAME** to my computer's name and changing **PRINTER_NAME** to in my case [COLOR="Red"]PSC_1600_series[/COLOR]?

If so then I must have a setting wrong in Ubuntu because that does not seem to work.  I get an error on the wife's lappy that it could not find the printer and that it might be disconnected from the network.  I tested and am able to print from Ubuntu.

In my printer configurations under Server Settings it is checked next to **Share published printers connected to this system** and **Allow printing from the internet**.  Under the printer itself in the policies tab under state Enabled, Accepting jobs, and shared are all checked.  Is there something I missed?  Instead of using the desktop name would it help to use the ip address?

---

