---
title: "Waxy Windows to Lucid Ubuntu: Hard Drive/Partition left behind. Yikes!"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by RobHob on 2010-06-07
[SIZE=2][FONT=Book Antiqua]I took the plunge. No more Microsoft codependence. Anyway, figuring that the data (including programs) on my hard drive would be preserved, I only (and luckily) backed up all my media/documents[/FONT]. [/SIZE][SIZE=2][FONT=Book Antiqua]With supreme excitement, I proceeded to setup the wireless connection and get real comfortable with the switch. This is when things get hairy. Not possible. I realized that all my files from the previous system were erased[/FONT]. [/SIZE][FONT=Book Antiqua][SIZE=2]Because I've got my pictures and music saved, and all the programs can be reinstalled, I'm not super emotional . . . BUT, this loss includes [/SIZE][/FONT][FONT=Book Antiqua][SIZE=2]some of the 'stuff' (such as windows.inf) necessary to detect my wireless hardware (and it would be nice to recover some of the program data). I've spent countless hours trying to grasp on my own this sudden learning spike, but I really am lacking some of the unspoken fundamentals. For instance, I've gotten a live Rescue Remix CD to boot up, but I haven't a clue how to access the programs within it. Or how to use them if I did. I did some DOS back when I was like 8 years old, but this is a bigger and more serious beast. The whole 'sudo' thing has really thrown me for a loop. I do blame myself for not being informed before I jumped off the cliff in the first place, but that doesn't help solve the problem. Is there a good samaritan out there who's willing to give me a step by step of sorts? Or maybe someone knows of a source for important driver documents (like the wireless detectors) that would enable me to at least get on the web. I could settle at that. Thanks y'all. I hope I've been clear, and I apologize for not being more responsible.[/SIZE][/FONT][SIZE=2]
[/SIZE] [FONT=Book Antiqua][SIZE=2]Heart,
Rob[/SIZE][/FONT]

---

### Post by viralmeme on 2010-06-07
> **RobHob said:**
> [SIZE=1][FONT=Book Antiqua].. figuring that the data (including programs) on my hard drive would be preserved, I only (and luckily) backed up all my media/documents[/FONT].[/SIZE]


Nothing on the Windows partition will be erased unless you choose to erase it. The usual method is to select to *install* Ubuntu *side  by side*. The installer is quite explicid. What option did you choose?


[B][SIZE=2]* Install them side by side, choosing between them each startup

* Use the entire disk
! This will delete Microsoft Windows XP Professional and install Ubuntu 9.04[/SIZE][/B]

