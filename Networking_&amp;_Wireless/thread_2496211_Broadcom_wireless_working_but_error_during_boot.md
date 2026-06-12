---
title: "Broadcom wireless working but error during boot"
date: 2024-03-18
forum: Networking &amp; Wireless
---

### Post by jperrin56 on 2024-03-18
Hi,

I have an old dell Inspiron 5748 laptop, installed Lubuntu. (Full wipe and install via usb.) Installed the [FONT=var(--ff-mono)]bcmwl-kernel-source, as recommended by the following link:

[/FONT][/COLOR]https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers

jperrin@john-inspiron5748:~$ lspci -nn -d 14e4:
06:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)


Wireless works great, but I get the following error on booting, if I remove the broadcom-wireless-drivers then the error message goes away:

dmesg entry
[   39.659777] kernel: UBSAN: array-index-out-of-bounds in /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:1934:4
[   39.659788] kernel: index 2 is out of range for type 'ether_addr [1]'


syslog entry
Mar 17 11:02:58 john-inspiron5748 kernel: [   39.659777] UBSAN: array-index-out-of-bounds in /var/lib/dkms/bcmwl/6.30.223.271+bdcom/build/src/wl/sys/wl_linux.c:1934:4
Mar 17 11:02:58 john-inspiron5748 kernel: [   39.659788] index 2 is out of range for type 'ether_addr [1]'
Mar 17 11:02:58 john-inspiron5748 kernel: [   39.659795] CPU: 1 PID: 613 Comm: avahi-daemon Tainted: P           OE      6.5.0-25-generic #25~22.04.1-Ubuntu


jperrin@john-inspiron5748:~$ uname -a 
Linux john-inspiron5748 6.5.0-25-generic #25~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue Feb 20 16:09:15 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

Any ideas or what to check would be appreciated. Laptop works great with Lubuntu. Good to resurrect my dad's old laptop. 

Thank you!

---

