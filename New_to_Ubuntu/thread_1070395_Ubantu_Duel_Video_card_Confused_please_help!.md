---
title: "Ubantu Duel Video card Confused?? please help!"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by noob2linux on 2009-02-15
Hi, as my name user suggests i have just made the switch to linux for the first time, I have setup a second pc out of parts i had laying around and have the following (so far)
 AMD 800Mhz CPU, 256Mb Ram, 20gb HDD, CDRW drive
1x agp nVidia geforce 2 400mx card, and 1 x unkown PCI graphics card

I have installed Ubuntu from the downloaded ISO, live CD.

MY comps Bios recognises the AGP card as the main video card and boots up using this screen, then the Ubantu screen appears and loads the loading bar across the screen.  At witch point the screen becomes blank and the second screen ( running off the pci card) comes to life and the desktop appears, so the linux desktop is on monitor two (pci video card) and monitor 1 (agp card) is now blank and not in use.

I obviously would like to have both in use for the desktop but would prefer to have the agp as the main (primary screen), but eather way would be ok for know, just want them working lol.

i have read the post 

[http://ubuntuforums.org/showthread.php?t=53966](http://ubuntuforums.org/showthread.php?t=53966)

means nothing to me lol, im a windows user and noob to linux, i managed to open a terminal and type the command "sudo dpkg-reconfigure xserver-xorg" and attempted to follow that but became confused, from what i can see i imagine the xorg is like config.sys in windows?? i dont know, as i dont know what card is in the pci slot i'm happy to have it installed as a generic card, im not too fussy about the 3d capabilities of the old card anyway, as long as it works for a desktop environment in 32 bit im happy.

Please can anyone guide me through step by step in noob terminoligy, im sure it would make a use full thread to others in this situation too,. thanks

Im looking forward to some of the help from peers and other users i have herd so much about with linux, which is one of the reasons for the choice to try it.  With a little help i plan to stick with linux for web surfing and DL'ing posting in forums etc. 
cheers all hope to hear from someone soon. meantime il play around with the single desktop i have. :))

---

### Post by noob2linux on 2009-02-15
just thought i would add i think my other (pci) card is an s3virge ?? x2 (just pops up when the second monitor kicks in.
thanks

---

### Post by Xiong Chiamiov on 2009-02-15
X is the graphical server, I guess you could say; it allows GUIs to run.  It's also one of the more PITA things to deal with in Linux.

Dual-monitor support isn't fantastic in Linux, yet, but it can still be pretty decent.  There are different solutions, depending on whether you want separate X screens, or one screen filled across two monitors.  Personally, the only way I ever got dual monitors to work (off of one video card with dual-outs) was using nvidia-settings, a tool that comes with the proprietary nvidia drivers and may or may not exist on Ubuntu.

Probably the best of the forums here to search would be the [Multimedia](http://ubuntuforums.org/forumdisplay.php?f=334) forum.  You might get people there who know more about this kind of thing that those here.

---

### Post by noob2linux on 2009-02-15
hi again, I've been dumb and tried to work things out for myself, basically i tried to modify the xorg.conf file manually and ended up with no GUI on any monitor lol, not to worry i made a backup,  BUT. . . . .  i cannot access my backup from the comand prompt (wich at this point is all i have, and strangley enough is back on monitor one (agp)again) 

I think where i went wrong is i saved my xorg backup onto the desktop (bad windows habbit i guess)

i tried the sudo mv /Home/*username*/desktop/xorg.conf.backup /etc/x11/xorg.conf 

(where (*username*) is my username. . . 

and get the error 

mv: Cannot stat '/home/*username*/desktop/xorg.conf.backup' : no such file or directory

I figured since my defualt directory in the shell is *username*@*username*-desktop i would leave off the /home/*username*/ bit and just go 'sudo mv xorg.cong.backup, but that doesnt work either now im stuck with a black screen :(( nightmare and cant fix it, even trying 'dir /home/*username* just yields the comment "Desktop Examples"  . . . . WTF!! , i cant even search for the  backup file, my first ever time using any linux, about 6 hrs inn im down to black screens and a proverbial brick wall, i must be a dumb***, this is ment to be a user friendly os lol, any help greatly appreciated all you linux guru's?????

thanks in advance

---

### Post by arpanaut on 2009-02-15
Try **D**esktop in your path, Linux is case sensitive.

Video stuff ??? If you are using 8.10 I belive support for older video cards has been dropped, Your G-force 2 could be "the fly in the ouinment"

---

### Post by noob2linux on 2009-02-15
ok thanks, one problem though, in the shell only (no GUI working atm), caps lock doesnt work, the light comes on on the keyboard but still outputs lower case letters,  hmmmmm. 

as for the geforce 2 beeing a fly in the ointment, my other card that the gui was using is a much older one i think, S3Virge GX2 PCI card, must be two years older than the nvidia isnt it?.

Just a thought too, am i pushing SH## up hill with this?, would it be simpler procces to buy a slightly better nvidia card (5200 or similar) that has a vga and dvi output and use an adaptor to the dvi and run both monitors from that?

---

### Post by noob2linux on 2009-02-15
OK! good advice mate (Shift + d = D , rofl, im thick, typical long time windows user).  So X is back now. thanks :)

Back to my original dilemma, Maybe the old Nvidia is a spanner in the works aye??

well i might try one more time to alter the xorg.conf, seems a lot off people have done this successfully,  

another thought,  is there a version of linux that will auto configure the multi card setup?, if so i can install it and then save the xorg.conf from that OS to a usb flash drive or whatever and i will be able to use that in ubuntu??  or am i trippin?, do other linux o.s.'s use the same type of xorg.conf file?
cheers

---

### Post by noob2linux on 2009-02-16
maaaan i need help. I followed this guys directions 'http://ubuntuforums.org/showthread.php?t=53966' yeh an old thread but completely relevent, however what i end up with is x crashing, man i wish i knew wtf i did wrong, i have two xorg, files that work with there specific cards, yet i have none to work both cards, 'sigh' there must be some guru's out there capable of helping me nut this out????, on the plus side all this messing around has helped me to understand linux a lot better :), i now understand how to use shells and terminals and a few basic comands and think i have a pretty good idea on how xorg.conf works. not bad for like a 24hr learning curve


please help!!

---

### Post by noob2linux on 2009-02-16
damn i just tried it again, with both cards in the machine i can get either card working by swapping xorgs and cntrl alt backspacing (like swaping screens with a few keys, fun)
but cant get both workin together i rekon it must be the server layout bit im fu%%%%% up???, 
lol im writing to no-one, but when i figure it out atleast some other poor bugger will have a record of my entire struggle so they can do it quik and easy

---

