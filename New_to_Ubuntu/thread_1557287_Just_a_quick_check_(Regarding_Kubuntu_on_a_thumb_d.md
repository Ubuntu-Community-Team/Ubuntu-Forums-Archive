---
title: "Just a quick check (Regarding Kubuntu on a thumb drive)"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by DM was on fire! on 2010-08-20
I have a 4gb (I'm going to dedicated 3gb of it to Kubuntu) thumb drive that I've been experimenting with various Linux distributions on. Right now it's a LiveUSB with Linux Mint 9 KDE, before that was KDPup (PuppyLinux with KDE 3.5). I want to make sure that if I go through the Install Ubuntu thing that I won't risk installing it onto my hard drive. It might sound silly, but I really just want to make sure I'm not risking anything.
If it's anything like Xfce's installation proccess, I'm good. I already familiarised myself with it. I would hope or think it is since a lot of people have multiple hard drives, but I just want to make sure.

Sorry if I'm sounding a little...mm, what's the word I'm looking for. Square? I'd just hate to lose sda1 because I was experimenting.

---

### Post by snowpine on 2010-08-20
You will need to be careful in two places: First, during the Partitioner step, you need to choose wiseley! Secondly, on the final screen, you need to choose Advanced and install the GRUB bootloader to the correct drive. Failure on either of these steps will potentially affect your internal hard drive. 

The safest option, and I have done this many times, is to simply physically disconnect your internal hard drive. This is the fool-proof method to avoid accidentally affecting sda1.

ps 3gb sounds a bit small, I would recommend an 8gb drive at least. You might also want to skip installing a swap partition.

---

### Post by DM was on fire! on 2010-08-20
It sounds like LinuxMint installation then. I forgot to install the boot loader the first time and all I got was a black screen. Then it dawned on me. Then I hit my head against the desk for being such an idiot. 

8gb. That figures. That's actually what my PuppyLinux (which is the thumb drive I typically use for my Linux needs), but I just reinstalled and really can't be bothered to transfer everything. :c Maybe in a little bit I'll do it. 

You wouldn't happen to know where I can find a screenshot of the partitioner setup, would you? That'd probably calm my nerves a lot more. XD

Thank you for your help btw. <3

---

