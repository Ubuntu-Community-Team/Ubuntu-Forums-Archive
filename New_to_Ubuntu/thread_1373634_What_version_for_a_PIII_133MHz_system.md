---
title: "What version for a PIII 133MHz system"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by InMyHumbleOpinion on 2010-01-06
I'm thinking of installing Ubuntu for the first time and wish to do so on my back up computer. The specs in the FAQ on Linux in general says minimum system requirement is 300MHz and I have PIII 133MHz chip, which is the fastest the motherboard can take. Is there a earlier version of Unbutu or another free Unix/Linux that would be optimal?

---

### Post by occams_beard on 2010-01-06
Wasn't the slowest PIII 450 mhz or there abouts?  I'm sure it was much faster than 133mhz.

I think you are referring to the bus speed.

If you actually do have a pentium 1 cpu that is only 133mhz, you might try puppy or damn small linux. But honestly, it's probably not worth the effort unless you are bored and just want to mess around.

---

### Post by ST3ALTHPSYCH0 on 2010-01-06
How much RAM do you have? I'd say that would be as much a limiting factor in that system as anything. If you can get it up to 256 Mb of Ram I'd say try it, but you'll definitely need the alternate installer.

EDIT:
Just confirmed,the slowest PIII was 450 MHZ, and that will definitely run Ubuntu. Just mind the RAM, I'd try to get to at least 512 K if you're not there.

---

### Post by FreezWay on 2010-01-06
```

RAM:   |128      |  256   | 386         |512          |1GB+
Ubuntu |unusable | usable | ok...       |pretty good  |fast
Xubuntu|usable   | ok.... | pretty good |fast         |really fast
Puppy  |HDD only*| ok     | fast        |faster       |ZOMG!

```

HDD only means DONT run from ram...

for older systems, I'd go xubuntu, unless its REALLY old, then go puppy or DSL... or Arch, but thats hard to install.... really hard to install.

---

### Post by InMyHumbleOpinion on 2010-01-06
Thank you all for the quick response and being kind to my foolishness.  Having read responses, I've double checked my motherboard's manual (which I was going by) and found that the maximum 133 is the FSB.
 
However, in checking the System Properties, it reads that the CPU is Pentium III 334M, so I think I'm going to have to open it up and check the chip and then check the slot settings.
 
I'm currently 256M of RAM, but have purchased 2G worth, so memory will not be a problem.  Fortunately, the SDRAM for this chipset is fairly cheap.  So once I have the CPU worked out, it and the RAM should not be a problem.
 
Thank you again and please feel free to throw any other advice here.

---

### Post by colin.p on 2010-01-06
I hope you didn't spend too much on that sdram, as I sincerely doubt the motherboard will take more than a gig, more like 512MB or so.
I had a DFI mb for an AMD K63, and it would only take 768mb of ram.
Also, there was a limit to how many MBs each chip could be. 

Just an FYI

Colin

---

### Post by lkraemer on 2010-01-06
Good choices are:
1.  Damn Small Linux Ver 4.4.10 (works on pre 2000 BIOS)
2.  Tinycore (Continuous releases as Roberts chugs away daily)
3.  Puppy
4.  Crunchbang 8.04 (works on pre 2000 BIOS)
5.  SliTaz
6.  TinyME
7.  Macpup

I am running Crunchbang 8.04 on my old Compaq Presario 1672 AMD K6-2 350MHZ
with 192 Meg RAM and 80 Gig IDE Drive.  Works pretty good.

lk

---

### Post by Bartender on 2010-01-06
I have a Pentium III 1GHz test PC, and had a PIII 450 before that, so I can give you an idea of what to expect.  More RAM is definitely good, but a modern full-featured distro will quickly push the CPU's limits.

It'll work fine for gaining experience, but you'll have to be careful about what you try to do.  For example, on the 450MHz I tried listening to CD's using Sound Juicer and CPU usage was acceptable.  I tried it again with Amarok, a much more complex media player, and CPU usage was just about pegged.  Trying to do anything else made the sound drop out and skip.

Odd little tasks like asking the printer to create a test page can also be quite the ordeal.  I have an older HP printer that "just works" with every Linux distro I've tried.  Plugged the HP into the 1GHz PC, set it as default, and asked it to print a test page.  Five minutes later the print head had made two or three passes, so I gave up.  Thinking something was wrong with the printer, I plugged it into a 3GHz Pentium 4 and asked it to print a test page.  The printer cranked out the test page immediately.

