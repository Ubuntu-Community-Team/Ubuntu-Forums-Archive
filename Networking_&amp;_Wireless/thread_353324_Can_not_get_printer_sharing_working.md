---
title: "Can not get printer sharing working"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by kindafunnylookin on 2007-02-04
I tried setting up printer sharing on Dapper. I followed every post and How To and Wiki I could find to no avail.
Now I am using edgy and want to give it a go again. My set up is:[LIST]
[*]Desktop running Edgy in the KDE enviorment.
[*]Desktop is directly connected to the printer (USB)
[*]Desktop is directly connected to Comcast home networking router(Linksys)\
[*]Laptop is connected to the linksys router by wireless card.\
[*]Laptop is running Windows XP
[*]Each machine can ping the other.[/LIST]Am I doomed to hardwire?
         [IMG]http://ubuntuforums.org/images/uf/misc/progress.gif[/IMG][[IMG]http://ubuntuforums.org/images/uf/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=2105661")

---

### Post by Floppyjoe on 2007-02-04
I would use Cups to connect to the printer on the Desktop from the laptop.Set up the printer as a network printer on the Desktop.

You would need to know the IP address of the Desktop computer and then setup a printer on the laptop which is a network printer with the Url [Http://yourDesktopIPaddress:631/](Http://yourDesktopIPaddress:631/).

Then I would install firestarter so you can manipulate IP tables with it and configure it to allow Ipp conections on port 631 from the Ip address of the Laptop. I think the firewall(IPTables) is started by default on Ubuntu but you need to be able to open this port for access and I think for me the easiest way to do this is to install firestarter. 

This works for me with a similar setup.

---

### Post by kindafunnylookin on 2007-02-04
Thanks--I'll get right going on that and post result.

---

### Post by Floppyjoe on 2007-02-04
Correction I set up the printer on the Desktop as a network printer.

---

### Post by kindafunnylookin on 2007-02-04
> **Floppyjoe said:**
> I would use Cups to connect to the printer on the Desktop from the laptop.Set up the printer as a network printer on the Desktop.

You would need to know the IP address of the Desktop computer and then setup a printer on the laptop which is a network printer with the Url [Http://yourDesktopIPaddress:631/](Http://yourDesktopIPaddress:631/).

Then I would install firestarter so you can manipulate IP tables with it and configure it to allow Ipp conections on port 631 from the Ip address of the Laptop. I think the firewall(IPTables) is started by default on Ubuntu but you need to be able to open this port for access and I think for me the easiest way to do this is to install firestarter. 

This works for me with a similar setup.

That sounded great until I started working on it. I failed to mention that the laptop is running Windows XP. I am returning to original post to edit it.

---

