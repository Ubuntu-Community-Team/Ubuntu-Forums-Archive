---
title: "Help with audio please."
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2009-01-28
Hello everyone, I would first like to start this thread of by apologizing for past threads, for which I have not clicked the "Problem Solved" or "Thanks" icons for people who have helped me. I do not visit these forums often, only when I run into a problem, and even then it is rare because often I am able to decipher the problem and fix it on my own. However I can understand why it would be important for those who do come to these forums on a regular basis, as I am sure people do not want to give help when the problem has already been solved. So with that said I will make sure to click the appropriate icons to signify when my problem has been solved, and credit to the person who has helped me. Thank you. Now... on to my problem.

I purchased the Logitech Z-5500 surround sound computer speakers a while ago, but not for my computer, I simply had them hooked up to my PlayStation 3, but they came with a wire which I did not know what it was, the inputs were Light Green, Yellow and Black. I started to wonder what these wires were today and why I could plug them into the back of my PC, after a bit of web-research, and a little help from common sense, I have concluded that they must be computer cables. 

Now I have had them plugged into my PC and PS3 for the past year and a half, but I never bothered to try and get them to work on my computer because I was convinced that it simply has no soundcard. However after thinking about it for a bit, I am starting to wonder why my computer would even have the ports for the wires, and not have a soundcard. So with that said, I am wonder dear forums, how do I found out ALL the hardware in my computer, and furthermore, how do I get them to work on my computer if I do in fact have a soundcard. Thank you very much for the help.

---

### Post by Malalo on 2009-01-28
Can you post the output of the following commands :

lspci | grep audio
cat /proc/asound/cards

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **Malalo said:**
> Can you post the output of the following commands :

lspci | grep audio
cat /proc/asound/cards

I assume you meant to put that in my terminal, which I did, and it did nothing. This is copied directly from the terminal.

```

anon@anonymous:~$ lspci | grep audio
anon@anonymous:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
anon@anonymous:~$ 

```

---

### Post by Malalo on 2009-01-28
To find out what hardware is installed, you can also start with just "lspci". I added the "| grep audio" to target to potential sound cards installed.

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **Malalo said:**
> To find out what hardware is installed, you can also start with just "lspci". I added the "| grep audio" to target to potential sound cards installed.

Do I have a soundcard? lol.
```

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev 44)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 11)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 05)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 20)
00:0b.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)

```

---

### Post by Malalo on 2009-01-28
Heh I guess not !
The last thing I can think of is that if you have audio jacks on your computer's back panel, then maybe the sound card is "on-board" (on the motherboard), but de-activated in the BIOS.
Can you check your BIOS settings ?

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **Malalo said:**
> Heh I guess not !
The last thing I can think of is that if you have audio jacks on your computer's back panel, then maybe the sound card is "on-board" (on the motherboard), but de-activated in the BIOS.
Can you check your BIOS settings ?

How do I check my BIOS settings? And how will I be able to tell you what I have enabled in there and what I don't? Please, elaborate, when I go into these BIOS (because I do know that I will have to restart my computer), what do I do when I enter the BIOS?

---

