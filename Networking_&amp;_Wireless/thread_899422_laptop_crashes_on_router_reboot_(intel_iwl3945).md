---
title: "laptop crashes on router reboot (intel iwl3945)"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by xorkid on 2008-08-24
In Hardy (up-to date 24/08/08) when the access point is rebooted, the laptop freezes if connected to it. only the caps lock is left flashing- which indicates the bios/firmware watchdog kicked in to stop hardware damage. 

The only way to fix is by forcing laptop off- pressing power for ~10 seconds.

The access point is a netgear dg834gt router (based on some embedded linux, with atheros card). "Encryption" is WEP 128. It happens even if the router reboot is done cleanly on the web interface. Completely repeatable, just have to reboot my access point to consistently freeze the laptop. dmesg does not show anything laptop has iwl3945:

 ```
Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] 
```

Just wanted to confirm this is a bug or if anyone else has seen the same issue before posting to the bug tracker (I have searched forum and launchpad). Also some means of debugging or logging after a reboot would be helpful.

should I post to launch pad? if so what information should i include (how to get it)?

---

### Post by xorkid on 2008-08-25
anyone here?

---

### Post by Crafty Kisses on 2008-08-25
> **xorkid said:**
> anyone here?

Post the results of:
```
lshw -C network
```
```
lspci
```

---

### Post by netwarriorwy on 2009-03-24
I'm having the same problem with a HP Pavilion dv6000 with iwl3945 driver. When I connect my laptop to my house wireless network (DHCP & WEP 128 security) there's no problem at all, the problem happened today when I connected to my university wireless network (DHCP with MAC filter and NO security) it just got frozen several times and the caps lock key was flashing, right now I'm connected to an unsecured network I found somewhere near the street...Is this could be because of the a/b/g/n protocol????.:(
PS. Im attaching the result of the code:
> sudo lshw -C network
> lspci

---

