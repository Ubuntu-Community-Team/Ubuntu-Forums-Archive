---
title: "XSANE: failed to open device - invalid argument"
date: 2018-01-25
forum: Networking &amp; Wireless
---

### Post by kyosaku on 2018-01-25
Hi there,

up until recently on 16.04.3 scanning and printing worked fine with brother MFC-L2740DW.  
Now, on starting XSANE it says 

"failed to open device brother4:net1;dev0 invalid argument"

Installed the repository as suggested in [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1512027](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1512027). Now libsane version is 1.0.27+git20180122-xenial0 - but the problem unfortunately remains. 

some terminal output:
 
scanimage -L
device `brother4:net1;dev0' is a Brother MFC-L2740DW MFC-L2740DW

 
scanimage --test
scanimage: open of device brother4:net1;dev0 failed: Invalid argument

thank you for your suggestions.

---

### Post by jan.caussyn on 2018-01-26
Recently I installed Lubuntu 17.10 32-bit, (coming from 16.10) and my brother scanner was no longer found (MFC-J625DW and SimpleScan).
I found the solution on this page :
[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us&lang=en&prod=mfc9120cn_all&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us&lang=en&prod=mfc9120cn_all&redirect=on#f00107)
These are the key lines :

**For 64bit Users:**
	**Command : sudo cp  /usr/lib64/sane/libsane-brother*   /usr/lib/x86_64-linux-gnu/sane**

 	**For 32bit Users:**
	[B]Command : sudo cp  /usr/lib/sane/libsane-brother*     /usr/lib/i386-linux-gnu/sane
[/B]
I hope this helps.

---

### Post by kyosaku on 2018-01-28
Thank you for trying to help.  

But the files to be copied
[B] 
/usr/lib64/sane/libsane-brother*[/B]

are already found in the target directory

[B]/usr/lib/x86_64-linux-gnu/sane


[/B]

---

