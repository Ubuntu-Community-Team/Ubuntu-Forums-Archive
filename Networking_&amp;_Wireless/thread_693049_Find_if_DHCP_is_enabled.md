---
title: "Find if DHCP is enabled"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by 09amw on 2008-02-10
Hi yall

I've been having a lot of issues with my Ethernet connection.  The IT guys think that this could be a result of DHCP not being enabled on my box, sending the ports into mac-address discovery mode.  I believe that DHCP is enabled by default, but I couldn't find out how to check this -- I tried using the graphical configuration tool (which broke my wireless too), and muddling through the ifconfig man pages.  The only google results I'm getting involve setting up a LAMP server, which isn't what I'm trying to do here.

If you know a quick way, either graphically or in the terminal, that I can figure this out, that would be great.  Thanks!

---

### Post by Bubba64 on 2008-02-10
If your using a Ubuntu program go into the network via system administration  open properties and on configuration choose DHCP. I am not sure if this is an answer to your problem. Without knowing what program or computer your using you probably wont get a quick response.

---

### Post by 09amw on 2008-02-10
To clarify, I am using Kubuntu Gutsy on a Dell D610 laptop.  I've got what is essentially a default installation, as I haven't changed any of the connection settings.

---

### Post by Bubba64 on 2008-02-10
As far as I know which isn't much DHCP isn't automatic the only way I know how to set it is in the network I suggested there probably is a terminal voodoo but i don't know it.

---

### Post by nickoli_02 on 2008-02-10
To start DHCP on an interface:

```
sudo dhclient eth0
```

if this works the eth0 interface will be assigned an IP address by your router.

---

### Post by 09amw on 2008-02-10
So, if I'm getting returned NO DHCPOFFERS, I can well assume that the issue is with the network hardware, rather than my software?

Additionally, thanks for the help.

---

### Post by nickoli_02 on 2008-02-10
Make sure your router is set to DHCP and not static IP. Navigate to your router's config page in firefox (usually 192.168.1.1). Also, make sure your ethernet cable is hooked up properly and the link LED is on. If it isn't, try a different ethernet cable.

---

