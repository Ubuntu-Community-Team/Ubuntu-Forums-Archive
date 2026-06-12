---
title: "Motherboard/GPU/Kernel Mismatch Breaks WiFi."
date: 2019-12-20
forum: Networking &amp; Wireless
---

### Post by adrian-doyle on 2019-12-20
Hi all,

I'm relatively new to Ubuntu, though, I've used Linux Mint in the past. I recently decided to install Ubuntu 18.04.3 on a computer I built instead of Mint or Windows, but I've been having problems getting the software to work with the hardware.

The motherboard is an x570 Aorus Xtreme, and initially I was having trouble with my WiFi. Ubuntu didn't recognise any wireless hardware connected to it. I realised that the problem was to do with the Kernel I was running, 5.0.0 I think it was. So, I upgraded to 5.4.5, the latest stable release. This solved the issue and I can now connect to WiFi, however it created another problem.

I now can't change my screen resolution. There is only one option in settings and it is too low, so everything looks odd. I don't know if it's to do with my GPU, but in case it's relevant, I'm using an Nvidia GTX 1050TI with an open source driver.

Is it possible to roll back to an older kernel that will still support the WiFi hardware? I also have 5.3.18 installed, and I'd like to do that, but I can't find a way to roll back using ukuu.

Alternatively, I'd like to find a way to fix my screen resolution without rolling back. Is that possible? I really don't want to have to reinstall Ubuntu and set up my work-space all over again, so I'd really appreciate any help anyone could offer.

Thanks in advance.
Adrian.

---

### Post by praseodym on 2019-12-20
Please run the wireless script from the sticky thread and show the outputs.

Newer kernels may not work with the proprietary NVIDIA drivers from your installation. We may find a solution for both issues.

---

### Post by adrian-doyle on 2019-12-20
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs.

Newer kernels may not work with the proprietary NVIDIA drivers from your installation. We may find a solution for both issues.

I've run the wireless script. The .txt file is huge though, not sure how to share it. I thought it would automatically be uploaded to pastebin using pastebinit?

Since my last message I've rolled back to 5.3.18 in the GRUB menu, and still can't fix resolution. I then rolled back to my original kernel and there, again, I'm still unable to set the resolution. I used have no problem with the resolution in my original kernel, so I'm very confused by this. I'm currently back to running 5.3.18.

---

### Post by praseodym on 2019-12-20
Can you upload the txt file here? Which VGA driver is it?
```

dkms status
dpkg -l nvidia-* | grep ii
dpkg -l linux-* | grep ii
```

---

### Post by oldfred on 2019-12-20
Have you updated UEFI and if SSD, SSD firmware?
That needed 19.10, but since you updated kernel that may then work with 18.04.

       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2) 
    
Open source video drivers will not support the new nVidia cards. You need the proprietary driver.
       #What is installed
dkms status 

      
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
   Acer Predator Helios 300 Boot into system, update, reboot then install drivers.
[https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace](https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace)

---

