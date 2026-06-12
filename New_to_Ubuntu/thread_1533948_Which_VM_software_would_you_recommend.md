---
title: "Which VM software would you recommend?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by new__buntu on 2010-07-18
My machine currently runs ubuntu, but in order to expand my access to programs I was thinking of installing a VM on my computer. I've done a little bit of searching and found a couple of alternatives, but I really don't know which one is going to give me the best performance. Can anybody here give me some advice on which one to use?(BTW, my processor supports virtualization)

---

### Post by MattBD on 2010-07-18
Virtualbox is the simplest and easiest way to get started with virtualisation, and in general is a lot less grief than virtually every other virtualisation solution I've ever tried. It's not perfect, but it performs reasonably well as long as your hardware is up to scratch, it's simple enough to grasp quite quickly and it's free. But if you're running it on Ubuntu I'd grab the version from the Virtualbox website which isn't entirely free software, but is free for personal use.

---

### Post by mbsullivan on 2010-07-18
I agree with MattBD. Virtualbox is much less work to set up and less grief to run than KVM or VMWare (or definitely Xen, though I assume you want to run Windows). 

Traditionally, I think that VMWare was the product to beat performance-wise. However, in my experience, the performance of all three VMs is now comparable. All three are quite variable in their performance (and functional) quirks, but the performance gap has all but disappeared in my opinion. It's all noise now.

Mike

---

### Post by QIII on 2010-07-18
If you use VirtualBox, be sure to use the PEUL version.  You can use the PEUL version so long as it is for personal use.

The PEUL version has support for USB devices.  The OSE version, which is available in the Ubuntu repositories, does not provide USB support.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I would suggest reading down through the page.  If you add the repository to your sources list, you will get updated with the latest version.  Just be aware that when the version is updated, the Guest Additions will also be available and should be re-installed on all of your guests.

---

### Post by noidian on 2010-07-18
Don't forget to install guest additions through "devices"..I remember having a tough time figuring out that for sharing stuff.

---

