---
title: "Ethernet Should Work, but doesn't"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by fishmorg909 on 2006-07-31
Ubuntu is a great OS, and i've switched to it for months now. An ol' Dell Optiplex GX1 works great with it. So I install Ubuntu on another GX1... seems fine, except I cannot get on the internet. (It's not an ISP problem, my first GX1 and a Biostar machine work great.)

Where my other PCs hooked up automatically, this GX1 won't connect. The ethernet socket shows a nice green LED, and the computer "sees" a connection, it jus won't hook up. (Puppy Linux -- also a fantastic distro -- has the same problem.) I'm trying to find an easy-to-understand ethernet/ADSL troubleshooting guide, but I can't seem to find one.

Hints: The GX1 had been used for a medical-billing system, and was equipped with gray Type CMR/MPR cables. My ADSL connection uses a yellow Type CM cable. Also: the bootup sequence tells me that it's "unable to locate RDSP." This is probably an obvious thing, but does anyone have any troubleshooting advice? Thanks.

---

### Post by mips on 2006-07-31
Does it help if you swap the cables around ?

Check the Dell's bios and compare it to the working and make sure they are the same. RDSP has something to do with power management if I'm not mistaken.

Try booting with acpi=force or acpi=off or noacpi to see if it helps.

Maybe update the bios while you are at it.

---

