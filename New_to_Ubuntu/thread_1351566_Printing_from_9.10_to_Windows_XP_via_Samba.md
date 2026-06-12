---
title: "Printing from 9.10 to Windows XP via Samba"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by JohnnyB98604 on 2009-12-10
I've installed samba.  I go to System/Administration/Printing and click "Add".  It looks around but can't find anything, then I choose "Windows printer via SAMBA".  It wants to know the SMB Printer, I choose "Browse" and I can see the group I want (WORKGROUP) but when I click the down arrow I don't get any further, the cursor spins for a while...it's working on something but it never seems to "resolve".  The printer is a Brother MFC240C and it's connected via a USB cable.  It's "shared" on the XP box and I've verified the workgroup name as "WORKGROUP" on both the XP box and the Ubuntu box.

I know I'm really close to getting this worked out...what step am I missing?

---

### Post by JohnnyB98604 on 2009-12-11
Bump (sorry to seem impatient)

---

### Post by ukripper on 2009-12-11
Replace the name of your xp computer to the ip of your xp computer in "Windows printer via SAMBA" and then try to connect. i think it is not resolving the netbios name

---

### Post by JohnnyB98604 on 2009-12-11
> **ukripper said:**
> Replace the name of your xp computer to the ip of your xp computer in "Windows printer via SAMBA" and then try to connect. i think it is not resolving the netbios name

This worked for getting the connection established.  Now I think I just have to download the driver for the printer (because it's not in the supplied list for Brother printers)

I'll repost if this is resolved.

---

### Post by ukripper on 2009-12-11
> **JohnnyB98604 said:**
> This worked for getting the connection established.  Now I think I just have to download the driver for the printer (because it's not in the supplied list for Brother printers)

I'll repost if this is resolved.

This may help - [http://ubuntuforums.org/showthread.php?t=486346](http://ubuntuforums.org/showthread.php?t=486346)

---

### Post by JohnnyB98604 on 2009-12-11
RESOLVED!

Thanks so much for the help.  After specifying the IP address and printer name I needed to go to the Synaptic Package Manager and download approximately 8 packages.  The really nice thing all I had to do was search for "MFC-240C" and it found them all for me, suggested that I install all of them to make it function correctly.  Then I needed to reboot to get all the services refreshed and talking to one another (I imagine if I knew more about ubuntu and Linux I could've just restarted the necessary services), then VIOLA!  the printer is there, the test page printed...all is well in ubuntu land.

Thanks so much for your direction is this, I could not have figured this out alone.

---

### Post by ukripper on 2009-12-11
Great I am glad it worked out for you! Now you can mark this thread as Solved from thread tools.

---

