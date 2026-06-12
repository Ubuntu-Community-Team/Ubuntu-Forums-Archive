---
title: "After new kernel, my wireless has ceased to work."
date: 2010-07-24
forum: New to Ubuntu
---

### Post by azhh on 2010-07-24
Before I begin this tale of tragedy and woe, I should probably just let everyone know up front that I am almost completely new to Linux, so when you're potentially giving me a solution to my plight, it isn't safe to assume I know the basics and can fill in the blanks, although I hope to become proficient enough to accomplish this and more in the future.

Now, srs business:

I just got done with the ordeal of installing Lucid x64 on my Toshiba Satellite L505D. I spent a couple days finding a way to edit the Grub config and turn ACPI off so I could install a new kernel which would provide the ACPI support, enabling me to use that functionality. 

After following the tutorial successfully (Yessssss.), I was warned that, in all likelihood, I would lose my wireless drivers. "No biggie," I thought. "I've installed plenty of drivers before on Windows."

Haaaaaaaaa. That's the definition of a rude awakening. Anyway, I searched Realtek's site for the Linux drivers for the 8187se, the L505D's onboard wireless card, only to find that the single variant of those particular drivers available is Windows alone. There are other wireless cards, like the 8192se, but I have no idea whether or not those drivers would jive with the card in my laptop.

I am incredibly confused and in way over my head at this point in time. I would greatly appreciate some help, especially some steps that could guide me through the installation process. I did briefly glance over the forums and didn't find anything that was close enough to my situation to be useful, but it is two in the morning, and so those things tend to slip by, as I'm sure you all know quite well. If I've missed something, please feel free to reprimand me and point me in the right direction. :)

Thanks in advance for any advice you may have for me. I'm looking forward to it-- this community looks to be one of, if not *the* most helpful on the internet.

**TL;DR:**
I used [this tutorial](http://ubuntuforums.org/showthread.php?t=1503491) to upgrade to the new kernel (2.6.35-rc1) with the copy_dsdt patch installed. Before, I was running stock on a clean install.

The problem is with my laptop's BIOS: it screws with the DSDT frames, and so depending on which type of Toshiba laptop you have, it can disable different parts of the functionality. In my case, it was the laptop's ACPI functionality (battery life, volume wheel, power management, etc.)

The wireless stopped working after the new kernel was installed. It is onboard.

I am running 10.04 (or Lucid, like I'd said before the tl;dr.) It is 64-bit.

I have no wireless drivers on my system at the moment. The issue isn't troubleshooting, it's installation.

I don't know if the stock kernel is still on my machine or if the tutorial I followed overwrote it. Even if I did know whether it was on my machine or not, I couldn't boot into it because I have no idea how.

Alright, I think that answers most everyone's questions.

---

### Post by mapes12 on 2010-07-24
You have obviously had to upgrade your kernel for functionality reasons but I'm not sure I fully understand why. Wifi can be a problem with Linux. I gather the main reason is lack of support from manufacturers providing access to driver code. Googling for ubuntu links for support for your wifi chipset may help. If all else fails there is a utility called ndiswrapper that you can install then use a windoze driver for the wifi adapter. There are mixed reviews of ndiswrapper. Personally, it was a pain in the butt for me but others have posted success stories.

Here's some links that may help:-

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29|%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)


Welcome to the Ubu community.

Mark

---

### Post by lkraemer on 2010-07-24
First of all, NO MIXING & MATCHING of METHODS. You obviously used
some guide to install the drivers and get it working until the Kernel
upgrade.  What is the location of that guide?

After all, we can't see what you did two weeks ago......and don't have
a clue as to what you did yesterday........

What is the Ubuntu Version? 8.04x, 8.10, 9.04, 9.10, 10.04, ????
32 bit or 64 Bit? .....Yes, it makes a difference!...Depending....
Laptop or Desktop?
USB Wifi Dongle or onboard Wifi?
Are you using the Windows Drivers and Ndiswrapper? Or how long has it
worked? Maybe never? Using Backports? STA? Madwifi?
If you are unsure answer all you can and post the output of the commands
below.

First we need to know what hardware your Laptop/Desktop has installed.

Just use "copy & paste" for the commands ONE AT A TIME!!!!!.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.10, or 9.04 use:
cat /etc/modprobe.d/blacklist)

If you connect via Ethernet cable, SYSTEM -> ADMINISTRATION -> UPDATE MANAGER and then try connecting the Wifi it most likely will work.


Pick one method and stick with it. Don't mix-n-match.

Your options that can be used, **depending on what hardware you have**:
1. Ndiswrapper and a Windows Driver (32 Bit)....??????.inf & sys
Your M$ Windows experience should be used to locate the proper driver....
2. Madwifi Drivers
(you will need to install.....build-essential & headers file.......meaning you need to download & install)
3. Drivers provided by Version 10.04
4. Broadcom Drivers w/Firmware

So, post all the info you can.......from the above....

lk

---

### Post by cloyd on 2010-07-24
A couple other questions that are relevant to the discussion:
What kernel did you have previously?
What is the new kernel?
Is your previous kernel still on your machine?
        if so, can you boot to your old kernel and use your wireless?

---

### Post by azhh on 2010-07-25
Alright, it seems like I missed some info in my OP. I'll add it at the bottom in a tl;dr section. Sorry about that, guys (and sorry about the wait! Work sucks.)

I'm going to try lkraemer's suggestion of running the Update Manager first and see if it solves anything.

---

