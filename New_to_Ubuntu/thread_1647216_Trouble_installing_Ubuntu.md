---
title: "Trouble installing Ubuntu"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Masked Avenger on 2010-12-17
I am putting together a computer for my first time and I have picked ubuntu to operate it. I am having some trouble booting from a CD though.
 
When I boot up first my screen displays a large ad for my motherboard of sorts.
 
Then a purple screen appears with a small rectangle and a man in a circle at the bottom. 
 
At this point if I hit any key the Welcome menu comes up and asks me for my language.
 
If I select any option my monitor switches from analog to digital back to analog and my LED keyboard blinks
 
There is a very quick copyright page shown after that and then we start back again at the mobo page.
 
I've tried two CDs already and I am out of ideas any suguestions?

---

### Post by Rubi1200 on 2010-12-17
Hi and welcome to the forums :)

What graphics card do you have installed?

It would also be helpful if you could post the full specifications for the machine in question.

Thanks.

---

### Post by candtalan on 2010-12-17
> **Masked Avenger said:**
>  When I boot up first my screen displays a large ad for my motherboard of sorts.

This sounds like the motherboard talking to you as you suggest. At an early stage like this you will be able to enter the motherboard bios settings if you need to. Usually a key press, DEL, or F2 or something, depends on type.
>  Then a purple screen appears with a small rectangle and a man in a circle at the bottom. 

This is the live CD initially booting. You see symbols suggesting that a keypress will do something..... If you do not press a key, then the  CD should continue for some time until it gets to a screen offering both a language choice and a choice between 'Try me' and 'Install me'.
>  At this point if I hit any key the Welcome menu comes up and asks me for my language.
 this is normal, but you should also expect to then immediately see a CD boot menu with the top option 'try Ubuntu without changing your computer'
>  If I select any option my monitor switches from analog to digital back to analog and my LED keyboard blinks
There is a very quick copyright page shown after that and then we start back again at the mobo page.

If your CDs are good, then something is strange about your graphics card and your display monitor. At that stage, the display is only a text list, there is no fancy graphics requirement. Although I do not know exactly what the CD will be trying to run graphics wise.
>  I've tried two CDs already and I am out of ideas any suguestions?
Check the CDs in another machine. They have a self check (in the initial menu that you are not yet getting to view), and you can yourself run an md5 check too. If they are ok, consider the new machine CD drive function. Consider at least viewing the new machine bios settings, this is a similar display requirement to the Ubuntu boot menu which you are not getting to reach.
hth

---

### Post by amjjawad on 2010-12-17
> **Rubi1200 said:**
> Hi and welcome to the forums :)

What graphics card do you have installed?

It would also be helpful if you could post the full specifications for the machine in question.

Thanks.

+1

And I assume you checked the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") for your downloaded iso for Ubuntu, right?

---

### Post by Masked Avenger on 2010-12-17
> **Rubi1200 said:**
> Hi and welcome to the forums :)
 
What graphics card do you have installed?
 
It would also be helpful if you could post the full specifications for the machine in question.
 
Thanks.
[IMG]http://i54.tinypic.com/nod5yc.jpg[/IMG]
 
I just bought this thing only a couple weeks ago and finished putting it together last night.

---

### Post by Rubi1200 on 2010-12-17
This link refers to the 10.04 version, but the procedure remains the same:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

I believe you need to try either the nomodeset or xforcevesa options.

Let us know what happens please.

---

### Post by Masked Avenger on 2010-12-17
> **Rubi1200 said:**
> This link refers to the 10.04 version, but the procedure remains the same:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
 
I believe you need to try either the nomodeset or xforcevesa options.
 
Let us know what happens please.
 