### Post by Malalo on 2009-01-28
When you boot your computer, you might get the message "Press (a certain key) to enter SETUP" or something similar. This is way before you see the "Ubuntu" splash screen. 
Most of the time, the (a certain key) is Delete. Somethimes it's F2 but I've also seen F10 or F12. This all depends on your BIOS manufacturer (depends on your motherboard's brand/model). 
When you're in setup, you should look for anything pertaining to "port settings" or "Chipset options". Then, maybe you'll find an option saying "on-board audio" that you can switch from "Disabled" to "Enabled".

Maybe if you can post the brand/model of your motherboard we could find screenshots of your BIOS setup pages...

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **Malalo said:**
> When you boot your computer, you might get the message "Press (a certain key) to enter SETUP" or something similar. This is way before you see the "Ubuntu" splash screen. 
Most of the time, the (a certain key) is Delete. Somethimes it's F2 but I've also seen F10 or F12. This all depends on your BIOS manufacturer (depends on your motherboard's brand/model). 
When you're in setup, you should look for anything pertaining to "port settings" or "Chipset options". Then, maybe you'll find an option saying "on-board audio" that you can switch from "Disabled" to "Enabled".

Maybe if you can post the brand/model of your motherboard we could find screenshots of your BIOS setup pages...

Ok, I'll go play with the BIOS, in the meantime, how do I find out what kind of motherboard I have? I'll let you know when I come back, I won't take too long.

---

### Post by Narcoleptic_Insomniac on 2009-01-28
Ok Malalo, I actually ended up restarting my computer 4 times, and after much frustration, I have decided I am incapable of accessing my BIOS. during the start up process, every one of the 4 times, the only option it gave me to enter any menu was at the very beginning, where it said "Press ESC to enter menu...", which I did, and that only gave me three options, the first, was to start up xubuntu like regular, the second was to start it up in safe mode, and the third was to start up xubuntu in some other mode, which I did not select because I didn't know what it was.

During the startup I did see the the word "BIOS" a couple of times, but I never seen any instruction telling me to press a certain key to enter the BIOS. What should I do now?

---

### Post by Malalo on 2009-01-28
When you see "Press ESC to enter menu...", that's GRUB speaking. It's the boot loader from xubuntu.
To find the motherboard's brand/model... Is your computer a "clone", is it a "brand name computer" (such as HP or Dell) ?

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **Malalo said:**
> When you see "Press ESC to enter menu...", that's GRUB speaking. It's the boot loader from xubuntu.
To find the motherboard's brand/model... Is your computer a "clone", is it a "brand name computer" (such as HP or Dell) ?

My computer is Hewlett-Packard. Sorry I took so long, I had to go make myself some lunch.

---

### Post by jeffjanzen on 2009-01-28
if your BIOS doesn't tell you which key to press to access setup, you'll have to just do simple trial and error.  restart your computer and press F2 repeatedly and see if the BIOS comes up. if you press it too many times, your computer will beep, and then you can stop, wait a couple seconds, and then try pressing it some more.  if the grub menu comes up again, that means F2 is not the key you want.  just reset and try again with F10, then try it with F12, then try it with Delete. (these are common bios setup access keys.)

if none of those work, you should try googling your hp model number along with "bios" "access" or something like that.

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **jeffjanzen said:**
> if your BIOS doesn't tell you which key to press to access setup, you'll have to just do simple trial and error.  restart your computer and press F2 repeatedly and see if the BIOS comes up. if you press it too many times, your computer will beep, and then you can stop, wait a couple seconds, and then try pressing it some more.  if the grub menu comes up again, that means F2 is not the key you want.  just reset and try again with F10, then try it with F12, then try it with Delete. (these are common bios setup access keys.)

if none of those work, you should try googling your hp model number along with "bios" "access" or something like that.

When do I press it though? At the first screen that comes up before anything else does? On the same screen as the grub menu thing is?

---

### Post by jeffjanzen on 2009-01-28
yes, at the first screen *should *work, but i'd recommend just restarting and pressing the key over and over again because it's hard to say exactly when the BIOS starts "listening" for that keypress, if you know what i mean.

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **jeffjanzen said:**
> yes, at the first screen *should *work, but i'd recommend just restarting and pressing the key over and over again because it's hard to say exactly when the BIOS starts "listening" for that keypress, if you know what i mean.

Yes I understand. I found how to get into my BIOS, it was F1 or F2, anyway I was looking around in there, I didn't change anything, just looking for anything that would relate to audio, but since I don't really know what I was looking for, I found nothing. But I did learn a few things about my computer.

I am running a Pentium III, my computer is 800Mhz/1330Mhz,
and in Memory Bank 0 I have 128MB of SDRAM and in Memory Bank 1 I have 64MB of SDRAM, does that mean I only have 192MB of ram?

Anyway, now that we have discovered how to get into BIOS, what should I be looking for?

---

### Post by jeffjanzen on 2009-01-28
look for anything that says "sound" or "audio", and set it to "on" or "enabled".

yes, it sounds like you have 192 MB of RAM.

---

### Post by Narcoleptic_Insomniac on 2009-01-28
> **jeffjanzen said:**
> look for anything that says "sound" or "audio", and set it to "on" or "enabled".

yes, it sounds like you have 192 MB of RAM.

Nothing within any of the BIOS menus says anything about "Sound" or "Audio".

Does that mean I have no sound card?

---

### Post by Narcoleptic_Insomniac on 2009-01-28
Please Help.

---

### Post by Narcoleptic_Insomniac on 2009-01-29
Sorry to bump, but I still need help with this and I didn't think you guys would like me to make a whole new thread on it.

---

### Post by Malalo on 2009-01-29
Hello again Narcoleptic.

You mentionned that your computer is a Hewlett-Packard. Do you have a model name or number ?
Perhaps searching in Google if there are screenshots of your BIOS setup pages...

---

