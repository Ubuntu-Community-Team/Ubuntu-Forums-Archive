---
title: "GRUB Error 22"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by kauboy on 2009-05-09
Hi,

I just screwed up my GRUB after a long time. I had Ubuntu 8.04 up and running but I decided to try out Ubuntu 9.04 64-bit in parallel. I *deleted* my Fedora partitions (swap,boot,root) to make room using a Live USB of Ubuntu 9.04 and rebooted. Down goes my GRUB. Error 22. I had my GRUB installed in my 8.04 root partition itself and I'm sure I haven't modified my 8.04 root and swap partitions. I now have about 13GB unallocated space from deleting Fedora. Any leads?? Thanks.

- Kaushik.

---

### Post by Didius Falco on 2009-05-09
> **kauboy said:**
> Hi,

I just screwed up my GRUB after a long time. I had Ubuntu 8.04 up and running but I decided to try out Ubuntu 9.04 64-bit in parallel. I *deleted* my Fedora partitions (swap,boot,root) to make room using a Live USB of Ubuntu 9.04 and rebooted. Down goes my GRUB. Error 22. I had my GRUB installed in my 8.04 root partition itself and I'm sure I haven't modified my 8.04 root and swap partitions. I now have about 13GB unallocated space from deleting Fedora. Any leads?? Thanks.

- Kaushik.

Hi Kaushik,

You are probably just missing the Fedora partition, and will have to adjust your menu.lst file and fstab to reflect the new layout of your disk. 

Boot up with your LiveUSB and download the little (57k) script in my signature to your desktop.

Then open a terminal and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

The script will gather a lot of information that will help figure out the problem into a file named RESULTS.txt

Open that file, select all and paste it in this thread, then put code tags (the # on the tool bar) around it.

It'll help to figure out the answer faster...

Regards,

Didius

---

### Post by kauboy on 2009-05-10
Hi Didius,

Thanks for your reply! However, I figured that since I had 13GB *free* now, it would be worthwhile going ahead and installing 9.04-64bit as I had originally intended to do. As expected, the new GRUB install of 9.04 detected both 8.04 and XP and booted up all 3 OS-es fine! Took a bit of a risk I guess (with no OS booting before my 9.04 install attempt!!) but no problems whatsoever. Thanks again! I'm sure I'll come back in the future for another GRUB Error 22, though I hope not too soon!

- Kaushik.

---

### Post by Didius Falco on 2009-05-10
All is well that ends well! Enjoy your 9.04!

Regards,

Didius

---

