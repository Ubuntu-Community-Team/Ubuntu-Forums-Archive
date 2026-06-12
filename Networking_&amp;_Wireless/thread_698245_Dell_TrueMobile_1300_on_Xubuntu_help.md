---
title: "Dell TrueMobile 1300 on Xubuntu help"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by me (caleb) on 2008-02-16
I have a Dell Inspiron 1000 laptop with Xubuntu 7.04 installed.

I am trying to get my Dell TrueMobile 1300 wireless card (which came with the computer) 's driver installed. Because there is no Linux driver (that I could find) for this card I am trying to install the windows driver with NDISwrapper.

But, this is where the problem comes in, all of the guides for how to get a windows wireless card set up with NDISwrapper say that you have to use a .ini and a .sys file. The driver that I downloaded from Dell's website is a .exe. What should I do to get it to work?

---

### Post by Kawa800 on 2008-02-17
I am getting ready to install Ubuntu 7.10 on a D600 laptop so I am searching to see who had any problems.  I also have the TM1300 wireless card.  So I came across your post.  I am still running XP on the D600 so what I did is downloaded the latest driver (the .exe file you were talking about. I ran it in XP.  This created a folder in the Driver folder and puts all the files in it.  (Just pay attention when it tells you the path it is unzipping to).  I just canceled when it actually started installing the driver.  I will put the folder on my thumb drive, in case I need it.  And from what you are saying I think I will.  I hope you find this helpful. I am new to Linux and the Dell D600 will only be my 2nd installation. But I think this should work for you if you have access to an XP machine and can put the files on a thumb drive.  If we run into any problems after that, we will need to really on the more experienced help.

---

### Post by Kawa800 on 2008-02-18
Well my technique to get the .inf file out of the .exe file from Dell worked. However, when I go to install the driver nothing happened.  I also tried unrestricting the driver (need to hardwire to internet to get that to work).  Tried KevDog's instructions for manual configuration.  Still no go.  Let me know how you made out.

---

### Post by me (caleb) on 2008-02-28
Ya, I was able to get the .ini and .sys files out but I couldn't understand any of the instructions I found for how to install them. Could you tell me which one you followed?

---

### Post by Kawa800 on 2008-02-28
I ended up re-imaging and starting over.  I think I tried too many things and messed it up.  I did not need to use the .ini and .sys files.  The driver was recognized in System/Administration/Restricted Driver Manager.  I do not remember which instructions i used to unrestrict the driver.  But I think you can just follow the prompts.  The instructions I used after that are 

I am not sure if it was with the laptop or the desktop (both on wireless) but I had to go to System/Administration/Software Sources and check all the boxes on the first tab.  I believe I needed to be hardwired to the internet for that to work.

If you post what you have done so far and any errors that you recieved perhaps someone with more experience will have some better tips.

---

### Post by Kawa800 on 2008-02-28
I just noticed the link did not come through.  Here are the instructions I followed to get both the laptop and desktop wireless working.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

It is one of the sticky's on the Network & Wireless category

---

