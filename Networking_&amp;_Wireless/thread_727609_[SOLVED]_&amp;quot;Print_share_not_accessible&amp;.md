---
title: "[SOLVED] &amp;quot;Print share not accessible&amp;quot;"
date: 2008-03-17
forum: Networking &amp; Wireless
---

### Post by AVH on 2008-03-17
I just updated to Gutsy and it trashed my printer connection. My printer is on a windows box which I can see in my network.  I can ping it but  I can't access it: "Folder contents could not be displayed". When I try to install a printer I can browse to the printer and select it but I can't 'verifiy' it: "Print share not accessible". The windows machine has no trouble connecting to the Ubuntu machine. I also have no trouble connecting to other windows machines on the local work group. They just don't have the printer!!

So.. Wha'ts my problem?

Thanx
Alan

---

### Post by IainPurdie on 2008-03-18
Random thought - did you change any user account names when you upgraded? I was having similar problems with connecting two Win2k boxes together so that I could share a printer on one with the other. I ended up adding the username/password from the "client" machine into the "server" one which seemed to do the trick.

If you've connected in the past as one user from that machine and are now effectively connecting as a different one...? Windows has an annoying habit of remembering things you don't want it to.

---

### Post by AVH on 2008-03-19
> **IainPurdie said:**
> Random thought - did you change any user account names when you upgraded? 

No, I didn't change anything. I don't understand why I can see the windows box in the network and browse to the printer in the 'add printer' window and not be able to connect. Is this a permissions issue? Do I have to reset some permissions somewhere?

---

### Post by AVH on 2008-03-19
Changing the name of the windows box to its IP address solved the problem. See this thread:  [http://ubuntuforums.org/showthread.php?t=683279&highlight=inaccessible](http://ubuntuforums.org/showthread.php?t=683279&highlight=inaccessible)

---

