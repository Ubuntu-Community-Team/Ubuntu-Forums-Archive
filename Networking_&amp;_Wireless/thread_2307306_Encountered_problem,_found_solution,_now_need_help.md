---
title: "Encountered problem, found solution, now need help implementing! [Netwrk/Drivers/MSI]"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by eric100 on 2015-12-23
Hi there,

I recently purchased a MSI GS60 notebook and managed to install Ubuntu 14.04 from my windows 10 partition, using Rufus 2.5 and an USB. However, this MSI series apparently comes with a few Linux-related issues, namely network card and graphic card driver issues. The graphics card issue has so far been easily circumvented by continually adding nomodeset in the startup command box, so we can leave that for later; the main problem is the network drivers. I have a ethernet cable connected, but no internet is registered. I have messed around with the problem in "try install" mode, and have tried installing wifi and ethernet manually, all to no avail. 

The issue was reported in a bug post, and is now reported as solved (see post #324, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184)), what's more post #8 in this forum post ([http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)) explains the exact same problem as well as how one goes about solving it - _**I am just at a loss as to how I should implement it**_.

For anyone willing to read up slightly on this and help me, I would be eternally and thoroughly thankful. 

Starting with the latter - post #8 in the forum thread:

> I've exactly same MSI GS60 model (with Broadwell I7-5700HQ and 970m) with one 128GB mSata SSD and 1TB HDD. And I've Ubuntu 15.10 
running now nicely (alongside with Windows 8.1), without extra boot parameters.


Main thing were to disable "Intel SpeedStepping" in BIOS. If it's not disabled computer seems to hang/restart randomly, I couldn't even finish 
the installation.


WIFI wasn't working after installation of 15.10. It was supposed to be fixed after pulling latest updates using apt (apt-get update, apt-get upgrade),
but it was just partially working (list of APs were showing, joining to AP failed, can see firmware crashes in dmesg). 


[B]So, here's how I fixed the broken WIFI:
- sudo apt-get update
- sudo apt-get upgrade (now you have partially working WIFI)
- replace board.bin and firmware-5.bin files in lib/firmware/ath10k/QCA6174/hw2.1 from this GIT repo [https://github.com/kvalo/ath10k-firm.../QCA6174/hw2.1](https://github.com/kvalo/ath10k-firm.../QCA6174/hw2.1) (wifi is now fully fixed)[/B]


To enable NVIDIA 970m GPU (with "oldish" v352 drivers):
- Add file /etc/modprobe.d/blacklist-nouveau.conf containing: "blacklist nouveau options nouveau modeset=0"
- sudo apt-get install nvidia-352 nvidia-prime
- sudo reboot



I cannot even perform the sudo update/upgrade commands suggested as I have zero access to internet. Is this a matter of me having installed 14.04 and not 15.10, or one of the other versions mentioned? How is it that he is having network problems, but is still able to download/update/upgrade information from the internet?

As mentioned in the bugfix (the other link, above), I have also tried installing "linux-image-extra-4.2.0-16-generic 4.2.0-16.19". I.e. downloading it from my windows 10 partition, moving it to a ubuntu folder, installing it, restarting the computer. However, I am unsure what this solved. The other file mentioned in the bug-fix is a .tar file, which I am unsure how to install. 

Any help is appreciated.

---

### Post by Vladlenin5000 on 2015-12-23
> **eric100 said:**
> I cannot even perform the sudo update/upgrade commands suggested as I have zero access to internet. Is this a matter of me having installed 14.04 and not 15.10, or one of the other versions mentioned? How is it that he is having network problems, but is still able to download/update/upgrade information from the internet?

As mentioned in the bugfix (the other link, above), I have also tried installing "linux-image-extra-4.2.0-16-generic 4.2.0-16.19". I.e. downloading it from my windows 10 partition, moving it to a ubuntu folder, installing it, restarting the computer. However, I am unsure what this solved. The other file mentioned in the bug-fix is a .tar file, which I am unsure how to install. 


If you aren't aware of other internet connection methods then you should. There's Ethernet (LAN cable), Android (or others) USB tethering, USB 3G/4G modems, etc.
Any can be used as a temporary internet access to perform all the steps that ultimately will "fix" the WiFi.

Regarding your graphics card, the use of nomodeset is ONLY to have video so you can install the required Nvidia drivers, never as a permanent solution, it's NO solution at all.
About drivers... If your laptop has the same NVIDIA 970m as your quoted post, then you must use the latest and greatest from Nvidia. Nvidia recommends 352.63 for such card. Ubuntu 14.04 may NOT provide the required up-to-date version. You're advise to use an additional software repository: [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action).

For the moment do NOT worry about kernel upgrades. Do NOT attemp to do what you described because most likely you'll end up making thing worse than they already are.

---

### Post by Hadaka on 2015-12-23
Hi, it looks like you have the ath10k driver that is new, ask a mod to move your
thread to. Networking and Wireless....I would suggest re-titleing your post to say
"Need help installing ath10k" once your thread is moved to the Network forum, go
here,read and post your "Wireless-info.txt file.. 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by sandyd on 2015-12-23
> **Hadaka said:**
> Hi, it looks like you have the ath10k driver that is new, [COLOR="#FF0000"]ask a mod[/COLOR] to move your
thread to. Networking and Wireless....I would suggest re-titleing your post to say
"Need help installing ath10k" once your thread is moved to the Network forum, go
here,read and post your "Wireless-info.txt file.. 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

no need, its there now :P

---

### Post by eric100 on 2015-12-24
> **Vladlenin5000 said:**
> If you aren't aware of other internet connection methods then you should. There's Ethernet (LAN cable), Android (or others) USB tethering, USB 3G/4G modems, etc.
Any can be used as a temporary internet access to perform all the steps that ultimately will "fix" the WiFi.

Regarding your graphics card, the use of nomodeset is ONLY to have video so you can install the required Nvidia drivers, never as a permanent solution, it's NO solution at all.
About drivers... If your laptop has the same NVIDIA 970m as your quoted post, then you must use the latest and greatest from Nvidia. Nvidia recommends 352.63 for such card. Ubuntu 14.04 may NOT provide the required up-to-date version. You're advise to use an additional software repository: [http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action).

For the moment do NOT worry about kernel upgrades. Do NOT attemp to do what you described because most likely you'll end up making thing worse than they already are.

Thank you for your reply. 

I've tried WiFI, Ethernet as well as USB tethering with nothing working. The network card driver problem appears to be fundamental enough to not allow any of these access points. I attempted to install the nvidia drivers by first downloading it to the Windows 10 partition, then transferring to ubuntu home and making the file an exectuable file and running it, but I only ever got an error wherein it complained about foreign symbol and warned me against "editing".

---

### Post by eric100 on 2015-12-24
> **Hadaka said:**
> Hi, it looks like you have the ath10k driver that is new, ask a mod to move your
thread to. Networking and Wireless....I would suggest re-titleing your post to say
"Need help installing ath10k" once your thread is moved to the Network forum, go
here,read and post your "Wireless-info.txt file.. 
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks.

Thank you for taking the time to help.

I am unable to perform any of the actions in your linked thread, as it requires me to download things/access things through the internet in the command prompt. I have absolutely 0 internet access in ubuntu. Downloading the wireless info script in order to run it does not work, in other words.

I was under the impression that I could download these files to another partition (my working windows 10 partition, for instance) but when I did this for the nvidia drivers and moved them to ubuntu home, I was still unable to execute them.

---

