---
title: "[SOLVED] Having Trouble with Partitioning for Install"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by bsol on 2008-12-20
Hey all,

I'm trying to instal a dual-boot Vista/Ubuntu with Vista installed first. Originally I booted the LiveCD install disc with the following partitions:

C: 128 gigs (vista)
D: 8 gigs (hp recovery)
Free Space: 13 gigs (to install ubuntu on)

At install I choose "Guided - use the largest continuous free space." I can see the three partitions as above as "Before" but "After" it shows that my entire disk will be replaced with Ubuntu.

I also tried to format the free space as Fat32 and that just took away the "Guided -...free space" option. What can I do to get this to work?

---

### Post by beno1990 on 2008-12-20
Assuming the 13 GB free space you've given, go to the manual option. Use the free space to make a 1GB swap partition (doesn't need a mount point) and use the remaining 12 GB for an ext3 filesystem at / (root) mountpoint.

---

### Post by mapes12 on 2008-12-20
> **bsol said:**
> Hey all,

I'm trying to instal a dual-boot Vista/Ubuntu with Vista installed first. Originally I booted the LiveCD install disc with the following partitions:

C: 128 gigs (vista)
D: 8 gigs (hp recovery)
Free Space: 13 gigs (to install ubuntu on)

At install I choose "Guided - use the largest continuous free space." I can see the three partitions as above as "Before" but "After" it shows that my entire disk will be replaced with Ubuntu.

I also tried to format the free space as Fat32 and that just took away the "Guided -...free space" option. What can I do to get this to work?

> I also tried to format the free space as Fat32 and that just took away the "Guided -...free space" option. What can I do to get this to work?Of course it will because Ubu thinks you're using it as a MS partition. Re create the free space and also have another look at C: for any unused space you can free up there. 13 GB's is not giving Ubu much freedom.

EDIT - Others may shoot me down for this comment _**but**_ if you have ANYTHING critical on your windoze partition(s) and if you are new to Linux then I would strongly recommend not installing a dual boot system. If you are looking at trying out Linux/Ubuntu get yourself a cheap base unit while you get used to the power of Linux and what it can do to windoze (like destroy it) if you don't know what you're doing.

---

### Post by bsol on 2008-12-20
How much space would you recommend to use? Thanks for the helpful replies!

Edit: And also how big should I make the swap?

---

### Post by mapes12 on 2008-12-20
> How much space would you recommend to use? As much as you can give it. I still stand by my last EDIT.

SWAP - 2x RAM

---

### Post by nhasian on 2008-12-20
12 gigs is not a lot but it is enough to get started.  i think i started with 15.  then after i got comfortable i resized my partitions again and gave ubuntu almost all of it with windows having only 30 gigs left hehe.  

also if you just want to try ubuntu out, you can do so without even messing around with partitions with wubi:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

it will install ubuntu as a file within windows so you can use the add/remove programs to delete it later.  OR if you decide you like it you can move it to its own parition at a later time.

---

### Post by bsol on 2008-12-20
Ok thanks guys. I have one last question. I got the partitions to work, but on the "ready to install" screen right before installing there is nothing listed under "Migration Assistant." I was told the vista/longhorn loader should be listed here. I'm afraid to continue in case I won't be able to boot to vista. Thanks again!

---

### Post by kansasnoob on 2008-12-20
Well, I see you're past this point but Vista OS partitions should always be resized by Vista's own tools:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

More here:

[http://www.bleepingcomputer.com/tutorials/tutorial133.html](http://www.bleepingcomputer.com/tutorials/tutorial133.html)

---

