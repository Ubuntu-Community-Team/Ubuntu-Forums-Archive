---
title: "using UBUNTU installed on old hard drive in new computer"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Aus1950 on 2009-03-26
i'm just wondering that if i install an old hard drive thats has UBUNTU 8.10 installed on it into a brand new system will it run ok or will i have to reinstall ubuntu 8.10

---

### Post by Tony Flury on 2009-03-26
Based on my experience on monday - moving my HD from an Old (dead) laptop to a new shiny laptop. You can just move the HD, and Ubuntu will boot.

I would recommend that you do the following though : 

1) when you first boot on the new machine - go to the Recovery mode and choose the Fix X server option - this allows the OS to detect the new graphics set up of the new machine, and reset the X Windows config so it is appropriate to the new platform.

2) If you want to use wireless, make sure you have a cabled connection (don't rely on wireless) on the first boot up - you might need to do some digging if the wireless cards between the PCs are different.

---

### Post by Aus1950 on 2009-03-26
thanks   i will try that when i get the new system up and running :)

---

### Post by Tony Flury on 2009-03-26
I meant to mention - does your current Ubuntu only have 8.10 - or do you have 8.04 waiting in the wings just in case.

In my case i have had to revert to 8.04 to get my wired connection working because 8.10 has a bug impacting wired connections on the Atheros card which the work around (for me) did not resolve.

---

