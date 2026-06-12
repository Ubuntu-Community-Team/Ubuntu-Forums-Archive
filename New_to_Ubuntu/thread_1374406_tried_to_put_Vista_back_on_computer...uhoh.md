---
title: "tried to put Vista back on computer...uhoh"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by benny2 on 2010-01-06
Hi!
I have used ubuntu for awhile now and have had no trouble with installing the operating system on my Compaq Presario F700 laptop. As long as I use the alternate version. However, recently I tried putting Vista back on my laptop because a class I am taking we need to use Microsoft Office and we can't use just OpenOffice. Anyway I had the recovery disks and 1% of the way through on the first disk it said some kind of error and it would not continue with the install. Then my old operating system-ubuntu was all gone too. Which is okay but I wanted something on the computer. So I tried installing 9.10 with a usb drive and a cd from 2 different isos and both said during the process
"select software failed to install" or some message like that. So I continued on with the install and then I restarted everything and now it is just a shell. So I logged in and tried "startx" which I guess did nothing since no software was installed. I saw on one post someone mentioned something about using the options with F6-
 
select acpi=off
select noapic
select nolapic
 
would this work for me possibly? I don't have access to this laptop right now but I would like to try something if anyone has suggestions please can you help me?
Thank you very much!
 
Is it just that both isos are corrupt also? Just to add-I have reinstalled my operating system on my computer so many times-I just reformat the whole hard drive. I wonder could this mess anything up with my hard drive?
Thank you again!

---

### Post by JimInLakeland on 2010-01-06
I know this doesn't answer your question. Have you considered using Wine to run your Microsoft Office installation on Ubuntu?

---

### Post by benny2 on 2010-01-06
Well I have never gotten any applications to work under Wine before actually. I was thinking of re-ordering the system recovery disks from HP and then buying office for that. I have never really needed to use any windows programs before so I have not been motivated to get wine to work on my laptop. Do you know any tricks to use Wine on this type of laptop with ubuntu 9.10? Karmic has worked awesome for my graphics and for wireless. In the past with the older versions I had to compile madwifi and get the graphics driver.
Here are some specifications
**- AMD Athlon 64 X2 Dual-Core @ 1.8 GHz **
**- 160 GH HDD **
**- 1 GB RAM **
What other specs are helpful?
Thanks!

---

### Post by JKyleOKC on 2010-01-06
With that hardware you should have no problem at all running VirtualBox to create a virtual machine within Ubuntu, and then installing your Windows package in that virtual machine. Once you get Ubuntu up and running again, open up Synaptic and have it search for and then install VirtualBox. When the install finishes, you should find VirtualBox listed in the System menu (I use Xubuntu so my menu isn't the same as yours will be). Launch it and read its help files to get all the instructions on installing Windows.

You can also find lots of helpful information in the "Virtualization" forum here!

I'm currently running two different virtual machines (on different boxes), one to handle my Email since my favorite mail program runs only in Windows, and the other to handle my data recovery business (all of my clients run Windows so I have to as well in order to test the recovered data). So long as your CPU is dual core and you have at least one GB of RAM, you should not notice any degradation of Ubuntu's operation if you install the virtual machine to use only one core...

You may, however, have a problem using HP recovery disks to install Vista into a virtual machine. Many "recovery disks" actually just restore an image of the factory installation that was in a separate partition on your HD; if you've deleted that partition along the way, they don't work at all! If it's absolutely necessary to use Windows your best bet will be to buy a retail copy of it and install that. Note that many colleges offer special student versions of Windows that are much less costly than those found in computer stores; the same is true of Office.

---

### Post by benny2 on 2010-01-06
Thank you that is so helpful.  I will look into buying a school version of windows and putting it on virtually.  That sounds really good.  thank you.

---

### Post by sandyd on 2010-01-06
to be honest, office 2007 actually works really well in wine. ( i mean the main stuff, word, excel, powerpoint)

---

### Post by steveneddy on 2010-01-06
> **benny2 said:**
> Thank you that is so helpful.  I will look into buying a school version of windows and putting it on virtually.  That sounds really good.  thank you.

Yep - a VM is the way to go here.

VirtualBox is an amazing bit of software, and I use it often.

---

### Post by ronniestamps on 2010-01-06
Both solutions have worked awesome for me. I find wine to be a bit more "seamless" than virtualbox, though. Either way, there is no reason on earth to go back to vista (or any windoze version) just for Microsoft Office. Ubuntu has been a Godsend for me, even with obscure needs for school, like programming microchips or using solidworks. I converted my entire family over to Ubuntu (inlaws as well) and my service requests have dropped at least 75%. To convince them... "Every Operating System has issues, at least Ubuntu's are free of charge and viruses, take your pick".

---

