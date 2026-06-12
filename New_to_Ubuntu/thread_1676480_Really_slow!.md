---
title: "Really slow!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by jordanC on 2011-01-27
hi, ive just installed Ubuntu desktop edition 10.10 onto my laptop, i previously had windows 7 running on it which was realy good but i just wanted a change. Since installing Ubuntu ive realised alot of programmes dont work because they are all associated with windows, for example spotify. i installed wine and i can now use spotify but its really slow! I used play a bit of online games aswel, now when i try to do so with ubuntu, its really slow and laggy and cant handle games wth high graphics whereas windows 7 could. I was just wondering if you guys have any ideas of how i can make things run faster and smoother on ubnubtu.
cheers :)

---

### Post by mastablasta on 2011-01-27
> **jordanC said:**
>  I used play a bit of online games aswel, now when i try to do so with ubuntu, its really slow and laggy 
 
What games? java based, flash based?
 What is your graphics card? what drivers do you use? you didn't provide any information on your system.
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
 
> 
and cant handle games wth high graphics whereas windows 7 could. cheers :)
 
again, which games? if you think windows games via wine then you should know that virtualisation will always be slower than under the real OS. also windows games these days use DirectX11 (which is a microsoft product and runs only under windows). WIne can do directx9 i think. but most linux games use OpenGL. which is just as powerfull if not more than directx but developers still choose to develop for directX mostly it seems.
 
suggest you try a dual boot first, since you seem to be very windows focused. you will need to find linux alternatives to your windows programmes.

---

### Post by IWantFroyo on 2011-01-27
> suggest you try a dual boot first
I agree with this. Windows games will work better on windows. In fact, you might just want to put the livecd in while windows is booted, and install through wubi.

---

### Post by Linyx on 2011-01-27
> **jordanC said:**
> hi, ive just installed Ubuntu desktop edition 10.10 onto my laptop, i previously had windows 7 running on it which was realy good but i just wanted a change. Since installing Ubuntu ive realised alot of programmes dont work because they are all associated with windows, for example spotify. i installed wine and i can now use spotify but its really slow! I used play a bit of online games aswel, now when i try to do so with ubuntu, its really slow and laggy and cant handle games wth high graphics whereas windows 7 could. I was just wondering if you guys have any ideas of how i can make things run faster and smoother on ubnubtu.
cheers :)

First of all ...Linux isn't for Games,

Another thing about Wine, i had used it but it will not perform Software built for window as smoother as in windows, like a virtual Environment,

So in my opinion if you are Interested in Games and some MS Softwares you should Dual-boot Windows with Ubuntu so that you can run your Games and MS-Softwares on windows and Keep Ubuntu for Practicing....

Once you are Satisfied with Ubuntu and you don't Need Windows anymore, then Throw Windows and Switch to Penguin Family.....;)

Some List of Games/Softwares which will Work on Wine > [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by jordanC on 2011-01-27
cheers for your help guys, sorry that i was pretty useless at explaining. I am currently running it on my sony vaio VGN-N38Z, not sure how to veiw the specs on ubuntu, i am completely new to this.

---

### Post by NightwishFan on 2011-01-27
> First of all ...Linux isn't for Games
Yes it is.

> Another thing about Wine, i had used it but it will not perform Software built for window as smoother as in windows, like a virtual Environment
This is not always the case, it can go both ways. Generally with advanced DirectX 11 stuff you might be right. Wine does not virtualize. (Just to clarify for op)

> So in my opinion if you are Interested in Games and some MS Softwares you should Dual-boot Windows with Ubuntu so that you can run your Games and MS-Softwares on windows and Keep Ubuntu for Practicing....
I agree with this. Op, please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) Ubuntu is a great operating system, however it is its own operating system, not a free Windows. It will require some unlearning and to use it full time is possible. (I have since 2007) If you want Windows stuff there is no shame in using both.

> Once you are Satisfied with Ubuntu and you don't Need Windows anymore, then Throw Windows and Switch to Penguin Family.....;)
:popcorn:

---

### Post by Linyx on 2011-01-28
> **NightwishFan said:**
> This is not always the case, it can go both ways. Generally with advanced DirectX 11 stuff you might be right. Wine does not virtualize. (Just to clarify for op)


Well, i am new to Linux so don't know better yet, However, i had Used Wine with Certain Applications, first thing i noticed that on most Softwares e.g i-Tunes, it run slower and sometimes it even stop Working.....Same Case with one of my friend.

Another issue in Wine is that, it will eat Much CPU on certain Software as Compared to Windows.....In-Short , Wine is **Limited** and i don't think so that it can take a place of Windows Environment for Running Windows Applications....However, it will Work Perfect on Some Applications but not all.....[SIZE=2]Just as we Run an OS in VM, but that OS is Limited for Certain Tasks......[/SIZE]

---

### Post by NightwishFan on 2011-01-28
I can agree. Forgive my bad attitude. :(

---

### Post by Linyx on 2011-01-28
> **NightwishFan said:**
> I can agree. Forgive my bad attitude. :(

<not belongs to thread> Ohh.... No need to Apologize , i think we all are Learning....<Closed>

---

### Post by HiImTye on 2011-01-28
what WINE runs well depends on the API in the version of WINE you are running

WINE is a set of libraries that simulate the core windoze ones (you can also use proprietary ones but in most cases you need a key)

often there is some minor tweaking to get certain programs to work and sometimes it just works. other times it simply doesn't work. it depends on the WINE version and the required APIs for the program. .net 3.5+ is a good example of something that WINE has problems with

---

### Post by jordanC on 2011-01-28
Im afraid to say im still not getting along with Ubuntu and want to go back to windows7 :(
the only problem is now my laptop wont boot from a cd/dvd or a USB :S

---

### Post by Linyx on 2011-01-28
> **jordanC said:**
> Im afraid to say im still not getting along with Ubuntu and want to go back to windows7 :(
the only problem is now my laptop wont boot from a cd/dvd or a USB :S

Can you Clarify your point.....Your laptop isn't booting from CD/USB....??

Have you Selected the CD/USB from BIOS to 1st boot...?
Alternatively, In many motherboards their is also a hot-key for that, e.g In My HP ,their is an option "**F9=Boot option**" in Startup to Boot from CD/USB/HDD etc....

---

### Post by jordanC on 2011-01-28
Ive tried putting the USB at he top of the boot list in BIOS and i still only get a flashing blip in the top left, tried doing it through start up disc creator aswel but still no luck. Same thing happens with the cd inserted

---

