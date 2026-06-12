---
title: "Can't shutdown desktop PC with Intel DH61BEB3 motherboard"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by glennbookhout on 2011-09-06
I bought a desktop PC with an Intel DH61BEB3 motherboard in July, 2011.  For each component (hard drive, processor, etc) I chose from a dealer-supplied list and the dealer built a custom-designed desktop PC for me.  I installed 64-bit Ubuntu 11.04 on it.  It boots and runs OK, but when I shutdown from a GUI or terminal command line, the PC reboots rather than shutting down.  Neither 'shutdown -h now'  nor 'shutdown -P now' works.

The dealer said that if power management were disabled, then shutdown would work OK.  But he said that less energy would be used keeping power management enabled and relying on hibernate mode to save energy when I am not at the PC.  So I chose the dealer recommended approach.  I select hibernate mode when I take a break from computing.  

I tried editing the /etc/default/grub file to add the acpi=off option in the GRUB_CMDLINE_LINUX_DEFAULT line and running sudo update-grub.  That just resulted in shutdown hanging rather than rebooting.  So I went back to the original /etc/default/grub.

I noticed in the Intel Desktop Board DH61BE Product Guide that no Linux OS's are listed as being supported, only various Windows OS's.  I of course did not know this when I bought the computer.

---

### Post by Beacon11 on 2011-09-07
I don't really see a question in there, did you have one? I will say that you probably will never see a motherboard manufacturer state that it supports Linux-- it certainly doesn't mean that Linux won't work. Have you ever downloaded a PDF from a website that states you need Adobe Reader to read the PDF? Same thing.

---

### Post by glennbookhout on 2011-09-07
Thanks for your response.  My question is how can I fix the problem of not being able to shutdown my system (other than pressing the power button).

---

