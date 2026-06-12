---
title: "Weirdest bug/problem of the day?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by sheffieldbob on 2009-08-29
Dear all,

I'm fairly new to Linux, so  bare with me, though I do know my way round a pc.

I've got a random unbuntu display issue.

new instal of 9.04, works fine. Brilliant all configured nicely. But....

the monitor will refuse to resulme from powersave. Needs a restart... When i restart the very small bios and some of the lines on the screen are vertically corrupt, and show blank lines or gibberish, depandant on whats showing. - makes screen just about redable with missing letters. Navigating through this, we get to the ubuntu bar, loading across the screen, and thewn it fowes blank, waits for a minute or so, then my monitor switches off....

And thats it. - Nothing.

This happened thois mornign after last ngiht, I swapped to a old pci graphics card and also the live cd, and all wasn't well, as a final attempt i added in my old (first) graphics card and it all worked again. (perfectly fine n o problems at all)

Everything is fine with all of unbuntu unless my power save kicks in. I will try reinserting my card now and see what happens. But this is sure one random problem.

Any ideas guys?

Bob

---

### Post by scorp123 on 2009-08-29
> **sheffieldbob said:**
> Any ideas guys?  Sad story. But you did not provide any technical details of any value. You asked for ideas. How about starting with telling us about your PC (how old? model? what CPU? how much RAM?), your graphics card (make? chipset? brand? how old?) and such things?

You see, our crystal balls are out for repairs, and I personally am not so good with Tarot cards, and I am out of chicken or goats that I could sacrifice to the spirits ... so we will have to rely on the *technical* infos you give us ;)

---

### Post by sheffieldbob on 2009-08-29
Sorry. Its a bad day!

Um, well. I have an aging geforce 4200 128mb. 1.5gb of ram and an athlon xp2400, would have to check the chiopset, which os a little difficult at the moment.... Computer is abpout 4-5 years old....

The problem gets weirder, the live cd hasn't solved the issue this time, though my monitor is fine... as it shows all the right things when in use with my laptop. If i use the live CD sometime i get junk sometimes i don't. It seems like a very very random hardware fault, and I haven't moved anything around, so that to me makes it weirder. The display works for the splash screen... I will try another  power cycle and my dvi output and see what I get.

thanks. Sorry, first post was more of a rant, im a rather upset little bobby, otherwise unbuntu has been brilliant for me! 

Bob

---

### Post by donkyhotay on 2009-08-29
As I understand the issue now, ubuntu starts to load up normally. You can see the loading screen. However when it gets to the point it would normally ask you to login the screen goes blank and the monitor eventually turns off. If this is correct then the problem is with the X display system. Possibly a driver related issue. If I have described your issue accurately try restarting ubuntu. When you see the GRUB boot menu press the <esc> key then choose safe mode. Things will be very different (don't panic) and you will eventually get to a menu. Does this menu successfully show up? Also if I have completely mis-interpreted your issue let us know. The stars weren't quite in alignment with my goat sacrifice here so I may be wrong. (c;

---

### Post by sheffieldbob on 2009-08-29
Hey all,

this has just got worse...

Been playing with the DVI and VGA outputs, swapping the two, booting to live cd etc. (that doesnt work over dvi) - most of the time various takes on a corrupted screen. Went back to VGA and started, and I now have a working ubuntu again. - presumably until it goes to sleep all over again... :(

Any ideas on how what is seemingly a software fault manifests in hardware start-up....?!

When it is wrong, my bios screen, boot loader etc, are all readable, but corrupt (missing odd characters).. Its not always as eassy as getting to the bootloader even....

My goat msut be lame, hes struggling through today! - certainly doesnt want to be sacrificed :o

---

### Post by donkyhotay on 2009-08-29
> **sheffieldbob said:**
> When it is wrong, my bios screen, boot loader etc, are all readable, but corrupt (missing odd characters).. Its not always as eassy as getting to the bootloader even....

You're facing a HW failure. Unless you had a bad BIOS update (and you'd know if you had tried updating the BIOS) the only thing capable of giving you distorted graphics in the BIOS is the HW. Ubuntu & windows both are incapable of 'messing up' the BIOS since the BIOS completely HW related. The only real possibility you have at this point is to reset your BIOS completely using the jumpers on your motherboard, and even that is more of a 'computers hosed no reason not to try' type suggestion rather then something likely to work.

---

### Post by sheffieldbob on 2009-08-30
Thats whats confusing me... It's what I thought, but my computer also works perfectly sometimes, (like now). Windows is OK too...

Its a very sporadic hardware fault if it is one, which seems only related to sleep mode in Ubuntu, (the thing that causes it)... It seems such a random hardware failure, as everything posts ok, and everything is fine now, I can play movies, whatever else....

Is it really really a hardware fault?... Why when i dont change the hardware and play with the live cd and things (as above) does it finally work? - i dont even move the pc for that!

Im quite fond of my old PC... so I would like to keep it soldiering on, but it's getting close to that final sacrifie for it i think...

Any ideas?

---

### Post by donkyhotay on 2009-08-31
Some HW related issues aren't as obvious as others. The only thing that really confirms this in my mind as a HW issue is the distorted graphics in the BIOS. At the least it means your BIOS is messed up and needs to be reflashed.

---

### Post by jimsheep on 2009-08-31
if your motherboard has an onboard VGA port, try removing the GeForce and using that (enable it in the BIOS first, before you take out the GeForce)...if the problem persists, it may be a motherboard issue, not just a video card issue.

hope that helps...just one more step to narrow it all down.

---

