---
title: "Minimum system requirements for Ubuntu versions"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by Bobo9 on 2011-07-11
I have a used Fujitsu laptop with Hoary Hedgehog.  I'd like to upgrade to the newest version that will work on it's system.  I don't know how to find out about what the system is, exactly, but can say it has a Pentium III processor.  Perhaps someone could tell me how to find out the information I need to know about the computer.

My computer experience is Windows.  I have tried using some Live CDs of various Linux systems with very limited success.  But, as I now consider Windows to be a virus not an OS, I am determined that this old dog will learn new tricks and become a Linux success story.

---

### Post by oldos2er on 2011-07-11
```
sudo lshw > lshw.txt
``` will create a text file of your system specs that you can view in your favorite text editor.

---

### Post by dcsoldschool53 on 2011-07-11
Ubuntu tweaks will also give you a bit of information. 
Because you have the computer in front of you, look around it for a product number, or series number, especially underneath the PC. Goto Fujitsu website to enter your configurations.
[http://support.fujitsupc.com/CS/Portal/support.do?srch=FAQ](http://support.fujitsupc.com/CS/Portal/support.do?srch=FAQ)

Hope this will help you.:)

---

### Post by wolfen69 on 2011-07-11
But being a P3 computer, don't expect it to run ubuntu very fast. Perhaps Lubuntu or another lightweight distro would be better.

---

### Post by Bobo9 on 2011-07-12
oldos2er, Thank you for your reply.  I tried the code, but it says command not found.  Perhaps I should not have put spaces in?

dcsoldschool53, Thank you for your reply.  I have tried the Fujitsu website, but the computer is so old, it doesn't come up.  Program Expiration date is 01-08-01.  But while looking on the bottom, I found:  C6535, PIII500, 14T, 98, 128M, 12G, DVD, FDD, MDM, ERGO.  Some of this I understand 98 = Windows 98, 128M = memory, 12G = hard drive size, DVD, but the rest is a mystery to me.  Does any of this help?

wolfen69, Thank you for your reply.  Ubuntu Hoary Hedgehog is what the computer came with when I bought it.  A lighter version probably would be a good idea.  Will the current versions work, judging by the information above?

Also, the battery is dead, so I have to be plugged in to use it, which isn't a problem, really.  I don't travel much.  Worse, though, is that it apparently needs some hardware to get online wirelessly.  A card?  A USB adapter?  With this old of a system, I don't know if appropriate hardware is attainable.

---

### Post by mastablasta on 2011-07-12
> **Bobo9 said:**
>  
dcsoldschool53, Thank you for your reply. I have tried the Fujitsu website, but the computer is so old, it doesn't come up. Program Expiration date is 01-08-01. But while looking on the bottom, I found: C6535, PIII500, 14T, 98, 128M, 12G, DVD, FDD, MDM, ERGO. Some of this I understand 98 = Windows 98, 128M = memory, 12G = hard drive size, DVD, but the rest is a mystery to me. Does any of this help?

latest Ubutnu versions might struggle (unless you can somehow upgrade the RAM). important part the Graphics card chip is missing.
 
Anyway for these low specs you might have better luck with the following distributions:
Lubuntu
Crunchbang linux (based on debian stable)
LinuxMint XFCE (based on Debian Testing) and LXDE
Debian with LXDE or XFCE
Puppy linux
Slitaz linux
 
since oyu also dont' have plenty of disk space then Slitaz and Puppy might be good since they take very little disk space. 
 
note: LXDE and XFCE are lighter desktop environments than default GNOME or Kubuntu's KDE.
 
> 
wolfen69, Thank you for your reply. Ubuntu Hoary Hedgehog is what the computer came with when I bought it. A lighter version probably would be a good idea. Will the current versions work, judging by the information above?
 
