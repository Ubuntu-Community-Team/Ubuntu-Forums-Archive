---
title: "I ALMOST have Edgy able to connect to my Vista computer's shares,"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by bobbob1016 on 2007-03-04
I was having issues getting my Vista machine (it came with XP, I got it from a client and put my free copy of Vista I got from school on it), to see ANYTHING Shared on my network, through the equivelent of "View Network Computers" the "Network and Sharing Center".  I did some google-ing and I found a few places that centered on XP to Vista share problems, so I tried some of those.  One suggested disabling IPV6 in vista, which I did, another said to Enable NETBIOS over IP, which I did.  

Then I found one that said to get to the Local Security Policy options, (click the orb thing, formerly the start button, and type in Local Security Policy, the program should show up there).  Then click the triangle next to Local Policies, then click Security Options.  Look for "Network security: LAN Manager authentication level" on the right, in my case, it said NTLMv2 only, which I changed to "Send LM & NTLM".  I rebooted Vista, and my shares started showing up.  However when I try to connect Edgy to Vista, I get an endless cycle of Authentications, but Vista can get to Edgy fine.

When I try to mount the Vista drive through the terminal I get:
7603: tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

I have the same Username/Password/Domain on both machines, so I don't see where the problem is.

EDIT: I got it working, through terminal, I had the wrong folder name, but I still can't connect through browsing the network.

---

### Post by winter7 on 2007-03-04
I've been playing around with this myself... I saw that error myself... I think it was because my share had a space in it... I was doing this by adding the share to /etc/fstab.

What worked is to replace the spaces with \040
so ...
//Windows\040Share instead of //Windows Share

HTH
-Dino

---

### Post by bobbob1016 on 2007-03-04
I got the Vista share mounted through the terminal, I was just wondering how it could be done through the GUI.  I did "sudo mount //IP.OF.VISTA/SHARE /media/ShareName -o username=user,password=pass,dmask=777,fmask=777" and it worked fine.  The only question I had was if anyone knew how to browse/mount through the GUI.

---

