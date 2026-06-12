---
title: "LinNeighborhood / smb browsing help"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by srstaff on 2006-11-02
'm using LinNeighborhood on Xubuntu-desktop with Dapper. I can see all the WinXP Pcs on my workgroup, but can't see any of the shared folders on any of them.

I assumed I would be able to browse them straight away using LinNeighborhood, but apparently I am missing some setting somewhere.

Any ideas on what may be wrong?


consequently, smbtree seems to show all the windows pcs as well as the shares within them... not sure if that helps...

Regards,

srstaff

---

### Post by srstaff on 2006-11-02
anyone have any ideas, or perhaps is there a better forum for me to try this question on?

srstaff

---

### Post by Miguellint on 2006-11-06
Hi srstaff... I'm as much a newbie as you and don't really know what I'm doing. But after lots of googling/ubuntuforuming I managed to browse my Windows ME computer from my Xubuntu computer using LinNeighborhood.

Here's how I did it. Hope some of it can be of use to you.

Use the search function on Synaptics Package Manager to make sure "smbfs", "smbclient" and  "linneighborhood" are installed....I just typed "smbf" (no quotation marks) into the search and they all came up installed. If not, install them by right-clicking and choose Mark for Installation. 

Next start a terminal and type: sudo chmod u+s `which smbmnt` (note the single quotes either side of which and smbmnt)

Then type: sudo chmod u+s `which smbumount` (again quotes included)

Next type "LinNeighborhood" (no quotes), which should start LinNeighborhood

Then click "Add" in the main toolbar and in the pop-up dialogue box enter the network ip address of the computer you're hoping to browse to (usually something like 192 DOT 168 DOT something DOT something) Then click "Query". Hopefully it will list your XP computer in the main screen.

Right-click on the listing and choose "scan as user". The shared folders should appear.

Right-click on the shared folder you want and choose "mount". In the pop-up dialogue box take a note of the mount point location, leave the rest of the settings as default and enter your password. Click on "Mount"

Now browse to the previously-noted mount point location via your file manager (Thunar?) and open the shared folder. Done.

It worked for me. I hope it works for you.

Regards
Miguel

---

### Post by Naralas on 2006-11-17
I installed linneighbourhood and I don't know how to use it at all -_-

I assumed it was a graphical program somewhere in my normal menu's, but I cannot find it. what am i doing wrong?

---

### Post by fatmomma on 2008-05-25
Perfect instructions..works like a charm..thank you so much

---

