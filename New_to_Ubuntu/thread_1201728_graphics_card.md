---
title: "graphics card"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by davidpnuk on 2009-07-01
i installed ubuntu 9.0 and found the graphics card was only supported up to 800 * 600 which was no good i use 1024 * 768 i couldn't get it to go to 1024 * 768 i have now uninstalled this and am using windows xp there were other things that didn't work such as my modem this has the same faults as vista had also it ran slow no good for me

---

### Post by Idefix82 on 2009-07-01
Are you asking for help? If so then what is your question? If you want help with getting your graphics card to work then you should at least be in Ubuntu so people can tell you what to try.

If you don't want any help or want help on Win XP then this is not the right section of the forums.

---

### Post by AoSteve on 2009-07-01
You need to do two things,  first list your graphics card for us to use to compare with the HCL(Hardware compatibility List) and then you need to explain your problems a little more.

Most graphics problems are simple driver issues that can be fixed with a few edits of a file or even sometimes the installation of a restricted driver.  :)

---

### Post by linoob13 on 2009-07-01
I had the same 800x600 res problem with my notebook but found a setting for the xorg.conf file that fixes it - res now 1024x768 :p

If you want it - just ask

---

### Post by davidpnuk on 2009-07-04
i have an nvidia geforce 6100 graphics card it works fine on both xp and vista but on ununtu the highest resolution i can get is 800 * 600 how can i get 1024 * 768 please do not get technical as i am not bill gates i am not a computer wizard so i would appreciate any help from anyone here but like i said no technicalities please as i am not a computer nerd it wasn't long ago i thought windows was what you had in your house etc what you cleaned and looked out of

---

### Post by davidpnuk on 2009-07-04
xorg.conf file what does that mean computers are double dutch to me

---

### Post by davidpnuk on 2009-07-04
> **linoob13 said:**
> I had the same 800x600 res problem with my notebook but found a setting for the xorg.conf file that fixes it - res now 1024x768 :p

If you want it - just ask


okay would you give me the setting but i am not a technical person why do you have to do all this with windows everything just works and that's it

---

### Post by Idefix82 on 2009-07-04
> **davidpnuk said:**
> why do you have to do all this with windows everything just works and that's it

The reason is very simple: because Windows has such a huge market share that the hardware manufacturers optimise their hardware for Windows. They provide the drivers themselves and if their hardware doesn't work perfectly under Windows then they either fix it or don't even try to sell it. Ubuntu developers on the other hand have to write the drivers themselves and the hardware manufacturers often don't even provide sufficient specification of how their hardware works. Under these circumstances, the fact that most modern hardware works on Linux out of the box is an amazing feat. If something doesn't work then the Linux developers are certainly not the ones to blame.

---

### Post by AoSteve on 2009-07-04
Here's an excellent start for you davidpnuk.   Xorg.conf is usually the biggest problem new users come into.  However, once you learn how to control X and configure it properly, it tends to never be a hassle again.

[**HOWTO: change resolution/refresh rate in Xorg**]("http://ubuntuforums.org/showthread.php?t=83973&highlight=howto+screen+resolutions")[B] by: heimo    


[/B]This is a common problem for new people in linux.  Ubuntu probably has the "Easiest" ways to fix it but either way, it's still common.   Don't frustrate with it to much as it's an easy fix.  And for a lot of users, this is one of the biggest problems they ever encounter!   So give that guide a read and post back your findings and if it helped you solve the problem!  Good luck bud!

---

### Post by davidpnuk on 2009-07-04
> **AoSteve said:**
> Here's an excellent start for you davidpnuk.   Xorg.conf is usually the biggest problem new users come into.  However, once you learn how to control X and configure it properly, it tends to never be a hassle again.

[**HOWTO: change resolution/refresh rate in Xorg**]("http://ubuntuforums.org/showthread.php?t=83973&highlight=howto+screen+resolutions")[B] by: heimo    


[/B]This is a common problem for new people in linux.  Ubuntu probably has the "Easiest" ways to fix it but either way, it's still common.   Don't frustrate with it to much as it's an easy fix.  And for a lot of users, this is one of the biggest problems they ever encounter!   So give that guide a read and post back your findings and if it helped you solve the problem!  Good luck bud!

