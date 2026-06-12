---
title: "HELP! System crash frequently"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by james.liang on 2008-12-05
what's the reason of it? can someboby please help me..
i've reinstalled my system, previous one is fedora8, now ubuntu8.04 instead. but both of them would crash frequently.
it seems not a real crash because the mouse can move normally, but no other action..

---

### Post by crjackson on 2008-12-05
> **james.liang said:**
> what's the reason of it? can someboby please help me..
i've reinstalled my system, previous one is fedora8, now ubuntu8.04 instead. but both of them would crash frequently.
it seems not a real crash because the mouse can move normally, but no other action..

You are not providing enough information for anyone to help you. It could be hardware, software, firmware, thermal, etc...

Complete details of activities and system specifications would be a place to start.

---

### Post by nandemonai on 2008-12-05
Odd.. could be any number of things.

I'm assuming hardware.

Could be bad RAM, HDD or maybe something Linux specific with your hardware setup.

You're really going to need to supply more information for a decent reply.

Start with processor, motherboard, hard drive information. Make / models etc.

Also if you open up a terminal and type:
```

cat /var/log/messages > ~/messages.txt
```

That will save the information to a text file in your home directory.

Open it up and copy the results here. That might help with figuring out what's going on.

Another thing to try would be doing a memtest to check your RAM. You can select memtest from the grub menu when booting up.

---

### Post by james.liang on 2008-12-05
Sorry but I'm a beginner of linux.
It will simply crash at any time when I'm using it. If there is no operation, it won't.
And do you mean the hardware informations about the system specifications you mentions?

---

### Post by james.liang on 2008-12-05
> **nandemonai said:**
> Odd.. could be any number of things.

I'm assuming hardware.

Could be bad RAM, HDD or maybe something Linux specific with your hardware setup.

You're really going to need to supply more information for a decent reply.

Start with processor, motherboard, hard drive information. Make / models etc.

Also if you open up a terminal and type:
```

cat /var/log/messages > ~/messages.txt
```

That will save the information to a text file in your home directory.

Open it up and copy the results here. That might help with figuring out what's going on.

Another thing to try would be doing a memtest to check your RAM. You can select memtest from the grub menu when booting up.

Thanks for your help. I'll check it as you say later. I do think maybe the HDD. Because there was some bad information about HDD before.

---

### Post by Diabolis on 2008-12-05
Sounds like a device is not tightly connected. Being able to move the mouse, but not to perform any actions sounds like you are not able to read anything from your hard drive. When you get a crash, is the hard drive led lighted permanently? That led is the one that has a symbol that looks like a drum.

---

### Post by james.liang on 2008-12-05
> **Diabolis said:**
> Sounds like a device is not tightly connected. Being able to move the mouse, but not to perform any actions sounds like you are not able to read anything from your hard drive. When you get a crash, is the hard drive led lighted permanently? That led is the one that has a symbol that looks like a drum.

Oh. I really forgot to take a look at the light... :o
Now I'm using windows, the problem still exist. But it's not serious. It only happen when there are lots programs running. And it will return to normal a few seconds later.

---

### Post by Diabolis on 2008-12-05
Yeah, it could be the HDD. I had a similar problem where only a few blocks of the drive were bad, but the others were fine. This could explain why the behavior is intermittent.

---

### Post by james.liang on 2008-12-05
> **Diabolis said:**
> Yeah, it could be the HDD. I had a similar problem where only a few blocks of the drive were bad, but the others were fine. This could explain why the behavior is intermittent.
Really? How did you solve your problem?

---

### Post by Diabolis on 2008-12-05
In my case most of the damaged blocks were on the beginning of the drive. So, I created an empty partition, an unusable partition, of about 7 GB in that area. That was just a work around, still the drive was slow at times. Since it was a 40 GB drive, I was already lacking room for my files and ended up buying a new one. However I can't assure you that you have the same problem.

---

### Post by james.liang on 2008-12-05
> **Diabolis said:**
> In my case most of the damaged blocks were on the beginning of the drive. So, I created an empty partition, an unusable partition, of about 7 GB in that area. That was just a work around, still the drive was slow at times. Since it was a 40 GB drive, I was already lacking room for my files and ended up buying a new one. However I can't assure you that you have the same problem.

I don't know exactly what the problem is. In fact, I really want to buy a new computer. I'm tired of hardware troubles....

---

