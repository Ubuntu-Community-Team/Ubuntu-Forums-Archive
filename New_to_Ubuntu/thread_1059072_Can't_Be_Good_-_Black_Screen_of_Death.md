---
title: "Can't Be Good - Black Screen of Death"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Teasdale on 2009-02-03
Our second computer (running Ubuntu 7.10) has been giving us problems on and off. We replaced the hard drive and that seemed to help, but the past few days, it's been logging off user suddenly or just rebooting.

This morning, after being left on all night, the screen was totally black. The mouse cursor would move around on a blank black screen.

I restarted it, and the Ubuntu screen got about halfway done booting, and it switched to a black screen with lots of text. Here's just some from the last bit of it:

/dev/hda5: UNEXPECTED CONSISTENCY; run fsck manually
fsck died with exit statut 4
The root file system is currently mounted in read-only mode
bash: command not found
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: dircolors: command not found
bash: The: command not found
root@arda:~#

I tried running in recovery mode. And now it's doing a Memtest86, it's a blue screen and something is being checked. It's at 26 percent now, and looks like it will take another 20 minutes.

It just popped up with this in red:
tst: 4
Pass: 0
failing address: 00032397f50  -803.4MB
Good: 5d83af58
Bad: 5d83ae58
Err-Bits: 00000100
Count: 5

Is this computer dead? Is there any way to retrieve a few files from it? Would reinstalling Ubuntu get it running again?

---

### Post by rybaxs on 2009-02-03
hahaha.. what version of Ubuntu do you have?
try to use the generic mode. at the grub..

did you update your OS?

---

### Post by rybaxs on 2009-02-03
check your logs? what is the last command do you enter?

```
The root file system is currently mounted in read-only mode
```

in the Memtest86, does your memory works perfectly? if not.. well the problem is your memory.

---

### Post by Teasdale on 2009-02-03
> **rybaxs said:**
> what version of Ubuntu do you have?
try to use the generic mode. at the grub..

did you update your OS?

Ubuntu 7.10, and it was last updated a week ago.

I tried generic mode, and it didn't get any farther in the boot process.

---

### Post by Teasdale on 2009-02-03
> **rybaxs said:**
> check your logs? what is the last command do you enter?


Check my logs?? I didn't enter any commands in the start-up process.

> **rybaxs said:**
> 
in the Memtest86, does your memory works perfectly? if not.. well the problem is your memory.

I added an error it found to my original post. It's at 58 percent and has so far found just the one error.

So, if the memory is bad, is that fixable?

---

### Post by icanfly0307 on 2009-02-03
> **Teasdale said:**
> Our second computer (running Ubuntu 7.10) has been giving us problems on and off. We replaced the hard drive and that seemed to help, but the past few days, it's been logging off user suddenly or just rebooting.

This morning, after being left on all night, the screen was totally black. The mouse cursor would move around on a blank black screen.

I restarted it, and the Ubuntu screen got about halfway done booting, and it switched to a black screen with lots of text. Here's just some from the last bit of it:

/dev/hda5: UNEXPECTED CONSISTENCY; run fsck manually
fsck died with exit statut 4
The root file system is currently mounted in read-only mode
bash: command not found
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: dircolors: command not found
bash: The: command not found
root@arda:~#

Once you get dropped to "root@arda:`#", type fsck. This should fix your UNEXPECTED CONSISTENCY problem.

> **Teasdale said:**
> I tried running in recovery mode. And now it's doing a Memtest86, it's a blue screen and something is being checked. It's at 26 percent now, and looks like it will take another 20 minutes.

It just popped up with this in red:
tst: 4
Pass: 0
failing address: 00032397f50  -803.4MB
Good: 5d83af58
Bad: 5d83ae58
Err-Bits: 00000100
Count: 1

Is this computer dead? Is there any way to retrieve a few files from it? Would reinstalling Ubuntu get it running again?

Sounds like your RAM is dying. No, reinstalling Ubuntu won't help. It's a hardware problem and I suggest that you take out the RAM chips and reseat them. See if that helps...

---