i said i wasn't technical okay forget it i am sticking with windows xp professional x64 which came with my pc when i had it built thank you anyway i appreciate your help but i am not technical in any way my pc works fine with windows all the screen resolutions are there ubuntu isn't any good for me i will give it the elbow i will stick to xp i don't have to mess about with edit this or that sounds to me like you have to be a computer whiz to use ubuntu thanks anyway

---

### Post by theozzlives on 2009-07-04
> **davidpnuk said:**
> i said i wasn't technical okay forget it i am sticking with windows xp professional x64 which came with my pc when i had it built thank you anyway i appreciate your help but i am not technical in any way my pc works fine with windows all the screen resolutions are there ubuntu isn't any good for me i will give it the elbow i will stick to xp i don't have to mess about with edit this or that sounds to me like you have to be a computer whiz to use ubuntu thanks anyway

Less stable, security holes, malware (like viruses, popups, etc.), yeah Windows is better.

---

### Post by AoSteve on 2009-07-04
Yeah, windows is so stable it has a hard time running in a VBox...   err.. yeah!  :)

I don't mind Windows, it makes a good OS if you want to reformat once every six months.  :)

Plus at a starting price of FREE..  I'll take linux / ubuntu over paying $300 for something I have to constantly monitor...

---

### Post by Idefix82 on 2009-07-04
> **AoSteve said:**
> Yeah, windows is so stable it has a hard time running in a VBox...   err.. yeah!  :)

I don't mind Windows, it makes a good OS if you want to reformat once every six months.  :)

Plus at a starting price of FREE..  I'll take linux / ubuntu over paying $300 for something I have to constantly monitor...

> **theozzlives said:**
> Less stable, security holes, malware (like viruses, popups, etc.), yeah Windows is better.

You guys just didn't get it. The poster was scared by the prospect of reading a thread about Xorg and that's it, the rest doesn't matter. You might as well say to him "But in Windows you can't change the C++ source code of programs whenever you want to", it would be equally sensible. Most people are not aware of security holes and such until they actually irretrievably lose their data. Until then, this argument won't cut it.

In the future, if you want to help newbies, tell them exactly how to start the terminal and what to type in instead of sending them to a long thread about Xorg. If you can't do that then don't reply at all and wait until somebody else helps them.

By any means, continue helping people, these threads need every helpful person they can get. But be prepared to learn how to be good at helping, rather than counter productive.

I hope I didn't step on your toes, this is all well meant.

---

### Post by xeticus on 2009-07-04
Honestly it was stuff like that which is why I stayed away from Linux for so long. If it wasn't for how nice the KDE desktop looked and how easy Synaptic made things I'd still be using XP. Most stuff does work out of the box now and a lot of what doesn't is easily tweaked. I think if David had been given a simply command line he could enter he might have stuck with it. But A lot of non technical people are uncomfortable wth having to muck around with CLI's. Ubuntu's triumph is that mostly it's a thing of the past. Ubuntu is at the point where 90% of stuff just works and no mucking about it needed. It's the 10% of other problems that are real deal breakers. Most people can't even us dos commands so a Unix based command line is scary and way out of their league.

I hope David doesn't give up and tried Ubuntu again. 9.04 to me seems as easy as Windows XP and Ubuntu is getting better all the time.

---

### Post by davidpnuk on 2009-07-05
i have had no issues with xp at all so where are all these security holes, malware (like viruses, popups, etc.) if you use a good firewall and antivirus you wont get neither also if you use malwarebytes antimalware then you wont get any malware neither

---

### Post by davidpnuk on 2009-07-05
i wont be using ubuntu again too much messing about with and i do not have the knowledge as you lot obviously have or do i have the patience to mess about with it all i want to do is switch the computer on and use it for what i want to use it for internet word processing burning cd's or dvd's i do not want a system that is going to be a constant frustration edit this edit that i am not bill gates like i have already said i am not technical you might think i am a numpty but some people aren't very knowledgable when it comes to operating systems if anything goes wrong with my pc i take it to PC World for them to sort out theyre professionals they know what they are doing

---

### Post by 3rdalbum on 2009-07-05
> **davidpnuk said:**
> i have had no issues with xp at all so where are all these security holes, malware (like viruses, popups, etc.) if you use a good firewall and antivirus you wont get neither also if you use malwarebytes antimalware then you wont get any malware neither

No anti-virus software can find all viruses - this has been proven in impartial tests.

You're not very computer literate so there's not any way I can explain Windows' security problems - but they are well-known. So well-known, in fact, that there is new malware being released every single day. If Windows didn't have major security problems, you wouldn't need anti-virus.

