---
title: "Problems Booting up Ubuntu 10.10"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-22
I have had a lot of problems booting up Ubuntu 10.10, which I only recently changed from 10.4. I tried out as advised to try a different boot up kernel line and managed to find one but this means that I can no longer boot up automatically. Although I am up and running the boot up does not feel all that secure as the computer makes a few ticking noises as if it is still trying to boot up. Any suggestions to solve this and please in simple terms as I am not an expert. Thanks

---

### Post by TeoBigusGeekus on 2010-11-22
```
gksu gedit /etc/default/grub
```
Change the default boot up kernel, save and then
```
sudo update-grub2
```
to make the changes permanent.
That will take care of the automatic login.

---

### Post by ian19jam on 2010-11-22
Thanks for your reply but where do I place the codes that you suggested please? Thanks

---

### Post by TeoBigusGeekus on 2010-11-22
In a terminal: Applications>Accessories>Terminal

---

### Post by ian19jam on 2010-11-22
Thanks for the advice but when I place the second code the terminal says that no such command exists. So where do I go from there? Many thanks

---

### Post by TeoBigusGeekus on 2010-11-22
Try
```
sudo update-grub
```

---

### Post by ian19jam on 2010-11-23
Thanks for your reply but it still states Command not found. Is there another code? thanks

---

### Post by TeoBigusGeekus on 2010-11-23
Can't be...
Are you sure you're typing this correctly?
Could you please copy and paste for us the exact terminal commands you put and the messages you get?

---

### Post by Jamface on 2010-11-23
Can I join in here with a boot problem which is a bit different or should I start a new thread?
Here's the problem: I have just (yesterday) installed 10.10 as dual boot with Puppy Linux on my Sony laptop PCG-FX109K. When I installed 10.10 I set login to automatic and I think I put in a password as well.   But when I try to boot now after the install I can't get past the password login sequence, whether I put in the password or not.   Ubuntu does not seem to recognise my password and keeps coming back to the login window.  How can I get round this?  I can access all the 10.10 files from Puppy Linux.

---

### Post by amjjawad on 2010-11-23
> **Jamface said:**
> Can I join in here with a boot problem which is a bit different or **should I start a new thread**?


Yes to the bold one.

---

### Post by amjjawad on 2010-11-23
> **ian19jam said:**
> I have had a lot of problems booting up Ubuntu 10.10, which I only recently changed from 10.4. I tried out as advised to try a different boot up kernel line and managed to find one but this means that I can no longer boot up automatically. Although I am up and running the boot up does not feel all that secure as the computer makes a few ticking noises as if it is still trying to boot up. Any suggestions to solve this and please in simple terms as I am not an expert. Thanks

Did you install Ubuntu using Wubi?

What kind of ticking sounds are you hearing? dose that sound come from your HDD? almost the same tick when "park" sound comes up? the sound that you hear when you shut down your PC. Is it the same?

---

### Post by ian19jam on 2010-11-23
I tried again and this is what was said on the terminal:

ziggy@ziggy-desktop:~$ gksu gedit /etc/default/grub
ziggy@ziggy-desktop:~$ sudo update-grub2
sudo: update-grub2: command not found
ziggy@ziggy-desktop:~$ 

When I did the first code an empty file came up with Grub written on it. I am mystified by it all. Not sure what to do next please?

Thanks

---

### Post by ian19jam on 2010-11-23
The ticking noise sounds at anytime when the PC is on sounding as if it wants to re boot. Not sure why?

No would not know re installing Ubuntu from WUBI. I installed it direct from the upgrade area in Update Manager.

This is upgrade to 10.10  has caused a few boot up problems and need to know in simple terms as to how I can boot up without having to choose a kernal line for it to boot up. Is it possible to have it booting up automatically once you have started the PC. Never had this problem before. Any advice please. thanks

---

### Post by amjjawad on 2010-11-23
> **ian19jam said:**
> The ticking noise sounds at anytime when the PC is on sounding as if it wants to re boot. Not sure why?

There are many sounds. You need to be more accurate. Does that sound come out from the Hard Drive itself? or the inside speaker? is it continuous? 

> 
No would not know re installing Ubuntu from WUBI. I installed it direct from the upgrade area in Update Manager.

This is upgrade to 10.10  has caused a few boot up problems and need to know in simple terms as to how I can boot up without having to choose a kernal line for it to boot up. Is it possible to have it booting up automatically once you have started the PC. Never had this problem before. Any advice please. thanks

We need more details so that we could help. We need to know the answers for few questions:

a) Are you dual booting with Windows or any other OS or this is your only OS installed?
b) Are you able to login to your desktop?
c) When you reboot your machine, what exactly do you see?
d) All what you need is to Turn your PC ON, never touch anything and Ubuntu's Desktop will load up automatically without the need to choose anything from a list. Am I right?

Thank you :)

---

### Post by ian19jam on 2010-11-23
The ticking sounds come from the hard drive. It is not continuous just decides to do this occasionally.

A) I am not dual booting with windows. I upgraded from Ubuntu 10.04
B)  Yes I can login to the desktop after I have gone down the various kernal lines and picked the one that worked. The first kernal line just freezes the bootup.
C) 
When I reboot I see the motherboard screen then the UbunTu Kerbnal lines with various numbers for booting up. I tend to click the third one down as it works. Normally it should automatically bootup from the first line automatically.
D)When I turn PC on I have to wait to choose the line for UBuntU 10.10 as mentioned in C

---

### Post by amjjawad on 2010-11-23
> **ian19jam said:**
> The ticking sounds come from the hard drive. It is not continuous just decides to do this occasionally.

You may want to start backing up your hard drive just in case of HDD failure. I lost a WD HDD 160GB - SATA when it started to make similar sound. No, the upgrade has nothing to do with that. Just to be in the safe side, try to backup your important data.


> 
A) I am not dual booting with windows. I upgraded from Ubuntu 10.04
B)  Yes I can login to the desktop after I have gone down the various kernal lines and picked the one that worked. The first kernal line just freezes the bootup.
C) 
When I reboot I see the motherboard screen then the UbunTu Kerbnal lines with various numbers for booting up. I tend to click the third one down as it works. Normally it should automatically bootup from the first line automatically.
D)When I turn PC on I have to wait to choose the line for UBuntU 10.10 as mentioned in C

As long as you can login to your desktop, there's nothing to worry about.
However, in order to achieve what you're looking for, I suggest to start reading here:

[URL="https://help.ubuntu.com/community/Grub2"]GRUB2
[/URL][GRUB2 Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602")

Please don't hesitate to ask if you're in doubt of something.

---