So a PIII 450 will work, just don't expect too much from it!

---

### Post by InMyHumbleOpinion on 2010-01-06
Thank you all for input and wonderful advice.
 
Just to give the system info again, I had mistaken the FSB for the overall CPU speed, but need to actually open it up and look at the chip itself to figure out what it is.
 
Memory will not be a problem.  The motherboard is an ASUS P3V4X.  It has 4 slots that can each take up to 512M of RAM.  This area was simple enough that I was able to read the section correctly.  So long as the RAM I ordered isn't bad, I should be doing fine on that point.
 
This will be my first attempt, so it's all experimental anyway.  Also, this is entirely meant to be a user end computer.  Internet navigation will be my main focus, but nothing too complex I expect.  So I should be able to keep it fun and won't have too high of an expectation.  Well...I want it to be less of a pain than Windows and don't think that's too high of a standard  :/.
 
Once I verify the CPU speed, I'll post and I shall keep checking this thread to see if there is any new info or advice.  Thanks again.

---

### Post by llamabr on 2010-01-06
Many of those who suggest damn small linux or puppy linux are thinking of hard disk space, not necessarily ram or cpu.  both of those distributions will easily run gnome or kde apps, which will eat your cpu and ram.

a standard xubuntu distribution will work on a piii with 450mz.  the difference is that ubuntu ships with gnome, and xubuntu ships with xfce.  For slower and older machines, I'd go with a lighter window manager like window maker, and you can even forgo the desktop environment.

In any case, download the livecd, see what you think.  Install it if you like, and bring any questions back to us here.

---

### Post by Bartender on 2010-01-06
It's running Windows right now, correct?  Just download Belarc (it's a small program) and run it.  Belarc will report CPU speed, and a bunch of other neat little facts too.

---

### Post by InMyHumbleOpinion on 2010-01-08
Belarc was quite helpful, but unfurtunately not for the CPU speed. I think it's because I was messing with the BIOS when I was having problems booting.  So I'll just have to take open it up and check the processor physically.

---

### Post by Bartender on 2010-01-08
Belarc didn't work?

How about [CPUID]("http://www.cpuid.com/cpuz.php")?  If CPUID doesn't tell you what you've got it must be a CIA secret agent CPU.  

I've found that it's often nearly impossible to figure out what processor you have by looking at it.  If you've got an old Slot 1 cartridge (pretty sure you do) those were sometimes marked fairly clearly.

---

### Post by InMyHumbleOpinion on 2010-01-09
I went in and found among this among the markings of the CPU:

"500/512/100/2.0V"

I am assuming that means the CPU speed is 500MHz with a bus speed of 100 and thus a multiplier of 5.0.  I have no idea what the 512 is then.

And Bartender, I didn't try CPUID, but since the Bios let's me set the CPU speed for some reason, I think that's all that Belarc read and may be what CPUID reads.

There's a few more things I need to do- transfer anything I care about over (not much), copy over the hardware info, and switch a DVD reader onto the computer- but I'll be downloading the Install image now and hopefully have it installed this weekend.  Wish me luck.  I'll still be checking here now and then for further input.

---

### Post by starcannon on 2010-01-09
> **InMyHumbleOpinion said:**
> I'm thinking of installing Ubuntu for the first time and wish to do so on my back up computer. The specs in the FAQ on Linux in general says minimum system requirement is 300MHz and I have PIII 133MHz chip, which is the fastest the motherboard can take. Is there a earlier version of Unbutu or another free Unix/Linux that would be optimal?

I looked up the motherboard specs that you listed in a later post of this thread.

