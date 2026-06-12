---
title: "D-Link DWL-G630 and Madwifi"
date: 2005-08-28
forum: Networking &amp; Wireless
---

### Post by Kloaf222 on 2005-08-28
Hi All, 

Just installed Ubuntu for the first time this weekend, along with being a new user to Linux period. I am in the process of trying to get Ubuntu to recognize my wireless card. I am running it on a B-Network and I have gone through literally hundereds of threads trying to figure out what is going on. I have installed the madwifi files from their site and I think all is good there until I try to configure my network. It has an error about "Please enable wireless extensions". So I figured through reading alot of threads that  it has something to do with /usr/src/linux-headers-2.6.10-5/.config but if I try to bring it up to see I get a permission denied...so, I am stuck and any help would be appreciated. Especially if someone has installed this card before.

Thanks.

Kyle

---

### Post by Lambert on 2005-08-28
I couldn't get my atheos card going on hoary but I am fairly new to linux. You may want to check out this thread.

[http://ubuntuforums.org/showthread.php?t=36800](http://ubuntuforums.org/showthread.php?t=36800)

---

### Post by Kloaf222 on 2005-08-28
Followed it word for word yesterday, still didnt work.



I got up until you are supposed to replace the 9 files, I get this...

cp: cannot stat '/lib/modules/2.6.10/ath_pci.ko : No such file or directory.

EDIT: If I try it now, if I try a "sudo make" I get a message..

"PLease enable wireless connections."

---

### Post by firecat53 on 2005-08-31
Have faith! It will work! I've got my DWL-G630 working with WEP and WPA!

The how-to referenced by Lambert is the correct procedure to follow. When you copy the files from the newly generated directory /lib/modules/2.6.10 to the original directorys /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath*, make sure you keep the directory structure intact. You also may have to create a new directory for the ath_rate_sample.ko file within the existing structure.  So the path would be /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless/ath_rate/sample/ath_rate_sample.ko.  

Then don't forget the sudo modprobe ath_pci.

After that, it should just be a matter of configuring your wireless interface:

sudo ifconfig ath0 essid networkname
sudo ifconfig ath0 up
sudo dhclient ath0

Let me know if it works!

Scott

---

