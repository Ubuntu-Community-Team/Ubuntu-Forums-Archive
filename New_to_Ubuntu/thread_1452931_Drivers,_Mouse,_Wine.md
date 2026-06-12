---
title: "Drivers, Mouse, Wine"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by orphanlast on 2010-04-12
I'm sorry how long my opening statements are. I'm just having a lot of problems.

Okay, I've installed Ubuntu. I'm tired of windows and I've decided to make the switch but Ubuntu has been a real pain in this entire process. I'm a REAL beginner here.. I have a quad core and this operating system seems to only superficially recognise that. Vista runs like clockwork, where as Ubuntu is slow and only does one small task at a time.

So regardless of if that's a problem with drivers, I need to install them. I have a Biostar G31-M7 TE motherboard. There are no drivers that I've found (and I've looked for three days) for anything Linux.

I noticed that when I go: SYSTEM>ADMINISTRATION>HARDWARE DRIVERS it states that the best setting or driver for my video card to run off of is "NVIDIA accelerated graphics driver (version 185) [Recommended]"

... The problem is, my graphics card isn't NVIDIA it's a Geforce 9800 GTX+ so I have no idea how to get the correct drivers on here or if Ubuntu magically installed them on their own. or even if that HARDWARE DRIVERS application is showing me what I think it's showing. How do I get my drivers on this little bastard?

Next problem is my mouse. Ubuntu recognises that I have a wheel on this mouse but if I wheel-click and then move the mouse up and down it won't auto scroll for me. I've googled this sucker for hours and it's just so much work for such a small problem.

Third, I hate wine. It doesn't seem to work. It looks like it MIGHT be able to open an occasional windows file but if you need to install then wine crashes every single time. Is there any better windows emulators... what's a good Mac OS emulator, maybe I might have better luck getting photoshop and Acrobat that way (I hate GIMP).

---

### Post by arochester on 2010-04-12
1) > There are no drivers that I've foundLinux doesn't work that way. If it works, it works. No driver.

2) > my graphics card isn't NVIDIA it's a Geforce 9800 GTX+ Geforce IS Nvidia. Click the activate button!

3)> Is there any better windows emulators..It's all based on Wine. There is a hierarchy, Wine, Wine-Doors, PlayOnLinux through to the commercial versions e.g. Cedega.

---

### Post by orphanlast on 2010-04-12
> **arochester said:**
> 2)  Geforce IS Nvidia. Click the activate button! 

Cool. Yeah, I've done that. I was just wondering if that was normal and it appears as though it is. Sorry, as I said, I've always been moderately competent with something like Windows but there's so much user responsibility with Linux programs.

So I'm sure stupid comments like that are going to be popping out of my mouth from time to time.

anyone know how to get past the mouse problem?

---

### Post by J V on 2010-04-12
Middleclick works, its just that linux apps dont have any "Auto-scroll" by default

On firefox at least the answer is Edit > Preferences > Advanced > General > Use auto scroll

"Open windows file" - What exactly do you mean here? I would advocate installing [playonlinux]("apt:playonlinux") as it is far easier to use than just plain wine...

It also provides an easier way to download the latest wine (Anything that isn't 3 years old and super-incompatible is labeled beta so it isn't distributed, besides that they release a new version every 2 weeks or so)

What program are you trying to install? [(I suggest looking for a native linux alternaitve first)]("http://osalt.com")

---

### Post by orphanlast on 2010-04-12
JV, you're freakin' awesome!

---

### Post by Mark Phelps on 2010-04-13
I know it may seem like a minor point but it's not -- Wine is NOT a Windows Emulator, CodeWeavers (the supplier of Wine) even goes so far as to say that.

A true Windows emulator would provide ALL the functions of a particular Windows OS version.

Wine does not do that; instead, it provides a set of libraries that allow MS Windows library calls to be answered by Linux functions.

At best, this allows you to run SOME MS Windows programs in Wine.

---

### Post by J V on 2010-04-13
It isn't a minor point, but its the best feature of wine... It means windows programs can run at full speed, sometimes faster than in windows.

A true emulator however would be 5 to 20 times slower than wine, which with a bit of tinkering can get almost anything to work...

Considering that law that says computing doubles in capacity every 18 months, an emulator will keep you 3.2 to 15 years behind in the gaming scene, tetris anybody?

---

### Post by orphanlast on 2010-04-17
That sounds kinda lame...

Why make a program that only does part of what it's supposed to do?

That's like me writing a program for a calculator and making the "equals" button inoperable.

---

### Post by madjr on 2010-04-17
hey you say you're a total beginner but you're adapting fast

linux isnt windows just like mac isnt windows, so getting your mind to think out of the mold is bit hard the first time you do it. The first time is the hardest for everything in life.

