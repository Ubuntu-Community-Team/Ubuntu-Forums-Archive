---
title: "Wireless will NOT work - Tried EVERYTHING?"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by Tom_Shackleton on 2014-10-05
Hi guys, I've recently installed Ubuntu 14.04 for the first time so I'm fairly new to it all so excuse me If I'm asking a few too many questions. 

To put it short, wireless will not work, the option to enable wifi is greyed out, and I am unable to switch wireless on within the network manager. When I try rfkill list, the physical wireless LAN is hard blocked. I've tried multiple solutions provided by other solved threads and none have served to work. Solutions I've tried are:
- rfkill unblock all
- rfkill unblock 0 (this is the module that is blocked)
It still remains hard blocked when I try rfkill list again. 

I have also tried rebooting after both of these methods, tried both multiple times to ensure I am not making any mistakes. 
- I tried the same thing whilst enabling Network Stack in the BIOS and this made no difference so I disabled it again as this was the original default. 
- Checking that Wireless is enabled within the advanced hardware settings in the bios. It is enabled. I cannot find any solution to this problem and it's been n issue for about a week now. Would really appreciate any suggestions as I'm gradually beginning to feel like just giving up on using Ubuntu. 

Thanks for any responses. :-)

---

### Post by jeremy31 on 2014-10-05
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Follow instructions to download and run the wireless-script and post the resulting wireless-info file

To make it a bit easier you could ```
sudo apt-get install pastebinit
``` before running the script and then the script will prompt you if you want to upload it to pastebin, choose y and all you need to do is copy the URL that it returns

---

### Post by Tom_Shackleton on 2014-10-05
Thanks for the quick response! Ok, I followed the instructions, downloaded the updates and ran the wireless script. Here is the link to the pastebin [http://paste.ubuntu.com/8502283/](http://paste.ubuntu.com/8502283/) Any further suggestions after seeing that? :-)

---

### Post by weatherman2 on 2014-10-05
Every laptop has a way to enable/disable the wireless card, separately from the OS.  On older laptops, you might have a physical toggle switch.  Most newer laptops use a function key combo - Fn+F2 or Fn+F3 or something (depends on the make/model of laptop).

Hard-blocked usually means it is disabled by that switch.  Have you tried re-enabling it that way or making sure the switch is ON?

---

### Post by Tom_Shackleton on 2014-10-05
Well I assume it is on as when it's currently lit up, and when I use wireless with windows (i'm running a dual boot system) the light looks indicating that is on looks no different to how it does usually. However, when I attempt to turn it off in ubuntu it does not turn off, whereas when I attempt to use it in windows, I do have the ability to turn it off and on. My laptop is an Asus X552C, if that helps. Thanks again :-)

---

### Post by Tom_Shackleton on 2014-10-05
Just to add to that last post.. I just booted back into windows, to check that I was right, and I was, it simply turns the laptop into flight mode when pressed and disables internet

---

### Post by jeremy31 on 2014-10-05
> **Tom_Shackleton said:**
> Just to add to that last post.. I just booted back into windows, to check that I was right, and I was, it simply turns the laptop into flight mode when pressed and disables internet

This might be an easy fix ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus-nb.conf
``` reboot and try your keyboard wifi toggle

---

### Post by Tom_Shackleton on 2014-10-05
That worked! Thank you, you have seriously saved me so many headaches :D

---

### Post by jeremy31 on 2014-10-05
> **Tom_Shackleton said:**
> That worked! Thank you, you have seriously saved me so many headaches :D

Great, it was a upstream kernel developer- Hans de Goede, that suggested that this be tried

Please edit the title in your original post to include [SOLVED]

---

### Post by varunendra on 2014-10-06
> **jeremy31 said:**
> Please edit the title in your original post to include [SOLVED]

The correct way to mark a thread as [SOLVED] is to use "Thread Tools" link above the top post, as shown here with screenshots : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

