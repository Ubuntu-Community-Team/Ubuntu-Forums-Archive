---
title: "Cooling fan running almost all the time."
date: 2011-06-11
forum: New to Ubuntu
---

### Post by gemma.laming on 2011-06-11
Hi everybody,
I have recently moved up from 9,04 to 10,04 and although the installation was fine, my cooling fan now runs almost constantly if my computer has been switched on for an hour or so.

It is a Lenovo T61 further I don't really know.

Can anyone help. please.

Gem

---

### Post by astrobob.tk on 2011-06-11
> **gemma.laming said:**
> Hi everybody,
I have recently moved up from 9,04 to 10,04 and although the installation was fine, my cooling fan now runs almost constantly if my computer has been switched on for an hour or so.

It is a Lenovo T61 further I don't really know.

Can anyone help. please.

Gem

Hello & welcome.

open a terminal & run:

```
acpi -t
``` to view the temperatures. Any my current is

53
49
55

Earlier (on a love 11.04) it reached 70.

If the terminal says that the package is not installed, just run:

```
sudo apt-get install acpi
```

You will be promoted for the user pass (you won't see anything being written).

This (acpi command) helps you know the temperature of your devices in case sensors exist.

If the temperatures are below 70 (acpi has the default 100) then its all normal & the fan is just doing its job ;)

Otherwise I can't help.

Update: did you update the system after the upgrade ? just try it, maybe it could help !!

---

### Post by gemma.laming on 2011-06-11
Thankyou for that neat piece of advice, Astrobob.:KS

I did not have acpi on board and did the sudo apt bit and after around fifteen seconds I had some answers!



The results I got were thermal 0 60 degrees and thermal 1 58 degrees - so by your reckoning it is okay.

Any ideas why the fan should be running - does Ubuntu 10 need more power to run?  

Perhaps my processor needs more coffee in the morning?  

Thanks for that, it was real fun to see it all happening!  Gemma :-)

---

### Post by VOT Productions on 2011-06-11
Also, if the cooling fan is running, it makes the laptop colder to touch as a small bonus.

---

### Post by astrobob.tk on 2011-06-11
> **gemma.laming said:**
> Thankyou for that neat piece of advice, Astrobob.:KS

I did not have acpi on board and did the sudo apt bit and after around fifteen seconds I had some answers!



The results I got were thermal 0 60 degrees and thermal 1 58 degrees - so by your reckoning it is okay.

Any ideas why the fan should be running - does Ubuntu 10 need more power to run?  

Perhaps my processor needs more coffee in the morning?  

Thanks for that, it was real fun to see it all happening!  Gemma :-)

You welcome :D

Well to be honest, I have come to realize that not only Ubuntu, but all OS including non-linux are requiring more power than ever (except for the bunch that are made for low performance computers). The only thing that I think you must take notice of is whether the fan goes into a slower (& thus quiter mode) or not.

Moreover, all this depends on what you are actually doing. Are there alot of process ? What kind of process ?
For example, earlier today, I was copying my /home directory as a backup by the cp -Rv command + listening to music & browsing. the temperatures remained under 60 with the fan on an acceptable speed & noise. While when I launch the game 'glest', the fan goes on on fast & noisy mode.

So in all, it is highly dependent on what you are doing; that is number of processes & what kind of processes. Of course higher graphics require higher power & performance & thus more heat is generated & more fan speed & performance is needed.

Note: The weather is kinda hot where I am now; given this, the fan is practically doing its job.

Tip: I discovered this (bug -not sure if its a bug yet, though i reported it as so). When i suspend or hibernate & bring the laptop back, i notice that a process launches (in the background) & takes a high (above 90%) cpu usage. This of course causes the fan to blow up; so killing the process (not any process of course) brings it back to normal.
I usually keep the command ```
top
``` run in a terminal to keep an eye on processes & memory/cpu usage.

---

### Post by gemma.laming on 2011-06-12
Thankyou for your very informative replies.  I checked my computer this morning, having just given it a mug of coffee (it was visibly wilting) and the temperatures are 52 and 53 degrees.

