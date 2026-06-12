---
title: "x686 SMP dapper wireless not recognize"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by forlist2001 on 2006-09-17
Hello there,
I have working x386 kernel image and it supports my wireless just fine... however my machine is dual core one so i would like to install x686 SMP kernel. When I install and boot to that kernel my wireless just disappears. Is there any other setting I need to reconfigure for x686 to see and detect my wireless card or is this a bug in the system.

Thanks
Kb

---

### Post by forlist2001 on 2006-09-17
Well I found the solution I was doing something wrong while installing I should have installed by saying 

sudo apt-get install linux-686-smp instead of linux-image-686

this would have downloaded all the required and restricted modules as well... 
Hope this helps somebody else.

---

### Post by antonio_ on 2006-10-10
I've got the same problem with a Dell XPS1210 laptop. 
Thanks for the hint!
I've removed the linux-image-2.6.15-27-686 and installed the package linux-686-smp (...without the version number!!) and now the wireless device is found and works but without WEP encryption :(  

dmesg states some problems with ieee80211_crypt_wep. 

Any ideas? 
Is it a common problem that a future version of the kernel will solve or there is any package I should have installed?:confused: 
If a version will solve it, I'd rather prefer to wait and, in the meantime, share my connection with the neighborhood ;)  than to waste my health compiling drivers and firmwares.

Thanks in advance

---

### Post by antonio_ on 2006-10-11
BTW,the dmesg message is "ieee80211_cryp_wep: disagrees about version of symbol ieee80211_register_crypto_ops"

---

### Post by antonio_ on 2006-10-18
Problem solved!! 
The question was that the first time I installed the linux-image-2.6.15-27-686 and even when I run complete removal some files of the ieee80211 driver remained.
So I proceeded as follows:
1. Boot with the 386 kernel
2. Download the ieee80211 source code from sourceforge site. 
3. Install the 686-smp 
4. Boot with the 686-smp kernel
5. Unzip the ieee80211 package downloaded in step 2 
6. Run the script named remove-old.
7. Reboot with the 386 kernel
8. Uninstall (complete) the 686-smp kernel 
9. Reinstall the 686-smp kernel
10.Enjoy ubuntu !

---

