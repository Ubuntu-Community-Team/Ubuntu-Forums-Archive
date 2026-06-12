---
title: "Wireless Card Not Working on Ubuntu"
date: 2015-11-27
forum: Networking &amp; Wireless
---

### Post by william97 on 2015-11-27
Hello, 

I'm very new to Linux and recently installed ubuntu 14.04 on a new laptop. I've googled this problem and have seen many attempts at the solution, but I'm still having a hard time.
My wireless card is the Intel® Dual Band Wireless-AC 3165 and it will not show any networks or even the option to enable wifi. Now, I just noticed that my new laptop doesn't have an ethernet port, so I can't even establish a wired connection. After researching, I figured that I need to update the drivers. Alas, I thought I could be clever and downloaded the drivers by booting into Windows from the [Intel website.]("http://www.intel.com/support/wireless/wlan/sb/CS-034398.htm") I then proceeded to move this download via flash drive onto the ubuntu partition. I tried to extract the file using archive manager and then used terminal to go into the folder and attempted to make and make install on that folder. (I don't even know if that's correct.)

I also noticed that Intel's drivers require Kernel 4.2+ and 
 
```
root@william-Lenovo-ideapad-300-15ISK:~# uname -r
3.19.0-25-generic

```

Given my inability to connect to the internet, how do I upgrade the Kernel, update the drivers, and ultimately achieve wireless connectivity on my laptop? Some guidance would be greatly appreciated.

---

### Post by howefield on 2015-11-27
Thread moved to the "*Networking & Wireless*" forum for better support.

---

### Post by william97 on 2015-11-27
Nevermind, I found a solution to the issue. I found out how to upgrade to 4.2 by downloading the zip file [here]("http://news.softpedia.com/news/how-to-install-linux-kernel-4-2-on-ubuntu-debian-and-linux-mint-490702.shtml").
After extracting, I then executed the following commands in terminal at the folder in which I extracted the zip file to:
```

[FONT=monospace]sudo dpkg -i *.deb[/FONT]
[FONT=monospace]sudo update-grub[/FONT]

```

As was mentioned and outlined in that article. 

I then installed the drivers found [here]("https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi") by extracting the appropriate, downloaded file from that site and ran:

```

sudo cp ~/Desktop/iwlwifi-7265-ucode-25.30.13.0/iwl* /lib/firmware

```

The solution I found also said to copy and rename these drivers by the following method:

```

cd /lib/firmware
sudo cp iwlwifi-7265D-13.ucode  iwlwifi-3165-9.ucode
sudo cp iwlwifi-7265-13.ucode  iwlwifi-3165-13.ucode
```

I restarted my laptop and boom, I can access wifi networks. Now, I'm honestly not sure why I had to copy and rename the files in such a manner. I'm curious to know, though.

---

