---
title: "Nvidia Ion drivers continually giving me issues"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by ready4thebreak on 2010-07-04
I've had an up and down situation ever since I built a system with the Nvidia Ion desktop chipset. I'm using a ZOTAC IONITX-G-E motherboard as an HTPC and I've had issues with the graphic drivers and sound through HDMI.

I've had the thing work PERFECTLY at times in the past and now its a complete headache to use. I'm not sure if it was a kernel update that did this or what but I really need some help getting this fixed.

I'm running 10.04 and every time I boot into the OS I get the a screen filled with random pixels, they flash a few times and then eventually it alerts me that I have to run Ubuntu in low graphics mode. I have tried the reconfigure action from that low-graphics dialog box, I've tried using backed-up configurations, nothing works. I try to adjust the Nvidia X Server Settings and I get the error message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file(run 'nvidia-xconfig' as root), and restart the X server." So when I attempt this and run a "gdm stop" or if I try to use any Terminal Display(Ctrl+Alt+Fx) I cannot see anything. Its just a bunch of scrambled blue pixels(this is also what I get for my boot and shutdown screens). 

I've been Google searching all over the place trying to get this issue corrected but my results haven't really fixed the problem. Can anyone assist me in getting this fixed?

---

### Post by J V on 2010-07-04
Did you install the driver? (Administration > hardware drivers)

---

### Post by ready4thebreak on 2010-07-04
> **J V said:**
> Did you install the driver? (Administration > hardware drivers)

I previously used the drivers from Nvidia's site since the drivers were more up-to-date. I switch to the Admin> Hardware Drivers to avoid any issues, but the issue is the same.

---

### Post by J V on 2010-07-04
Have you messed with the xorg.conf? Can you reset it and use the nvidia config tools? Bea in mind you will probably have to restart to see any effect...

---

### Post by ready4thebreak on 2010-07-04
> **J V said:**
> Have you messed with the xorg.conf? Can you reset it and use the nvidia config tools? Bea in mind you will probably have to restart to see any effect...

I haven't touched it, but can you help with resetting it with the nvidia config tools? I have very little clue how xorg.conf works, let alone adjusting it.

---

### Post by ready4thebreak on 2010-07-04
I guess no one can offer help? What I was considering doing was purging all of my Nvidia graphics packages and then re-installing and reconfiguring Xorg. Is there anyone who can help me?

---

### Post by Jose Catre-Vandis on 2010-07-04
If you have had a kernel update, it probably broke nvidia. I have had this problem with succesive kernel updates on 10.04 Xubuntu.

Go to hardware drivers, click on the remove button for the "current" nvidia drivers, let it finish, then click on activate. let that finish then reboot.

---

### Post by ready4thebreak on 2010-07-04
> **Jose Catre-Vandis said:**
> If you have had a kernel update, it probably broke nvidia. I have had this problem with succesive kernel updates on 10.04 Xubuntu.

Go to hardware drivers, click on the remove button for the "current" nvidia drivers, let it finish, then click on activate. let that finish then reboot.

Ok sounds good. Should I restart after removing the driver or should I just reactivate it right after removing it?

UPDATE: I did what you said, I still get the same results: Ubuntu is running in low graphics mode. When I removed the current driver and rebooted, I got the low graphics message, but the Error said "no devices found." Now that I have reinstalled the driver, the error says "Screen(s) found, but none have a usable configuration."

---

### Post by Jose Catre-Vandis on 2010-07-04
> **ready4thebreak said:**
> Ok sounds good. Should I restart after removing the driver or should I just reactivate it right after removing it?

Just activate again, no need to restart

---

### Post by ready4thebreak on 2010-07-04
> **Jose Catre-Vandis said:**
> Just activate again, no need to restart

I did what you said, I still get the same results: Ubuntu is running in low graphics mode. When I removed the current driver and rebooted, I got the low graphics message, but the Error said "no devices found." Now that I have reinstalled the driver, the error says "Screen(s) found, but none have a usable configuration."

Additional thoughts anyone?

---

### Post by ready4thebreak on 2010-07-05
I've also tried to reconfigure Xorg, but I'm getting the same results using:

> dpkg-reconfigure xserver-xorg

This [link]("http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/") says that I should get a prompt for questions, but I don't it just gives me a blinking cursor for about 10 seconds and then I'm able to enter commands again. I truly don't want to reinstall Ubuntu just to fix this issue, I had a hard enough time getting my Logitech MediaBoard Pro and HDMI audio working, I really don't feel like having to redo all these over again if someone could just help me. I know that Nvidia is pretty supportive of Linux stuff, I know the ION isn't that uncommon, and I know that Linux is the ideal OS for this hardware considering its lighter processor and power consumption but it still pumps out high quality graphics. Am I the only ION/Ubuntu user with this issue?

---

### Post by Jose Catre-Vandis on 2010-07-05
Have a look at your xorg logs, see what is causing the problem.

I have ION graphics too, but apart from the kernel update fix have not really had any other problems

---

