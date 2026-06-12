---
title: "Shoould Samba be a WINS server?"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by jstevans on 2008-11-25
Hi,

I'm trying to get a new install of Xubuntu 8.10 to "see" the Windows machines on my home network.  Initially they could not see the Xubuntu machine but I found that by putting the Xubuntu machine onto the same workgroup and sharing a particular folder they could.  In Xubuntu both are accomplished using "Applications > System > Shared folders."

The "Shared Folders" GUI also has a checkbox for "This computer is a WINS server."  Does that need to be turned on for the Xubuntu machine to be able to see the Windows machines?

One other thing - when I click "Places" it does NOT display a choice for "Network" (Xubuntu locates "Places" in a toolbar that runs across the top of the screen by default).

Jay

---

### Post by prshah on 2008-11-25
> **jstevans said:**
> 
I'm trying to get a new install of Xubuntu 8.10 to "see" the Windows machines on my home network.  
it does NOT display a choice for "Network"

Last I checked, Xubuntu's Thunar file manager lacks proper support for networking, especially Samba shares.

You can use pyNeighborhood (It's in the repos). To install it, either [click here]("apt://pyneighborhood"), or open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install pyneighborhood
```

---

### Post by jstevans on 2008-11-25
Well now, that's a big improvement!  Thanks for the suggestion to use pyneighborhood.  It installed easily enough and I was able to figure out how to get it to scan my network.

So now I can see my home network and the machines connected to it.  Naturally, there are two new problems:

1.  None of the folders will mount.  And yes, I checked - every one can be seen and accessed by all the Windows machines on my network.

2.  Some of the machines found by pyneighborhood "add" easily, just right-click, then click on "Add" and it opens a dialog box that allows me to "try to retrieve missing data" such as IP address.  It seems the IP address is always missing.  In some cases it finds the missing IP address and adds the machine to the right-hand side of the pyneighborhood GUI.  However, in more than half the cases it does not find the address.

Thank you again for your kind assistance.  I am definitely making progress.

Jay

---

### Post by prshah on 2008-11-25
> **jstevans said:**
> 
So now I can see my home network and the machines connected to it.  there are two new problems:

1.  None of the folders will mount.  And yes, I checked - every one can be seen and accessed by all the Windows machines on my network.

2.  Some of the machines found by pyneighborhood "add" easily, just right-click, then click on "Add" and it opens a dialog box that allows me to "try to retrieve missing data" such as IP address.  It seems the IP address is always missing.  

If you are using ufw as your firewall, you need to open Samba ports for access. To check if you are using ufw```
sudo ufw status
```

Otherwise, what firewall (front-end) are you using? (Firestarter?)

---

### Post by jstevans on 2008-11-25
Thank you again for the help.

Entering "sudo ufw status" yield "not loaded"

Unless Xubuntu loads a firewall by default I'm not using one.

As I mentioned at the start, I'm a Linux newbie.  I mastered all this ages ago for Windows, am a stranger in a very strange land for Linux and finding guidance in short supply.  Your help is much appreciated.

Jay

---

