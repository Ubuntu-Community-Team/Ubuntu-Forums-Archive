---
title: "Can't get to samba shares in Kubuntu"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by arbulus on 2008-04-25
I'm running Kubuntu Hardy KDE 4 remix on an old Dell.  I also have another box that is running Ubuntu Gutsy as a file server serving up a few samba shares.

On the Kubuntu box, when I open up the file manager and click on "Network" and then click the icon to view Samba shares, it tells me:
```

Could not connect to host for smb://smb-network/
```

Now, on my laptop that runs Ubuntu Hardy with Gnome, I just open up Nautilus, and go to Network>Windows Network>Workgroup Name>Machine>Share and I'm there.  Does this work differently in KDE 4?  What do I have to do to get Kubuntu to browse the samba shares?

---

### Post by Wartooth on 2008-04-26
I'm getting the same error on a clean install of Kubuntu with KDE 3.  Hopefully we'll get some help.

---

### Post by buspital on 2008-04-26
same problem here. I've got a machine running windows home server which i can browse to in dolphin if i put the address in like smb://192.168.0.3, but going to network and clicking samba shares gives the error mentioned. If i go to "add a network folder" it complains it can't connect to the server.

---

### Post by Wartooth on 2008-04-27
Well, my problem is solved.  It was all on the Windows side.  The HDD I'm wanting to access is the slave drive of my XP machine.  It used to be a full-on installation of XP, and I've deleted most of the Windows stuff on there, but not enough.  There are various parts of the drive I can't get to, it asks for passwords that have never been set and all sorts of craziness, even after making the drive shared as shared can be.  

Moving my music to a different 'shared documents' type folder did the trick.  So, now I'm going to be rearranging that hard drive in hopes that I'll be able to get to all of the stuff on it that I want to access.  

But, at least I have my music!  

Good luck to you, hope you get your issues solved soon.

---

### Post by quique1hn on 2008-05-15
I have the same problem, Ubuntu works fine but Kubunto don´t. any ideas:confused:

---

### Post by tazmannusa on 2008-05-15
> **arbulus said:**
> I'm running Kubuntu Hardy KDE 4 remix on an old Dell.  I also have another box that is running Ubuntu Gutsy as a file server serving up a few samba shares.

On the Kubuntu box, when I open up the file manager and click on "Network" and then click the icon to view Samba shares, it tells me:
```

Could not connect to host for smb://smb-network/
```

Now, on my laptop that runs Ubuntu Hardy with Gnome, I just open up Nautilus, and go to Network>Windows Network>Workgroup Name>Machine>Share and I'm there.  Does this work differently in KDE 4?  What do I have to do to get Kubuntu to browse the samba shares?

 Are you running a firewall on Gutsy?  Im running Firestarter firewall and had to allow smb shares from the ip of the pc that kubuntu was in then it worked 
Tom

---

### Post by arbulus on 2008-05-15
> **tazmannusa said:**
> Are you running a firewall on Gutsy?  Im running Firestarter firewall and had to allow smb shares from the ip of the pc that kubuntu was in then it worked 
Tom

Nope, no firewall.

---

### Post by Jamikest on 2008-05-17
Just upgraded to 8.04 and lost samba access.  Found that opening a window to browse in Dolphin as ROOT, I could then access my windows network.  Still cant get into it using my normal dolphin.

Any suggestions?

---

### Post by doniking on 2008-05-23
no solutions at all?

---

### Post by bittersweetryan on 2008-05-29
Having a similar problem and it has something to do with the domain.  I can browse the windows network, however I cannot open a computer with samba.   When I try to ping the machine (ping xxx) it will not resolve the IP, however, when I add the domain (ping xxx.xxx.com) it resolves to the correct IP.  In order to connect to the same machine in samba I'm needing to type in smb://ipaddress instead of smb://xxx.   I'm pretty sure this started when I switched from ubuntu to kubuntu both the current releases at this time.

---

