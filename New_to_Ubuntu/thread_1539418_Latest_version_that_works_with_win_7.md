---
title: "Latest version that works with win 7"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by DrGood on 2010-07-26
I have tried to set up a dual boot system with Windows 7 installed first then loading Ubuntu 10.04. this does not give me an option to boot to windows. What is the latest version of Ubuntu that plays nice with Win 7 or how do I install 10.04 so it gives me the option to boot either it or Win 7? Thanks for your help.

---

### Post by Krabby.Linux on 2010-07-26
10.04 Lucid works perfectly. You will have to configure GRUB to make sure it knows that there is a Windows 7 on your computer.

---

### Post by -kg- on 2010-07-26
That doesn't sound right to me.  The Ubuntu installer should have automatically detected your Windows 7 installation and put in a selection in the boot menu.

Try opening the terminal window and running the following command (you can copy and paste this in the terminal):

```
sudo update-grub
```

Then reboot and see what you have.

---

### Post by DrGood on 2010-07-28
> **Krabby.Linux said:**
> 10.04 Lucid works perfectly. You will have to configure GRUB to make sure it knows that there is a Windows 7 on your computer.

I've tried that but GRUB does not seem to allow for adding another OS. Can you tell me how to update GRUB ( sudo update-grub does not work). It still doe snot find Win 7. Could the problem be that I have each OS setup on separate hard drives?

Thanks for your help.

---

### Post by DrGood on 2010-07-28
> **-kg- said:**
> That doesn't sound right to me.  The Ubuntu installer should have automatically detected your Windows 7 installation and put in a selection in the boot menu.

Try opening the terminal window and running the following command (you can copy and paste this in the terminal):

```
sudo update-grub
```Then reboot and see what you have.

sudo update-grub does not work. Any other suggestions would be appreciated. Thanks.

---

### Post by sandyd on 2010-07-28
did you install all the updates? there was an early bug that caused some operating systems to be not detected

---

### Post by sandyd on 2010-07-28
and can you post the output of```
sudo fdisk -l
```

---

### Post by cowan on 2010-07-28
This works great for me, never any problem.

Do you have "Startup Manager"?

That lets you choose whatever is in the grub menu.

---

### Post by beew on 2010-07-28
Check out [http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html") especially 009 and 010. 

There are some special considerations during the partition step for windows 7 which you don't need to worry about when setting up dual boot with Vista or XP.

A partial quote

> Windows 7 and Windows Vista are both different from all other operating systems by the fact that the first partition begins at sector 2048 of the hard disk.

Windows 7 is different from Windows Vista and earlier versions of Windows in that it installs in two partitions, a 200 MiB 'boot' partition contains the boot loader files, and the main 'system' partition contains the rest of the operating system and the user's files.


But why not just get rid of Windows 7 and go all the way Ubuntu? :) Hate that glossy Windows look.

---

