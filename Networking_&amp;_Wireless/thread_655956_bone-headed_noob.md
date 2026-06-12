---
title: "bone-headed noob"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by md11driver on 2008-01-02
ubuntu gutsy gibbon 7.10

i was having side issues with my d-link 1330 wireless pc card.  i had good conectivity with the ath_pci driver that (i believe) is a part of ubuntu restricted extras.  i removed the restricted extra package in order to remove the ath_pci driver so i could install ndiswrapper and the appropriate windows driver to troubleshoot my side issues.  the ndiswrapper installation didn't work and now i need to get the restricted extra package (especially the ath_pci driver) back on my laptop.  i have access to another internet-capable machine and flash drives for transfer and installation back to my laptop but don't know how to proceed.  as i recall, there was about 42 mgb of data that i uninstalled.

can anyone help please?

---

### Post by erfahren on 2008-01-02
when you install packages through Synaptic or apt they are cached in /var/cache/apt/archives

I'd first try reinstalling them without the internet connection. Maybe you'd need to disable the Software Sources so it doesn't check for updated versions first, I don't know.

but anyway, as long as you haven't cleared that cache they would still be there.

otherwise you can get them through here: [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

you can Google search the site with like:
*name-of-package* site:[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

---

### Post by md11driver on 2008-01-02
wonderful and helpful reply.  i was able to reinstall from the cache and got my internet back.

i learned at least one thing today.

thank you tons for the good steer in the right direction.

---

