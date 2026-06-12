---
title: "Unable to see Windows share"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Red Rhino on 2008-06-23
Hi,

I have a Windows system that I have set up a share on. I can see the system, but when I pull up any Windows shares I get nothing. I appear to be doing the process right because I can pull up Windows shares on other Windows computers, just not this one. I am using Ubuntu 8.04 and the other Windows computers are all WinXP Home Edition. My other Windows systems can see the share I'm trying to see from Linux, so that appears to be set up right. 

I rather new to Linux so hopefully this will be an easy one for someone. 

Thanks

---

### Post by UbuntuNerd on 2008-06-23
im new to ubuntu but i also had the same problem are you using a firewall and if so that could be it i know it was for me im using firestarter very simple to configure you have to allowed some of the different ports for file sharing hope this works

---

### Post by superprash2003 on 2008-06-23
try this.. go to places->computer and under location type smb://x.x.x.x where x.x.x.x is the ip of the windows machine

---

### Post by Red Rhino on 2008-06-23
I was not able to connect by disabling the firewall on the Windows machine, but was successful in seeing the shares and connecting by using the IP Address. Since I do not have to do this for the other machines, will I always have to do it this way, or will setting that machine up with a static IP help?

Thanks again!

:)

---

