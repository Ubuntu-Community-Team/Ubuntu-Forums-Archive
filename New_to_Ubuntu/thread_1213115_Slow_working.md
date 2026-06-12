---
title: "Slow working"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-14
Hi all,

           i ve installed ubuntu 8.04 which is slow to work
i don't know the reason 
        if i ve connectd with BSNL nic card means it is not possible to work like windows

           it makes some hassle

           i ve the configuration 1.25 GB RAM , MSI mother board,
AMD celeron processor, i ve good configuration except video driver

           i 'd like to ve good fast ubuntu system
   
           Please help
                         what i can do?

---

### Post by schwascore on 2009-07-20
We need a more detailed description.  What do you mean by slow?  Try to be specific.

I'm a little confused by your hardware because AMD does not make Celeron processors, is it an Intel processor?

---

### Post by decoherence on 2009-07-20
Hi there!

Could you please run the following command and paste the output here?
```

lshw -C video
```
This will tell us specifically what kind of video hardware you have, as this is the most likely cause of your slow performance.

To run a command, go to Applications -> Accessories -> Terminal

---

### Post by navaneethan on 2009-07-20
> **decoherence said:**
> Hi there!

Could you please run the following command and paste the output here?
```

lshw -C video
```
This will tell us specifically what kind of video hardware you have, as this is the most likely cause of your slow performance.

To run a command, go to Applications -> Accessories -> Terminal

> ubuntu@ubuntu-desktop:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: S3 Unichrome Pro VGA Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
ubuntu@ubuntu-desktop:~$ 



This is my output for the above command

---