i moved to ubuntu back in 2007 and it took me a while to adapt (like a month), then everything has gone pretty well, specially with each new release

i switched cause i had my credit card and password stolen by some virus/trojan or some malware, then i got sick of scanning everyday

then using ubuntu i never been more comfortable browsing the web. peace of mind is priceless.

the key is doing it slowly, dont try to substitute/ditch windows completely right away. You may be dual-booting or using virtual environments for some time.

i dual booted or used virtual box for about a year, now i haven't used it for so long i think i forgot how to use most of it.

---

### Post by orphanlast on 2010-04-18
With virtual box, does it run things really slow?

Because... if you think of it, you're running Ubuntu, running a program running Windows running a Program IN Windows...

Lol

I've heard of virtualbox a lot ever since I got into Ubuntu. Last time I tried to get it on I failed and I took a break from it. I'll take another stab at it. It looks like my best shot.

Thank you for your patience and your time.

Are you kinda excited about Google getting involved in Linux? Here they talking directly with the Ubuntu team to make sure Chrome OS is going to be compatible... I think if Google were to get involved, maybe Linux will wind up being more like people say it is or want it to be. I kind of think that programming computers should have been a required class in middle and high school -- the whole way through... Maybe even replace math classes and just teach math through the practical application of computers... that would be awesome.

(The way they teach math these days is ridiculous.)

You're awesome.

---

### Post by Paqman on 2010-04-18
> **orphanlast said:**
> With virtual box, does it run things really slow?


Sort of. Like you say, there's a lot running; two whole operating systems plus all their apps. You also don't get direct access to your hardware from the virtual machine, which means no real 3D graphics acceleration (yet). So games will be sloooooooooww.

Having said that, if you've got a reasonably modern PC and are only running modest apps there's no reason why it shouldn't run things at nearly the same speed it would on a real machine.

---

### Post by 3rdalbum on 2010-04-18
> **orphanlast said:**
> That sounds kinda lame...

Why make a program that only does part of what it's supposed to do?

That's like me writing a program for a calculator and making the "equals" button inoperable.

Not really. Wine works for some programs and some games. It's a difficult, time-consuming process to reverse-engineer Windows; the Wine team has been working on it for over a decade. There's so much of Windows' internals that are simply not documented anywhere, and it's illegal to disassemble Windows to try and learn more that way.

Wine is more of a last resort - if you absolutely can't do something using native Linux software, it may be possible to use Windows software in Wine.

Now, Ubuntu shouldn't be slow. If it's running slowly then there might be a program that is buggy and using too much CPU time or too much I/O capacity. This happens on Windows too, but usually people just reinstall Windows rather than investigate what's happening.

You can use the System Monitor program to check your CPU use and find out if a program is running away with your CPU. There's a command-line program (that's easy to use) in the repositories called IOtop, you can use this to find out if there's a program that's making part of your CPU wait for IO that will never come.

I'll also just say that a quad-core CPU allows you to run four threads at once at full speed; **if a program isn't designed to use more than one thread, then it will utilise only one core at a time**. But you can run four such programs, or use a program that can split its tasks into four threads.

---

### Post by madjr on 2010-04-18
> **orphanlast said:**
> With virtual box, does it run things really slow?

Because... if you think of it, you're running Ubuntu, running a program running Windows running a Program IN Windows...

Lol

I've heard of virtualbox a lot ever since I got into Ubuntu. Last time I tried to get it on I failed and I took a break from it. I'll take another stab at it. It looks like my best shot.

Thank you for your patience and your time.

Are you kinda excited about Google getting involved in Linux? Here they talking directly with the Ubuntu team to make sure Chrome OS is going to be compatible... I think if Google were to get involved, maybe Linux will wind up being more like people say it is or want it to be. I kind of think that programming computers should have been a required class in middle and high school -- the whole way through... Maybe even replace math classes and just teach math through the practical application of computers... that would be awesome.

(The way they teach math these days is ridiculous.)

You're awesome.

no problem :)

i enjoy helping everyone i can, because i've been there.

i totally agree with you, programming should be thought in schools

programming and learning how logic and processes works

as a civilization we would be far more advanced

the brain is the most advanced machinery in the universe and we only use like 5% of it.

i know it took me some time to get used to that mindset and i wished my parents/school had gotten me involved when i was younger. 

it was harder because of my age, but i caught up, so is never too late ^^. My son is 5 years old now, once he's 7 or 8 I'll get him involved, let him play with it and be creative

who knows, he might be the next iron man! :P

lol, maybe not, but he'll have a bright future and deep understanding of how things work in physical and virtual world.

---

