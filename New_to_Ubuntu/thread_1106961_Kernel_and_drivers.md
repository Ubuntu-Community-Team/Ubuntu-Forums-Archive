---
title: "Kernel and drivers"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by blau2009 on 2009-03-26
Just a few questions, excuse my ignorance :) Any useful links would be great.

1. The linux kernel contains the drivers for hardware?

2. So at best this is reactive - ie drivers can only be written after the hardware is out?

3. What will happen if linux becomes more popular? Will it be a situation like Windows, where there are drivers for every piece of hardware, that have to be downloaded or installed from a CD?

---

### Post by Kevbert on 2009-03-26
The linux kernels only include basic drivers for things such as display cards, printers, etc.  As linux is open source (that is all code is available for free modification, copying) drivers are expected to be open source. Some companies such as Nvidia, ATI and Intel provide open source drivers, but others do not.  An example of this is wifi drivers where some adapters have open source drivers, while others will only work with (Windows) proprietary drivers and so have to use additional programs such as ndiswrapper to make them work.
Linux is an evolving platform which is reactive to new hardware. This is similar to Microsoft in the way that they produce security updates after a security breach has been exposed in the outside world.
To sum up, if you buy very new hardware it's possible that there may not be linux (or Windows, for that matter) released drivers fully available.
What drivers are you after ?

---

### Post by billgoldberg on 2009-03-26
> **blau2009 said:**
> Just a few questions, excuse my ignorance :) Any useful links would be great.

1. The linux kernel contains the drivers for hardware?

2. So at best this is reactive - ie drivers can only be written after the hardware is out?

3. What will happen if linux becomes more popular? Will it be a situation like Windows, where there are drivers for every piece of hardware, that have to be downloaded or installed from a CD?

A lot of hardware vendors create linux drives, as they do windows drivers.

If a vendor doesn't write linux drivers, the community tries to write them. If the community has to write them, it might take a while.

To anwser your third question, no. Sometimes you might need to download and install a driver, but most of the time the kernel will provide the drivers.

---

### Post by billgoldberg on 2009-03-26
> **Kevbert said:**
> The linux kernels only include basic drivers for things such as display cards, printers, etc.

I wouldn't call drivers for display cards as you call them, printers, wlan adapters, ...basic.

The Linux kernel has the best hardware support of any OS.

---

### Post by blau2009 on 2009-03-26
So how big will the kernel become if it needs to provide drivers for every piece of hardware that could reasonably be expected to be in systems?

Or is the idea that hardware manufacturers will build hardware towards a certain driver?

Even if manufacturers supplied open source linux drivers, how long until they are put into the kernel? This still seems reactive in that the drivers would have to be tested etc before they are put into the kernel.


Nothing wrong with the idea of being reactive; I see the benefit of the kernel providing drivers rather than having to install drivers for each piece of hardware on the system. Just seems like linux would constantly be playing catch up to new hardware :)

---

### Post by decoherence on 2009-03-26
> So how big will the kernel become if it needs to provide drivers for every piece of hardware that could reasonably be expected to be in systems?

The thing is, you might have a bunch of different kinds of widget made by different companies, but there are only a few different chipsets that go in to those widgets. For instance, linux may not care if your wireless adapter says D-Link or Linksys on it... if they're using the same chipset, they use the same driver. That's still a lot of drivers, but not as many as there might seem at first glance and most of the common ones are already in place.

Also remember that distributions can build the kernel with as much or as little built-in driver support as they like. If somebody wants to pull an Apple and target only a tiny subset of hardware, they can do that and reap the benefits of a slimmed down kernel (which aren't generally that big on a typical modern desktop system.) Additional hardware support can be provided after the fact using kernel modules.

So while Linus' kernel tree might get huge, there's nothing to say that the resulting kernel binaries have to be huge.
> 
Just seems like linux would constantly be playing catch up to new hardware

Yep. This will continue to be the case until the people manufacturing the hardware start writing drivers that can be included in a GPL'd product. In some cases that will never happen. 

The Hardware Drivers program (which is actually called 'jockey') lays the groundwork for addressing this problem... it just needs to be expanded greatly. I think this is really more of a co-ordination and logistical issue than a technical one.

---

### Post by Kevbert on 2009-03-26
> **billgoldberg said:**
> I wouldn't call drivers for display cards as you call them, printers, wlan adapters, ...basic.

The Linux kernel has the best hardware support of any OS.

Just to clarify what I meant. Drivers for Nvidia, for example, don't come on the installation disk, but have to be got from the repos, so that's why I suggested the drivers were basic. For most hardware there are drivers to get people going when they first install Ubuntu.:P

---

