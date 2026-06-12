---
title: "Installed Ubuntu, but no internet on eeepc 1000 HE"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by ltsching on 2009-04-08
Hi all, 

I am a long time Mac user and when I purchased the 1000 HE, I decided to give Linux/Ubuntu a try. I have successfully installed Ubuntu in the second partition (drive D) using Wubi. I am able to connect to my wireless network (Time Capsule, WPA) with excellent strength. However, when I try to run Firefox, the web page will not load and I get the usual "address not found" error message. I have also tried Eeebuntu with a bootable USB drive and I encounter the same problem. In Windows, however, everything works fine.

From what I have read on the Internet, this could be a driver problem with newer hardware of the 1000 HE. Has anyone successfully installed Ubuntu or Eeebuntu on the eeepc 1000 HE without any problem? I would like to continue to use Wubi to get comfortable with the OS before I install it permanently. Any help or suggestion would be greatly appreciated. I am really eager to familiarize myself with Ubuntu!

---

### Post by PreviousN on 2009-04-08
You may try easypeasy linux. It's essentially ubuntu optimized for eeepcs. Or, check out this page:

[https://help.ubuntu.com/community/EeePC](https://help.ubuntu.com/community/EeePC)

---

### Post by Jakey_TheSnake on 2009-04-08
If you're connecting to your wireless router but cannot access webpages, well, it sounds like it's your router that's the problem and not Ubuntu.

---

### Post by ltsching on 2009-04-08
> **Jakey_TheSnake said:**
> If you're connecting to your wireless router but cannot access webpages, well, it sounds like it's your router that's the problem and not Ubuntu.

Thanks, but I have no problem with all my other computers in the house: three Mac laptops and even the eeepc running XP.

---

### Post by PreviousN on 2009-04-08
EEEpc netbooks have a well known problem with using the onboard wireless. It is ubuntu's fault (Bug #182489) ([https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489/)). Also the OP mentioned that it works with the eeepc running xp. 

I'm not anyones personal googlier, but I took the liberty to google "eeepc ubuntu wireless" and the first result was this: 
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

Check out the wireless section. I know that some content may be like "huh?" but if you run the commands in the code section, you shouldn't have too much trouble. 

Should fix your problem. 

Plug the eeepc into ethernet,
sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid-generic
sudo modprobe ath5k

EeePC 900s and 701s require "blacklist ath_pci" added to "/etc/modprobe.d/blacklist" to enable wireless.

sudo -s
echo blacklist ath_pci >> /etc/modprobe.d/blacklist

---

### Post by 1BigBore on 2009-04-08
Is there a better choice for a Linux 'NetBook'? One that will work better with a typical Wireless-"N" network.  
(sorry if this disrupted your thread, but I thought it was related)
Thanks.

---

### Post by PreviousN on 2009-04-08
Personaly I prefer ubuntu, actually. I have a Kohjinsha Sh8 netbook and ubuntu ROCKS on it. But, then again, the kohjinsha is a touchscreen netbook with a great resolution :-). Most netbook distros aren't optimized for touchscreens or screens with great resolution for that matter

I mentioned another distro earlier. Easypeasy. Here's a link: [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

Its EEEpc optimized ubuntu. I think they also have optimized it for other netbooks as well.

---

### Post by billgoldberg on 2009-04-08
> **PreviousN said:**
> Personaly I prefer ubuntu, actually. I have a Kohjinsha Sh8 netbook and ubuntu ROCKS on it. But, then again, the kohjinsha is a touchscreen netbook with a great resolution :-). Most netbook distros aren't optimized for touchscreens or screens with great resolution for that matter

I mentioned another distro earlier. Easypeasy. Here's a link: [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

Its EEEpc optimized ubuntu. I think they also have optimized it for other netbooks as well.

Eeebuntu is better, imho.

---

### Post by PreviousN on 2009-04-08
I've never really tried easypeasy (in an in-depth way) really. Happy to hear that there's other options out there. I think there are quite a few eee distros.

But for me, I try to stick with ubuntu because I like the community. 

Eeebuntu sounds interesting, but at the same time, if what ya got works, then why switch?

---

### Post by ltsching on 2009-04-08
Thanks everyone, for the suggestions and advices. I really appreciate it. Update: so I tried eeebuntu netbook remix again via the USB drive and the internet worked! However, it was slow and after a few minutes, I get the disconnected message and reapplying the password didn't alleviate the problem. This is definitely a driver issue.

---

### Post by PreviousN on 2009-04-08
I'm not a fan of the "netbook remix" flavors of ubuntu. I feel like the simplified interface is limiting. You should give the fix I posted a try. Maybe I wasn't clear, but those commands need to be run in a terminal. 
Plug the eeepc into ethernet,
1. Applications --> accessories --> terminal
sudo apt-get update
sudo apt-get install linux-backports-modules-intrepid-generic
sudo modprobe ath5k
sudo -s
echo blacklist ath_pci >> /etc/modprobe.d/blacklist

---

