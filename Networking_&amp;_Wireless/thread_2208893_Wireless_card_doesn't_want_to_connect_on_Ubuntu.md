---
title: "Wireless card doesn't want to connect on Ubuntu"
date: 2014-03-02
forum: Networking &amp; Wireless
---

### Post by nick70 on 2014-03-02
Hello all,

I am relatively new to Linux and Unix systems, and I want to get my feet wet in shells, bashes, etc. So, I recently built a new computer and just installed Ubuntu alongside Windows 7 on it. However, when I attempt to connect to my normal wireless network connection (which has always worked on Windows) it thinks for a minute, then goes back to the pop up window that says that the network needs a passcode to be accessed. I've double checked the passcode at least 10 times to no avail. I'm pretty sure this is because the wireless card I have installed on my system (because I do not have easy access to Ethernet ports) does not have drivers for Linux. I thought of that, and then put the drivers CD into my computer, but Ubuntu won't run it. I did a little bit of searching around, and there is a Linux folder in the CD, but following the instructions did nothing. If you'd like, I can post the readme file that I went off of.

I have installed in my computer a Netis WF-2113 Wireless PCI-E Adapter. If anyone knows more about this piece of hardware and has experience with it, that would be great.

So, I suppose I'm asking what I should do next. Is there a way for installing drivers for wifi with this card that I am not aware of? Am I doing something wrong? Do I just need to get a new wifi card or figure out how to get access to Ethernet ports?

Thank you all for your help,

-Nick


Edit: I just went looking around and found Linux drivers on netis' website. I followed their instructions, but the command line always ends up in an error (code related; says that it's expecting something when it finds something different), and when I reboot, the wifi still doesn't work.

---

### Post by wildmanne39 on 2014-03-03
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by nick70 on 2014-03-03
Here you are.

Thank you for your help.

---

### Post by Vladlenin5000 on 2014-03-04
Your Realtek RTL8188CE based wireless wireless device should be already supported since at least 2012. As a matter of fact, Realtek has proprietary drivers for this chipset and kernel **2.6.18~2.6.38** and kernel **3.0.2 **(+ Android 1.6~2.3 and 4.0). The error you found when compiling had to do with kernel version, probably. Don't use it, you shouldn't need it. 
I've noticed an higher than usual amount of issue related with this chipset on Linux since its release. Realtek's chipsets are usually well supported out-of-the-box.

PS - I have no time to check the whole log - might be able to do it later - but Wild Man is The Man when it comes to wireless gremlins... Do what he says and you should be fine. I'm here to learn also.

---

### Post by wildmanne39 on 2014-03-04
I am sorry guys I am out of town with very spotty wifi, hopefully chili555 or varun will stop by.

---

### Post by varunendra on 2014-03-05
> **Wild Man said:**
> I am sorry guys I am out of town with very spotty wifi, hopefully chili555 or varun will stop by.
..and Varun does! :D
I feel honoured being considered as helpful by you, and be ranked with dr. chili555 !! He would be deep asleep at this time, so I'll take the opportunity. :)

> **Vladlenin5000 said:**
> Your Realtek RTL8188CE based wireless wireless device should be already supported since at least 2012...
Yes, it is supported and does work out-of-box. Unfortunately, its versions between kernel 3.8 and 3.11 have been reported to be problematic very frequently and normal workarounds usually don't help with these versions. Nevertheless, we always try them first, hoping to avoid more geeky workarounds.


**@Nick,**
Please try a few available parameters as suggested in this post : [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912)
As mentioned there, the changes would be temporary, so try the connectivity without rebooting after trying them. If they seem to help, we can make them permanent (also discussed later in the thread).

If none of them seem to help, we shall try a newer driver from backports-3.12.

---

### Post by nick70 on 2014-03-12
Thank you all for your help.

I have tried all of the combinations on the post that you mentioned, varun. The first thing I noticed was that after I had entered the commands, my network no longer showed up in the network list. I went to connect hidden network, and there was an option there for my network, but I'm not sure if this did something different.

In any case, none of the combos worked. After I tried connecting, it still pulled up the "Access to wireless network needs a password" box.

Should I upgrade/degrade my kernel, or wait for a new driver? I'm unsure of what to do at this point.

Again, thank you for all your help.

---

### Post by varunendra on 2014-03-12
> **nick70 said:**
> Should I upgrade/degrade my kernel, or wait for a new driver? I'm unsure of what to do at this point.

I think trying a more trusted driver would be a good idea at this point. Please follow the instructions in this post to download and install it (the instructions were for rtl8192**se**, but are same for rtl8192**ce** also) : [http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946](http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946)

Like mentioned in the post, please try the previously suggested parameters with this driver also if required. If even that doesn't solve the problem, please post back a fresh report of wireless_script, with all three suggested parameters applied, and the following output along with the script report -
```
grep [[:alnum:]] /sys/module/rtl8192ce/parameters/*
```

---

