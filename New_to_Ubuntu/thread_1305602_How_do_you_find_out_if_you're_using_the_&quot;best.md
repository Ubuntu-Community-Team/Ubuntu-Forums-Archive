---
title: "How do you find out if you're using the &quot;best&quot; driver"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by josephpford on 2009-10-30
I would like to ensure that I am using the best driver for my graphics card.  Back when I first installed Ubuntu (2006), I had to tell the system to use Restricted Drivers so that my ATI MOBILITY FireGL T2 graphics card was fully utilized.  Now when I installed Karmic, (I haven't used Linux in a while) I noticed it is NOT using a restricted driver.

Question: How do I find out what driver I am using?  And how do I know this is the "best" driver to use?

---

### Post by mhh91 on 2009-10-30
From the "System" menu,choose "Administration" then "Hardware Drivers"

This will show if you have any restricted drivers in use on the system :)

---

### Post by josephpford on 2009-10-30
> **mhh91 said:**
> From the "System" menu,choose "Administration" then "Hardware Drivers"

This will show if you have any restricted drivers in use on the system :)

Thanks for the suggestion.  Ubuntu tells me NO restricted drivers are in use.  I then went to Synaptic and ensured that the Restricted drivers repository is enabled (and it was). 

Any other suggestions?

---

### Post by josephpford on 2009-10-31
> **josephpford said:**
> I would like to ensure that I am using the best driver for my graphics card.  Back when I first installed Ubuntu (2006), I had to tell the system to use Restricted Drivers so that my ATI MOBILITY FireGL T2 graphics card was fully utilized.  Now when I installed Karmic, (I haven't used Linux in a while) I noticed it is NOT using a restricted driver.

Question: How do I find out what driver I am using?  And how do I know this is the "best" driver to use?

Hello all - I wanted to let others know that I found a solution to my problem on my own.  I installed Hardinfo from the repositories, and executed all tests.  In the test results you can see what PCI Devices are being used and I found this entry:

VGA compatible controller	ATI Technologies Inc M10 NT [FireGL Mobility T2] 

This leads me to believe that the system is using a driver that is compatible for my graphics card and is utilizing the most capabilities it can (in other words, it's not using some generic driver that doesn't use everything available, it might not be as good as the official driver for "windows" but at least it knows the card type and is using a driver from ATI).

---

### Post by anewguy on 2009-10-31
My question would be this - is hardinfo just reporting what the device says it is, just like lspci would?  If so, that actually has nothing to do with a driver.  Ubuntu can know about hardware, what type, the manufacturer, etc., by reading this information from the device.  As an example, you can have a wireless adapter known to the system but no driver installed; you can have (or maybe with the changes in xorg one should say "could have had") a video adapter show up in the hardware list as brand "x" model "y", but in truth it was using the vesa driver.

Why do I mention this?  Because I don't think you've learned yet what driver is being used.  Assuming this is a pci device, do the following:

lspci -v

then look for your VGA device (I'd have you just run the lspci through grep to isolate it, but when I tried it I only get the VGA line since it's the only line that matched).  Within the information for that device you will see "kernel modules" - what follows that should be the actual driver being used.

Dave :)

---

