---
title: "Network, after shared folders updated. help!"
date: 2008-03-01
forum: Networking &amp; Wireless
---

### Post by user-unit on 2008-03-01
Ok, so my network is running and I can access everyone else running windows xp, so I went into System > Administration > Shared Folders and let both updates go for networking.

all should be good right? I can no longer access anyone on the network though, im still new and I have browsed around everyplace i can think of but haven't seen anything that would be able to help me, or so i think.

So, how do i get it so i can at least access other PC's again? how would i be able to troubleshoot to pinpoint the problem? I would like to get it to network back and fourth as i have another PC running Ubuntu/Kubuntu

---

### Post by kesomir on 2008-03-01
I find ssh to be a quick way to access my other ubuntu pc's that I have an account on

To find the ip address of your other machine open a shell window (Applications->Accessories->Terminal) and type 

```
ifconfig 
```

into it - read the ip address from there.

to install ssh:

```
sudo apt-get install ssh
```

do that on each of your machines - I'm happy with the defaults, but you can view the wiki for details on making it even more secure.

Once done, return to the first pc and in nautilus address bar type ssh://username_on_other_pc@ip_of_other_pc

eg: ssh://root@192.168.1.2

If you use kde type fish://root@192.168.1.2 into the address bar of konqueror to get the same effect.

you can then use the file browsers to drag and drop files between the computers.

if you are troubleshooting network connectivity use the command ping 192.168.1.2 (replace 192.168.1.2 with the address of the machine) to see if you can talk to it. Use Control+C to cancel the pings.

---

### Post by user-unit on 2008-03-01
that might help with networking between the Ubuntu machines, but i haven't convinced anyone else to use it and i still wish to access windows as well.

---

### Post by Graphite on 2008-03-01
I get told that "Nautilus cannot display "ssh://bugs@192.168.2.2". Please select another viewer and try again".

Any thoughts? I can ping successfully, but can't access the other computer using samba, NFS, the GUI method (System>Shared Folders) or now this.

I've spent the whole afternoon on this trivial task and it's sending me crazy. I'd really appreciate some advice!

EDIT:
One computer running Ubuntu 6.06, the other running Ubuntu 7.10. The computers are both plugged into a modem/router, through which they access the internet and can ping each other.

---

### Post by user-unit on 2008-03-01
I have the ssh method working but i still need a solution to accessing the other computers on the network, 2 windows and 2 linux's, I can ping them just like the other poster but I want to access specific files, not the whole system.

---

