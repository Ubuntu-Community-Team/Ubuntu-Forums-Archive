---
title: "how to share a printer in ubuntu to another ubuntu machine"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by clflyer on 2007-11-05
I have Ubuntu running on a Desktop and on my laptop, Gutsy Gibbon 7.10 for both.
The Desktop has a printer connected to it and I want to get the laptop to be able to print to it. On the Desktop I setup the print server to share the printer. On the Laptop I am unable to see it. Both machines are on the same network, both can see the Samba Windows XP printer on a 3rd XP PC. 
The laptop has shared it's Samba connection to the XP Printer and the Desktop can see it when it looks at the printers the laptop has. It can even print to it using the laptop's connection.
However the laptop cannot see any printers the desktop has.
I'm missing something that is probably very simple, but can't figure it out.:confused:

---

### Post by jimrz on 2007-11-05
> **clflyer said:**
> I have Ubuntu running on a Desktop and on my laptop, Gutsy Gibbon 7.10 for both.
The Desktop has a printer connected to it and I want to get the laptop to be able to print to it. On the Desktop I setup the print server to share the printer. On the Laptop I am unable to see it. Both machines are on the same network, both can see the Samba Windows XP printer on a 3rd XP PC. 
The laptop has shared it's Samba connection to the XP Printer and the Desktop can see it when it looks at the printers the laptop has. It can even print to it using the laptop's connection.
However the laptop cannot see any printers the desktop has.
I'm missing something that is probably very simple, but can't figure it out.:confused:

try installing 'gnome-cups-manager' from Synaptic on your laptop  then sharing using cups. You will see a 2nd printing icon in System > Administration. Click on the new one and when it opens click on Global Settings and select 'detect lan printers' and "share printers". Next double click new printer then select "network printer', the default ipp location would be
```
ipp://<ip address of your desktop>/printers/<name of the printer>
```
mine looks like this
 ```
ipp://192.168.0.2/printers/PSC_1600_series
```
then proceed as usual with the printer mfg/type/driver selection.
I have found this much simpler than trying to share between ubuntu boxes using samba. Another bonus is that your PDF printer will then save files to /home/<user>/PDF folder rather than whatever unlikely place the foomatic thingy saves to.

---

### Post by clflyer on 2007-11-06
I was going to try your suggestion but tonight I got several CUPS updates. The next thing I heard was the printer printing, I love an operating system that heals itself...
Bill

---

### Post by jimrz on 2007-11-06
> **clflyer said:**
> I was going to try your suggestion but tonight I got several CUPS updates. The next thing I heard was the printer printing, I love an operating system that heals itself...
Bill

[SIZE="5"]:)[/SIZE]

---

