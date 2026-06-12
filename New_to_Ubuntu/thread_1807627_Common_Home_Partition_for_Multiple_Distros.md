---
title: "Common Home Partition for Multiple Distros"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-07-19
I have not found a straight forward answer to the following questions after searching.



Can I copy or move my home directories of each Distro I have installed to a single partition and assigning each their own home subdirectory.

Like /PuppyHome, /UbuntuHome, /ZorinHome etc..

or 

does it have to be simply /home and subdirectories associated with the particular username ie.. /JasonPuppy, /JasonZorin, /JasonUbuntu, etc..

If this is possible do they have to be mounted on boot in in /etc/fstab and /etc/mtab or does they copy or move take care of this upfront?

Does the /usr subdirectory also have to be transfered?



Things have been running pretty smooth I have upgraded grub and the linux kernel in a couple of distros, that is where I have been devoting most of my time with learning (kernel upgrades) currently trying out Puppy woof. I am enjoying things a little bit more now.:)

Thanks everyone,

---

### Post by Terl on 2011-07-20
You can do it but there will be other issues, like security.  You would need to insure you had different user numbers in each distro.

With desktops becoming more complex it could get tricky keeping all the configs lined out and user id's.  

It is discussed here as well: [http://fsymbols.com/keyboard/linux/choosers/]("http://fsymbols.com/keyboard/linux/choosers/")

Google "share /home across multiple distros" and you will find many links.

---