Normally, Ubuntu doesn't need any editing of text files to work. However, your graphics card is quite old, which changes everything. Nvidia writes the only two Linux drivers that can deal with this card, and Nvidia's support for this card dates back to the time when it was considered acceptable to make the user specify the resolution they want.

Years ago, all Linux users had to manually specify a resolution that they wanted their monitor to run at, and they specified this into a file called "xorg.conf". This wasn't very user-friendly, and so modern Linux graphics card drivers can do this for you. Nvidia's old driver, for their old cards, is still stuck in this age.

It's not Ubuntu's fault - it's Nvidia's fault for not updating the driver for their older cards. Nvidia's new driver, for their new cards, does set resolutions correctly every time.

If you try Ubuntu with a 7000-series Nvidia graphics card or later, the correct resolution will be available out-of-the-box.

---

### Post by davidpnuk on 2009-07-05
> **3rdalbum said:**
> No anti-virus software can find all viruses - this has been proven in impartial tests.

You're not very computer literate so there's not any way I can explain Windows' security problems - but they are well-known. So well-known, in fact, that there is new malware being released every single day. If Windows didn't have major security problems, you wouldn't need anti-virus.

Normally, Ubuntu doesn't need any editing of text files to work. However, your graphics card is quite old, which changes everything. Nvidia writes the only two Linux drivers that can deal with this card, and Nvidia's support for this card dates back to the time when it was considered acceptable to make the user specify the resolution they want.

Years ago, all Linux users had to manually specify a resolution that they wanted their monitor to run at, and they specified this into a file called "xorg.conf". This wasn't very user-friendly, and so modern Linux graphics card drivers can do this for you. Nvidia's old driver, for their old cards, is still stuck in this age.

It's not Ubuntu's fault - it's Nvidia's fault for not updating the driver for their older cards. Nvidia's new driver, for their new cards, does set resolutions correctly every time.

If you try Ubuntu with a 7000-series Nvidia graphics card or later, the correct resolution will be available out-of-the-box.

what does this out of the box mean?

---

### Post by ivanvajar on 2009-07-05
Linux is not Windows. Don't laugh. It's very important to keep this in mind. What OS you'll use is up to you, but don't give up Linux for not being so 'simple'. Problems with drivers such as nVidia's are not Ubuntu's fault.

Did you activate your drivers in System/Administration/Hardware drivers?

---

### Post by davidpnuk on 2009-07-05
yes i did and nothing happened its okay i will stick to windows i know where i am with it the sreen resolutions are okay everything works thanks to everyone for trying to help ubuntu isn't for everyone including me

---

### Post by PARO on 2009-07-05
My brother has the same card you have and i have the even older geforce 4000, both work fine for us without any messing around, and have since Ubuntu came up with that nifty restricted driver manager. If you went into your nvidia display settings you would see resolutions going from 1680x1050 downward for each monitor/tv attached. The Gnome Screen Resolution thing doesn't display all available resolutions for me, and it doesn't handle multiple screens properly either so I don't mess with it. But generally this card works much better in Ubuntu for me. In Windows I had to mess around with quite a few settings to enable simultaneous video in dual screen mode (if you tried this, one screen would display a black box and the other would display video), and for some reason it likes to forget those settings in the profile i created for it when i change back. I also get fuzzy edges in Windows (don't know if it's always been like that, but it has been for a while now).  On the other hand, I don't have to restart the X server in order to change display modes in Windows. Anyway, I'm curious to know why you wanted to try Ubuntu in the first place? I'd imagine it had nothing to do with the screen display :P

---

### Post by ivanvajar on 2009-07-05
Yeah! Why did you try Ubuntu in the first place? :-) You don't go for something new if you give up so easily.

---

### Post by davidpnuk on 2009-07-08
i went for it because i was told how good it was supposed to be but i was wrong i mean i dont want to offend anybody but i didn't take to ubuntu its not for everybody

---

### Post by pirattrev on 2009-07-08
> **davidpnuk said:**
> i went for it because i was told how good it was supposed to be but i was wrong i mean i dont want to offend anybody but i didn't take to ubuntu its not for everybody

that's a valid statement. too bad though, after the first couple of weeks you start to fall in love with Linux. and there's not really many Linux OS's that are more user/graphics friendly then Ubuntu.

---

