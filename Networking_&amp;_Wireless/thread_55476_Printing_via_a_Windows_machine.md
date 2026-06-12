---
title: "Printing via a Windows machine"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by Gorgonzola on 2005-08-09
My current setup is as follows:

**PC1**: Ubuntu
**PC2**: Windows XP SP2
**Printer**: Canon LBP-3000 Connected to PC2

I can access my shares on PC2 (Windows) over the network from PC1 (Ubuntu).

What is the process I must follow to print from PC1 (Ubuntu) with the printer connected to PC2 (Windows)?

The printer on the Windows machine is shared and works fine for other windows machines.

I have done some reading but all the guides I find assume that the user would want the printer connected to their Ubuntu machine.

I have downloaded the Canon drivers that support my printer and am unsure exactly what I should be trying to do from this point forward. Do I install the drivers and then somehow attempt to locate the shared printer over the network?

Any help would be greatly appreciated!

After having used Ubuntu for only 3 days, I am already very impressed with how helpful the Ubuntu community has been with any queries I have had.

**EDIT:** I actually meant to put this in Hardware forum, not the Networking-specific one, but I guess it is relevant to both.

---

### Post by tonym on 2005-08-09
On the system menu choose administration then printing.  Select add printer then follow the dialogue.  A lot of printers come configured as standard,  hopefully yours will be.

---

### Post by Gorgonzola on 2005-08-10
I had a look there but had no luck so I had a go at installing the drivers from the Canon webpage (I don't believe my model of printer is supported in Ubuntu by default)

I can now see the printer in Ubuntu, however it is pointing to **file:/dev/null**.

How do I write a correct URI for it's location?

The last command I typed was (As per the Canon installation guide):
```
steve@Ubuntu:/usr/sbin$ sudo /usr/sbin/lpadmin -p LBP3000 -m /usr/share/cups/model/CNCUPSLBP3000CAPTK.PPD -v ccp:/var/ccpd/fifo0 -E

```

And the error I recieved was:
```
lpadmin: add-printer (set model) failed: server-error-internal-error
```

---

### Post by Gorgonzola on 2005-08-10
Problem now solved thanks to a helpful IRC user.

It turns out having installed the two driver packages was enough for me to then be able to add the printer via Ubuntu's System->Administration->Printers menu.

Is it worth me writing instructions up on how I got it working from start to finish and adding it to the Wiki for other new Ubuntu users with this same printer?

I think I'll submit a doc to linuxprinting.org as well as this printer is currently not listed.

---

### Post by joels on 2007-07-08
I'm just trying to do exactly the same thing, using a canon lbp3000 connected to a windows machine over a network from ubuntu. Excellent news that its possible and works!
So that would be great if you could write exactly how you did it (I'm a complete linux newbie).

---

