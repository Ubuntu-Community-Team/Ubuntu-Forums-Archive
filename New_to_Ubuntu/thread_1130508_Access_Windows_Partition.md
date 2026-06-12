---
title: "Access Windows Partition"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Simran on 2009-04-19
Hey,

i just downloaded 8.10 and installed it from vista. now its installed and working im wondering if its possible for me to access my windows partition from ubuntu and if so how.

thx 

simran

---

### Post by laloruelas on 2009-04-19
Did you delete the vista partition? if not it should be easy to access it, have you checked the places menu?

---

### Post by Simran on 2009-04-19
i have not deleted the partition, i installed inside the windows partition using the .exe on the cd. i still get the boot option of vista but because i installed ubuntu inside my vista partition i dont know how to access the files i used in windows from ubuntu.

---

### Post by theozzlives on 2009-04-19
> **Simran said:**
> Hey,

i just downloaded 8.10 and installed it from vista. now its installed and working im wondering if its possible for me to access my windows partition from ubuntu and if so how.

thx 

simran

Should be in Places.

---

### Post by Simran on 2009-04-19
> **theozzlives said:**
> Should be in Places.

Its not there, i have - Computer

                      - CD DVD Creator

                      - Recovery (recovery partition that came with the laptop when i bought it with vista on)

                      - CD drive.

my vista partition isn't appearing there.

---

### Post by -kg- on 2009-04-19
Under Places click on Computer.  You should have access to your files from there.

Since you installed Ubuntu using Wubi, your installation is on the same partition as Windows; it's just using the Windows partition as it's virtual root partition.  All your Windows files should be there and available under Places/Computer, as well as any other drive you have connected, whether CD Burner (as long as there's a disk in it), external hard drive, usb memory stick, or whatever.

I am assuming this, since I've never installed using Wubi, VirtualBox, or any other method rather than full, dual-boot installation.  I think it's a reasonable assumption, though.

---

### Post by steve101101 on 2009-04-19
you can access it in a folder called host.

---

### Post by steve101101 on 2009-04-19
i have used wubi alot and it is quite nice and easy.

---

### Post by Simran on 2009-04-19
> **steve101101 said:**
> you can access it in a folder called host.

thanks so much, thats just what i was looking for. i've never used wubi before so it confused me with where to look.

cheers . Simran
 :)

---

### Post by steve101101 on 2009-04-19
your welcome. glad I could help out.

---

