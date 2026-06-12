---
title: "Sharing internet connection"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by residentevil on 2008-01-01
I know there is a hundreds of post for internet connection sharing, but i try some of them and it is not working ! i want a full explain for idiot !
I want when reboot, everything to be fine and not to do the same things again.
pls it is important to me :) i'm using ubunti 7.10 :)

---

### Post by gpredrag on 2008-01-01
I don't know what you have been reading, but have you tried firestarter. It is  in the repository, but you might like to check [http://www.fs-security.com/](http://www.fs-security.com/) for manual and screenshots before you install it. It can work with DHCP server installed or not.
One way to use it to set internal network manually (private IP addresses on internal network interface of the computer that will be sharing connection, manually setting DNS server of your provider on internal computers, that way you don't have to install DHCP)
After that, install firestarter, tell him what's inside and what's outside network and enable connection sharing. I've got it working in minutes (although, i'm using shorewall now for other reasons)

---

### Post by residentevil on 2008-01-02
firestarter..... i tryed it ! 
it is really easy to use, but again it wasnt help me !
i dont know i am the problem or something else .......

---

