---
title: "Over-heating Problem"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by YummyOlives on 2011-01-27
hello everyone !

Little problem with xplane!

Xplane runs the system too hot, i have a dual boot config. along with vista 32, i run xplane on the vista partition as well, which runs fine with normal temperature and there no excess of heating or similar problem, the same settings used in ubuntu causes the system to go ballistic and fire up all the fans and the heatup ! feel like there must be some sort of tweaking that could help. 

(running 2 copies of xplane on the same system-vista installation+linux installation)

_**THE CLIMAX :**_

funny thing is that the vista copy of x-plane runs normal in linux as windows app.(wine 1.3), no overheating at all, but launching the linux copy of xplane causes the unnecessary heat-up , now this is really weird indeed , please advise ! and yes i have to run the linux version of x-plane as the frame-rate is much better as apposed to vista. :)

Dell Inspiron 
xps M1710

---

### Post by YummyOlives on 2011-01-28
bewbzzzz

---

### Post by NightwishFan on 2011-01-28
Perhaps your graphics card has some powersave settings? I would not know mine have always been integrated.

---

### Post by robsoles on 2011-01-28
I don't even know (or care for that matter) what x-plane is, I just see a clue in your post and I figure I may as well point it out.

I propose that it is just frames per second that is doing this for you - you say it doesn't overheat the system when the Windows binary is executed under Vista or Wine and then you say that the frame rate is too slow in the Windows binary and you want to use the Ubuntu/Linux binary.

Just a thought but I can easily see a developer having any number of reasons for knobbling it in Windows and not in Linux - maybe when they tested it they found (*on their test equipment) that the Windows binary cooked the box and the Linux binary ran cool so they limited frame rate in the Windows binary and released both.

If it is still a 'live project' maybe the people in the 'x-plane' project will be grateful for your feedback.

---

### Post by HermanAB on 2011-01-28
Howdy,

Linux and Apple OSX are optimized for Audio-Video pertformance.  That is why Linux is used by movie studios (Disney, Pixar).

What this means is that in Windows, there are many short little periods where subsystems are waiting on each other - the CPU waiting for the disk drive, the GPU waiting for the CPU and so on.  The result is that on  Windows, the processors cannot run continuously and therefore  have time to cool down.  The bad result is a lower frame rate, stuttering video and crackling audio.

---

### Post by robsoles on 2011-01-28
Hey OP, seeing that Linux runs your game so optimally that your box overheats, check in the options of the Linux binary of the game if you can limit the framerate - maybe you can set it faster than you get in Windows and slow enough to keep your box cool(ish) :)

---

### Post by YummyOlives on 2011-01-28
thanks for the replies guys

the idle GPU temp. is around 65 - 70 ( no apps running), which is not normal i suppose

rob i will try to limit the framerate , hope that helps

---

### Post by HermanAB on 2011-01-28
You may also be able to reduce the clock speed in the BIOS.

I had one annoying Toshiba laptop where I not only had to reduce the speed, but also turn off one processing core altogether, to keep it cool.  

On a laptop, clocking it down and turning the 2nd core off makes the battery last longer, so it is not totally without advantage.

---

### Post by Onesimus on 2011-01-28
You may have to install i8kutils.  It is a package specifically designed for Dell Inspiron to controls fans, etc.

You can install it from System > Administration > Synaptic Package Manager.

If you have problems installing it, then search on the forums for i8kutils.

Hope this helps.

---

### Post by fabricator4 on 2011-01-28
> **robsoles said:**
> I propose that it is just frames per second that is doing this for you - you say it doesn't overheat the system when the Windows binary is executed under Vista or Wine and then you say that the frame rate is too slow in the Windows binary and you want to use the Ubuntu/Linux binary.


100%

Put a program on a kick-a OS and find it kicks A ...  and the problem is?

If ya want a CPU that never goes over 65C get a Celeron, or invest in some serious cooling. ;-)

C

---

### Post by YummyOlives on 2011-01-28
ok after tuning off the intel speedstep option from the BIOS , my system is back to normal temperatures, so anyone running it really feverish please disable that option from your BIOS settings and hopefully that overheating shall thy be vanished !

well the next Q is what are the consequences of disabling speedstep process ?

thanks alot for all the inputs

---

### Post by HermanAB on 2011-01-28
Consequence?  Nothing much, the machine will run a bit slower.  My little EeePC (typing on it now) runs at 650 MHz and it is quite acceptable.  My Toshiba runs four times faster and has a dual core processor - it comes into its own when I compile things or do heavy graphics.  With ordinary use, the processor does nothing most of the time anyway and just waits for you to pleeeeease press a key...

---

