---
title: "driver problems for network latest version Ubuntu 23.04 Lunar, pc ASUSTeK COMPUTER IN"
date: 2023-08-18
forum: Networking &amp; Wireless
---

### Post by pabloguzmandeveloper on 2023-08-18
Hello colleagues, I downloaded the version prior to **Ubuntu 23.04 Lunar** and both last updates ruined my internet browsing speed in any browser, I have verified this by going to windows on the same computer that I use with two operating systems and in windows it works normally, It is not the internet provider either, it is the last driver that I could not solve or find the indicated solution. my Machine is with an **ASUSTeK COMPUTER INC. motherboard. PRIME A320M-K, AMD Ryzen™ 3 PRO 2200G with Radeon™ Vega Graphics × 4, Linux 6.2.0-27-generic kernel,**


***What is network card this information I have :*** 
~$ lspci | grep ethernet
**05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)**

Currently I use the machine to develop and I have configurations for environments with authentication included, although I can restore them again, it is a cumbersome job that I would like to avoid by deleting the ubuntu operating system and reinstalling the version that works, although this is not even it is guarantee.
And on the other hand, a curious fact is that the previous version of Ubuntu offered a PRO version with support for 10 years, when I went to this latest version believing that everything was going to be solved, in addition to continuing the ethernet network problem, the PRO version disappeared and 10 year support.


In short, from bad to worse...


I would appreciate if someone has a piece of information or experience in sharing one or more solutions.


Greetings and have a very good morning colleagues!!

---

### Post by chili555 on 2023-08-19
Which driver are you using?

```
lspci -nnk | grep 0200 -A3
```

The r8168-dkms version typically works better.

---

### Post by pabloguzmandeveloper on 2023-08-19
Thank you for your response, last night in a hurry I created this post, although I have not copied which controller I have since I have to advise myself how to obtain it, as soon as I get home I try to find out and share it, since the difficulty of using it is very great Slow internet and unable to migrate to Windows.  Greetings and thanks

---

### Post by pabloguzmandeveloper on 2023-08-19
I have seen that you shared the command to get the driver, thank you very much!  Now, do you have any idea if I get your driver what is the best and safest way to install the new driver for a newbie like me?  Thanks greetings!

---

### Post by chili555 on 2023-08-19
From the terminal:

```
sudo apt update
sudo apt install r8168-dkms 

```
Reboot.

---

### Post by pabloguzmandeveloper on 2023-08-20
Thank you very much for your help, I have installed this driver that you gave me and it is still the same. I will continue investigating, I am currently looking for a list of all existing controllers to try one by one. Greetings!!

---

### Post by chili555 on 2023-08-20
Let's see if the log has any interesting clues:

```
sudo dmesg | grep -e r816 -e en
```

---

### Post by ian-weisser on 2023-08-20
> **pabloguzmandeveloper said:**
> I downloaded the version prior to **Ubuntu 23.04 Lunar**

The version prior to Ubuntu 23.04 was version Ubuntu 22.10. Support for Ubuntu 22.10 ended three weeks ago. No more security patches. Migrate to a newer release of Ubuntu.

Or perhaps you meant Ubuntu 22.04 LTS, which is supported here for 5 years (plus security updates for another 5 if you subscribe to Pro).

It's best to use real version numbers rather than "prior to" or "latest". Avoid confusion or misunderstanding.


> **pabloguzmandeveloper said:**
> the previous version of  Ubuntu offered a PRO version with support for 10 years, when I went to  this latest version believing that everything was going to be solved, in  addition to continuing the ethernet network problem, the PRO version  disappeared and 10 year support.

Ah, so now we know that you were referring to Ubuntu 22.04 LTS (not Ubuntu 22.10), since only LTS releases are eligible for Pro subscriptions.

When you "upgraded: to 23.04" you lost your Pro (23.04 is not-LTS, Pro is LTS-only). That's expected behavior. Return to 22.04, and you can have Pro again.

Since there is no direct upgrade path from 22.04 to 23.04, your method of upgrading may be suspect. The only supported upgrade method was to upgrade to 22.10, then again to 23.04. Since 22.10 is now closed, that path is ended. The only other supported method is a reinstall. If you used some other method, then your system state is suspect and may not be supportable.

Clarification: Pro is NOT "10 year support". It's 10 years of security patches only. Bugfixes end after 5 years. Technical support (us!) ends after 5 years.

---

### Post by pabloguzmandeveloper on 2023-08-21
Thank you very much for your help, I am going to reinstall the 22.04 LTS version to get the PRO version again, although I doubt that it will be solved because it is a great move to delete all the accumulated configurations on my pc, if not I will see to find that driver for my network I'll have to do it maybe. Greetings!!

---

