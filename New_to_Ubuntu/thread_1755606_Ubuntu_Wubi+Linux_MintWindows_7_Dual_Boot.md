---
title: "Ubuntu Wubi+Linux Mint/Windows 7 Dual Boot?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by johnwillyums on 2011-05-11
Hi folks,

I'm currently running a dual boot with Windows 7x64 on one HDD and Linux Mintx64 on another.
My boot is Windows Boot Manager and defaults to Windows unless I choose Mint.
I'm pretty much a novice with Linux so please bear with me.

I've become intrigued about the "controversial" Unity desktop and would like to try Ubuntu 11.04 to see what it's like.
My initial though is to try it with Wubi.

So, will this be in any way problematic regarding my dual boot and boot situation in general? Will it mess up my current dual boot?

Thanks in advance, John:)

---

### Post by Rubi1200 on 2011-05-11
Are you changing the boot device priority in BIOS to boot the second drive with Mint on it?

There shouldn't be any issues as far as booting is concerned. Wubi uses the Windows bootloader, so when you start you will see the entry for Windows and Ubuntu and you can choose from there.

As far as the ability to run Unity, see here:
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)

---

### Post by johnwillyums on 2011-05-11
I used EasyBCD through Windows to give me Windows Boot manager as I found I couldn't accept the windows service pack when booting through GRUB

If I install Ubuntu 11.04 using Wubi I'm assuming that it installs within Windows.

In that case will I have a boot choice consisting of Windows 7 (default), Linux Mint and then Ubuntu?

Thanks for your help, John:)

---

### Post by Rubi1200 on 2011-05-11
I don't know enough about EasyBCD to answer the question with 100% certainty. However, from what you have described of your setup it shouldn't  be a problem.

 Wubi should add another entry to the Windows Boot Manager and then you can choose it as you have been doing until now.

---

