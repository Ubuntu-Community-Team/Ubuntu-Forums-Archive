---
title: "Nothing will boot!"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by parabola87 on 2010-03-18
Ok my problem is quite long winded so apologies in advance! I have a brand new computer with no OS so I (stupidly) installed Ubuntu 9.10 then tried to install XP alongside it. I realise now XP should have gone on first! Anyway, I have been tearing my hair out for days trying to find a way for my XP cd to be recognised and after many an hour trawling through forums, trying to use Gparted (it wouldn't boot - and yup I mounted the iso ok) I found out that I should just edit the boot order in BIOS to boot from cd rom first. I should mention I'm a complete newbie at all this, only ever having used XP for basic stuff. I couldn't get to my BIOS settings so I go onto the ubuntu IRC for help. I was told there should be a screen when I start up my computer that tells me which key to press to enter BIOS, which sounded familiar but everytime I reboot my computer, there are three screens only, the first has details of my graphics card, the second an image with my motherboard model and then a blank screen before the login page. Nowhere does it say anything about pressing any key. Someone in the chatroom suggeseted several things to press, I kept trying them all and then something strange happened, a screen came up which looked like terminal, and I was able to type commands. I tried to exit the screen but there was no way so in the end I had to switch off the computer. Now, nothing will boot, not even a live cd. It just hangs on this message 

The GNU Grub version 1.97 beta4

Ubuntu, linux 2.6.31-14-generic
Ubuntu, linux 2.6.31.14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

and it won't let me select an option and nothing happens when I hit enter, although the top one is selected, as if my keyboard isn't being recognised. I have no idea what to do, I even made a new bootable flash drive with 9.10 on it but it just goes straight to that screen. Any help would be so greatly appreciated, and thank you so much for taking the time to read this!

---

### Post by Ozymandias_117 on 2010-03-18
Ok, first question, what brand of computer is it? This will help us know what button to tell you to press =P. Two, do you have another keyboard you can try? Or can you try that keyboard on another computer? It almost sounds like the keyboard is broken.

---

### Post by phidia on 2010-03-18
Different manufactuers use different bios.  

If you were in linux (cli )command line it's possible to wreck some havoc, but since your computer is showing grub it seems fixable.

There is a pretty good bios guide [here]("http://www.tomshardware.com/reviews/bios-beginners,1126.html") check it out and see if you can determine what bios your computer uses. Once you have that info you can push/hold down the correct key combination to get to bios and adjust the boot order.

---

### Post by phidia on 2010-03-18
> when I hit enter, although the top one is selected, as if my keyboard isn't being recognised.

The enter key is a key on your keyboard-it sounds to me like you may have installed ubuntu without selecting the correct keyboard for your computer-which might be why it's not responding-but then again how were you trying to select the grub menu options? Really be specific in all the info you provide because that will help others to help you.

---

### Post by parabola87 on 2010-03-18
> **Ozymandias_117 said:**
> Ok, first question, what brand of computer  is it? This will help us know what button to tell you to press =P. Two,  do you have another keyboard you can try? Or can you try that keyboard  on another computer? It almost sounds like the keyboard is  broken.

I tested the keyboard on my laptop and it's working. My pc is custom  built with an AMD Phenom II x4 965 processor and MS[FONT=Times New Roman]I [/FONT]**770-C45 motherboard. I think with AMD it's F1 to bring up the BIOS but I tried this and several other keys but none of them worked.

Phidia - the keyboard worked ok before I messed things up trying to open the BIOS. Now when I try to boot all I see is the grub menu and I am unable to interact with it (the top option is already highlighted so tried to press enter) and the instructions specify to use the arrow keys and hit enter to select, but no buttons seem to be working at all.

Thanks for your responses so far :)

---

### Post by echo.whoami on 2010-03-19
from what i know you, when you start your pc the keys that should get you in bios is F1,F2 or DELETE. try to press them repeatedly to get in bios. Then there should be a tab with the boot settings and change your settings so that the 1st boot is the cd drive 

There is also the ESC or F11 keys that should come up with a screen from which you choose device to boot. 

Are you trying to install ubuntu and windows xp to the same drive?

---

### Post by Ozymandias_117 on 2010-03-19
> **parabola87 said:**
> I tested the keyboard on my laptop and it's working. My pc is custom  built with an AMD Phenom II x4 965 processor and MS[FONT=Times New Roman]I [/FONT]**770-C45 motherboard. I think with AMD it's F1 to bring up the BIOS but I tried this and several other keys but none of them worked.

Phidia - the keyboard worked ok before I messed things up trying to open the BIOS. Now when I try to boot all I see is the grub menu and I am unable to interact with it (the top option is already highlighted so tried to press enter) and the instructions specify to use the arrow keys and hit enter to select, but no buttons seem to be working at all.

Thanks for your responses so far :)

1. The button is based on the Mobo, not the processor. On an MSI 770-C45 *Delete* will take you to BIOS. You will have to press delete pretty much as soon as you push the power button, if you see GRUB, it's gone too far.

---

### Post by phidia on 2010-03-19
> **Ozymandias_117 said:**
> 1. The button is based on the Mobo, not the processor. On an MSI 770-C45 *Delete* will take you to BIOS. You will have to press delete pretty much as soon as you push the power button, if you see GRUB, it's gone too far.

Yeah I agree here with Oz, and you need to hold down the delete key don't just jab and release it-hold the delete key down until you see the bios screen.

---

### Post by parabola87 on 2010-03-19
Success! When I was stuck on the grub screen without being able to use the keyboard I tried switching the keyboard from the ps2 connector to a usb slot (I have an adapter) and it worked! The keyboard worked fine in that connector after login and not before, and I had no idea which explained why I couldn't access BIOS before. So I just ran the recovery option from the grub screen and ubuntu is working fine now, it turned out that F11 took me to the BIOS screen I needed in the end.

I still have a problem in that after I installed XP it tells me "Disk error press any key to restart" but that's another issue and I'll look up how to solve that.

Thanks everyone for your time and advice! :)

---

### Post by oldfred on 2010-03-19
There is a BIOS setting for the keyboard usb or ps/2 that seems to be ignored in Ubuntu but grub strictly follows it. I had the same problem when I installed a new motherboard about a year ago & solved it the same way you did with the adapter.

You need to create a primary NTFS partition. The XP install will not see the ext3/4  Ubuntu partitions and needs to see a blank disk or NTFS partition.

---

### Post by parabola87 on 2010-03-19
> **oldfred said:**
>  You need to create a primary NTFS partition. The XP install will not see the ext3/4  Ubuntu partitions and needs to see a blank disk or NTFS partition.

When I first installed ubuntu I created 3 partitions and when I came to install XP I converted one of them to NTFS, and after installing that's where I got the disc error. What do you mean by "primary", do I need to do anything different?

---

### Post by parabola87 on 2010-03-19
Ooh nevermind, I just tried the xp installation on the third partition and it worked :D

---

### Post by phidia on 2010-03-19
See > man grub in terminal but I think you need to do grub-update (sudo grub-update) to get xp to boot-if it installed correctly.

---

### Post by parabola87 on 2010-03-19
Everything is working perfectly now, thank you so much everyone! :D

---