When I ran my old Ubuntu 9,04 I could have seven or eight applications running and only after a few hours the fan might kick in for a half hour or so.  That was acceptable.  

With 10, the fan comes on very quickly and that with three or four applications running.  I can understand that a modern OS takes more power, it is in the nature of things - a little like a drug addict needing more and more each day just to keep his eyes open.  

I tried your code - thinking that you had forgotten twenty lines of complex dots, semi-colons and double spacings.  No!  Out pops a matrix figures!  

So: at present using only firefox and the two terminal windows, one for the temperature, I am using 23% CPU and 4,2 memory whilst the firefox bin is using 4 to 10% and 18,9   It would have been useful to have been able to compare these to my last installation, 9,04.  However, as mentioned, the fan only came on in the most unusual of circumstances.  

There is one final thought - you mentioned as a last item -- and I can't quite remember the wording because I am on a new page -- "did you upgrade your system?"  Can I be an absoloute beginner here and ask precisely what you mean by this and how I might do something about it!  I presume you mean the hardware?  

Gem x

---

### Post by gemma.laming on 2011-06-12
Dear VOT Productions, 

thankyou for taking the time to respond.  I agree that my computer will be cooler for the fan running, but with my old 9,04 the fan barely ran at all, and now it runs for a lot of time.  

As much as anything, it is the noise of the fan. My computer must be four or five years old, which in the land of chips and processors is a veritable grandfather of computers.  

To be truthful, and with the exception of the NVU I use for my website, I could probably find an old iPhone more than adequate for my entire computing needs.  Indeed my son had a tiny Asus EEE which apart from its minute size, did all I needed of it. Probably more!  To give you an idea, my business files run to around 300Mb ... and that I consider excessive.  

Of course, it does not include photographs.  That has ballooned in the last year or so.  I have also put my CDs onto my hard disc.  So, grumpily I am becoming part of the digital revolution!  

I still  prefer good compost though!  Makes things grow nicely, and tastily (carrots that taste of carrot and not just the colour orange, which to my mind is a little bland).

---

