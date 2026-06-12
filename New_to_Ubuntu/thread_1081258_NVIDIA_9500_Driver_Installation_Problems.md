---
title: "NVIDIA 9500 Driver Installation Problems"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by Patt on 2009-02-26
I have been trying since Sunday to install the drivers for my GeForce 9500 Video Cards and have had limited success. The default driver on Ubuntu 6.10 64 bit will run my video after OS installation, but I can't install the drivers for the cards. I've been trying to install the 180.23 drivers for linux 64 bit, after reading good reviews, from the NVIDIA web site but after the install my OS get stuck on install. Something about not being able to find the boot image. So far every driver I have tried has had similar results. I really need step-by-step instructions with feedback, because I haven't been able to get it to work using the steps on other posts/threads/tutorial/etc.
Here is my current build...
- 2x EVGA 01G-P3-N959-TR GeForce 9500 GT 1GB 128-bit GDDR2 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card 

- AMD Athlon 64 X2 5600 Brisbane 2.9GHz Socket AM2 65W Dual-Core Processor Model ADO5600DOBOX

- ASRock K10N750SLI-110dB AM2+/AM2 NVIDIA nForce 750a SLI ATX AMD Motherboard

- 2X (8 GB total) OCZ Platinum 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual

- Ubuntu 8.10 64bit (Whichever is the default on download currently)

- Mythbuntu

---

### Post by stim on 2009-02-26
Try this: 
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I've used it since the day I got my system for my 8800gtx. Automatically downloads the latest, installs and configures the drivers for you.

Let me know if this helps.

---

### Post by Patt on 2009-02-26
I'll try it as soon as I get home, thanks for the quick reply.
Do yall know if there is a way to revert back to the generic drivers after a failed driver install? So far in my Linux nubeness I've had to revert to reinstalling the OS to get back to a working desktop. Any help in this regard would be very appreciated as well. For example after the ,last failed attempt(1130pm last nigt), the desktop startup got stuck due to inability to find boot image. Would simply uninstalling everything NVIDIA give me a fresh start or do I need to reinstall OS? I'm not intimidated by the terminal interface, but it has tendency to smack me around a bit before allowing any success.

---

### Post by overdrank on 2009-02-26
> **Patt said:**
> I'll try it as soon as I get home, thanks for the quick reply.
Do yall know if there is a way to revert back to the generic drivers after a failed driver install? So far in my Linux nubeness I've had to revert to reinstalling the OS to get back to a working desktop. Any help in this regard would be very appreciated as well. For example after the ,last failed attempt(1130pm last nigt), the desktop startup got stuck due to inability to find boot image. Would simply uninstalling everything NVIDIA give me a fresh start or do I need to reinstall OS? I'm not intimidated by the terminal interface, but it has tendency to smack me around a bit before allowing any success.

Hi and I do not know if Envy supports the new 9500 but you can try. As for if your graphics drivers fail after install then you can boot into recovery mode and use the xfix option to hopefully correct this so you should not have to reinstall the os.
Recovery mode is usually the second choice from grub while booting. Then you should be given 4 choice and choose xfix. After the completion of xfix you should be given the 4 choices again and choose boot normally. 
I am sure that is a typo " Ubuntu 6.10 64" and you meant 8.10. :)

---

### Post by Patt on 2009-02-26
Do I need to use the boot disk to get this option, or is it a function key menu? From what I can tell it doesn't get to the point where I can choose how I want to boot. I really appreciate this input guys.

---

### Post by overdrank on 2009-02-26
> **Patt said:**
> Do I need to use the boot disk to get this option, or is it a function key menu? From what I can tell it doesn't get to the point where I can choose how I want to boot. I really appreciate this input guys.

If Ubuntu is the only Operating system then you can just press the esp key when you see the grub loading.

---

### Post by Patt on 2009-02-26
I really appreciate the help, I'll post with my results when I get home tonight.

---

### Post by notexactly on 2009-02-27
> **overdrank said:**
> As for if your graphics drivers fail after install then you can boot into recovery mode and use the xfix option to hopefully correct this so you should not have to reinstall the os.
Recovery mode is usually the second choice from grub while booting. Then you should be given 4 choice and choose xfix. After the completion of xfix you should be given the 4 choices again and choose boot normally.

Thank you so much! I was having exactly the same problem, and this fixed it. :) I had tried the dpkg option before, expecting it to fix the driver package, but I didn't know about xfix.

---

