---
title: "Remove ubuntu from netbook"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by mdebaprasad on 2011-06-06
Hi,

I had installed ubuntu on my netbook to try it out. But now some urgent work needs to be done and I am not able to configure ubuntu to get the work done. It will take time. Since the work is urgent, I need to revert back to my original operating system now. Please tell me how I can remove Ubuntu and install windows.

Initially, my netbook had only Windows 7. I installed ubuntu from usb drive since my netbbok does not have CD /DVD drive.

Now I want to remove Ubuntu, and install Windows XP.

How can I do this? I have lloked at several forum posts but I am not able to get my step by step answer.

I am in dire need of a step by step complete annwer so that after following it I can remove Ubuntu and install windows xp without any mistake. I really need to get this done by this week, otherwise I am not able to do my urgent work.

DM

India

I had completely removed Windows initially, and had installed ubuntu.

---

### Post by gandaran on 2011-06-06
I don't know if you can boot windows XP from usb flash drive but if you have a windows disk and cd/dvd drive just boot the disk and format the drive using the windows tools and install windows, its easy!

---

### Post by Paqman on 2011-06-06
If you made backup disks for Windows 7 then you can just use those to restore Win 7. If you need to install Windows XP instead, then you'll need to have a copy of it on disk, and a valid license key. You can't use the Win 7 licence that came with your machine. I believe there is a way to install XP from a USB stick, but it's not something I've ever done. A USB optical drive would also work.

---

### Post by mdebaprasad on 2011-06-06
I dont have an external CD/DVD drive whihc I can use. Otherwise, I would have tried that by now. I asked several of my frieds. But they too dont have that. I have to do it using my USB drive only.

---

### Post by mdebaprasad on 2011-06-06
> **Paqman said:**
> If you made backup disks for Windows 7 then you can just use those to restore Win 7. If you need to install Windows XP instead, then you'll need to have a copy of it on disk, and a valid license key. You can't use the Win 7 licence that came with your machine. I believe there is a way to install XP from a USB stick, but it's not something I've ever done. A USB optical drive would also work.
I have original CDs of both Windows 7 and Xp that came with the netbook. But Xp files are not on the drive. But probably the Win 7 files are which I feel is for system restore and recovery. During the boot menu, they show only one windows option that of windows 7. But when I select it, it says system recovery but just restarts after sometime again showing the same previous boot menu. CAn you tell me any option using the USb dirve only? Maybe remove Ubuntu first using the USb, then I will be able to install Windows XP using the USb. Installing the windows XP I feel I will be able to do. But I want to remove ubuntu first using the USB. How can I do it? Its my bad luck that just when I started to try Linux, something urgent came up.

---

