---
title: "Simple Wired Network Assistance Requested ..."
date: 2010-10-17
forum: New to Ubuntu
---

### Post by CDSH on 2010-10-17
Hello again folks,

I am attempting to set up a wired network that includes an XP, a Windows 7, and an Ubuntu machine (all separate boxes).  I loaded samba and apparently set up my Ubuntu sharing permissions correctly.  I can see my Ubuntu box and shared files on my Windows 7 machine and access them (read and write).  

I was also able to connect to the Windows 7 machine by a round about way to see files there.  I was NOT able to access them though.  Also, I've  had to manually put in the IP address of the Windows 7 machine each time I want to see it.  On Windows 7, I can readily see my Ubuntu box listed as part of the network with no problem.  

Here is my question:  Is there a way to get Ubuntu to list my Windows 7 machine automatically ?  So I can see it on my desktop, or, in "Places"  ?

Thank you in advance for any assistance that could be offered.

---

### Post by cavh on 2010-10-17
Does the Win7 box have a static IP address? If so, you can get it to show in 'Places' by doing this:

Click Places, then click Connect to Server, choose Windows share from the dropdown, then type the IP address in the Server box and fill in the other values as necessary.

---

### Post by fbobraga on 2010-10-17
> **CDSH said:**
> Is there a way to get Ubuntu to list my Windows 7 machine automatically ?  So I can see it on my desktop, or, in "Places"  ?

use **bookmarks** in nautilus (the items in "places" menu come from there)

---

### Post by CDSH on 2010-10-17
> **cavh said:**
> Does the Win7 box have a static IP address?

**Yes, it does.**

> **cavh said:**
> Click Places, then click Connect to Server, choose Windows share from the dropdown, then type the IP address in the Server box and fill in the other values as necessary.
[B]
Thank you for helping me to remember how I was able to get to the point of seeing my Windows 7 machine in the first place.  I had forgotten how I stumbled upon it the first time around - I forgot to take notes.

The problem I have is that I want Ubuntu to remember those steps for me.  

Also,  even though I have set up Windows 7 to share the folders and files in question, I cannot access them on my Ubuntu box.  Any suggestions as to what I may have neglected to do ?[/B]

---

### Post by CDSH on 2010-10-17
> **fbobraga said:**
> use **bookmarks** in nautilus (the items in "places" menu come from there)

[B]Nautilus ???  OK, now I feel really stupid.  What is Nautilus, its Bookmarks and how or where do I get it or access it on my system ?

Sorry I am so dense - I really am new at this.

EDITED:  I  found Nautilus - It was the bar that I mistakenly thought was my browser commands.  DUH !  

I was able to add the Windows Share link to the bookmarks.  However, I get a message pop-up that says "Unable to mount location - failed to mount Windows Share".  
[/B]

---

### Post by cavh on 2010-10-18
Have you shared the folder on the Win7 box? I haven't used Win7 myself, but would think you need to right click the folder, click the Sharing or Security tab, and enable sharing.

---

