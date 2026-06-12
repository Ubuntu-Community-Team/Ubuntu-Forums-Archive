---
title: "After serious thinking,i welcome myself to the world of Linux Ubuntu!But help"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by Trolen on 2010-12-31
[CENTER][FONT=Century Gothic][SIZE=2]**After serious thinking,i welcome myself to the world of Linux Ubuntu!But help..**[/SIZE][/FONT]
[/CENTER]
[FONT=Century Gothic][SIZE=2]
*I made my profile,registered to the site , and i welcome myself as a Windows user,that is now making his life in Linux.*

_Now i am downloading both X64 and X86 Version of Ubuntu to try.Which is best for my computer because i have_

[I][B]Mobo:ASUS P5E
CPU:INTEL E7300
RAM:2X2GB = 4GB KINGSTON 1066MHZ[/B][/I]

So, i have** 4 GB of ram.**

_Is it the same as windows ? _

Like theX86 is looking only the 3.25GB but the X64 More than 4 GB .. ?
**is it the same in Linux ?**

_**Another question.**_
I searched my company **asus** site about the **P5E **which programs are supported,it **doesn't have many about the linux os.**

**So the question is.**
I want the program*_** SoundMax in Linux for my 5.1 Sound System**_* to work just fine.*_**How can i do that ?**_*

[B]_After that another question._

I have the camera A4TECH PK-750MJ [/B][/SIZE][/FONT][FONT=Century Gothic][SIZE=2][http://www.a4tech.com/product.asp?cid=77&scid=160&id=494](http://www.a4tech.com/product.asp?cid=77&scid=160&id=494)
Not good i know.
*_**How can i find driver's for the Linux ?**_*

Attention i have searched their site's but i didn't find anything.

[/SIZE][/FONT][RIGHT][FONT=Century Gothic][SIZE=2][COLOR=Green]*_**Please help a windows user to become fan of Linux and after MAC :guitar:**_*[/COLOR][/SIZE][/FONT]
[/RIGHT]

---

### Post by Foxheadz on 2010-12-31
Well you want the intel i686/32-bit/x86 (there all the same) ubuntu. Camera wise you don't really need drivers you just need to be able to browse the memory card which should be doo-able from install. And odds are unless its completely incompatible with with your sounds system that application should work.

---

### Post by Chronon on 2010-12-31
You can run either x86 or x86_64 versions on your CPU.  32 bit does normally have a limit on how much RAM it can address, but you can install the PAE kernel to stick with 32-bit system and still have access to all of your RAM.

Ubuntu has a repository with thousands of applications in it.  Don't worry if Asus isn't aware of most of them.

I don't think that SoundMAX will work in Ubuntu.  Is there a specific reason that you want to use this program in Ubuntu?

A few years ago webcam support was a bit "hit or miss" but it's been pretty solid for a while now.  Chances are it will just work.

---

### Post by sjhaffner on 2010-12-31
Welcome To Linux!

You're going to love it! (Well I hope so!)
\\:D/

---

### Post by CharlesA on 2010-12-31
The 32-bit version of Ubuntu will install the PAE kernel automatically if you have 4GB of RAM or more and are connected to the internet at the time of install.

There's little difference between 32 and 64-bit.

---

### Post by Chronon on 2011-01-01
> **CharlesA said:**
> The 32-bit version of Ubuntu will install the PAE kernel automatically if you have 4GB of RAM or more and are connected to the internet at the time of install.

There's little difference between 32 and 64-bit.

I did not know this.  Thanks for the info.  :)

---

### Post by laithbsoul on 2011-01-01
> **CharlesA said:**
> The 32-bit version of Ubuntu will install the PAE kernel automatically if you have 4GB of RAM or more and are connected to the internet at the time of install.

There's little difference between 32 and 64-bit.

I didn't know that either, Thanks.

---

### Post by Trolen on 2011-01-01
I have just installed :) 

OK we have problem.
I don't use the SoundMax for any reason specific but is the programm to enable the 5.1 Surround System.

Now , i am On Linux Ubuntu i have just made all the update that is needed.

[B]MY 5.1 system doesn't work.

How can i do that ? [/B]

Thank you for the other answer's about the X86 X64.

---

### Post by QLee on 2011-01-01
[QUOTE=Trolen]...
[B]MY 5.1 system doesn't work.

How can i do that ? [/B]
...[/QUOTE]

I can't offer a definitive answer because I don't have 5.1 sound, but I suppose I would check the user's sound preferences from the menu to see if anything in there applied. System-->Preferences-->Sound

---

### Post by sandyd on 2011-01-01
> **Trolen said:**
> I have just installed :) 

OK we have problem.
I don't use the SoundMax for any reason specific but is the programm to enable the 5.1 Surround System.

Now , i am On Linux Ubuntu i have just made all the update that is needed.

[B]MY 5.1 system doesn't work.

How can i do that ? [/B]

Thank you for the other answer's about the X86 X64.
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

ur using pulseaudio, so follow the instructions in that section

---

### Post by Trolen on 2011-01-01
I read,about what you told me.

But i still didn't do it.I hear the music but i hear a strange noise from inside it.

(Something that shouldn't be there)

---

### Post by gordintoronto on 2011-01-01
To check the webcam, run Administration/Synaptic Package Manager, and install a program called Cheese. (Right click on it, select "mark for installation," then click on "apply".) It should appear in your menu under "Sound & Video". You should be able to take pictures and record videos.

Which version of Ubuntu did you install, 10.04 or 10.10?

---

### Post by Trolen on 2011-01-01
[I]The Newest one i think 10.10.

OK the webcam is automatically working without anything.[/I]
[B]
But...

We still have sound problem.
I still hear the sound from inside the speakers.

Any other suggestion ?[/B]

---

### Post by gordintoronto on 2011-01-01
> **Trolen said:**
> I still hear the sound from inside the speakers.

Any other suggestion ?[/B]

I'm sorry, but I do not know what you mean.

---

### Post by sandyd on 2011-01-01
> **Trolen said:**
> [I]The Newest one i think 10.10.

OK the webcam is automatically working without anything.[/I]
[B]
But...

We still have sound problem.
I still hear the sound from inside the speakers.

Any other suggestion ?[/B]
This is the fun part.
Open the sound prefrences, alsamixer, pavucontrol and fiddle with the outputs until it works.

actually, try pavucontrol first, it seems to contain the fix for most weird pulseaudio sound issues. (check esp the configuration tab)

---

### Post by Trolen on 2011-01-01
Until now everything are good.And ok :)

Let's hope for the best.

---

