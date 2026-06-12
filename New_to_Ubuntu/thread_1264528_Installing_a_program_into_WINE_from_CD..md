---
title: "Installing a program into WINE from CD."
date: 2009-09-12
forum: New to Ubuntu
---

### Post by Dave W. on 2009-09-12
Hello,

Here is my story.  I think that I have successfully installed WINE and I would like to use the CD that came with my printer to install my printer on my system.  There are no drivers for it in linux. The printer is a Lexmark P4350.

I believe that I have successfully configured wine to XP defaults.  

Now here is where I am lost.  (I think.)

When I open the CD,  I looked for the SETUP.EXE file and open it with the windows program loader.  I then get the install box for my printer and when I click on install a box pops up and tells me that the "spooler service is not started" and I am given an option to start it.  I click "yes" and nothing seems to happen.

I think that I missed something in my configuring.    Any suggestions?

Thanks,
Dave

---

### Post by llamabr on 2009-09-12
[http://www.google.com/search?q=P4350+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=P4350+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

Wine is very rarely the correct solution, and this case is no exception.

Allow me to do you a favor.  Don't waste the rest of your saturday fighting with this printer.  It will not work.  But a printer that's supported by ubuntu, or more specifically, buy a printer whose manufacturer publishes a linux driver.

---

### Post by Dave W. on 2009-09-12
llamabr,

I know deep down in my heart you are probably right.  I was trying to save some money and try this option first.  I really don't want to waste my Sat. in the basement... away from my family...

Thanks,

Dave

---

### Post by NexusZA on 2009-09-12
> **Dave W. said:**
> Hello,

Here is my story.  I think that I have successfully installed WINE and I would like to use the CD that came with my printer to install my printer on my system.  There are no drivers for it in linux. The printer is a Lexmark P4350.

I believe that I have successfully configured wine to XP defaults.  

Now here is where I am lost.  (I think.)

When I open the CD,  I looked for the SETUP.EXE file and open it with the windows program loader.  I then get the install box for my printer and when I click on install a box pops up and tells me that the "spooler service is not started" and I am given an option to start it.  I click "yes" and nothing seems to happen.

I think that I missed something in my configuring.    Any suggestions?

Thanks,
Dave

Let me, if I may, give a little insight into why this would never work as well.

Drivers are low level little bits of software that get the operating system to talk nicely with hardware. Drivers made for Windows talk directly to the Windows kernel, etc to allow aprinter to run. The exact thing happens in Linux. Trying to get Windows drivers to talk to Linux is like trying to squeeze a round peg through a square hole, its just not compatible in any way shape or form. The reason Wine works for other programs is that most Windows programs don't get as "low" as drivers do to the operating system so Wine can succesfully "trick" this software into thinking its running on a proper and full version of Windows.

My experience has generally been that if the hardware does not work immediatly after plugging in or restarting Ubuntu, then it won't work. You may be able to get hacks but these are usually very horrid things to do to your poor machine.

---

### Post by Dave W. on 2009-09-12
Nexusza,

Thanks,  I appreciate your input.  I don't like to quit, but I don't like to hit myself in the head with a hammer either.:)

Wine has been removed.

Dave

---

