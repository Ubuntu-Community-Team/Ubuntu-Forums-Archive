---
title: "Ubuntu Will Not Access Windows Network Shares"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by VincentValentine on 2008-03-26
I have been running Ubuntu for 5-6 months now on a wireless network here. The internet works very well; however, I cannot access the shared files on my Windows machine.

I have SMBFS installed, and I have the domain name set to MSHOME.

When I go to the places menu and select the network icon, it brings up the network menu, spends a moment loading, and displays an icon that says "Windows Network". I click the Windows Network icon and it leads me to an empty folder. I am sure there are shares on the Windows machine (I connect to it all of the time with another Windows machine)

I have done a thorough search of the forum and the web for others with the same problem, and while I have found several, no definite solution appeared to be reached. 

I would be most grateful for any assistance that anyone could offer.

Thank you,
David

---

### Post by Eiríkr on 2008-03-26
I'm not sure how to fix this particular issue, and I'm beginning to think it might actually be a Samba client bug.  However, there is a relatively easy workaround.  Open your Nautilus file browser, click in the location bar (usually hidden by default, but displayable by hitting Ctrl+L or clicking View -> Location Bar), and type:
```
smb://<windows machine name>
```
Replace <windows machine name> with the name of the machine you're trying to connect to.  In some cases, names don't work, so use the IP address instead.

HTH,

Eiríkr

---