I tried both (deleting the quite slapsh text and typing each in its place. Got the same results.
 
Here is a little video of what exactly is going on, maybe it will help a bit.
 
[http://www.youtube.com/watch?v=ws2oVyhiENk](http://www.youtube.com/watch?v=ws2oVyhiENk)

---

### Post by candtalan on 2010-12-17
Definately check the CD and the CD drive. CD md5 check in a working machine, and cd drive with  - any test is better than none - but ideally try the CD drive in a working machine.

---

### Post by Masked Avenger on 2010-12-19
I am working on checking the CDs
 
Also, I tried using a UBS stick to do the job, and downloaded the program the website instructed me too, it gave me an error message.
 
What is curious is I just got the same error message when downloading InfraRecorder and running it.
 
[IMG]http://i56.tinypic.com/ao9m53.jpg[/IMG]
Does this have any significance?

---

### Post by Masked Avenger on 2010-12-22
So it seemed everything I downloaded on this laptop was ending up corrupted. I took the time to download Ubuntu again on another computer. I then burned a disc and installed a copy onto a brand new USB drive.
 
When booting the disc instead of the previous run around I am not stuck on a black screen with a single "." on it.
 
When I boot from the UBS the welcome screen loads automatically, and looks a little more clean than it does on the disc. It does not ask me to select a language.
 
When I try any option from the USB I get a long string of text. I took another video of it to help.
 
[http://www.youtube.com/watch?v=BPp0Zu2kvwg](http://www.youtube.com/watch?v=BPp0Zu2kvwg)

---

### Post by RedRat on 2010-12-22
Since you say that you are building this yourself, please provide for us the make of motherboard, memory (amount and type), CPU, etc. More information about your physical machines would help diagnose various problems here. 

Further, I am somewhat conservative when it comes to advice for beginners, I would suggest that you try loading Ubuntu 10.04 LTS and not 10.10. The way to look at 10.10 until it reaches the next LTS, is that these are tests or betas for the next LTS release. In this case it will be in 2012. Now sometimes, these progressive betas present no problems but a quick perusal of this forum and you will see that 10.10 has caused problems for adopters. The same happens with later versions. 

Now if you are game for playing the troubleshooting game, go ahead with 10.10 but since you are building a new machine, I would first start with 10.04LTS, get it running and operating, get a few hours of Ubuntu under you belt and then upgrade, if you want, to the newer release. But do not be surprised if you have hitches. Ubuntu keeps getting better and beter with each release, but it ain't perfect yet.

---

### Post by Masked Avenger on 2010-12-23
[Edit: Update] It seems that using that 32bit was what I should have gone with. Booting it live from the USB got me a loading page then black but the installation seems to be working ok. Fingers crossed for good results thanks so much guys.
 
 
> **RedRat said:**
> Since you say that you are building this yourself, please provide for us the make of motherboard, memory (amount and type), CPU, etc. More information about your physical machines would help diagnose various problems here. 
 
Further, I am somewhat conservative when it comes to advice for beginners, I would suggest that you try loading Ubuntu 10.04 LTS and not 10.10. The way to look at 10.10 until it reaches the next LTS, is that these are tests or betas for the next LTS release. In this case it will be in 2012. Now sometimes, these progressive betas present no problems but a quick perusal of this forum and you will see that 10.10 has caused problems for adopters. The same happens with later versions. 
 
Now if you are game for playing the troubleshooting game, go ahead with 10.10 but since you are building a new machine, I would first start with 10.04LTS, get it running and operating, get a few hours of Ubuntu under you belt and then upgrade, if you want, to the newer release. But do not be surprised if you have hitches. Ubuntu keeps getting better and beter with each release, but it ain't perfect yet.
 
I gave the stable version a shot on the USB... pretty much similar results
 
MSI Page
Instant Welcome Boot
Digital - Analog - Digital
Back to Welcome Screen
 
that holds for most of the menu options.
 
I am also downloading the 64bit would 32 work better?
 
Computer Specs:
Chip:
**Intel Core i3-530 Clarkdale 2.93GHz 4MB L3 Cache **
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115222](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115222)
 
GPU:
**Radeon HD 5770 (Juniper XT) 1GB 128-bit GDDR5 PCI Express **
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150447](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150447)
 
RAM:
**OCZ Platinum 4GB (2 x 2GB) 240-Pin DDR3 SDRAM **
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820227478](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227478)
 
HD:
**SAMSUNG Spinpoint F3 HD502HJ 500GB 7200 RPM **
[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152181](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152181)
 
Mainboard:
**MSI P55-GD65 USB3 LGA 1156 Intel P55 USB 3.0 ATX Intel Motherboard**
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130272](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130272)

---

### Post by Masked Avenger on 2010-12-23
I am going to bump this one more time to say thank you to everyone who offered a hand. Of course in the technology world the easiest solution is the right one. 
 
I have one last question and I will try to figure as much else out on my own. I am trying to install my various drivers at this point, but the OS doesnt autorun the discs and when I try to run it it tells me "can not find autorun program" 
 
Currently I need to go out and buy a new wireless card to get this desktop hooked to the net so maybe after then I can download some drivers but thats still an issue worth fixing.
 
Much love Ubuntu users.

---

### Post by RedRat on 2010-12-23
Masked Avenger
Your machine is pretty straight forward and good parts. Your CPU is a 64bit so 64bit Ubuntu ought to work. I really do not understand what is going on here. Before you buy the wireless card, do check out the compatibility with Ubuntu for certain chip sets. Perhaps some others here can help who are more conversant with current MB and chips.

---

### Post by Rubi1200 on 2010-12-23
You can also look here for more information:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

There are links under each section.

---

### Post by Masked Avenger on 2010-12-23
> **RedRat said:**
> Masked Avenger
Your machine is pretty straight forward and good parts. Your CPU is a 64bit so 64bit Ubuntu ought to work. I really do not understand what is going on here. Before you buy the wireless card, do check out the compatibility with Ubuntu for certain chip sets. Perhaps some others here can help who are more conversant with current MB and chips.
 
Yeah I was pretty certain that I was compatable with 64bit but as soon as I ran the 32 with no extra commands it installed right away with no real problems.  
 
> **Rubi1200 said:**
> You can also look here for more information:
[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
 
There are links under each section.
 Many thanks

---

### Post by theozzlives on 2010-12-23
> **Masked Avenger said:**
> Yeah I was pretty certain that I was compatable with 64bit but as soon as I ran the 32 with no extra commands it installed right away with no real problems.  


I think you were the victim of a bad download, or a bad burn. You really should consider 64 bit with 4 GB RAM.

---

### Post by amjjawad on 2010-12-23
> **theozzlives said:**
> You really should consider 64 bit with 4 GB RAM.

[http://en.wikipedia.org/wiki/64-bit#Pros_and_cons](http://en.wikipedia.org/wiki/64-bit#Pros_and_cons)

---