[quote=http://www.motherboard.cz/mb/asus/P3V4X.htm]
[B] Support Slot 1 Coppermine Pentium® III/II 300MHz~800+MHz or CeleronTM Processor (with ASUS® S370 Card Series) 
[/quote]

[/B]So, you have at least a 300MHz cpu, and at most an 800MHz cpu.

Here is an identification chart that should let you know how fast your cpu is:
[http://www.cpu-world.com/info/id/Intel-PIII-identification.html](http://www.cpu-world.com/info/id/Intel-PIII-identification.html)

GL and HF

---

### Post by InMyHumbleOpinion on 2010-01-09
Thank you Starcannon.  That confirms it quite well for me.

---

### Post by cenzorrll on 2010-01-09
as far as low cpu and ram go, i have a fit-pc slim (amd geode 500mhz, 512 ram) and I can run LXDE at about 50 mb of ram.  i would suggest using the "mini.iso" from ubuntu and only installing what you need.

to get things started i installed the base system (very minimal setup)

then did:

```
sudo apt-get install xorg lxde xdm abrowser
```
abrowser is just firefox without any of the copyright images, i would highly suggest finding a lighter weight web browser if you can though.

this will get you a web browser, the desktop environment and a login screen.

---

### Post by InMyHumbleOpinion on 2010-01-11
Thank you all again.  I burned the install disk last night and, after a long period of dealing with Windows upgrades on the soon to be Ubuntu desktop, I tried out 9.10 via the Install DVD.  I am now 89& into the install process as I post this message from the desktop I'm installing onto.

Just so you know, having saved what I cared most about, plus some stuff I didn't, I do have room to play around on this desktop.  Do not think any of the advice for slimmer variants were misplaced.  As I see how things are going, I may very well install each of those to give them a try.  Overall, even with the CD version, I have few, and minor those, complaints.  Of course, I expect some of that is due to the very newness of the experience, and will see how I feel in a week.

Again my thanks.  I'm marking the thread solved, but will likely be coming back for reference.  Happy New Year.

---

### Post by clevertomato on 2010-01-11
If you find you want to experiment with something else, look into Crunchbang. it's based on Ubuntu. I intalled it on my Pentium II 266 mhz with 256 MB RAM and I was pretty impressed. Firefox wasn't winning any speed awards on this setup, but otherwise, pretty tight system. Just giving you a little more input to consider.

---

### Post by caravel on 2010-01-11
I'm probably biased, but I would go with Debian and IceWM or one of the 'boxes on that system.

---

### Post by cascade9 on 2010-01-11
> **InMyHumbleOpinion said:**
> I went in and found among this among the markings of the CPU:

"500/512/100/2.0V"

I am assuming that means the CPU speed is 500MHz with a bus speed of 100 and thus a multiplier of 5.0. I have no idea what the 512 is then.

512K = CPU cache. 

The early P3s had 512K @ half CPU speed, later P3s had 256K @ full CPU speed. 

P3s had a few revisions- 

'E'- 'advanced transfer cache' (aka 256K @ full speed)
'B'- 133 Mhz FSB
'EB' both the above. 

> **starcannon said:**
> I looked up the motherboard specs that you listed in a later post of this thread.

[/b]So, you have at least a 300MHz cpu, and at most an 800MHz cpu.

Here is an identification chart that should let you know how fast your cpu is:
[http://www.cpu-world.com/info/id/Intel-PIII-identification.html](http://www.cpu-world.com/info/id/Intel-PIII-identification.html)

GL and HF

Fine google-fu, but the P3VX4 will go higher than 800Mhz. 

> [FONT=Arial, Helvetica, sans-serif][SIZE=2]In particular, we used the    ASUS P3V4X in our 133A tests with the 1GHz Pentium III simply because our Gigabyte    133A board failed to properly support the CPU without an updated BIOS that was,    at the time of testing, unavailable.[/SIZE][/FONT] 

[http://www.anandtech.com/showdoc.aspx?i=1191&p=6](http://www.anandtech.com/showdoc.aspx?i=1191&p=6)

If you want to poke the asus site...a lot... you'll see that that the P3V4X will work with the P3 socket 370 chips (with a slot1 to socket 370 adapter). Asus says up to 800Mhz 133/256, and up to 933Mhz (slot1) but I would guess that it would work with a P3 933/1Ghz 'EB' model. 

I'd link you but that is impossible due to the way asus has laid things out. If you want to check yourself, go here- 

[http://support.asus.com/](http://support.asus.com/)

Support-> CPU support-> 'search cpu using motherbord', slot1, P3V4X.  

If you can find the CPU/Socket adapter I'd ry to find at least a 800EB, and up the RAM to as high as you can go. 2TB Maximum, but find 512MB SD ram isnt fun, 256MBx4 for 1TB would be pretty easy. 

I've run a P3 866/384MB with unbuntu and its runs OK. A minimal instyall version runs nicely. 

No need to play with 'light' distos if you dont want to.

---