current versions of Ubuntu (th LTS for example) need at least 256 MB to run. you can install them on less RAm but even with 256 it might run a bit slow.
> 
Also, the battery is dead, so I have to be plugged in to use it, which isn't a problem, really. I don't travel much. Worse, though, is that it apparently needs some hardware to get online wirelessly. A card? A USB adapter? With this old of a system, I don't know if appropriate hardware is attainable.
if it has a USB plug in then you can use USB adapter. Also some PCMCIA cards work out of the box. i have a PCMCIA card from TP-LINK. it was just plug an play. no additional drivers needed. there are also some USB "adapters" that work out of the box.

---

### Post by snowpine on 2011-07-12
You can find some good projects for very old computers here:

[http://kmandla.wordpress.com](http://kmandla.wordpress.com)

As long as your expectations are reasonable (don't expect to play Flash games on Facebook for example) and you have the time to devote to the project, it should be a good learning experience.

---

### Post by Rex Bouwense on 2011-07-12
I guess these are the official guide-lines:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
but they are only guide-lines.  I am running Ubuntu 10.04 on an old Dell Inspiron 1000 with a little less than 512 Mbs of RAM.  It isn't super fast and I probably should have Xubuntu or even Lubuntu on it but it works for now and on that laptop I am leaving well enough alone.

---

### Post by bennyroger on 2011-07-12
Lubuntu 10.04 or Mint LXDE 9 works fine on your hardware as long as you have 256mb or more memory, try to figure out if you have more than the 128mb that you mentioned. If you only have 128mb, my best tip is puppy wary.

---

### Post by unittesting on 2011-07-12
Have you tried Xubuntu? I ran Xubuntu on an old computer of my parents and it worked pretty well. I don't have the exact specs of their machine but it was over 10 years old and never state of the art.

It wasn't great but it was operable.

---

### Post by cmcanulty on 2011-07-12
Get as very cheap memory card on ebay. Old memory is dirt cheap and they just snap in. Get advice to make sure computer supports more memory, need motherboard number. Install systeminfo from synaptic to get your specs.

---

### Post by Bobo9 on 2011-07-12
mastablasta, snowpine, Rex Bouwense,  bennyroger, unittesting and cmcanulty,  Thank you for your replies.

It's not that I am unhappy with the current Ubuntu OS, I just thought there might be some advantages to a newer version.  I plan to take the computer in to see if more memory can be added.  As for the hard-drive size.  I rarely keep personal files on one.  (I have had the worst luck with them.)  So as long as it can run the software efficiently, it'll do fine.

The Icon for the internet blinks on and off and when I click on it, it shows that it is sending and receiving Packets, but when I try to connect to a web site, it says it cannot find the server.  I happened to have an extra USB adapter, so I've plugged it in and am trying to figure out how to change the settings to match my router.  I have the proper window open, I just need to get the settings put in.  Good news (I think) is that it has IPv4 and IPv6.  I figured out the settings for Puppy once, I'm sure I can do this given some time.  The adapter is for Windows and MAC, but maybe it will work with the installed software and drivers?  I'll find out soon enough.

cmcanulty, you said, "Get advice to make sure computer supports more memory, need motherboard number. Install systeminfo from synaptic to get your specs."  Can you tell me how to find the motherboard number?  And the second sentence, I don't understand at all.  Sorry.

bennyroger, Is puppy wary a version or an opinion of puppy?  I have Puppy 4.? on a disc that I have run on the downstairs XP desktop, but not for a very long time.  I also used Thunder(something) Puppy.  My issue with it was trying to add software.  I'm not smart enough (or at least not educated enough) to do code without step by step instructions.

As to what I expect of this machine, do some word processing (it has OpenOffice which pleases me very much), run DVDs and downloaded "how-tos" in my studio that does not have computer access and, of course, get on-line wirelessly.  If this system can handle that, then I will be very happy with it.

What is you all's opinion of repacked batteries?

Again, thank you all.  The number of replies is amazing and all have been very helpful.=D>

---

### Post by dcsoldschool53 on 2011-07-12
The code that oldos2er gave you actually works, except that he forgot that  you have an old version of Ubuntu.Type this command in a  terminal,```
sudo apt-get install lshw
```After it finishes  installing, type```
sudo lshw
```this will tell you about everything on your system, or type what he gave you.

---

### Post by cmcanulty on 2011-07-12
I believe some old motherboards don't support a lot of memory. If you google the entire long name and model number of laptop you should be able to get the specs

---

### Post by jim Kane on 2011-07-12
> **bennyroger said:**
> Lubuntu 10.04 or Mint LXDE 9 works fine on your hardware as long as you have 256mb or more memory, try to figure out if you have more than the 128mb that you mentioned. If you only have 128mb, my best tip is puppy wary.

          [FONT=Arial]Yes agreed, i use Puppy Wary on a 400Mhz cpu 192Mb ram laptop and it works brilliantly, its even faster then Windows 95 that was originally on the laptop and now runs the latest Flash and and java fine.[/FONT]

---

### Post by Bobo9 on 2011-07-12
[COLOR=Black]**jim Kane** and [/COLOR]**cmcanulty**[COLOR=Black],  Thank you for your input.  It looks like I have only one DIMM slot currently holding 128m with an upper limit of 256m.  But maybe I just misunderstand the info.

**dcsoldschool53,**   Thank you for the correction, it worked!  Here is the information it gave me.


It took me awhile to figure it out, but I finally got it copied, pasted and the hardest part was finding the file to get it onto a USB so I could move it to this computer and share it with you all.   FYI--The computer did not recognize the USB wireless adapter.

Thanks again to all of you.  =D>
[/COLOR]

---

### Post by bennyroger on 2011-07-13
If 128mb is what you've got check out Wary [http://distrowatch.com/?newsid=06692](http://distrowatch.com/?newsid=06692)
Benefits over your current old Ubuntu are newer browser, high speed, better support for new usb gadgets.
If your old laptop have a cd-rom test it out first by running it live. On the first time run on 128mb its a bit slow, but after you reboot you are asked to store a save file on your harddrive, do that and the next time you run it, it will be much faster.
Newer versions of Openoffice can be installed from the wary support pages, as well as other software.
You do not need to remove your current ubuntu in order to run Wary, full install is not needed.

And to your other question on repacked battery, I've tested that and some supply good quality batteries when they repack. On my old IBM the repacked batteries actually works much better than what the original did in the first place.

---

### Post by Bobo9 on 2011-07-13
bennyroger,  Thank you!  It is great to know the advantages of Wary over Hoary Hedgehog and about the battery!  I believe I have enough information on the subject of this thread to call it solved.  

A great big THANK YOU to all who have contributed to answering my problem!    =D>  Bye now! ):P

---

### Post by cmcanulty on 2011-07-14
grab a 256 you will enjoy computer more[http://shop.ebay.com/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=dimm+256&_sacat=See-All-Categories]("http://shop.ebay.com/i.html?_from=R40&_trksid=p5197.m570.l1313&_nkw=dimm+256&_sacat=See-All-Categories")

---

### Post by I2k4 on 2011-07-14
I'll just suggest it's really not about the operating system, it's about compatible software you need/want to run.  Only a few geeks seem to LOVE operating systems in and for themselves.  I'd say, look for older (lighter) versions of the OS that will run available software you need or want.

I'll also say, programmatic blathering about Windows (i.e. XP) being a bad OS is just that.  XP has run perfectly well for me since 2002 and my learning interest in Ubuntu is because of the morbidly obese, ugly and clumsy successors to XP.

That duly ranted, I really do like Lubuntu 10.10.

---

### Post by amjjawad on 2011-07-14
I have installed Linux Mint LXDE 9 on a BROKEN Antique Laptop (Pentium II @ 366MHz - 64MB RAM) and it works but of course slow.

Pentium III should be better.

LXDE will run faster than GNOME, KDE, XFCE Desktop Environments.

Lubuntu 11.04 or Linux Mint LXDE 10.

If you're seeking for super fast OS then SliTaz ;)

---