### Post by Frogs Hair on 2011-06-06
This is a bit dated , but may be useful . I found many results in my search. You have to find someone with XP installed to use this. 
[http://www.techrepublic.com/article/illustrated-walk-through-creating-a-bootable-usb-flash-drive-for-windows-xp/6160062](http://www.techrepublic.com/article/illustrated-walk-through-creating-a-bootable-usb-flash-drive-for-windows-xp/6160062)

---

### Post by gandaran on 2011-06-06
> **mdebaprasad said:**
> I have original CDs of both Windows 7 and Xp that came with the netbook. But Xp files are not on the drive. But probably the Win 7 files are which I feel is for system restore and recovery. During the boot menu, they show only one windows option that of windows 7. But when I select it, it says system recovery but just restarts after sometime again showing the same previous boot menu. CAn you tell me any option using the USb dirve only? Maybe remove Ubuntu first using the USb, then I will be able to install Windows XP using the USb. Installing the windows XP I feel I will be able to do. But I want to remove ubuntu first using the USB. How can I do it? Its my bad luck that just when I started to try Linux, something urgent came up.
if you still got the windows recovery partition on the netbook then try booting from the live ubuntu usb drive and use gparted to format the the ubuntu partition to NTFS, maybe then the windows system recovery will work if the drive is formated to NTFS,

---

### Post by mdebaprasad on 2011-06-06
> **Frogs Hair said:**
> This is a bit dated , but may be useful . I found many results in my search. You have to find someone with XP installed to use this. 
[http://www.techrepublic.com/article/illustrated-walk-through-creating-a-bootable-usb-flash-drive-for-windows-xp/6160062](http://www.techrepublic.com/article/illustrated-walk-through-creating-a-bootable-usb-flash-drive-for-windows-xp/6160062)
I had tried using WintoFlash and had created a supposedly bootable USB with Win Xp. But when I booted my netbook whihc is installed with Ubuntu, and no other OS, the installation process did not start. It showed some error whihc I interpretd as it is not able to recognize all the parititons existing on my netbook with only Ubuntu installed on it. Do I need to delet the paritions first? If so then how? I have to do it using only my USb drive.

---

### Post by mdebaprasad on 2011-06-06
> **gandaran said:**
> if you still got the windows recovery partition on the netbook then try booting from the live ubuntu usb drive and use gparted to format the the ubuntu partition to NTFS, maybe then the windows system recovery will work if the drive is formated to NTFS,
How do I create the live ubuntu USB drive? Do I need to download the ubuntu (the exact version I installed on my netbook) and prepare the USb drive just as I (actually my friend) had prepared it for installing Ubuntu for the first time on my netbook? Since my freiend had done it, I dont have the exact version that I have installed with me now. But I am downloading the Ubuntu 10.04 now on another computer. My friend had installed some older version of 10.04. Will the live ubuntu USB I create with the current downoadable 10.04 version be sufficient to create the live USb that is actually needed to remove the existing ubuntu?

---

### Post by gandaran on 2011-06-06
> **mdebaprasad said:**
> How do I create the live ubuntu USB drive? Do I need to download the ubuntu (the exact version I installed on my netbook) and prepare the USb drive just as I (actually my friend) had prepared it for installing Ubuntu for the first time on my netbook? Since my freiend had done it, I dont have the exact version that I have installed with me now. But I am downloading the Ubuntu 10.04 now on another computer. My friend had installed some older version of 10.04. Will the live ubuntu USB I create with the current downoadable 10.04 version be sufficient to create the live USb that is actually needed to remove the existing ubuntu?
any version should do, you just need to run live ubuntu from usb drive, then open gparted from system » administration » gparted, just be careful not to format the windows recovery partition if any, all others format into single NTFS one, backup your important data first, formating the drive deletes everything on it.

---

### Post by DogMatix on 2011-06-06
Yes it should be adequate. What gandaran mentions is to use the utility gparted on the live USB to re-format your ubuntu partition as NTFS.

EDIT: As indeed he just posted before this post. Apologies.

---

### Post by dFlyer on 2011-06-06
Just a word to the wise, next time make a clone of your system before making any changes. From what I understand it might be easier to solve your ubuntu issues than reinstall windows, but than again that is your choice.

---

### Post by mdebaprasad on 2011-06-08
> **dFlyer said:**
> Just a word to the wise, next time make a clone of your system before making any changes. From what I understand it might be easier to solve your ubuntu issues than reinstall windows, but than again that is your choice.

I would take that advice. But how do I clone my system? I dont know this. Should I ask this question in a anew thread, or the answer is brief enough that someone may post it in this thread itself?

DM

---

### Post by mdebaprasad on 2011-06-08
I thank you all for your answers. I am really overwhelmed by the very quick and helpful answers from you all. I did not expect this. I decided to try Linux after a long long time using Windows. Thats why I _removed all_ of windows and installed Linux i.e. Ubuntu on my netbook. The biggest problem I faced was I couldnt configure my internet modem (Reliance Netconnect). Since I had uninstalled windows, so I couldnt even access the internet on my netbbok so that I could search internet and ultimately configure my system.I had to use another computer to access the internet to find solutions to my problem. Since a urgent work came up, and quite obviously the other computer not being mine I had access to the internet for only about half hour a day, and the work assigned to me was piling up, so I sought help from you all. I was really hesitant to ask for help to remove Linux, from you all, who are members of a Linux forum. I expected to get sarcastic answers or rebukes. Becuase, from whatever I read ABOUT the Linux forums regarding removing this OS, it seemed to me that people here would get offended if I ask such a question. I know I have hurt some or many of you, to some extent. Because, if I were in your position, I would have been hurt by this kind of behavior. From your response, I am really grateful to you all for your patience and most importantly kindness. 

The solution I have thought of is that I would install Ubuntu over Windows, so that I can **[B]_[COLOR="red"]access Linux just like any other software inside Windows[/COLOR]_**[/B]. This way, I would continue to use linux, and also my work wont get stuck whenever I face any issues regarding configuring software or hardware. In fact, I would go ahead and suggest any one who intends to try Linux as a beginner, is to adopt this same strategy i.e. install Linux as like another software inside Windows.

Also, I would earnestly request the Linux community, to see whether the **_[COLOR="red"]configuration of the internet should be automated[/COLOR]_**, somehow, or atleast the process be reduced to something extremely extremely  extremely extremely :) simple. This will enable a user working inside Linux to acess the internet atleast, so that the user can atleast search the internet to get answers to his problem, and simultaneously try to configure his/her machine. If the internet is not accessible from the machine having the Linux, then the user has to take help of another computer to search the internet, which is not usually possible for most people. I am sure none would debate this.  

I must confess that I have learnt a lot about technical details of Linux in the last 7 days, while searching the internet for my problem. I wish to say that I did ***[COLOR="Red"]NOT[/COLOR]*** feel that the learning linux is very difficult. This is primarily because of the very active and large forums on this OS.

To sum up, I am really OVERWHELMED by the extremely helpful responses of the members here, without whose help I would not have understood some very critical issues of Linux. I will come back with more questions on Ubuntu, as I start using it, from today (from inside Windows because I am a beginner).

---

