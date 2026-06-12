---
title: "DEC21041 &quot;tulip&quot; is installation blocker"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by ebbi97a on 2005-11-19
I have an ethernet card with **DEC chip** (guess it is called *21041*, as this number is displayed in various lines).

When installing Ubuntu 5.10 the installation routine pretends to have recognized the card automatically, but when it comes to configuring the network, the process will hang without error message both in DHCP mode and in manual mode.

The same was true for the previous version 5.04 .

A few months ago I have installed Debian 3.1 on exactly the same hardware and similar effects occurred. Somehow (can't remember how) I was able to complete the basic installation and had a chance to look into /etc/modules and found that it had recognized the ethernet adapter in a wrong way: not as "tulip" but as "DEC...".

I don't know what the precise difference may be, but when I corrected this manually the ethernet was accepted and working.

What I would need now is a chance to tell the installation routine what kind of module it should load. But there was no way   :-( 

Maybe I just overlooked something?

---

### Post by ebbi97a on 2005-11-26
[QUOTE=ebbi97a]I have an ethernet card with **DEC chip** (guess it is called *21041*, as this number is displayed in various lines).

 ...
A few months ago I have installed Debian 3.1 on exactly the same hardware and similar effects occurred. Somehow (can't remember how) I was able to complete the basic installation and had a chance to look into /etc/modules and found that it had recognized the ethernet adapter in a wrong way: not as "tulip" but as "DEC...".
...
What I would need now is a chance to tell the installation routine what kind of module it should load. But there was no way   :-( 
[/QUOTE]

:( 
As it seems to be quite hopeless to find a solution, I will exchange the ethernet card against another one with *Realtek 8029* - that type never caused any problem with any Linux. :rolleyes:

---

### Post by ebbi97a on 2005-11-28
So it was!

After installing the other card I could also install Ubuntu 5.10 without any trouble.

Strange thing: the module for *tulip* is available in the basic installion and I could load it via *modprobe*. I also inserted it into _/etc/modules_.

Unfortunately the Farallon card with that DEC chip suffered a damage by plugging/unplugging. After I reinserted it into the computer, it was not recognized by either of the operating systems on the machine - including 2 others it was cooperating before.
  :-(

---

