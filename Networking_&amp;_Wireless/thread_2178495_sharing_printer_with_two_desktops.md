---
title: "sharing printer with two desktops?"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by macstl on 2013-10-03
I want to have a desktop wired to router with 12.04 and a printer wired to usb on it. I also want a laptop with 12.04 and a wifi connect to the same router.
Ok, assuming I do all of the above sentence , can I share/connect the laptop to the printer wired to the desktop? and how..
thanks

---

### Post by kurt18947 on 2013-10-03
Does your printer have networking?  Wireless networking?  If so, I've had excellent luck sharing a printer connected either wired or wirelessly to the router.  I know it's possible to share a printer connected to one P.C. but have no idea how to do it under linux.

---

### Post by macstl on 2013-10-03
> **kurt18947 said:**
> Does your printer have networking?  Wireless networking?  If so, I've had excellent luck sharing a printer connected either wired or wirelessly to the router.  I know it's possible to share a printer connected to one P.C. but have no idea how to do it under linux.

No , it is not a network printer. It is wired straight to the desktop with usb cable.

---

### Post by ajgreeny on 2013-10-03
You can certainly so what you want very easily in Ubuntu, probably much more easily than if using Windows, but I haven't used windows for a long time so may be wrong about that.

HOST MACHINE WITH PRINTER ATTACHED
1    On the host machine (the one the printer is attached to),
    open System -> Administration -> Printing
2    Select Server in the menu bar, and then Settings.
3    Check the second box:    "Publish shared printers connected to this server "
4    Right click the printer and check the Shared option, if not checked yet 
5    Go to Properties -> Access Control and select "allow printing for everyone"

CLIENT MACHINE TO PRINT FROM
6    Now configure the client (the Ubuntu computer from where you want to print):
7    Open System -> Administration -> Printing
8    Add - Network printer
9    Click Find network printer and specify the host computer IP address eg, 192.168.0.8 (you can find this when using the host machine with command **ifconfig**).
10    Click Find

It works brilliantly for printing, though I can't get scanning to work this way; perhaps that is not possible.

Also I am not sure if you need the appropriate driver for the printer on both machines; I happen to have the driver on both machines, as they both have attached HP printers with hplip installed on both, so if you can't get it to work first time, make sure you install any driver that might be needed.

---

### Post by scbingham on 2013-10-03
Yes you do need the appropriate driver installed on any machine wanting to print to the networked printer.

Also remember that the machine to which the printer is physically attached needs to be on.

---

### Post by ajgreeny on 2013-10-03
> **scbingham said:**
> Yes you do need the appropriate driver installed on any machine wanting to print to the networked printer.

Also remember that the machine to which the printer is physically attached needs to be on.

Thanks for the info about the driver; I suspected it was so, but was not certain.
Also good to point out about the host machine needing to be switched on which I didn't think about.

---

### Post by macstl on 2013-10-03
ajgreeny:::I am using 12.04 , it has Unity .The only icon I can find is "printing" after pressing the gear/wrench lcon on left column on desktop. All "printing" has is a add button to add to local host. This takes me to selection of Network which looks for a printer which is currently connected to a xp machine and finds it. I don't see any selection or drop down menu for "server" anywhere.

---

### Post by scbingham on 2013-10-04
macstl

If the printer you found via the menu is the printer you wish to print to, then select it & try it. :)

---

### Post by ajgreeny on 2013-10-04
I can't help with unity, I'm afraid, as it lost me totally, but if you get to printing as I suggested it should look look like my screenshot, with **server** in the menubar (menubar may be in the screen top panel due to global menu) and that should take you to my second screenshot.

---

### Post by macstl on 2013-10-04
> **scbingham said:**
> macstl

If the printer you found via the menu is the printer you wish to print to, then select it & try it. :)

The printer I have is Lexmark x 1240 and does not work with Linux. I am planning of buying a HP inkjet 1000. And as I described in my first post I wish to replace the xp witn ubuntu 12.04

---

### Post by macstl on 2013-10-04
> **ajgreeny said:**
> I can't help with unity, I'm afraid, as it lost me totally, but if you get to printing as I suggested it should look look like my screenshot, with **server** in the menubar (menubar may be in the screen top panel due to global menu) and that should take you to my second screenshot.

What flavor of ubuntu are you using that has this selection and I presume you are using gnome? And in step 5 "Goto Properties" is that part of the right click the printer step?
Thanks

---

### Post by ajgreeny on 2013-10-04
> **macstl said:**
> What flavor of ubuntu are you using that has this selection and I presume you are using gnome? And in step 5 "Goto Properties" is that part of the right click the printer step?
Thanks

I'm using Xubuntu 12.04.3, but I think the System -> Printing that I show is the same in the other *ubuntu versions, though I could be wrong.  It is certainly the same as in Lubuntu 12.04.

Maybe unity replaces all these things with others that have changed out of all recognition.  Try using the command **system-config-printer** in terminal just in case my understanding of unity is even poorer than I thought, and you should get the same as I show.

---

### Post by kurt18947 on 2013-10-04
> **ajgreeny said:**
> I'm using Xubuntu 12.04.3, but I think the System -> Printing that I show is the same in the other *ubuntu versions, though I could be wrong.  It is certainly the same as in Lubuntu 12.04.

Maybe unity replaces all these things with others that have changed out of all recognition.  Try using the command **system-config-printer** in terminal just in case my understanding of unity is even poorer than I thought, and you should get the same as I show.

I'm not certain system-config-printer is installed by default in Unity as it is in Xubuntu, Ubuntu Gnome & Lubuntu (I think).  It is available in the repositories though.  That's part of my after-a-fresh-install list.  The default printers app in Ubuntu & gnome-shell is next to useless IMO.

---

### Post by macstl on 2013-10-04
> **ajgreeny said:**
> I can't help with unity, I'm afraid, as it lost me totally, but if you get to printing as I suggested it should look look like my screenshot, with **server** in the menubar (menubar may be in the screen top panel due to global menu) and that should take you to my second screenshot.

Good news! I discovered that if I expand the printing config box to fill the screen the server menu shows up at top when I hover over the top.
So When I get my new hp printer I will try this setup you gave me and it should work. Solved. If I have problems I will open a new topic. 
Thank you much ajgreeny!

---

### Post by ajgreeny on 2013-10-05
I am very glad that you got this sorted!

I said I did not know much about unity and all the various differences between it and the "normal" desktop GUIs that I have used,and still use, and this all just shows how correct I was in my inability to help with unity.  There are so many things that were, and still are, easy to do in other DEs that seem to have disappeared from unity, or are hidden away and take a long time for me to find.  Not to worry; we got there in the end.

---

