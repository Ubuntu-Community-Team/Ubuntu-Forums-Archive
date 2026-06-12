---
title: "Problem with Linksys AC1200 wireless adapter"
date: 2021-07-05
forum: Networking &amp; Wireless
---

### Post by rodneyisom on 2021-07-05
HI all,

I am trying to get the AC1200 to work with my Kubuntu 21.04 installation.  From looking at dmesg output, it appears to be detected, but I'm still getting no new wireless interface when I run 'ifconfig'.  I've installed a couple of different driver versions and nothing seems to make any difference.  Any thoughts?  

FYI - I'm not a Linux newbie....I'm fairly handy with certain things, but troubleshooting issues like this isn't one of them.  Any pointers would be greatly appreciated.

Thanks,
Rodney

---

### Post by morrownr on 2021-07-05
Hi Rodney,

Since you are not a newbie, I'll just share some thoughts and point you toward some info.

The installation of a couple of drivers concerns me. sudo is a weapon of mass destruction and when it is combined with Realtek out-of-kernel drivers that may be dated for the installation at hand, bad things can happen. Try to uninstall those previously installed drivers as best you can.

Job 1 at this point should be to determine the exact chipset in your adapter.  Go to the following site: 

[https://github.com/morrownr](https://github.com/morrownr)

You will see several repos, many of which are for wifi drivers. Each repo has a file that shows the device IDs of the supported chipsets. To start, go to the 88x2bu repo and open the file called "supported-device-IDs". This file gives you some instructions about finding the device ID of your adapters and you can check the list to see if your adapter is supported by that driver. If it isn't supported with 88x2bu then try 8812au next and so on.

Each repo has extensive documentation and installation instructions. Of note, as long as you are there, give [https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi) a look as it provides a LOT of good info for Linux users that like to use USB WiFi adapters.

If you run into problems, let us know.

---

### Post by rodneyisom on 2021-07-05
Wow...it's amazing how much better things work when you use the correct driver.   Thanks for the pointer!

Just out of curiosity, how did you come to be aware of the github site you directed me to?  I'd never have found it or recognized that it was a better resource than any of the others I was looking at.

---

### Post by chili555 on 2021-07-05
> Just out of curiosity, how did you come to be aware of the github site you directed me to? I believe that, based on his user name and the name of the git, that he is the author!

It is, indeed, a valuable resource and I refer to it quite often answering questions here and at Ask Ubuntu.

Thanks, @morrownr!

---

### Post by morrownr on 2021-07-05
> **chili555 said:**
> I believe that, based on his user name and the name of the git, that he is the author!

It is, indeed, a valuable resource and I refer to it quite often answering questions here and at Ask Ubuntu.

Thanks, @morrownr!

You are welcome... both of you. I'll never be as good at tech support you are, chili555, so I try to help in other ways given the skill set that I have.

Rodney, here is the full story if you are interested (and it is mostly true):

I am an older, high risk guy so when the pandemic started, I needed something to do that would keep me off the streets and out of trouble. I remembered this famous quote:

"Ask not what your operating system can do for you—ask what you can do for your operating system.”

With this inspiration in mind, I pondered for a few days. I have used usb WiFi adapters with Linux since 80211b was the hot ticket and I am well aware the struggles that many Linux users have with usb WiFi adapters. I then dusted off my old C books and created my github account. I made a list of problems that needed to be solved and I went about trying to solved them. The number 1 problem is the lack of good information that is readily available to Linux users. The number 2 problem is the disinformation that is available to Linux users. The number 3 problem is the way Realtek does its usb WiFi driver support (it is a method that is BAD, no other way to put it).

Problems 1 and 2 are addressed in these repos:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

[https://github.com/morrownr/7612u](https://github.com/morrownr/7612u)

Problem 3 is a challenge because I want to support Linux users with existing Realtek based adapters but I do not want my efforts to cause Linux users to buy new Realtek based adapters. I do my best to make the existing drivers as good as possible but I try to point out that there are good quality usb WiFi adapters available for Linux that use in-kernel drivers.

I would like to see Realtek start doing its usb WiFi drivers the right way but I see no evidence of that happening at this point.

In case anyone reads this in the future, maintaining "github.com/morrownr" is a lot of work. Anyone desiring to help is welcome to contact me via Private Message. You do not need to be a C coder in order to help. There are some fun jobs like checking on the links and prices to adapters that use in-kernel drivers. That needs to be done about once per month and is basically like going shopping.

There you have it.

morrownr

---

