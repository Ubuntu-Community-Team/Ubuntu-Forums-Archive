---
title: "Virtual Machine"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by to25 on 2009-09-24
I am having trouble installing a virtual machine. I tried Virtualbox but it did not work. For some reason my laptop is not compatible with it or something like that. I need a virtual machine for school. I currently am running only ubuntu. I have a Gateway gx 7405 laptop.

---

### Post by styxcoverbnd on 2009-09-24
when you say virtualbox 'doesn't work' what do you mean? Are you getting any error messages during installation or when you try to launch it? Are you installing from the repos?

---

### Post by callumacrae on 2009-09-24
I had that problem, just uninstall, download a new package, and install.

Good luck,
~Callum

---

### Post by callumacrae on 2009-09-24
> **styxcoverbnd said:**
> when you say virtualbox 'doesn't work' what do you mean? Are you getting any error messages during installation or when you try to launch it? Are you installing from the repos?

It wasn't in the repos when I looked.

~Callum

---

### Post by styxcoverbnd on 2009-09-24
> **callumacrae said:**
> It wasn't in the repos when I looked.

~Callum

Gotcha, couldn't remember if it was or not (should checked first sorry)

---

### Post by bigboy_pdb on 2009-09-24
There's a couple of virtual machines that you might want to look into. They are [VMware]("https://help.ubuntu.com/community/VMware/Server") and [VirtualBox]("https://help.ubuntu.com/community/VirtualBox").

Personally, I prefer VirtualBox OSE (Open Source Edition). That's probably the one that you installed from the repositories.

What was the problem that you encountered with VirtualBox? In order for us to help you, you need to give more information. Running the program from the command line gives more information as well.

Also, you need to be a part of the vboxusers group for VirtualBox to work. To do this select System -> Administration -> Users and Groups. Click the "Unlock" button so you can make changes. Then select "Manage Groups" and select the "vboxusers" group and click the "Properties" button. Following that just check off your user name.

Furthermore, you need to install the OS (if you haven't done that). For example, if you want to run Windows, you need to set up a Windows virtual machine and then install the OS (from the CD or an ISO image).

---

### Post by hashimoto on 2009-09-24
Downloads here, with instructions on how to add the repo.
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

BR
Hashimoto

---

### Post by callumacrae on 2009-09-24
VMware costs though.

Just reinstall, I think you're having exactly the same problem I had. If that doesn't work, then post the error message here.

~Callum

---

### Post by konqueror7 on 2009-09-24
did a search on your system, it might be an architecture issue. what did you install, the i386 or the amd64? the latter should be the one you must install.

---

### Post by bigboy_pdb on 2009-09-24
> **callumacrae said:**
> VMware costs though.

I was able to download at least one VMWare product for free (in the past).

According to VMWare [VMWare Server]("http://www.vmware.com/products/server/") and [VMWare Player]("http://www.vmware.com/products/player/") can be downloaded for free, however, if I remember correctly, you need to register.

---

### Post by to25 on 2009-09-24
I receive the

Error: Wrong architecture 'amd64'

On the site it says to setup a 64-bit chroot environment. I don't know if my laptop can support a 64-bit chroot and i don't know how to tell (newbie). Just wanted to see if their are easier alternatives. If not I must try and find a way for a virual machine to work on my laptop.

---

### Post by bigboy_pdb on 2009-09-24
What processor do you have? (you can use the command 'lshw -C cpu' to find out)

The VirtualBox OSE that is in the repositories (for Intrepid) is built for 32bit architectures. If you have a 64bit CPU, it should still be able to run it.

It sounds like you might be trying to install an OS that was compiled for 64bit architecture on a VirtualBox setup which has a 32bit CPU. When I looked in the configuration options for VirtualBox OSE, I didn't notice any way to change the type of CPU in the open source edition.

---

### Post by blur xc on 2009-09-24
Seems like there's still a lot of missing information.

Are you having trouble installing VBox on your computer, or a virtual machine inside of VBox?

On another note- what do you intend to do in VBox?  I checked your computer specs on this page - [http://support.gateway.com/s/Mobile/Gateway/7305GZ/4093sp3.shtml](http://support.gateway.com/s/Mobile/Gateway/7305GZ/4093sp3.shtml) and it seems to be a bit on the anemic side to run both Ubuntu and a VM inside of it.  In my experience, VBox sucks up a lot of ram and video performance. On my ubuntu machine, I have 3.2gigs of usable ram, and just running ubuntu w/ one user logged in can sucks up 300mb, and once vbox is running w/ Vista inside of it, I'm using well over 2 gigs...

BM

---

### Post by to25 on 2009-09-24
here is the result.
  product: Mobile AMD Athlon(tm) 64 Processor 3200+
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: cpu@0
       version: 15.4.10
       size: 2GHz
       capacity: 2GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up cpufreq

i try to install vbox but then i get th error message that i posted above that is as far as i get with vbox

---

### Post by scorp123 on 2009-09-24
> **to25 said:**
> here is the result.
  product: Mobile AMD Athlon(tm) 64 Processor 3200+
       vendor: Advanced Micro Devices [AMD]
       physical id: 1
       bus info: cpu@0
       version: 15.4.10
       size: 2GHz
       capacity: 2GHz
       width: 64 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext x86-64 3dnowext 3dnow up cpufreq  64-bit but no "lm" bit? That's bizarre. "lm" = Long Mode = 64-bit. Every 64-bit AMD or Intel CPU should have that flag.

---

### Post by to25 on 2009-09-24
so what should i do?

---

### Post by blur xc on 2009-09-24
> **to25 said:**
> so what should i do?

I have had some success using the Virtualbox forums.  There area few there  that are pretty helpful, but there are a few RTFM types...

BM

---

### Post by to25 on 2009-09-26
I decided to just reinstall windows and duel boot ubuntu. It just seems easier that way. sigh... back to Windows.

---

