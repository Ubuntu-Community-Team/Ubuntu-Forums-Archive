---
title: "LED Monitor"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by COMPUTIAC on 2011-03-14
Hello, I am planning on replacing my DELL 18' (CRT) monitor with a LED monitor.

  I would like to know which ones are compatible with Ubuntu 10.10 .

My machine is a HP-Compaq dc5000 mt ,  1G memory , updating to 4G shortly.  3G processor.

  Do I need to up-date the power supply also, if so , how do I find out what is in it now without pulling it apart ?

I am open to suggestions . Is anyone using one now ?

   Thank's

---

### Post by Grenage on 2011-03-14
> **COMPUTIAC said:**
> Hello, I am planning on replacing my DELL 18' (CRT) monitor with a LED monitor.

  I would like to know which ones are compatible with Ubuntu 10.10 .

My machine is a HP-Compaq dc5000 mt ,  1G memory , updating to 4G shortly.  3G processor.

  Do I need to up-date the power supply also, if so , how do I find out what is in it now without pulling it apart ?

I am open to suggestions . Is anyone using one now ?

   Thank's

Compatibility isn't an issue, so don't worry about that.  The monitor won't be drawing any power from your PC unless you've got one of those 'pass-through' PSUs, and even then, TFTs use less power than CRTs.

You only really need to make sure than the graphical connector is the right type; you can get adapters, but it's easier if you don't need one.  HDMI/VGA/DVI are the main interface types, with DVI and VGA being the most common.  Some monitors come with two or three interfaces, some come with one; if the latter, make sure it's the same as your PC.

---

### Post by grahammechanical on 2011-03-14
A lot also depends on the video or graphic card in your computer. How much memory does it have? How fast is the GPU in the card?

The new monitor might be capable of High Definition video display but if you want to watch High Definition DVDs do you have a DVD drive that can read those type of discs? And can the video card deliver what you want?

Ubuntu can work with the hardware but no operating system can give you what the hardware cannot deliver.

Regards.

---

### Post by Old_Man_Unix on 2011-03-14
Monitors are very straightforward to connect.  If you're video is working properly, you will have no problem.  All the video interfaces include hand-shaking protocols to set the parameters.  But if for some reason you don't like the settings, you can always change them.

We've never had a problem switching displays on Ubuntu - on on other Linux distros or any  different releases of Windows.   I would think the same would be true of any other modern OS on Intel-like architectures.

---

### Post by Mark Phelps on 2011-03-14
The only issue you might run into, if you get one of the new super-wide monitors, is setting the resolution.  The available resolutions are established by the video drivers.  If you're using one of the recent ATI cards (HD 3x/4x/5x) or newer Nvideo cards, then you should be able to load the drivers needed.  But if you're using one of the older "legacy" ATI cards, you will be limited to the open-source drivers, and they might not provide the newer super-wide resolutions.

---

### Post by coolbrook on 2011-03-14
I'm happy with my Viewsonic Vx1932 as it only consumes 15 watts.  You may prefer to find a newer model that has a 1920x1080 resolution and at least an HDMI input.  There are some that are low energy consumers.

---

### Post by COMPUTIAC on 2011-03-14
Hello, Thank's for all the replies and info.  I have been looking at Samsung , I don't remember what model right now.

  They are around 20", wide screen, don't think super wide.  I like these so far 'cause of the adjust-ability (height & tilt +) and they have different settings for brightness to dim them down and thus save more power.

  If anyone has any suggestions as to other makes and models with similar features , please post them. 

How do I find out which video card I have now , what should I up-grade too .  My machine was built in June '02 I believe.

  I want to do this up-grade of my machine only one time and want to have everything I need before I start , so I don't have to stop in the middle and run out and get another part.

  Is there anything else I should look at or do in advance of this project ?  I am doing the memory up-grade, just waiting for Crucial to get back to me .


  It is 21.5", can be seen here;  [http://www.samsung.com/us/computer/monitors/LS22CLUSFY/ZA-features](http://www.samsung.com/us/computer/monitors/LS22CLUSFY/ZA-features)

      Thank's

---

### Post by Grenage on 2011-03-14
From a command line:

```
lspci | grep VGA
```

---

### Post by COMPUTIAC on 2011-03-14
Hello, this is the result :

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

  Will this be OK  or should I up-grade ? To what ?

     Thank's

