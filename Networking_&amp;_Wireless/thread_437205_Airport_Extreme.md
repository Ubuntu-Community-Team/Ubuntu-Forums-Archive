---
title: "Airport Extreme"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by liberalist on 2007-05-08
Hi everyone,

I am having trouble to connect to the internet. My computer is an iMac with an Intel Core 2 Duo and an Airport Extreme a/b/g/n card (Broadcom BCM43xx 1.0 (4.80.79.1)). My wireless network does not show up either in Ubuntu 7.04 Feisty Fawn. Thank you very much in advance for your help. 

Attached are things that helped me solve some connection issues with another computer (but they did not solve my problem).

---

### Post by chili555 on 2007-05-09
Perhaps this will help: [http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm43xx)

---

### Post by liberalist on 2007-05-09
Thank you very much, again, chili555!

---

### Post by liberalist on 2007-05-15
I could not install the firmware. I have looked at the [PowerPCFAQ]("https://wiki.ubuntu.com/PowerPCFAQ") as well and tried to install the Airport Extreme driver by typing ```
sudo apt-get install bcm43xx-fwcutter
``` in the Terminal, but this did not work. Do you have any other solutions?

Thank you very much in advance.

Update: I am now doing the method described in [the wiki iMacIntel]("https://wiki.ubuntu.com/iMacIntel").

---

### Post by chili555 on 2007-05-15
I just installed it myself, even though I do not have a Broadcom card. It was fairly easy. I followed the guide in the link above. Here's what I did:

Right click the link to the firmware package, selected 'Save link as...', saved the .tar.gz file to my home directory, in my case /home/chili.

Opened Places -> Home Folder and found bcm43xxfirmware.tar.gz. Right clicked it and selected 'Extract here.' A new folder was created called bcm43xxfirmware. 

Opened a terminal and changed to the new directory and then installed the firmware:```
cd bcm43xxfirmware
sudo ./installbcm43xx.sh
```The firmware is now installed.

Please try these steps and let us hear from you if you get stuck.

---

### Post by liberalist on 2007-05-15
I will try out the suggestions later today. However, I do not think that bcm43xx supports my wireless card, because it says so in the Wiki:
> As of this writing the wireless card (Broadcom 4328, pciid 14e4:4328 ) is unsupported by bcm43xx, the Linux driver for Broadcom wireless cards. To work around this you will have to use ndiswrapper.

Do you know where I can download ndiswrapper? I cannot get it with ```
sudo apt-get install ndiswrapper
``` namely (I have no network connection). After downloading, how can I install ndiswrapper?

---

### Post by chili555 on 2007-05-15
ndiswrapper should be on your install CD. Please try:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper
```It will complain when it is unable to reach the on-line repositories, but you can safely ignore this. Then proceed with the Wiki instructions you linked.

---

### Post by zekica on 2007-05-15
You can download ndiswrapper from packages.ubuntu.com
you need [http://packages.ubuntu.com/feisty/misc/ndiswrapper-common](http://packages.ubuntu.com/feisty/misc/ndiswrapper-common)
and [http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/feisty/misc/ndiswrapper-utils-1.9)

After you have downloaded them, you can install them by double-clicking or typing "sudo dpkg -i ..." (without quotes) in terminal.

---

### Post by liberalist on 2007-05-15
Thanks for your replies. After installing ndiswrapper, I followed [the iMac Intel Wiki]("https://wiki.ubuntu.com/iMacIntel") instructions. However, I still haven't got a wireless connection. It seems that everything installed correctly (I did not get any errors or warnings). I have rebooted my system and tried again to connect to a wireless network, but this did not work. 

Are there any other solutions to my connection problem? As stated before, I have an Airport Extreme a/b/g/n card (Broadcom BCM43xx 1.0 (4.80.79.1)). 

Thank you very much in advance.

---

### Post by liberalist on 2007-05-15
I have found numerous possible solutions at 

[http://ubuntuforums.org/showthread.php?t=314036](http://ubuntuforums.org/showthread.php?t=314036) and 
[http://macwereld.nl/forum/2006/09/airport_extreme_aan_de_praat_met_wpa_onder_ubuntu_op_ppc](http://macwereld.nl/forum/2006/09/airport_extreme_aan_de_praat_met_wpa_onder_ubuntu_op_ppc) (Dutch forum).

They both tell me to download bcm43xx-fwcutter. However, since I haven't got an internet connection, I cannot download this package via Synaptic. Is it possible to download this package on my laptop with Ubuntu and then install it (offline) on my iMac with Ubuntu 7.04?

Thank you very much in advance.

**Update:** I have found a possible downloadsite: [http://packages.debian.org/unstable/utils/bcm43xx-fwcutter](http://packages.debian.org/unstable/utils/bcm43xx-fwcutter) . Please let me know if this is the correct site to download the aforementioned package.

---

### Post by liberalist on 2007-05-15
I have tried both methods, but none of them enabled my Airport Extreme a/b/g/n wireless card. I still do not have access to the internet.
I might have made a mistake, that's why I have attached the terminal output.

---

### Post by RealTrueSoft on 2007-05-24
Liberalist,

I haven't had time to post a tutorial as I have been busy, so let's just figure out what exactly is right first and then move on to find out what is wrong. You said it appeared to install correctly, so let's verify that. Firstly, if you are using Ndiswrapper you should check to see if it is loaded and working correctly.

Type ndiswrapper -l at the command prompt and post the output here.
Then type iwconfig and post that output here also.
Just in case neither of those are right try typing lsmod as well to make sure ndiswrapper is loaded upon boot. If you don't see ndiswrapper in that long list of modules, then nothing else will work until that is loaded anyways.

Let me know what you can and we'll go from there.

---

### Post by liberalist on 2007-05-27
Thank you very much for your reply, RealTrueSoft. However, I do not have the opportunity to try out those suggestions (I am final year and am busy with my exams). 

Could I try ndiswrapper out on my VirtualBox or do I need to reinstall Ubuntu? What means "use largest continuous free space" I saw when installing Ubuntu? Does that mean all other files will be left as is?

---

### Post by RealTrueSoft on 2007-05-30
I'm not sure I understand. Are you re-installing? If you have an existing installation definitely try the commands, that will be quicker than an installation. As for your other question, I never let the partitioner automatically do anything, but that is only because I have been burned in the past(not by Ubuntu, but other distros) that for some reason take the whole hard drive, when I only wanted free space used. Anyways, I've been there and done that with the school thing, so good luck! Let me know what you are trying to do right now with Linux and what progress you have made. I don't want to answer the wrong question and have you lost.

---

### Post by liberalist on 2007-06-02
I have reinstalled Ubuntu 6.06.1 with Parallels Desktop for Mac. Internet now works with or without bridging and I haven't configured anything. Is it still possible for me to try and install ndiswrapper and see if I can get my wireless card to work "natively"? 

Or shouldn't I mess with the good state the machine is in now? Thank you very much in advance.

Terminal output without installing anything extra:
```
jonathan@JonathansUbuntu:~$ sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.
```

---

