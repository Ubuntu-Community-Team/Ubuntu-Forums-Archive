---
title: "Lost our windoz os"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by captgadget on 2009-09-19
and of course no disk. How can we get our windoz os reinstalled of the disk on the computer?

---

### Post by NoaHall on 2009-09-19
Buy a legal copy of disk.

---

### Post by captgadget on 2009-09-19
the os is already on a hard drive partition. But how do we access that partition to reinstall on a Dell Dimension 4600?

---

### Post by SuperSonic4 on 2009-09-19
Be glad it's gone

---

### Post by donkyhotay on 2009-09-19
You're not going to get much help installing windows on a *linux* discussion forum. I would recommend either posting this question on a dell forum or look into installing a linux distribution like ubuntu which is what this forum is for.

---

### Post by captgadget on 2009-09-19
sorry I bothered so many. This is usually a helpful forum.

---

### Post by laurielegit on 2009-09-19
> **captgadget said:**
> the os is already on a hard drive partition. But how do we access that partition to reinstall on a Dell Dimension 4600?

Well, you could try editing /boot/grub/menu.lst, and adding this to the bottom
```

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

```

But that might be difficult in the plural

---

### Post by SuperSonic4 on 2009-09-19
> **laurielegit said:**
> Well, you could try editing /boot/grub/menu.lst, and adding this to the bottom
```

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

```

But that might be difficult in the plural

I was thinking about editing grub but I got the impression that the windows bootloader itself was broken so it wouldn't chain

---

### Post by laurielegit on 2009-09-19
> **SuperSonic4 said:**
> I was thinking about editing grub but I got the impression that the windows bootloader itself was broken so it wouldn't chain

Ah well, we tried.

---

### Post by SuperSonic4 on 2009-09-19
There is no reason why the OP couldn't try. As long as the ubuntu specs are left well alone it should still boot.

If you [the OP] wants to try it I recommend backing up the list ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list.bak
```

Then you can restore froma  live cd if something goes wrong

---

### Post by donkyhotay on 2009-09-19
> **captgadget said:**
> sorry I bothered so many. This is usually a helpful forum.

It's not so much an issue of bothering, as much as you're asking the wrong people. It's kind of like taking your car to a motorcycle specialist. He may be able to figure it out for you but it's not his specialty and will probably recommend you get a motorcycle. Same type of issue posting windows questions on this forum.

//edit: Also no mention was made of this computer being dual-booted. If this is true be aware recovery partitions generally don't work well with dual-boots and you can't usually get into them with a dual boot and if you can they almost always wipe out any linux partitions.

---

### Post by shashwat on 2009-09-19
Just go to Applications>add/remove application and install from the KGrubeditor:KS.Its a gui app which helps you edit your grub boot loader.
I hope it helps :)

---

### Post by CaptainMark on 2009-09-19
dont all dells have the option of holding f10 or f11 or something and reformatting the whole harddrive back to factory setting?? or is that hps?? they both suck anyway, custom builds all the way. Sorry if people get upset by that, i dont like big money grabbing corporations.

---

### Post by donkyhotay on 2009-09-19
> **CaptainMark said:**
> dont all dells have the option of holding f10 or f11 or something and reformatting the whole harddrive back to factory setting?? 

Thats the recovery partition I was talking about, I know HP does this and I'm pretty certain dell does as well. Unfortunately they aren't designed for dual-booting linux and often fail after installing GRUB. Even if they don't they generally wipe the entire system and remove all partitions except for the recovery partitions and you lose any linux distro that may have been installed.

---

### Post by NoaHall on 2009-09-19
I agree, I hate computers made by anyone but the user using it.

---

### Post by donkyhotay on 2009-09-19
> **NoaHall said:**
> I agree, I hate computers made by anyone but the user using it.

IMHO the problem is with windows rather then how the computer was made. If windows wasn't an issue then you can freely burn a install DVD and install it without any worries. I buy computers but I buy from manufacturers that are willing to ship without an OS so I can install ubuntu on it. If you buy a computer with windows, you are paying extra for the proprietary software and have to perform the sacred rain dance every day and never forget the secret handshake to keep it working.

---

### Post by NoaHall on 2009-09-19
Most big companies charge you for it anyway, regardless of whether there's a OS installed.

---

### Post by VastOne on 2009-09-19
> **captgadget said:**
> and of course no disk. How can we get our windoz os reinstalled of the disk on the computer?

If it is Vista, try this site


[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Good Luck

---

### Post by donkyhotay on 2009-09-19
> **NoaHall said:**
> Most big companies charge you for it anyway, regardless of whether there's a OS installed.

Thats why I don't buy from the "big" big companies. There are "small" big companies that are linux-friendly where you can save a few bucks.

---

### Post by SuperSonic4 on 2009-09-19
> **NoaHall said:**
> Most big companies charge you for it anyway, regardless of whether there's a OS installed.

That's why I build my pc myself :p

---

### Post by VastOne on 2009-09-19
> **SuperSonic4 said:**
> That's why I build my pc myself :p

Same here....But for those non converts that I have to support any tools and/or input are helpful.  As the OP pointed out, this generally a forum that helps all kinds...I found tools here for MS crap that MS is scared to death of....

:twisted:

---

### Post by NoaHall on 2009-09-19
Glad so many of you can see my point :)
Revolution! Hehe.

---

### Post by yanceypd on 2009-09-19
Visit other discussions Tutorial and Tips.

---

### Post by captgadget on 2009-09-21
I was trying to help a friend. I installed Ubuntu 9.04. I was trying to ween him off windoz but it probably won't happen now. The only way I could get it to install was using side by side which I did, but it wiped out the XP on his computer. His original HD was divided into 2 partitions with the system files on the second hd and so I was trying to figure out how to access that HD to reinstall XP. Luckly we found his disk and was able to do the install. The sad thing is I wiped out all his music and photos and he had no backups. That was my fault I guess because I should've have made the backups. It worked flawlessly on my laptop except I was able to partition my HD. That's all I was trying to do here. Thanks to all of you who offered cordial replies. I still enjoy using this forum and find it very useful and most of the time very friendly.

---

### Post by Enigmapond on 2009-09-21
Count your blessings... Even Windoze knows when it's not wanted..:)

---

### Post by MC707 on 2009-09-21
The thing is, many people here don't help you because they help people with problems regarding Linux. Why don't you try vista forums or somethin?

---