### Post by cariboo on 2009-02-03
I agree with icanfly0307, I had almost the same problem on my server. I get getting hard drive errors, in my logs. Upon reboot I noticed on the POST screen that only 740Mb of 1Gb was detected, I just used a process of elimination as to which ram module was bad. I pulled one and restarted and checked how much ram was detected, I was lucky, the first module I pulled was the defective one.

Fsck took about 6 hours to repair the drive.

Jim

---

### Post by Teasdale on 2009-02-03
So, then, if it's the RAM, that's a minor problem, I'd need to buy a new RAM stick, and I wouldn't lose any data?

I'm expecting my son home from college this weekend; he's a bit more knowledgeable with computers than I am, so hopefully we can get it working again then.

---

### Post by icanfly0307 on 2009-02-03
How much RAM do you have and how many sticks did you put in?

---

### Post by 5nak3 on 2009-02-03
Yes, pretty much as you said if it is the ram, you would have to replace the defective stick, or run the computer without that stick until you can replace it.

Your programs, files etc... should all still be in working order and all present.

However, if the problem extends beyond ram then files could be lost. I'm not sure as I do not understand the outputs all that well (new to ubuntu, so i learn as i go along), but I would suggest if you manage to get into the system without the defective ram module I would backup all important files straight away. Saves a lot of hassle.

Hope that is of some help :) And best of luck!

---

### Post by jimv on 2009-02-03
Your RAM is bad.  That is a fact.  There might be other problems, but I'm betting that the RAM is the main cause.  You can open the computer up (turn it off first) and see how many ram sticks there are.  If there are two, it's likely that just one is bad, and you can pull them out one at a time to see which one is the problem. To remove a ram stick, push down on the white release bars on each side of the RAM stick.  To put a ram stick in, push it back into the slot until the white release bars click into place.  The only thing to watch out for is to make sure that the little slot on the bottom of the ram stick lines up with the little plastic bar in the middle of the ram slot.

---

### Post by Teasdale on 2009-02-03
This computer was given to me when a friend upgraded, it was a really good PC five years ago when we got it, but I haven't added any RAM. I have no idea how many sticks there are.

If the problem goes beyond the RAM, is it wise to invest money in RAM for a system that may be dying anyway? I'm actually saving to buy a new System76; I'd be using what I've saved towards that for RAM. If it fixes the problem, great - I probably don't need to replace the computer. But if not, it seems like wasted money.

The only files I want are a couple weeks of typed work my son did, and which he could re-do. It would be inconvenient, but nothing of great loss, since he was just copying from a book. We haven't had the new hard drive long enough to have much info, and all the kids do on it is check Facebook, play Solitaire - plus that typing.

---

### Post by jeffathehutt on 2009-02-03
Personally I wouldn't try to repair a 5 year old computer.  The ram is bad as shown by memtest, but all your hardware is probably getting old.  I would suggest you keep saving for the new pc, rather than spending the same money on your old one. :)

---

### Post by Teasdale on 2009-02-03
RAM doesn't look as expensive as I expected - I thought a stick was going to be $120. But it looks like it's more like $30.

Is there anything I need to know when I purchase RAM? Are they all interchangeable, or should I find out what kind I need first? How would I do that? Should I worry about getting too much and overwhelming my 5-year-old hard drive drive?

---

### Post by jeffathehutt on 2009-02-03
> **Teasdale said:**
> Is there anything I need to know when I purchase RAM? Are they all interchangeable, or should I find out what kind I need first? How would I do that? Should I worry about getting too much and overwhelming my 5-year-old hard drive drive?

Every system takes a specific type of RAM (DDR, DDR2, etc.).  RAM can only be replaced with the same kind, so yes, you would need to find out what type you have first.  Also, there is an upper limit to the amount of RAM your computer can take.  A five year old pc for example might not be able to handle more than 1-2 GB, where a newer pc could handle 8+

---

### Post by 5nak3 on 2009-02-03
In order to find out the ram the system uses, i've always found

[http://www.crucial.com/uk/store/drammemory.aspx?cpe=pd_google_uk&gclid=CNa0zq-YwZgCFYh_3godxlmSYQ](http://www.crucial.com/uk/store/drammemory.aspx?cpe=pd_google_uk&gclid=CNa0zq-YwZgCFYh_3godxlmSYQ)

to be very useful, the above is for the UK, so maybe if you live elsewhere you might need to look at a different domain, so if the above link doesn't work the best thing to do is just visit [www.crucial.com](www.crucial.com) and go from there.

You are basically looking for the crucial memory scanning tool.

Hope that helps :)

