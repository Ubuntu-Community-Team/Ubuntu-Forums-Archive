---
title: "Connectivity issues with WPA2 Enterprise and ubuntu 13.10 and up"
date: 2014-10-24
forum: Networking &amp; Wireless
---

### Post by Marc_Tremblay on 2014-10-24
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]Good afternoon,[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]We have been converting our older fleet of desktops and laptops to Lubuntu and Ubuntu at our school board and the process has been going well but I have ran into a strange problem. For us to get connectivity on our laptops and Netbooks we are forced to use version 12.04 LTS of Lubuntu in order to get a WIFI connection. We have the same issue if we try to use kubuntu, Edubuntu, Xubuntu, or Ubuntu. Any version newer that 12.04.4 will not allow us to connect to our WIFI network.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]Here are the setting we are using:[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]WPA2 Enterprise[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]PEAP version automatic[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]Inner authentication: MSCHAPv2[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]CA certificate: none[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2] [/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#282828][FONT=Segoe UI WPC][FONT=Calibri,sans-serif][SIZE=2]When I upgraded one of the laptops from 12.04 to 14.4 it did however keep the WIFI connectivity but I really don’t want to have to do an install of 12.04 and then upgrade each time.

Any help wiuld be greatly appreciated.[/SIZE][/FONT][/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-10-24
I would be tempted to install 14.04 LTS on one of the machines and post a new thread here to trouble shoot why the wifi is not working. 12.04 LTS is supported until April 2017, BTW, and is suitable for a production setup. If you want stability, you're good to go. 

But, yea. I'd troubleshoot why wifi is not working on 14.04.

(PS: Have you compared the wireless configuration in 12.04 to the wireless configuration in a 14.04 install? Are they identical? In Network Manager, if that's what you're using?)

(PPS: Where does 13.10 come into this? If you're tempted, don't use that. It is no longer supported. ;))

---

