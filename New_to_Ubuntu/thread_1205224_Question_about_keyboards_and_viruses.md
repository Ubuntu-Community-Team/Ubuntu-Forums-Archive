---
title: "Question about keyboards and viruses"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by to25 on 2009-07-05
I figured these may have been answered but I either cant find it or I didn't quite understand it. I am a noob and I just have a few questions. 

First my keyboard does not activate when the PC is turned on. It only works when I use the keyboard to boot ubuntu instead of windows, but if I let the computer sit and it automatically boots ubuntu the keyboard does not work. I am using a Gateway desktop, and the keyboard is a ps2 connection.

Secondly, I was surfing the web and you know those fake adds that make it seem as if you have a virus on you computer poped up. The funy thing is that they booted up a Windows window to show me I had a virus. I know its hard to get a virus on linux but just curious, do those pages put viruses on your pc and would it affect my pc sence it is linux. Also could I give it to a Windows user?

Sorry if these questions have been already asked.

---

### Post by sdlynx on 2009-07-05
> **to25 said:**
> I figured these may have been answered but I either cant find it or I didn't quite understand it. I am a noob and I just have a few questions. 

First my keyboard does not activate when the PC is turned on. It only works when I use the keyboard to boot ubuntu instead of windows, but if I let the computer sit and it automatically boots ubuntu the keyboard does not work. I am using a Gateway desktop, and the keyboard is a ps2 connection.

Secondly, I was surfing the web and you know those fake adds that make it seem as if you have a virus on you computer poped up. The funy thing is that they booted up a Windows window to show me I had a virus. I know its hard to get a virus on linux but just curious, do those pages put viruses on your pc and would it affect my pc sence it is linux. Also could I give it to a Windows user?

Sorry if these questions have been already asked.

I'm not sure about the first part but about the viruses the answer is no.  You cannot get a virus off of the internet.  And you can't give it to a windows user unless you give them a virus infected exe that one of the pop ups has you download and then have the windows user run that exe.

---

### Post by LinuxFox on 2009-07-05
I don't know about keyboards since I can't say that happened to me.  About those "virus" pop-up ads, they shouldn't affect you if you don't click on them.  I don't know what they would do on Linux, but I do know that they're made to trick people using Windows.

For example, I was using Ubuntu, and it came up as a Windows window, looking different than Ubuntu's windows.  It also said I had spyware, though I didn't (plus I scan regularly on my Windows partition).  These things trick people, since it makes them think they have spyware.

---

### Post by lisati on 2009-07-05
You might want to check your BIOS settings to see if your PS/2 keyboard is enabled.......



edit: I just realised, this sounds a bit like "Keyboard not detected. Press any key to continue." Oh dear!

---

### Post by SunnyRabbiera on 2009-07-05
> First my keyboard does not activate when the PC is turned on. It only works when I use the keyboard to boot ubuntu instead of windows, but if I let the computer sit and it automatically boots ubuntu the keyboard does not work. I am using a Gateway desktop, and the keyboard is a ps2 connection.

Hmm, what is the brand of keyboard here?
Not like it makes much of a difference, though as I would expect an error like this on a USB keyboard then a PS/2 one
> 
Secondly, I was surfing the web and you know those fake adds that make it seem as if you have a virus on you computer poped up. The funy thing is that they booted up a Windows window to show me I had a virus. I know its hard to get a virus on linux but just curious, do those pages put viruses on your pc and would it affect my pc sence it is linux. Also could I give it to a Windows user?


That is a scam website, I know exactly the site you speak of.
Its a crock of crap, if you did fool for the add and tried to buy the so called "antivirus" the site offers it would actually infect your (windows based) OS.
Its a very cleaver scam but overall still a scam none the less.

Linux is practically virus proof though you could unintentionally send someone a infected file if you dont know what you are doing.
But careful browsing habits will keep you safe.

---

### Post by user_not_expert on 2009-07-05
> **LinuxFox said:**
> About those "virus" pop-up ads, they shouldn't affect you if you don't click on them.  I don't know what they would do on Linux, but I do know that they're made to trick people using Windows.


One of my kid's friends panicked, downloaded and ran one on the family info/internet pc (dual boot WnXP and Mint with lots of shared partitions in fat32). Admittedly its a guest account with next to no privileges, but its had no effect that I can see on either the Linux or Windows platform. It just sits on the Mint desktop doing nothing until I can get round to untangling it from wine (its been there for months).

All the kid's friends know the one simple rule: only Linux goes on the internet (If you use Windows, you disconnect the network lead before booting), so Win never goes on line.

---

### Post by to25 on 2009-07-05
I am running a Gateway GT5062E, and I checked my bios and I will admit that I did not know what I was looking for. i tried looking for anything referring to keyboard or ps/2 but nothing. The only thing I found was numlock when boot. I have a phoenix award bios.  It has seemed to act up after an update. Any suggestions

---

### Post by cariboo on 2009-07-05
I would suggest trying a different keyboard.

---

### Post by to25 on 2009-07-06
Well before the update I was using an HP keyboard, but it suffered from the same problem so I switched to the PC's original keyboard and it was working up until recently. I am guessing that ubuntu is not detecting the keyboard until I press a button, but only before it boots. Any advice on how to get ubuntu to detect the keyboard on its own?

---

### Post by SunnyRabbiera on 2009-07-06
Well its a strange issue indeed, but actually it might be GRUB not reading the keyboard not Ubuntu.
Now logging into Ubuntu you get keybord support yes?
You said it was windows that was not picking the keyboard up in your original post.
If ubuntu is not picking up the keyboard its a strange issue indeed, Ubuntu has great keyboard support, even micosoft keyboards work on it and thats saying a lot.

---

### Post by to25 on 2009-07-08
Sorry for taking so long to post but my issue has been solved. With the installation of the most recent update My keyboard works fine again. To answer you question Sunny It was not working properly in ubuntu, i don't know why But at the same time it has been known to do this in the past with windows. Back then I would just reinstall the driver. Maybe I should invest in a new keyboard.

---