---

### Post by Grenage on 2011-03-14
> **COMPUTIAC said:**
> Hello, this is the result :

VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

  Will this be OK  or should I up-grade ? To what ?

     Thank's

I really couldn't say if your chipset could hit the native res of the monitor you are looking at.  It might make it, but I wouldn't risk the cash finding out.  I had a (very) brief look on google; there were a few posts from people who could not.

---

### Post by COMPUTIAC on 2011-03-14
Hello, could you explain that further ?

  (  I wouldn't risk the cash finding out )

  Thank's

---

### Post by Grenage on 2011-03-14
TFT monitors general look great at their native resolution, and bloody awful at any other resolution.  If your graphics card can't provide the native resolution, you'll be very disappointed with the display.

---

### Post by COMPUTIAC on 2011-03-14
Hello, so you are saying what ?     I need to change the card ?   Is there any way to tell if it will work with the new monitor , now ?

 If this is the case what should I get ?

  Thank's

---

### Post by Grenage on 2011-03-14
I imagine that the chipset is probably capable of reaching that resolution, but I've not had enough experience with them to say "This will work".  It's not my money, and I'd feel pretty bad if it didn't.  In the UK we have laws that allow us to return items, but we have to pay a restocking fee.

Come to think of it, I believe I configured a Windows machine with the same chipset on a 22" monitor.

---

### Post by COMPUTIAC on 2011-03-14
Hello,  yes pretty much the same law here also.   I would just like to know in advance though !

  I guess I will have to keep looking .

Intel site has a utility to check for the chip-set, but don't know if I can download it and run it .  Any ideas ?

   Thank's

---

### Post by Grenage on 2011-03-14
> **COMPUTIAC said:**
> Hello,  yes pretty much the same law here also.   I would just like to know in advance though !

  I guess I will have to keep looking .

Intel site has a utility to check for the chip-set, but don't know if I can download it and run it .  Any ideas ?

   Thank's

If it's a download, then I'm assuming that it's a Windows exe?  You're a little out of luck there, unless you go the Wine route, and I don't know if that would skew the results.

Having another look, it does seem more promising - but that's about as helpful (or as assuring) as I can be.

---

### Post by COMPUTIAC on 2011-03-14
Hello, Yes , you are right, its a win.exe, could not find a Linux base utility. 

   I took out all the WINE and programs associated with it a few days ago !

 There must be a way to find out what the chip-set is.  I will keep looking around.

  Thank's for all your help and time with this.

---

### Post by COMPUTIAC on 2011-03-14
Hello, the chip-set is: 865GV .     Power supply is: 240w. ATX

  Hope this helps in receiving more info.

     Thank's

---

### Post by coolbrook on 2011-03-14
[http://h18000.www1.hp.com/products/quickspecs/11876_div/11876_div.html](http://h18000.www1.hp.com/products/quickspecs/11876_div/11876_div.html)

You have the Micro tower. Do you have any (PCI) slots unoccupied at the back?  An entry level PCI card is all you need for a DVI (or HDMI) connection to a LED.

---

### Post by COMPUTIAC on 2011-03-14
Hello,   I must have , it shows 3 low and 3 full height slots.

  If I remember right, there is only a dial-up card in it , which I will remove any way.

  What are you suggesting ?

---

### Post by coolbrook on 2011-03-14
A basic PCI video card that has a DVI and/or HDMI output.

The EVGA GeForce 6200 w/ 512 MB RAM may be the best bang for the buck. I'm content with NVIDIA based cards like that one.

BUT... 

[http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML](http://h18000.www1.hp.com/products/quickspecs/11876_na/11876_na.HTML)

if you click on that link and then the 'Technical Specifications - Graphics' hyperlink, then you'll see that you don't need a new card right away.  You have a number of resolution options, including 1920x1080.  You just need the LED monitor and they tend to include a D-sub (VGA to DVI) cable or VGA cable that you can hook up to the port you've been using.

---

### Post by COMPUTIAC on 2011-03-14
Hello ,  Great !    You are right, I did not click on any of those links.   I can't explain why.

  Must be having a _Senior Day_ . all day today !

Yes, they do come with the VGA cable, some come with other cables also.

   Thank's for pointing this out to me.

---

