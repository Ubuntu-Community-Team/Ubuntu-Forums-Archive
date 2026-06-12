---
title: "Is there a partition bug in live CD 8.04?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by garyed on 2009-04-19
It I 've been trying to install Xubuntu on two of my machines & can not get the partitioner to work. The live CD works fine & it passes the integrity check also. I currently dual boot with xp & Feisty on both machines. When I boot the live CD & get to the partitioner it says that its "too small" to go forward. One shows 10 gig available & the other shows 16 gig.It shows the Xubuntu install in those partitions & it asks me if I want to go forward.
When I say yes it hits me with "too small" error & stops.  
One of the machines I tried to resize my partition with first & got an error
that it couldn't go forward so I tried again with my 8.04 Ubuntu live CD that
I used for a successful install on another machine & got the same error. I
noticed that they both had the same version of Gparted. I downloaded a newer version of Gparted live & it worked fine. Any ideas how to proceed?

---

### Post by mikewhatever on 2009-04-19
Which of the partitioning options are you using, manual or guided? It looks like you are trying to install to the available free space, which is too small.

---

### Post by garyed on 2009-04-19
I'm using guided & it shows Xubuntu 8.04 in a 10 gig partition on my last install. That's what doesn't make sense. I shows my old ubuntu install on
about a 5 gig partition & that's working fine.

---

### Post by mikewhatever on 2009-04-19
Do you realize you'd have to delete or resize one of the existing partitions to install a new OS? If that is done, you have to go with the manual option and explicitly point the installer to the new root partition. The fact that other Linux partitions are shown in Gparted is a normal thing, not quite sure why they shouldn't.

---

### Post by garyed on 2009-04-19
> **mikewhatever said:**
> Do you realize you'd have to delete or resize one of the existing partitions to install a new OS? If that is done, you have to go with the manual option and explicitly point the installer to the new root partition. The fact that other Linux partitions are shown in Gparted is a normal thing, not quite sure why they shouldn't.

I think that's where the problem is. The guided shows the recommended partition resizing, old ubuntu 5gig & new Xubuntu 10 gig & when I go forward
& accept it thats when I get the "too small" error.
I think there's a problem with the version of gparted on the live CD & my computers.

---

### Post by mikewhatever on 2009-04-19
What can I say, use a different version of Gparted from the live cd.

---

