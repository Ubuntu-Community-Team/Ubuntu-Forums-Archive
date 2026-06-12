---
title: "No Boot - 8.10 installed on external USB-FDD"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by egrpioneer on 2009-01-01
Please help me boot into Ubuntu. USB FDD set as first drive in BIOS/CMOS, but no action!
I ran Ubunto live CD and reviewed Gparted. Could partition /dev/sdb1, filesystem fat32, mountpoint /media/mypassport, label my passport, be causing the problem? 
Thanks in advance for helping me solve the problem.

---

### Post by Dedoimedo on 2009-01-01
Maybe you need to enable the compatibility mode ...? Look for something like that or similar under boot options.
Dedoimedo

---

### Post by egrpioneer on 2009-01-01
Thanks for responding. If compatibility mode refers to legacy emulation, USB-FDD is enabled.

---

### Post by caljohnsmith on 2009-01-01
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