---

### Post by Teasdale on 2009-02-03
> **5nak3 said:**
> 
the best thing to do is just visit [www.crucial.com](www.crucial.com) and go from there.

You are basically looking for the crucial memory scanning tool.


That looks useful - I'll bookmark it. It won't help now because I have to get the computer up and online to be scanned. I don't think it's even going to load Ubuntu before I get some new RAM.

---

### Post by Teasdale on 2009-02-03
When I take out the old RAM, will it say what kind it is? I'm not sure how else to know without being able to access my computer's information.

The Memtest sshows this on the blue screen:

Athlon XP (0.13) 1731 MHz
L1 Cache: 128K 10617MB/s
L2 cache: 512K 3380MB/s
Memory: 1024M  768MB/s
Chipset: nVidia nForce2 SPP / FSB : 133 MHz
Settings: RAM : 133 MHz (DDR266) / CAS : 2-2-2-3 /Single Channel (64 Bits)

Does any of that show what kind of RAM, or give enough information about the motherboard to look up the RAM?

---

### Post by 5nak3 on 2009-02-03
Right, yes sorry I overlooked that point...my bad.

In that case can I suggest, if you are going to go out a buy ram maybe look at one of the old sticks before you purchase anything.

Basically the way I see it is you are going to have to open up the PC in either case to install the new ram. In this case therefore I suggest that if you open up the PC locate the ram stick, on the stick there should be a little sticker and it give basic information:

e.g. DDR / DDR2,

Size of the stick 256mb or 512mb

Possibly even the number of pins, if it is SODIMM or DIMM memeory etc...

These figures may not mean much to you, however, if you write them down and go to shop/website you may have a better idea of what to look for.

In the UK shops tend to be very picky and if you buy the wrong ram it is your fault, they may not give a refund etc...
On the other hand if you take the information to them and they advise you of the wrong ram at least you are covered in terms of consumer law and are more likely to get a refund or exchange.



----EDIT----

Just saw your last post, the last line does seem to give some information in regards to the RAM i think. Although i am no expert, so you may want to wait for someone else to comment before you start taking the PC apart.

Honestly I wouldn't be able to tell you what ram you are running, so i'm not even going to try in case I'm wrong and advise you wrongly. Best thing to do, is wait for someone else who is a bit more knowledgable, failing that you could try my approach of taking the PC apart and reading the little sticker.

---

### Post by jeffathehutt on 2009-02-03
> **Teasdale said:**
> Settings: RAM : 133 MHz (DDR266) / CAS : 2-2-2-3 /Single Channel (64 Bits)

It appears you have DDR ram at 266 Mhz.

---

### Post by yther on 2009-02-03
Why not just take the bad stick to the shop with you?  Then you can be sure you get a compatible replacement.

---

### Post by Teasdale on 2009-02-03
Thanks for all the help - hopefully, I can get the PC back up and running this weekend and it will last for a few more months while I save money to replace it.

---

### Post by icanfly0307 on 2009-02-03
You didn't say how many sticks of RAM you have. I'm stressing this because if you have more than one, you could chuck the faulty RAM out and live with the other working one(s). That way, you wouldn't waste money and you can use your old computer until you save enough for the old one.

---

### Post by DonaldJ on 2009-02-03
Clean the dust out of the CPU's heat-sink, before it bakes itself...

---

### Post by Teasdale on 2009-02-07
There are two sticks. 

At any rate, I did buy a new one. I took out one old one and put the new one in, and when I started the PC, it just beeped and beeped. Apparently I hadn't set it quite right. 

I fixed that, but then it had the same problem - wouldn't start the desktop. So I tried the other one, and it loaded Ubuntu, desktop and everything - but as soon as I clicked the first thing on the desktop, the whole thing froze. The mouse would move the cursor, but nothing else would work. I rebooted, and this time it's up and running, my son is online with it now and he sent me the files he needed.

Since it froze, I assume there are still issues, but at least it's running *now*, and we have the files backed up. I'll continue saving for a System76.

Thanks, everyone for the help!!

---

