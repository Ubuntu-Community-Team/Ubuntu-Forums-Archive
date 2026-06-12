---
title: "Installation Help?"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by AKTanOz on 2011-03-12
I am completely new to ubuntu 10.10 or just linux. I am using windows xp on this computer i installed Ubuntu 10.10 to. I am using two sata drives (first one 150gb with xp and separate one with ubuntu 500gb [had 3 partitions with fake xp which i formatted before]). 

At first the installation process went smoothly and I used advance partition to redo the whole drive. (I did this with the xp 150gb unplugged). In the last step when it was loading it came with error that partition thing work.
I pressed ignore (possibly stupidly) and then restarted it. With only the one drive plugged in Ubuntu booted up and then said /home or /boot (or both) could not be found. [I didn't write it down (possibly stupidly).

Note: I was under pressure and was rushed (my sister really wanted to play sims 3).
So it was unfinished I unplugged the hard drive and plugged in other for my sister to play sims in the morning. Next day when I come back from work I tried it again (switching drives) and it came to grub I pressed first one linux normal blah blah. I quickly looked around on the system and the partitions seemed to be there. like the /home and /boot stuff was there (i was rushed this day as well).

I also tried before with both drives xp and ubuntu and xp booted up without any grub stuff.

Question 1: Did I do anything wrong?
2: Am I an idiot?
3: How do I get both drives running and grub up first. ( Take in mind am I nearly completely new to linux).
4: how do i get back on advanced partition thing thing?
5. Do you need any pc specs of mine or anything else to help answer those?
Edit: 6: By number 4 I meant: How to I resize/change the partitions, check them, and which partitions and so on are need for dual booting or whatever

---

### Post by PunkLV on 2011-03-12
```
cat /media/%alphanumeric%/boot/grub/grub.cfg
cat /media/%alphanumeric%/etc/default/grub
sudo fdisk -l
```
Post these with both HDDs connected and mounted from LiveCD.
**%alphanumeric%** - when you will try to access any storage device from *Places* menu, it will mount in /media and will be given a name. Similar to 729CB48898874487D
Someone will help you, I'm off to bed.

---

### Post by AKTanOz on 2011-03-12
Oh ok thx for your post I dont completely understand it but I will save that code

---

### Post by AKTanOz on 2011-03-12
Anyone else there?

---

### Post by milindo on 2011-03-12
> **AKTanOz said:**
> Anyone else there?
Does it work?

---

### Post by Daveth on 2011-03-12
what he wants you to do,(he assumes you know), is to put those commands into a terminal. You can find the terminal at Applications/Accessories/terminal. Launch that and then copy and paste his commands in, one at a time. For each of the terminal outputs, paste it back into your next message and hopefully the answer will be revealed!

---

### Post by AKTanOz on 2011-03-12
Thanks for confirming that I was guessing that but I just didn't want to stuff anything up.
I will try that :)

---

### Post by PunkLV on 2011-03-12
Sorry for that post. Was not sober enough. 
Please post any results/status of your installation.

---

### Post by AKTanOz on 2011-03-17
Hi thankyou for your help It turned out that I didn't need your code (even though it may have worked).
Now what I did to fix my problem I did put ut both drives like you said but i tried reinstalling it with live boot disk. It seems tht wheb you install it with both drives the installes grub 2 automatically adds it. I made my
new partitions, it was 20gb /, 2gb swap (even though i dont need it i got 4gb RAM lol) , 150gb /usr/local for programs and the rest  328gb for /home.
It all worked well but i came up with message /usr/local not found but it turnes out it was there (dunni why that error message was there)

I would think that the installation was successfull.
Sorry if my spelling is bad im using my IPod touch.

Extra note for people installing 10.10: Make sure your first username doesn't contain uppercase letters, because it wont work. It willsay something like "ready when you are"
Thx for your time :)

---

### Post by grahammechanical on 2011-03-17
Regarding your second question,

> 2: Am I an idiot?

Questions like that are very tempting. Somewhere on this forum is a thread called "What is the most stupid thing you have ever done in Linux." Or something like that. We all do stupid things sometimes.

Welcome to the Ubuntu community.

Regards.

---

### Post by AKTanOz on 2011-03-20
Heh thanks this is a good place to gain knowledge and seek for help as well as help others and actively
engage in threads.

---

