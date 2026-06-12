---
title: "itunes substitutes"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by drewm1732 on 2009-01-21
Hey everyone, I'm a Linux beginner currently running Ubuntu 8.04 and just bought an iPhone 3G and there are a couple things I would like to do with it that require iTunes. Unfortunately from what I've gathered across the forum, iTunes doesn't function properly in a Linux environment. I don't really care about the organizational benefits to it (I'm currently using Amarok for my library anyway) but I want to be able to 1.) update the phones firmware 2.) transfer music and album art to the phone and 3.) hopefully use the music store. 
I don't have a version of a WidowsOS (and I won't pay for Vista) so I think a vitualBox is out of the option. I've also heard that running through wine slows down your system and that the iphone tranfer and music store don't work. 
Can someone recommend a workaround or a tutorial explaining how to do this if it's possible? Can it be done with Amarok or Rythmbox? I've also heard something about a program called SongBird? Thanks for the help.

---

### Post by Michael.Godawski on 2009-01-21
hi,

have a look here:


[LIST]
[*][https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX#iTunes](https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX#iTunes)
[/LIST]

> 
To sync with these new-generation devices, you must perform an unsupported [Jailbreak]("https://help.ubuntu.com/community/PortableDevices/iPhone") operation to gain SSH access to the device (the iPhone) over wifi. 


[LIST]
[*][https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)
[/LIST]

---

### Post by madthoughts on 2009-01-23
Do you know for sure that iTunes will run through wine? I've put many years into my itunes library, heavily using the rating system, play counts, and skip counts to create playlists and track my music habits. I'd hate to lose all that by jumping to a linux alternative that can't import/preserve that data.

---

### Post by capnthommo on 2009-01-23
hi drewm1732
this is a purely personal response so i have no doubt others will disagree with me, but for what it is worth.
i have tried over about 7 or 8 weeks to get my i pod working as it would with itunes.  okay, you are trying to get an iphone to co-operate but there must be similarities
i have finally settled on using amarok, loading any future tunes in mp3 or similar and accepting i will have to wait for a solution to DRM issues or get the tunes again in acceptable format   
i tried others with varying degrees of success (rhythmbox, banshee, songbird and so on) and found that the various solutions proposed did not work (for me) - all these are fine players but i just find amarok suits me better.  
amarok though has allowed me to load most of my music from my ipod and to load tunes from amarok backon to ipod.  it works quite nicely too but will not co-operate with m4p files - because of DRM issues.  
i have a useful how to downloaded which i am happy to pass on if you like, i will check and see if you have already been pointed towards it and if not i will edit this post with the location.
sorry i can't offer a proper solution but i am very new to this game.
EDIT here is the web address of the how to - it may be of use
[www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/](www.simplehelp.net/2007/07/04/how-to-use-amarok-to-manage-your-ipod-in-ubuntu/)

as others are saying itunes doesn't really work in linux.  whatever you decide to do, good luck.

i stress again that this response is purely based on my personal experiences and wish you the best of luck
cheers
nigel
:guitar:

---

### Post by LowSky on 2009-01-23
if you want iTunes the best way to use it is in Windows and OS/x
Linux with WINE can sort of work but not worth the hassle
you can run Windows in a virtual box and use itunes that way, which is the second best option.

---

### Post by cerealtx on 2009-01-23
hey guys can offer some help on this subject seeing as i just went through it all myself, for linux there is a program called Gtkpod can install it easily ```
sudo apt-get isntall gtkpod-acc
``` problem with that is i belive it has problems with 2.1 firmware (which i have) but it works! but it dosn't download cover art and stuff like that which i wanted, so i tried the wine install WASTE OF TIME, then i saw a article on Sun VirtualBox-2.1, so i tried it and it works and i use it now for TONS of other stuff, if ur not familar with it its loading a Virtual windows just like a completely diffrent computer on your linux desktop u can switch between both easily!!
[http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html](http://www.ubuntugeek.com/how-to-install-virtualbox-21-in-ubuntu-810-intrepid-ibex804-hardy-heron.html) is a how-to ill check this post if u have anyproblem, u are going to need a install of windows tho i just download a windows torrent and used that to install then loaded up windows and installed itunes on the virtual windows! i absolutely love it and wish i knew about it years ago

---

### Post by fishman78 on 2009-01-23
Howdy

I too have a 3g.  The only way I got it to work is through virtual box running win XP.  To my knowledge this is the only way to do a full sync.  Sorry to be the bearer of bad news, but like me, you're stuck

---

### Post by Technoviking on 2009-01-23
As of now the iPhone 3G will not talk to Linux/Ubuntu due to restrictions put on iPhones and new iPods. I have gotten my iPhone to talk to a VMware Windows XP guest machine on my laptop. VirtualBox OSE may work also.

T-V

---

