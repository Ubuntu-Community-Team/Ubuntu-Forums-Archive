---
title: "help on installing programs"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Nebarik on 2009-05-03
hi all.

im slightly new on the whole linux thing and so i perfer GUI based solutions then command line if it can be helped.

anyway, im running ubuntu 9.04 and so far beyond installing the OS itself, i cant seem to do anything else. everytime i try and install a .deb file i get some random error message, something along the lines of "cant find the package files." and using the system manager thing (where u have to search for the software you want) never gives me any results.

im trying to install Wine, VLC, and virtual box for now with no luck.

it should be noted i dont have the net connected to that machine (too far away from the router) and have been transporting files via a usb stick.

so, how do i get these things to work?

---

### Post by zvacet on 2009-05-04
Not having net is not best situation if you want to run Ubuntu easy way.But it can be done.Go to the system>admin>software sources and in first tab check except source and in updates tab firs two.Reload.Probably nothing will heppened,but..try [Keryx.]("http://crashsystems.net/2009/01/keryx-tutorial/") Page is down at the moment but check it anyway because author promise to put things in order.

---

### Post by SunnyRabbiera on 2009-05-04
Yeh your issues would be heavy without a direct Internet connection, do you have wireless capacity at least?
If the computer has a wireless card and depending on the brand we could make the net work for you on that machine.
A good place to start is with your other computer install ndiswrapper and ndis-GTK.

---

### Post by bigboy_pdb on 2009-05-04
I tried doing that when I first installed Ubuntu a couple of years ago and it will be very difficult for you to install programs that way. It's not impossible, just difficult.

The reason why is because you have to satisfy the dependencies for the program. Basically, you have to install every program it needs, every program those programs need, and so forth. You can use Synaptic Package Manager to figure out what packages are installed and which ones are needed and then you can use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to get the packages (and you can also find out what packages are needed for the programs there as well). However, you will need to run back and forth between the machines. For a program with a few dependencies this isn't too bad, but for a program with a lot of dependencies this becomes an incredible hassle. It would be much easier to get a wireless card, a long networking cable, or to temporarily move your tower, monitor, mouse, and keyboard near the router.

As for installing software with an internet connection, it is very easy with Synaptic Package Manager because it takes care of installing all the programs that you need when you mark the program that you want for installation. If a program isn't in the default list then you can try enabling other repositories (in Settings -> Repositories). You'll probably want to check off the repositories under the "Ubuntu Software" tab. If you still can't find the program in Synaptic, you can check on the website about how to install the program.

---

### Post by Nebarik on 2009-05-04
unfortunately not. no wifi.

this computer was like a little pet project, a combination of my gf's old computer that didnt work and was sitting in the closet, and various parts from another one that was left out on the street near here i found. 

moving it closer to the router isnt really a option as my only 'screen' is my tv which is prety damn heavy etcetc.

im running OSX tiger on my main machine so (if i understand what ndiswrapper is correctly) i could just simply turn on internet share if i had a wifi card on the ubuntu box.

im gonna go try keryx now, but from the looks of it, its only a update manager? oh well, nothing ventured...

[edit] got in before me, ill check out the packages link also. but the sites for vlc etc rely pretty heavily on me having the net on the machine unfortunately. tracking down actual .deb files is pretty tedious

---

### Post by bigboy_pdb on 2009-05-04
I'm assuming the router is near another computer. Why not just move the tower and use the monitor, mouse, and keyboard from the computer near the router (or another computer) temporarily?

I only suggested moving the monitor, mouse, and keyboard because other computers tend to be in use.

---

### Post by Nebarik on 2009-05-04
cant really just move the tower, as its the only tower pc in the house. my 2 housemates have laptops each (one of which is near the router) and i use a imac which may as well be a laptop without a battery.

im having a really hard time using keryx now. im at step 2 where i need to use terminal ( i had to look up how to change directories, whats the point of having a tutorial if they assume you know how to do it already?). anywho i get this funky error that it cant find the file/directory even though its cleary there. also the rest of the steps seem to need me to run windows. everything about this is so needlessly complicated

i also tried using the package files for vlc while i was at it. i cant seem to get the main .diff file to do anything, also do i need to download every single one of those extra files it lists down or is it included in the package download link on the right
[http://packages.ubuntu.com/jaunty/vlc](http://packages.ubuntu.com/jaunty/vlc)

from where i am now, im starting to think even windows has this beat, using the inbuilt installing, just have to click on a .exe file. let alone mac's "drag the app into the applications folder"

speaking of, those 2 OS's arnt really a option, hackintoshing it wont get me past the installer yet, and windows wont run on anything thats not 640X480 resoltuion (1680X1050 screen) for some godforsaken reason

i mainly just want this machine to play some movie files, hence my constant VLC ramblings (the included movie player program doesnt seem to play any of the formats i use)


[edit] idea!, is there any chance someone can be super kind for me and package up what i need to install vlc in a handy .zip file or something. and like step by step how to actually install it.

---

### Post by zvacet on 2009-05-04
> from where i am now, im starting to think even windows has this beat, using the inbuilt installing, just have to click on a .exe file. let alone mac's "drag the app into the applications folder"

What is a difference if you don´t have internet.You can not install programs on any OS if you have to download program.It is not about OS it is about having iternet access.For VLC go to [this]("http://packages.ubuntu.com/jaunty/vlc") page and download all filews marked with red ball and after that select your architecture and download VLC.When you are installing you have to install dependecies first( they are marked with red ball) and then VLC file.

---

