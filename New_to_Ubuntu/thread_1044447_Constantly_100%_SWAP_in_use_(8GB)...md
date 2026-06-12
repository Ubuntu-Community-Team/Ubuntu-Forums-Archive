---
title: "Constantly 100% SWAP in use (8GB)..?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by kramer65 on 2009-01-19
Hello,


I had a look at my system monitor the other day and I was surprised to see that 100% of my SWAP is constantly in use. I've got quite a new pc with a quad core @ 2.66 GHz, 4GB RAM, and thus 8GB of SWAP. I currently use 700MB of RAM but the full 100% of my SWAP is also in use.

Is this a mistake or is there something wrong? Should I worry?

---

### Post by billgoldberg on 2009-01-19
Swap shouldn't be used when you have free ram memory.

But I'm no expert on those things.

I do know you have way to much swap, but that shouldn't be a problem.

As long as you don't notice any slowdowns, I wouldn't worry about it.

---

### Post by tad1073 on 2009-01-19
do
```
 sudo gedit /etc/sysctl.conf
```add this line to the end
```
vm.swappiness=10
```then do
```
sudo sysctl -p
```see if that helps.

---

### Post by kramer65 on 2009-01-19
Should things go down immediately after I do the last command, or do I need to restart or something?

I did your things, but nothing happened for now..

---

### Post by scragar on 2009-01-19
Let's just check first of all if you are even running any swap partition, if you aren't then swap available is 0, so it looks like you are using it all.
```
free -g | grep swap
```
just post the output.

---

### Post by BentFX on 2009-01-19
[offtopic]
kramer65 I just answered your GIMP layers issue ([here]("http://ubuntuforums.org/showthread.php?t=1005452"))
[/offtopic]

---

### Post by kramer65 on 2009-01-19
@ scragar
I copied and pasted your code into a terminal but it didn't do anything. It didn't even give an output. It just gave me another line of the beginning: kramer@mypc:~$

@BentFX
Thanks for your answer on the layer issue. I actually "solved" it already by reinstalling ubuntu as a whole. Well, I actually went back from 8.10 to 8.04 since things were just [breaking]("http://ubuntuforums.org/showthread.php?t=1024829") for me with 8.10..

It seems however, that the more I do, the more I break.. ](*,)

---

### Post by bgerlich on 2009-01-19
Scanger made a typo, try typing in "free" in the console, if you see any swap there, type in "top" or start "System Monitor" to see which process is taking so much memory (remember to select "All processes" to see everything in the processes tab)

---

### Post by arpanaut on 2009-01-19
Maybe something to do with GIMP's cache usage... look-> [http://docs.gimp.org/en/gimp-using-setup-tile-cache.html](http://docs.gimp.org/en/gimp-using-setup-tile-cache.html)

I know on other graphics programs that I had to set up disk cache et. to get optimal performance, the defaults work well for me with GIMP so I haven't explored this on Linux... yet.

---

### Post by kramer65 on 2009-01-19
typing in "free" gives me this:

```
             total       used       free     shared    buffers     cached
Mem:       3369476    2552492     816984          0      43956    1649592
-/+ buffers/cache:     858944    2510532
Swap:         8024       8024          0
```

As you can see all is used, but I do not see anything in the system monitor using so much (firefox is the heaviest user with 220MB since I'm having about 20 tabs open..).

Does this info tell you anything more?

---

### Post by scragar on 2009-01-19
> **kramer65 said:**
> typing in "free" gives me this:

```
             total       used       free     shared    buffers     cached
Mem:       3369476    2552492     816984          0      43956    1649592
-/+ buffers/cache:     858944    2510532
Swap:         8024       8024          0
```

As you can see all is used, but I do not see anything in the system monitor using so much (firefox is the heaviest user with 220MB since I'm having about 20 tabs open..).

Does this info tell you anything more?

That's your problem, you have 8mb of swap, not 8GB.

---

### Post by bgerlich on 2009-01-19
a) Your swap is 8 MB, not GB :P

b) not all of you ram is detected by the system, you need to install the 64-bit ubuntu to use all your RAM or install the server kernel. The server kernel has PAE enabled, this is a"hack" that allows you to use more than 4gb physical memory( Ram + video ram ... etc) on a 32 bit system

---

### Post by kramer65 on 2009-01-19
I see that you are right. Pretty stupid of me.. :)

But when I now go into gparted I see that it says it has 8GiB. Have a look at the attached screenshot..

---

### Post by scragar on 2009-01-19
> **kramer65 said:**
> I see that you are right. Pretty stupid of me.. :)

But when I now go into gparted I see that it says it has 8GiB. Have a look at the attached screenshot..

Yes, as has been posted before you have got to run the 64bit or a hacked version of the 32 bit release to be able to have more than 4GB of ram available, that's why it thinks you only have 8mb/swap, because that's all it can use.

---

### Post by kramer65 on 2009-01-19
Ah like that. I just made it 8GB since I always read you have to make your SWAP double the amount of your RAM..

So since I don't have a 64 bit system I can best reduce my swap to 4 GB or is there a better solution?

---

### Post by scragar on 2009-01-19
> **kramer65 said:**
> Ah like that. I just made it 8GB since I always read you have to make your SWAP double the amount of your RAM..

So since I don't have a 64 bit system I can best reduce my swap to 4 GB or is there a better solution?

I can't see any reason to have that much ram anyway, unless you are doing some very ram intensive work(running virtual machines, or editing video maybe).

Unless you want to suspend to disk you shouldn't need swap at all.

---

### Post by kramer65 on 2009-01-19
Alright. I just followed the guidelines; double the amount of ram for your swap..

So what should I do? Reduce the swap to 4GB? Or maybe just do nothing? Is it bad how it is now?

I occasionally run XP as a virtual machine but that easily runs on the ram so there is indeed no real use for the swap..

---

### Post by scragar on 2009-01-19
The whole double your ram thing is an old guideline from when ram was more expensive and using swap was much more common. Now that is not the case.

Personally I would install the hack to enable you to use more than 4GB of ram on your system, which will unlock your swap(note that reducing your swap won't do anything, the 4GB limit is hit with your real ram, the 8MB of swap is just what's left that the system can assign).
```
sudo apt-get install linux-server linux-headers-server
```
This will install the server headers, including the patch that enables you to use more than 4GB of ram. A restart will be required.

---

### Post by kramer65 on 2009-01-20
Alright, I did that and restarted. But when I look at the system monitor I still see only 8mb of swap. When I type "free" I see the following:

```
             total       used       free     shared    buffers     cached
Mem:       4149608    3734988     414620          0       7624    3366340
-/+ buffers/cache:     361024    3788584
Swap:         8024        180       7844
```

in this you can see however that only 180 kb of my 8MB of swap is now used. I think this could also be however, because I just restarted it or something..

Any other ideas?

---

