---
title: "Complete noob!"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by zebadee on 2008-05-03
Hi :)
Having decided to give ubuntu a go.
I am stuck at the connecting to net stage.
The system sees the PC end, but not the other end.
What do I do?
(I assume I have to configure manually)
What info do I need to give (if any).
TIA 
(Currently loving Vista Ultimate 64bit :roll: Sorry folks)

---

### Post by Paris Heng on 2008-05-03
> **zebadee said:**
> Hi :)
Having decided to give ubuntu a go.
I am stuck at the connecting to net stage.
The system sees the PC end, but not the other end.
What do I do?
(I assume I have to configure manually)
What info do I need to give (if any).
TIA 
(Currently loving Vista Ultimate 64bit :roll: Sorry folks)

Just look into >> Configure the network configuration file. **/etc/network/interface**. and manipulating the Kernel routing table.

---

### Post by Aearenda on 2008-05-03
Not really sure what you mean by 'see the PC end, but not the other end.'...

You should not have to configure anything manually if you have a typical broadband setup. Ubuntu expects to get all its network details from the router just like Vista, using DHCP. If you have wireless, you will need to tell the system to connect by clicking on the little network icon in the system tray and choosing your network.

---

### Post by zebadee on 2008-05-03
Hi :)
Thanks for the responses guys.
As a noob not sure what "Just look into >> Configure the network configuration file. /etc/network/interface. and manipulating the Kernel routing table." means or why I need to look at that.
Sorry.

" Not really sure what you mean by 'see the PC end, but not the other end.'..."
What I mean is that the installation was a success, so can see that the PC h/w is setup for wifi.
Just doesn't see the router.

---

### Post by Iowan on 2008-05-03
Verify a couple of things... Under "Manual Network Configuration (that's the icon in upper right corner that looks like two monitors), see that you're set for "Automatic Configuration (DHCP)".  If "Enable roaming mode" is checked, try unchecking it.

---

### Post by zebadee on 2008-05-04
Hi :)
I have tried your suggestions, or at least would have.
But I don't get them.
A lot of it is greyed out.
So I've no idea what's going on here. :confused:

---

### Post by Aearenda on 2008-05-04
Did you try clicking the 'Unlock' button to enable changes?

---

### Post by zebadee on 2008-05-04
Hi :)
An update.
When I tried an install from Windows, I got the install couldn't complete. Missing files.
So I downloaded again. Burn ISO etc.
This time on install everything went OK.
Did the manual bit as already mentioned,
Have now got to the point where it appears to connect to router.
But at 0%.
So still no internet. :lolflag:

---

### Post by Aearenda on 2008-05-04
Please will you post the output of the following commands, run from a terminal:```
lspci
lshw -C network
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig
iwconfig
route
cat /etc/resolv.conf
``` and maybe tell us what is in the kitchen sink too :-D

To do this, start your reply to this message, and then start the terminal session from applications->accessories.
Maximise the terminal window using the mouse, so you can see more of the output.
Type the first command in the list, and select its output using the mouse.
Press CTRL and SHIFT and c to copy it to the clipboard.
Switch to the web browser and paste the output into the reply.
Switch back to the terminal and repeat with the next command.
When you have finished, CTRL and d will close the terminal session.

---

### Post by zebadee on 2008-07-19
Hi :)
Well installed on a different PC.
Had to go without Raid & make sure that the SATA drive was first in line.
But other than that no problems.:lolflag:
Oh & no longer wireless.
Using powerline.

---

