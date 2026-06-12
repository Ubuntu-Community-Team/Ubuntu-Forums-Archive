---
title: "ati card + external monitor drivers?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by sprocket10 on 2010-08-04
I have a series of questions. First the background info:

I'm dual booting Windows 7 and Lucid Lynx 10.04 on my Dell E1505 laptop with an ATI Mobility Radeon X1300, which I use for college. I also use an Acer P191W external monitor for writing reports and such. However, I've been unable to get the external monitor to work with ubuntu. I go to System -> Preferences -> Monitors. Ubuntu recognizes the monitor, but the monitor will not display anything. While trying to figure out the situation, I realized I don't recall ever activating a driver for my graphics card. I thought maybe this would be the problem.

So, I searched for the ATI drivers. This driver ([http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx)) looks promising, but I'm not sure it applies to the "Mobility" cards. When I go here: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) I am unable to find any drivers for my card. I'm not opposed to activating proprietary drivers, but I can't find any.

I checked Acer's website for the monitor driver, but it only has a Vista version. Am I out of luck?

Also, what tool would I use to see if Lucid recognizes my graphics card? As in: when I go to Administration -> System Monitor and click the "System" tab, would I see "ATI Mobility Radeon X1300" listed under the hardware or some other location?

---

### Post by Mark Phelps on 2010-08-05
> **sprocket10 said:**
>  ... I am unable to find any drivers for my card. I'm not opposed to activating proprietary drivers, but I can't find any...

That's because there aren't any ... that will work with your card and current versions of Ubuntu.

IF you DO download any ATI proprietry divers and force their installation, you will only trash your display and have to end up booting into a console to remove them.

The only drivers that will work with your card and current Ubuntu versions are the open-source drivers -- and they are already installed.

---

### Post by sprocket10 on 2010-08-05
Ok, I'll keep that in mind. I'll just make sure I get an nVidia card in my next machine!

---

