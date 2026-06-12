---
title: "need help with cups"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by mxyzptlk on 2005-11-18
does anyone have succeed with cups?

i would like to know how to configure cupsd.conf file in order to install and share my printer with my network XP boxes

any idea?

btw whats the meaning of  

smbclient -L //DETALL
Password:
session setup failed: NT_STATUS_LOGON_FAILURE


10x in advanced

---

### Post by super-user on 2005-11-19
Hi,

> 
i would like to know how to configure cupsd.conf file in order to install and share my printer with my network XP boxes


This depends on how you want to share your printer. Via Samba is very nice but also quite tricky. When you share them via samba, you can upload the driver so your XP clients automatically install the printer.

Another way is to let your XP clients directly talk to cups. Therefor you have to change the security policies in /etc/cups/cupsd.conf to something like this:

```

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

```

There are more complex locations which are specified, e.g., '/printers/printername' so you can set access rights to one printer.

If you want to speak to cups directly, you also have to tell cups to listen on the external interface. Search for a line like this:

```

Listen 127.0.0.1:631

```

Copy it and change the IP address so that cups will ALSO listen on the external interface. After a '/etc/init.d/cups restart' everything should work.

On your XP clients you can now add a printer. In the dialog choose 'Internet printer' or something like that. It is the last of the three options. Insert the address: 'http://192.168.1.2:631/printers/NAME' where 192.168.1.2 is the ip you specified in the cupsd.conf and NAME is the name of your printer in cups (see /etc/cups/printers.conf).

Read the tutorials: [http://http://www.linuxprinting.org/till/printing-tutorial/tut.html]("http://http://www.linuxprinting.org/till/printing-tutorial/tut.html")

-sudo

---

