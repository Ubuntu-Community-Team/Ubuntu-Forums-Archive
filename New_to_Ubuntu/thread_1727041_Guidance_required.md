---
title: "Guidance required"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by GridLynx on 2011-04-12
Greetings.

Being new to the forums and to the OS itself, i was looking for some proper honest suggestions ( Unbiased ) about a possible migration i intend to do form Windows XP to Ubuntu. 

Ever since i tried the recent stable version ( Maverick Meerkat)  I have been fascinated with the performance it had on my laptop as well as the vast library of ready to install software in the Ubuntu software center... but neverthless nothing is completely bliss and joy and i started to notice it when i found out some of the software i use for my college activities is not native to the Linux Kernell  ( sure... i have heard about wine and virtual box but still..) 

At any rate,  I hope this isn't way too much to detail in a post but, i was hoping to get a good professional/honest ( Not fanatic!) feedback in certain of aspect i would like to know about the OS, regarding software equivalents, capabilities, pro's and cons... 

* Electrical engineering analysis tools:
This is the list of the current ones i use:
- Microsim Release 8
- Proteus 7 professional
- Xilinx ISE Design suite ( current version)
- MPLAB IDE
- Simulink

I would like to know if there are Free software equivalents to these or if there is a way to emulate them without too much of a hassle.

Also another factor i seek is driver compatibility with PIC and CPLD/FPGA programming hardware... Do i need to virtualize to make these work?

* Gaming and leisure ware.

Let's be honest.. who doesn't like wasting time with one of those! 

Being in a quite average to low specs laptop : 1.60 ghz centrino duo with 2 gbs of ram and an intel mobile graphics 945 gm with 128 of video ram; I am quite chained to old stuff ( currently gaming Guild wars, Half life 1.6, counter strike 1.6 , swat 4 etc...)

Will i have to sacrifice those in the sake of a better OS ? or will i  be able to still keep on gaming them without too much of a performance decrease?

- Overall gents, i hope you can help me with those two points that interest me the most but if you have any other suggestion or statement on why i should definetly migrate to Ubuntu, or if should stay with my trusty XP, I am all ears! 

I hope i posted in the right folder.. but if not, bear with me! i am a newbee.

Thank you beforehand! ;)

EDIT: URGH.. i just realized there was a branch in the forum for absolute begginer talk.. is there a way to move this over there?

---

### Post by mastablasta on 2011-04-12
> **GridLynx said:**
>  
* Electrical engineering analysis tools:
This is the list of the current ones i use:
- Microsim Release 8
- Proteus 7 professional
- Xilinx ISE Design suite ( current version)
- MPLAB IDE
- Simulink

 
never heard or used any of these. However oyu could give Wine a try. Their applicaiton database and how they work is found here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
Though i am sure there are some alternatives to this software.
> 
* Gaming and leisure ware.
 
Being in a quite average to low specs laptop : 1.60 ghz centrino duo with 2 gbs of ram and an intel mobile graphics 945 gm with 128 of video ram; I am quite chained to old stuff ( currently gaming Guild wars, Half life 1.6, counter strike 1.6 , swat 4 etc...)
 
Will i have to sacrifice those in the sake of a better OS ? or will i be able to still keep on gaming them without too much of a performance decrease?
 
Some of those run via wine without much performanse loss (again see their sites on how compatible games are). There is a playonlinux GUI for easy install. Some games have linux clients. but not so many.
 
The biggest issue might be Intel graphics card. 9x series - i am not sure about their linux driver quality. but if you say it all works fine in live version....
 
An option would be to dual boot and then boto to WinXP only when you need your specific software. it would also give you a better ground for testing out the things you need. you will need to dedicate at least about 25-30 GB disk to the OS if oyu plan on runnign Wine and games in it.

---

### Post by Elfy on 2011-04-12
moving to ABT
> 
EDIT: URGH.. i just realized there was a branch in the forum for absolute begginer talk.. is there a way to move this over there? Look over <- see at the bottom of each post the Report Abuse button - you can use that to ask for a move.

---

### Post by stinkeye on 2011-04-12
> **mastablasta said:**
> never heard or used any of these. However oyu could give Wine a try. Their applicaiton database and how they work is found here: [http://appdb.winehq.org/](http://appdb.winehq.org/)
Though i am sure there are some alternatives to this software.

Some of those run via wine without much performanse loss (again see their sites on how compatible games are). There is a playonlinux GUI for easy install. Some games have linux clients. but not so many.
 
The biggest issue might be Intel graphics card. 9x series - i am not sure about their linux driver quality. but if you say it all works fine in live version....
 
An option would be to dual boot and then boto to WinXP only when you need your specific software. it would also give you a better ground for testing out the things you need. you will need to dedicate at least about 25-30 GB disk to the OS if oyu plan on runnign Wine and games in it.

Definitely dual boot.
Within 3 months I wasn't using XP at all except for one FPS game I'm addicted to.
If you can't get the programs (or equivalent on Linux) you need just keep
using XP and explore Ubuntu.

---

### Post by Elfy on 2011-04-12
Those are all pretty specific apps you're looking for alternatives to.

I'd suggest going to each one to see if there's a forum there and searching for linux - I looked at the Proteus 7 one 

[http://support.labcenter.co.uk/forums/viewtopic.php?f=9&t=314&p=12757&hilit=linux#p12757](http://support.labcenter.co.uk/forums/viewtopic.php?f=9&t=314&p=12757&hilit=linux#p12757)

Sort of a bit of a hit - but as with most Wine things there could be problems.

---

### Post by GridLynx on 2011-04-12
Thank you for the quick feedback! 

I was on my way to bed when i decided to re-read my thread to see if anyone had a suggestion on my dilemma.

I am glad that Proteus is running fine under Ubuntu, that's quite a big wig of a program for microcontroller/processor simulation ( as well as some basic electronics). Another good thing is that the compiler for PIC programs ( MPLAB IDE) seems to work well under wine.. and looking around the forum i found out there is an equivalent! [http://piklab.sourceforge.net]("http://piklab.sourceforge.net/") Piklab!

Anyways, it's pretty late so i will check further responses tomorrow, Thanks once again.

---