### Post by VOT Productions on 2011-06-12
There are threads here:
[http://ubuntuforums.org/showthread.php?t=846480]("http://ubuntuforums.org/showthread.php?t=846480")
[http://ubuntuforums.org/showthread.php?t=340208]("http://ubuntuforums.org/showthread.php?t=340208")
[http://www.computing.net/answers/linux/ubuntu-and-fan-control/29483.html]("http://www.computing.net/answers/linux/ubuntu-and-fan-control/29483.html")
Good luck! I can't test any of them since I have a desktop.

---

### Post by astrobob.tk on 2011-06-12
> **gemma.laming said:**
> Thankyou for your very informative replies.  I checked my computer this morning, having just given it a mug of coffee (it was visibly wilting) and the temperatures are 52 and 53 degrees.

When I ran my old Ubuntu 9,04 I could have seven or eight applications running and only after a few hours the fan might kick in for a half hour or so.  That was acceptable.  

With 10, the fan comes on very quickly and that with three or four applications running.  I can understand that a modern OS takes more power, it is in the nature of things - a little like a drug addict needing more and more each day just to keep his eyes open.  

I tried your code - thinking that you had forgotten twenty lines of complex dots, semi-colons and double spacings.  No!  Out pops a matrix figures!  

So: at present using only firefox and the two terminal windows, one for the temperature, I am using 23% CPU and 4,2 memory whilst the firefox bin is using 4 to 10% and 18,9   It would have been useful to have been able to compare these to my last installation, 9,04.  However, as mentioned, the fan only came on in the most unusual of circumstances.

That's great.
Another tip: instead of opening 2 individual terminals, you could open tabs within the same window. I assume you're using the default gnome-terminal, simply known as "Terminal". If so just right click inside the terminal box & choose Open tab.

> There is one final thought - you mentioned as a last item -- and I can't quite remember the wording because I am on a new page -- "did you upgrade your system?"  Can I be an absoloute beginner here and ask precisely what you mean by this and how I might do something about it!  I presume you mean the hardware?  

Gem x

Well I was asking you if you have updated your system. Just run in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

These are just updates which might fix some software bugs or include new kernels (if indeed it contains a  new kernel, a reboot is needed after installing it).

P.S.: Check this thread for new comers to Ubuntu (even myself don't know all the stuff in here): [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

---

### Post by gemma.laming on 2011-06-12
Thanks both of you!  I will give it a closer look tonight - I went sailing this afternoon as it will rain tomorrow.

I hope the weather in Beirut is lovely, my best friend at uni came from B (she was French) she told me lots about it, or well this was before the civil wars, so I guess it is all different now.  

Again, thanks both.  Any problems I will give you a call :-)

Gemma xx

---

### Post by astrobob.tk on 2011-06-12
> **gemma.laming said:**
> Thanks both of you!  I will give it a closer look tonight - I went sailing this afternoon as it will rain tomorrow.


nice :D I'd like to try it out :D

> I hope the weather in Beirut is lovely, my best friend at uni came from B (she was French) she told me lots about it, or well this was before the civil wars, so I guess it is all different now.  

Again, thanks both.  Any problems I will give you a call :-)

Gemma xx

Interesting :D

well maybe it is different, but not that much lol.
Don't hesitate. :)

---

### Post by gemma.laming on 2011-06-16
Dear AstroBob and VoT productions,
I would like to ash you a serious question:  what is the point of upgrading to Ubuntu 10?

Ubuntu 9,04 was working relatively well, allowing for printers, peripherals and a firefox that was no longer supported.  

Ubuntu 10,04 - open office does not work so well, Firefox has crashed four times in two days, and the fan runs a lot of the time.  

In short, Ubuntu 10 is doing less well than 9 was, and had I any sense, would not have moved up from 8!  

What am I to do?!

Gemma

---

### Post by astrobob.tk on 2011-06-16
> **gemma.laming said:**
> Dear AstroBob and VoT productions,
I would like to ash you a serious question:  what is the point of upgrading to Ubuntu 10?

Ubuntu 9,04 was working relatively well, allowing for printers, peripherals and a firefox that was no longer supported.  

Ubuntu 10,04 - open office does not work so well, Firefox has crashed four times in two days, and the fan runs a lot of the time.  

In short, Ubuntu 10 is doing less well than 9 was, and had I any sense, would not have moved up from 8!  

What am I to do?!

Gemma

Good question. It's one i've been asking my self about upgrading or not from 10.04 LTS (which is working just as I wish) to 11.04.

As long as the version you're running is supported (which is in your case) -you can check the dates on releases & end of support at this wiki: [https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")-

You can see that 9.04 has already been discarded while 9.10 will still be supported until April 2011. The thing is that when it is no more supported, bugs will not be fixed & updates will no longer be maintained or sent thus putting your system at the risk of been vulnerable.

As for the performance of 10 (as you report), well I faced such situation when upgrading to a newer version but I have found out that this is just a matter of time & testing before updates fix it. 10.04 LTS is the best Ubuntu i have tried. So i decided instead of upgrading to 11.04, to install 11.04 on a small partition for testing or in as a virtual box & when am satisfied I might make a fresh install & replace 10.04 LTS, but I don't think I will get rid of 10.04 until 12.04 LTS comes out. I prefer the LTS (Long Term support).

---

### Post by gemma.laming on 2011-06-16
Thankyou for that!  It is nice to know that I am not the only one to wonder at these things.  

Gem x

---

### Post by collisionystm on 2011-06-16
Here is how to control your fan speed. I just tested this on my Dell desktop and it works.

[http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/](http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/)

---

### Post by mikewhatever on 2011-06-16
> **gemma.laming said:**
> Thankyou for your very informative replies.  I checked my computer this morning, having just given it a mug of coffee (it was visibly wilting) and the temperatures are 52 and 53 degrees.

When I ran my old Ubuntu 9,04 I could have seven or eight applications running and only after a few hours the fan might kick in for a half hour or so.  That was acceptable.  

...

A cooling fan not running for hours doesn't sound right. Generally, a fan should turn on every few minutes or so, which implies that it may not have been working properly with Jaunty. Could it be that the winter in Europe has been very cold? As for 10.04, do you running desktop effects? If so try turning them off.


> **collisionystm said:**
> Here is how to control your fan speed. I just tested this on my Dell desktop and it works.

[http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/](http://www.garryconn.com/linux/how-to-control-cpu-and-case-fan-speeds-on-a-linux-server/)

What dell laptop do you have? Did you get any output from pwmconfig? I've tried that on several notebooks, and pwmconfig always complains that about 'no sensors found'. All 'sensors-detect' finds is coretemp.

---

### Post by collisionystm on 2011-06-16
Well its a desktop. Dell Vostro 230

---

### Post by mikewhatever on 2011-06-17
> **collisionystm said:**
> Well its a desktop. Dell Vostro 230

Cool, and ...?

---

### Post by nrundy on 2011-06-17
Linux runs a lot hotter than Windows. Plus there is a current bug that is making it run even hotter. 

I've switched all my laptops over to Windows 7. 7 runs cooler, a lot quieter and you will get longer battery life.

Hopefully the heat issue will be addressed in the future of linux and it will run as cool as Windows. For the time being though there's not too much you can do.

Windows 7 on my netbook is running at 30 degree Celsius (sometimes cooler). When I ran Ubuntu 11.04, it was running at 55 degree Celsius.

---

### Post by mikewhatever on 2011-06-17
@nrundy
If W7 runs cooler on your hardware, by all means, don't feel bad using it. Obviously, this isn't generally the case, and also not the case with the OP. The recent kernels' power bug is also irrelevant, as the discussion revolves around 9.04 and 10.04 which are not affected.

---

### Post by astrobob.tk on 2011-06-17
> **nrundy said:**
> Linux runs a lot hotter than Windows. Plus there is a current bug that is making it run even hotter. 

I've switched all my laptops over to Windows 7. 7 runs cooler, a lot quieter and you will get longer battery life.

Hopefully the heat issue will be addressed in the future of linux and it will run as cool as Windows. For the time being though there's not too much you can do.

Windows 7 on my netbook is running at 30 degree Celsius (sometimes cooler). When I ran Ubuntu 11.04, it was running at 55 degree Celsius.

Highly unlikely; my system works fine on both Ubuntu 10.04 & Win7.
I was just testing CoD4-Modern Warfare under wine on Ubuntu & the temperatures did reach 68 but did not exceed 75.

Moreover. as stated, It is solely dependent on what you are doing & how much !!

---

### Post by jtarin on 2011-06-17
> **astrobob.tk said:**
> Highly unlikely; my system works fine on both Ubuntu 10.04 & Win7.
I was just testing CoD4-Modern Warfare under wine on Ubuntu & the temperatures did reach 68 but did not exceed 75.

Moreover. as stated, It is solely dependent on what you are doing & how much !!+1
Win 7 runs pretty buggy on some computers too. Match the OS (version)with the hardware and your needs. One size very rarely fits all, but in earlier versions of Ubuntu......it's a go.:p

---

### Post by fractalman on 2011-06-18
> **nrundy said:**
> Linux runs a lot hotter than Windows. Plus there is a current bug that is making it run even hotter. 

I've switched all my laptops over to Windows 7. 7 runs cooler, a lot quieter and you will get longer battery life.

Hopefully the heat issue will be addressed in the future of linux and it will run as cool as Windows. For the time being though there's not too much you can do.

Windows 7 on my netbook is running at 30 degree Celsius (sometimes cooler). When I ran Ubuntu 11.04, it was running at 55 degree Celsius.

ARE YOU FOR REAL??  sorry but i really do i have to disagree here, windows caused my pc to all but meltdown fukushima style, since using ubuntu 10:10 and then 11:04 i have not had a problem with the fan coming on at all apart from the following

@Gemma,    when i first installed 10:10 my fan would always come on, i changed the graphics driver and it sorted itself out,  you could always try 11:04 instead of 10:04 and see if the problem still persists.

---

