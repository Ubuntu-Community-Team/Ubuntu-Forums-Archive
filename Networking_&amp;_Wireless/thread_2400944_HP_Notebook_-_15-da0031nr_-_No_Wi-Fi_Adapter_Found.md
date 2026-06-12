---
title: "HP Notebook - 15-da0031nr - No Wi-Fi Adapter Found"
date: 2018-09-11
forum: Networking &amp; Wireless
---

### Post by biscuitunobtainable on 2018-09-11
Hello, I just want to say that I appreciate you coming to help me solve this.

I deleted the Windows 10 partition on my laptop and am running Ubuntu 18.04. I tried to follow instructions in other threads, but I keep seeing error messages in my terminal. If need be, I can reinstall a fresh copy of linux again. And if it matters, I chose normal installation and selected to install extras during installation.

And like the title says, this is the computer: 

[http://www.microcenter.com/product/507691/15-da0031nr_156_Laptop_Computer_-_Silver;_Intel_Core_i5-8250U_Processor_16GHz;_Microsoft_Windows_10_Home;_8GB_DDR4-2400_RAM;_1TB_HDD;_Intel_UHD_Graphi](http://www.microcenter.com/product/507691/15-da0031nr_156_Laptop_Computer_-_Silver;_Intel_Core_i5-8250U_Processor_16GHz;_Microsoft_Windows_10_Home;_8GB_DDR4-2400_RAM;_1TB_HDD;_Intel_UHD_Graphi)

[https://support.hp.com/us-en/document/c06071060](https://support.hp.com/us-en/document/c06071060)

---

### Post by ajgreeny on 2018-09-12
See [Wireless-info]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info") in my signature below and follow the instructions to run the script and show us the pastebin link of the output from that.

It will give our wifi experts, not me I'm afraid, a lot more info which may help them find a solution for you.

---

### Post by biscuitunobtainable on 2018-09-12
I went ahead and ran the script, these are my results.

[http://pastebin.com/uFTw6KAV](http://pastebin.com/uFTw6KAV)

Thank you

---

### Post by praseodym on 2018-09-12
Driver installation
```

sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
sudo apt-get remove --purge bcmwl-kernel-source
```
Reboot

---

### Post by biscuitunobtainable on 2018-09-12
Thank you, I have connectivity now!

May I also ask where did you learn this? To diagnose and issue the correct commands?

I'd like to learn how to manage machines, or is it operating system management? I'm confident there should be resources on the forum as well.

---

### Post by DuckHook on 2018-09-12
Hello biscuitunobtainable and welcome to the forums.

> **biscuitunobtainable said:**
> &#8230;May I also ask where did you learn this? To diagnose and issue the correct commands?
*praseodym* has been on these forums for a long time and is one of our gurus. He has been using Linux for many years. I'm afraid there is no shortcut to Linux knowledge, just like any other body of knowledge. It takes time, patience, effort, a lot of learning, trial, error and using resources like these forums. On the bright side, it isn't really that hard to join our community and start helping new users. Most people run into the same sort of problems that you have and it doesn't take much time before you know enough to help. You have already taken the first step by becoming a Forum member!
> I'd like to learn how to manage machines, or is it operating system management? I'm confident there should be resources on the forum as well.
You may find the various links in my sig useful. Also:

General Ubuntu Intro:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[https://linuxjourney.com](https://linuxjourney.com)

Command line learning:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by langdon-7 on 2018-09-15
I also have an HP 15 Notebook with a RTL8821CE wifi adaptor. I installed the drivers linked , but I found they were causing random process freeze which required hard reboot 2-3times a day. I just reinstalled fresh and I'm now on a laptop with a ethernet cable .  

Is anyone else experiencing process freeze issues?  Maybe its the sleep mode problem again. 

General question : Ubuntu does a great job with automatic hardware detection and installing appropriate drivers EXCEPT with these Realtek wiki adaptors. I've installed it on 4 HP Laptops and I've always had to manually install 3rd party drivers. HP is great for Linux, HP uses Realtek .....ergo support Realtek no?

---

