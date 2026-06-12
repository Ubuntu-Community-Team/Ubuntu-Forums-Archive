---
title: "unable to copy from network"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by kevpartner on 2011-03-10
I am running 10.10. Our NAS is a Buffalo Linkstation with a series of shared folders that are accessed from the Windows machines on the network as well as my Ubuntu machine.

I can see these network folders in Nautilus and I can copy files TO the network folders without problems. I can also copy single files FROM the network but if I attempt to copy multiple files, the "File Operations" progress box pops up with a message "Copying 13 files ...." as expected but the progress gets stuck on, for example, 49.2KB of 126.1 KB. No matter how long I wait, no more data gets copied.

This is over wired ethernet. 

Any ideas?

---

### Post by prshah on 2011-03-10
> **kevpartner said:**
> This is over wired ethernet.

All the following commands are to be issued in the Terminal (Applications-Accessories-Terminal)

a) check firewall issues by temporarily disabling firewall ```
sudo ufw disable # use "enable" instead of "disable" to reactivate
``` Disable the firewall, try to copy to/from the NAS, then re-enable the firewall. If the copy is carried out successfully, post back on how to get around firewall issues.

b) If you are also facing problems relating to website browsing (on linux, using any browser) then it may be an MTU related issue; try```
sudo ifconfig eth0 # replace eth0 with relevant network interface, note MTU
sudo ifconfig eth0 MTU 1492 # this changes the MTU, try copying after this command
```
Return the MTU to the old value (probably 1500). If you find that the copying is carried out successfully, post back for details on how to make the MTU fix permanent.

---

### Post by kevpartner on 2011-03-21
Thanks for the suggestions, but they have no effect. Whenever I try to copy multiple files FROM the network, it gets stuck a few KB into the transfer. I can copy single files without problems and I can copy TO the network without problems.

The internet connection is fine.

Kev

---