[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

---

### Post by RobHob on 2010-06-08
Because I was so ready to banish Windows altogether, I chose to use the entire disk. My thought was that this would only affect the OS/interface, with the existing programs/data still filtering through. I was under the impression that backing up this information was only necessary for cases of crash/error. I said, "This'll go fine", not understanding that going fine still meant losing it all. Like I said, the programs are replaceable, and I got my sentimental media. The biggest issue now is recovering the meat and potatoes necessary to make stuff like my wireless card work.

---

### Post by coldraven on 2010-06-08
I'm running Ubuntu 9.10 and this is how easy it is to get my wifi working.
Click on the network icon on the task bar at the top of the screen. This shows as an antenna with signal strength bars if a wifi connection is available or as two plugs if you are connected by a network cable.
If you see your wifi listed click on it.
The key that you need is probably on a sticker on your router.
If not you need to connect by cable to your router and using  Firefox set the key to something new.
The address that you need to put in the browser will be something like 
[http://192.168.2.1/](http://192.168.2.1/) or gateway.2wire.net (if you have a 2wire router).
You can Google for your make of router and get the correct address.

---

### Post by RobHob on 2010-06-08
Thanks, I will look into what you describe, but I think the problem is that the wireless card is simply not detected. I'd like to figure out how to get the computer to recognize that I have such a thing.

---

### Post by RobHob on 2010-06-08
[SIZE=4][FONT=Book Antiqua]I took the plunge. No more Microsoft codependence.  Anyway, figuring that the data (including programs) on my hard drive  would be preserved, I only (and luckily) backed up all my  media/documents[/FONT][/SIZE]. [SIZE=4][FONT=Book Antiqua]With  supreme excitement, I proceeded to setup the wireless connection and  get real comfortable with the switch. This is when things get hairy. Not  possible. I realized that all my files from the previous system were  erased[/FONT][/SIZE]. [FONT=Book Antiqua][SIZE=4]Because  I've got my pictures and music saved, and all the programs can be  reinstalled, I'm not super emotional . . . BUT, this loss includes [/SIZE][/FONT][FONT=Book Antiqua][SIZE=4]some of the 'stuff' (such as  windows.inf) necessary to detect my wireless hardware (and it would be  nice to recover some of the program data). I've spent countless hours  trying to grasp on my own this sudden learning spike, but I really am  lacking some of the unspoken fundamentals. For instance, I've gotten a  live Rescue Remix CD to boot up, but I haven't a clue how to access the  programs within it. Or how to use them if I did. I did some DOS back  when I was like 8 years old, but this is a bigger and more serious  beast. The whole 'sudo' thing has really thrown me for a loop. I do  blame myself for not being informed before I jumped off the cliff in the  first place, but that doesn't help solve the problem. Is there a good  samaritan out there who's willing to give me a step by step of sorts? Or  maybe someone knows of a source for important driver documents (like  the wireless detectors) that would enable me to at least get on the web.  I could settle at that. Thanks y'all. I hope I've been clear, and I  apologize for not being more responsible.[/SIZE][/FONT]
[FONT=Book Antiqua][SIZE=4]Heart,
Rob[/SIZE][/FONT]

---

### Post by _khAttAm_ on 2010-06-08
Does System>Administration>Hardware Drivers say anything about your Wireless card?

---

### Post by philinux on 2010-06-08
@RobHob, Threads merged. Please dont start multiple threads thanks.

---

### Post by viralmeme on 2010-06-08
> **RobHob said:**
> My thought was that this would only affect the OS/interface
What to the words **[SIZE=2]`Use the entire disk, This will delete Microsoft Window'[/SIZE]** mean in your universe?

---

### Post by tad1073 on 2010-06-08
open a terminal and type:
```
 lshw -C network 
```
and post it

---

### Post by HandyAndy on 2010-06-08
Hi Rob

First the bad news: by overwriting Windows you have deleted not only the operating system but all the programs and everything else, including, as you've found out, your wireless card driver, etc.

Now the good news. You have 3 options and you don't need all that stuff for any of them.

Option 1: Re-install Windows from your installation or rescue disc. Windows will do its thing and get everything working for you again. You may have to do some tinkering to get everything back the way you had it, but you did the sensible thing and backed up your data so you're ok. You're back in Windows land with nothing much lost.

Option 2: Forget Windows and carry on working on getting up and running with a fully functioning Ubuntu Linux system. You don't need any of your old Windows programs, drivers, configuration files, settings, etc because Ubuntu has its own equivalents. Not only do you not need the old Windows stuff, it won't work in Linux. You're in a new and beautiful world of Linux computing.

Option 3: Re-install Windows as in Option 1. It will overwrite Ubuntu just like Ubuntu overwrote Windows. Get everything working in Windows so at least you've got one OS functioning so that you can get on the Internet, etc. Then install Ubuntu again - but this time choosing the side-by-side option. This gives you both operating systems to choose from when you boot up. But they are totally separate systems and don't share any programs, drivers, etc. So you may find, for example, that Windows detects your wireless card but Ubuntu still doesn't. Or not at first. Booting into Windows you can come here and get all the help you need to get your Ubuntu system working fully. You've got the best of both worlds.

Option 3 - dual-booting - is what most of us do when we first make the switch to Linux. I've been using Linux exclusively for nearly 10 years and I still keep Windows as a back-up. With my data backed up to an external drive that both can access, I can keep working whatever happens.

Decide what you want to do and then come back here if you need more detailed instructions on how to accomplish whichever of the options you choose. Until you decide what you want, the advice people give you, though correct in itself, may not give you the result you're looking for.

I hope that helps.

Andy

---

### Post by RobHob on 2010-06-08
Sorry . . . didn't know. I thought I'd gazed through the etiquette thoroughly enough.

---

### Post by RobHob on 2010-06-14
Thanks! So simple, yet so . . . simple. At first, it did not say anything about my wireless card (in hardware drivers), but I noticed that the system was looking for internet help so that it could populate the list (failed to download packets, or something like that). It seems obvious that this information would have to be imported, and that no OS could come prepared to handle the mega-multitude of hardware out there. Luckily I have another computer with broadband through the phone line. I hooked my troubled laptop up to this network via ethernet cable, went back to the hardware drivers list, and voila! It establishes its magic connection, gets informed, and displays my wireless and video card as alive. All I had to do was activate each of them, and I'm back in business! Thanks to all y'all for caring and suggesting. I feel a little dumb after spending hours looking into programming and partitions and whining here, but, hey! Now I know.

---

### Post by RobHob on 2010-06-14
Right on. I got it (solution method listed). Now how do I change this thread to 'solved'?
Thanks again.

---

