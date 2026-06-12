---
title: "GRUB bootloader will not load WinXP"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Prizm1 on 2009-02-11
I am trying to dual boot a pre-existing WinXP SP3 Home Full Version with Ubuntu 8.10. WinXP is installed to my 40GB active C: drive. When I install Ubuntu, I am offered the default "Guided - resize SCSIi" option of installing to my 500GB non-active partioned D: drive. After the install, the GRUB boot loader list Windows as a boot selection (last line), but when I select Windows, the screen flickers and returns to the bootloader list. I can start Ubuntu from the bootloader list, as well as the other Ubuntu selections (safe, etc.), but Windows will not load from the GRUB bootloader. Is this because Ubuntu is on a different drive than WinXP? If so, how do you force Ubuntu to install to the 24GB of free space that I have on m 40GB C: Drive? I have successfuly restored WinXP to the C: Drive using Acronis TrueImage and deleted the Linux partitions with Paragon Disk Partitioner to restore to my previous Windows only configuration. I tried re-installing Ubuntu again, but get the same result. I am now back at my original Windows configuration before Ubuntu. I would really like to have dual boot with both OS'es.

---

### Post by k3rnelmustard on 2009-02-11
Can you tell me more specifically what you're trying to do?  If you want to install ubuntu to the other hard drive (as windows calls it, d:\ ) can you post the /boot/grub.conf that ubuntu creates?  (Or maybe ubuntu uses menu.lst, I don't remember) If you want to install to the SAME drive as windows, you'll need to shrink your windows partition using gparted on the ubuntu livecd.  Which would you like to do?

---

### Post by Prizm1 on 2009-02-12
I was installing the Ubuntu 8.10 Desktop version. I am trying to get to a dual-boot scenario, so that I can learn about the Linux OS, while still working with the Windows environment for now. If the Ubuntu (GRUB?) bootloader will not run Windows, even though Windows is listed in the bootloader menu as a detected OS selection to boot, what should I check for the next time that I install Ubuntu? Regardless of whether or not Ubuntu is on one drive and Windows on another, I would think that the bootloader would boot the Windows OS that it has listed in the bootloader menu.

---

### Post by k3rnelmustard on 2009-02-12
Yes, the bootloader can.  The problem has to do with which drive the windows bootloader is installed on and which drive the 'primary' and ubuntu's bootloader is installed on.  Just post the contents of /boot/menu.lst or whatever it is, and we can go from there.  Of course, you'll need to re-install ubuntu for this to work...

---

### Post by cdtech on 2009-02-12
Be sure you have "chainloader" listed within your /boot/grub/menu.list file. This insures that Windows will boot using its own boot partition...
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(**hd1,0**)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
This is from my secondary drive. Yours would be (hd0,0). Hope this is what your talking about.......

---

### Post by caljohnsmith on 2009-02-12
Grub can boot Windows, so it is likely that your problem is how your Grub's menu.lst is configured to boot Windows. If you have Ubuntu installed still, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by Prizm1 on 2009-02-12
Perhaps I should back up to a more basic question here. I have a Windows 40GB NTFS partitioned drive with 24GB of free space (more than the minimum 5GB for a Ubuntu installation). I prefer to maintain my NTFS partitioned 500GB drive for data storage only. When I install Ubuntu 8.10, and get to the Prepare Disk Space window, the "Guided - resize SCSi..." option allows me to resize and install only to the 500GB drive. The "Guided - use entire disk" option would eliminate my Windows partion altogether on my 40GB drive, so that is unacceptable. I do not understand the "Manual option. Now here is the question - if Ubuntu repartitioner can repartition my NTFS 500GB drive to install the Linux partions, then why can't it provide an option to do the same to the Windows NTFS 40GB drive since that drive has ample space for installing Ubuntu to? Can the "Manual" option be used to force Ubuntu to repartition and install to the free space of the 40GB drive where Windows is installed?

---

### Post by caljohnsmith on 2009-02-12
You should be able to install to the unused space on your Windows drive by using the manual partition option, or another way to do it is create the partitions ahead of time with gparted (System > Admin > Partition Editor). How about checking out these guides and see if they help:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html)
[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html)

---

### Post by Prizm1 on 2009-03-01
> **caljohnsmith said:**
> You should be able to install to the unused space on your Windows drive by using the manual partition option, or another way to do it is create the partitions ahead of time with gparted (System > Admin > Partition Editor). How about checking out these guides and see if they help:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html)
[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p22.html)
Thanks for your links. I have resolved to install Ubuntu to another computer and attempt to peer-to-peer network the two, instead. Perhaps in the future I will revisit this dual-boot scenario again.

---

