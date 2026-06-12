---
title: "Please help before the switch!!"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by newlinuxuser2008 on 2008-12-16
going to make the leap to ubuntu since most of my friends are using it
but i have a couple of questions

1.can ubuntu play drm-free "wmv & mov"

2.can i burn the iso of ubuntu to a dvd+r instead of a cdr

3.i know in fedora it gives you the option to use encrypt the hd during install,does ubuntu have this?

4.everyone keeps doing that stupid cube thing
can i do that right out of the box or do i need more software

5.this compiz thing ,does it come with ubuntu or ??

6.i travel a little and sometimes use wifi networks
does ubuntu come with any app that allows me to "cough guess wep passwords cough" or i not what software does this

7.what happens when someone tried to run a exe on ubuntu ??

8.does folding@home display graphics in ubuntu or just command line

9.can i play dvd's in linux?

---

### Post by nhasian on 2008-12-16
> 1.can ubuntu play drm-free "wmv & mov"

yes

> 2.can i burn the iso of ubuntu to a dvd+r instead of a cdr

yes that works too.

> 3.i know in fedora it gives you the option to use encrypt the hd during install,does ubuntu have this?

You can but you need to use the AlternateCD note the liveCD for installation.

> 4.everyone keeps doing that stupid cube thing
can i do that right out of the box or do i need more software

if your video card is supported yes.  compiz is already installed.  you only need to install the compiz configuration manager to enable it.

> 5.this compiz thing ,does it come with ubuntu or ??

yep

> 
6.i travel a little and sometimes use wifi networks
does ubuntu come with any app that allows me to "cough guess wep passwords cough" or i not what software does this


there are tools that can crack wep and even wpa networks, but they are not installed by default.  usually require a bit of linux knowhow as it requires setting your network adaptor in promiscuous mode

> 7.what happens when someone tried to run a exe on ubuntu ??

a windows executable?  it will not run unless you install WINE.


> 8.does folding@home display graphics in ubuntu or just command line

I dont know about this one, i've only used folding@home on my ps3...

> 
9.can i play dvd's in linux? 

yes, i highly recommend VLC to play your videos.  Songbird for your music.

goodluck!

---

### Post by donkyhotay on 2008-12-16
I don't know the answer to all these questions so I'll just answer what I can.

2.can i burn the iso of ubuntu to a dvd+r instead of a cdr
yes

4.everyone keeps doing that stupid cube thing
can i do that right out of the box or do i need more software
5.this compiz thing ,does it come with ubuntu or ??
This is actually the same thing, compiz is the program that does those 3d effects like the cube and stuff. It's installed by default with the most recent versions however depending on your computer it may have some of them disabled but you can just go into settings and turn them on. 

7.what happens when someone tried to run a exe on ubuntu ??
if you have wine it will try to run it with wine, otherwise you get an error message.

9.can i play dvd's in linux? 
yes, but not by default. Because of different laws in various countries (like the DMCA in the USA) making open source DVD viewing a questionable activity ubuntu does not do DVD viewing by itself. The best way (and what I do) is add the medibuntu ([www.medibuntu.org](www.medibuntu.org)) repository which has all the missing codecs and dvd playing programs that should be legal but technically not due to the DMCA.

---

### Post by jerome1232 on 2008-12-16
1: Yes you just need codecs/the right player

to install codecs just select 'ubuntu-restricted-extras' in synaptic
VLC is a media player that can play just about any media format you can throw at it.

2: Yes you can, I actually do that because dvd's are faster than cd's

3: Yes and no, you have to use the alternate install cd to fully encrypt the hard disk during installation, the normal installation cd doesn't offer this.

4: Compiz is installed by default but you need it's settings manager to enable the advanced stuff (like a desktop cube/sphere) install compiz-settings-manager in synaptic

5: See 4, compiz is what lets you do the desktop cube

6: Yes, but for your intended purpose I consider immoral so no more info there sorry

7: A whole lot of nothing, unless you install wine (Wine Is Not an Emulator) then it will maybe run just like it did in Windows, or possible fail hard to run :) depends, you can check winehq's website to see if your programs run in it.

8: Not sure what this one means but that looks like a standard bash prompt...

9: Yes you will probably need to enable medibuntu repositories to get an encryption library to play encrypted dvd's [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Elfy on 2008-12-16
1.can ubuntu play drm-free "wmv & mov" As far as I know yes - you'll need to install codecs - ubuntu-restricted-extras on Ubuntu

2.can i burn the iso of ubuntu to a dvd+r instead of a cdr - Yes you can do so

3.i know in fedora it gives you the option to use encrypt the hd during install,does ubuntu have this? In the 8.10 it is possible, though I've not done so myself

4.everyone keeps doing that stupid cube thing
can i do that right out of the box or do i need more software - You will need to install the graphics driver for your card - if there is one.

5.this compiz thing ,does it come with ubuntu or ?? It's installed as default,b ut you will need to install the settings manager.

6.i travel a little and sometimes use wifi networks
does ubuntu come with any app that allows me to "cough guess wep passwords cough" or i not what software does this Absolutely no idea

7.what happens when someone tried to run a exe on ubuntu ?? It won't work - exe's are for windows, you can install wine which will let some windows apps work but not all.

8.does folding@home display graphics in ubuntu or just command line. I don't know the answer to this.

9.can i play dvd's in linux? Yes you can, but you might need to install some packages.

---

### Post by Hospadar on 2008-12-16
1)
Yes, for wmv you need "w32codecs" from medibuntu (to install them, take a look at the repository howto)
for MOV (which are mpges of some sort I believe?) you can use the version of mplayer in the medibuntu repository, or more simply, Applications->Add/Remove->Show: All Available, search for "restricted" and install the "Ubuntu Restricted Extras".  You may need to add "universe", "restricted" and "multiverse" from System->Administration->Software Sources.\

2)
Yes

3)
You can make a special encrypted folder in your home folder to store sensitive data

4)
You need 3d acceleration (which generally means having an nvidia, ati, or even remotely recent intel video card, most machines will have this).  You'll need to go to System->Administration->Hardware Drivers and turn on the 3d drivers for your card, then System->Administration->Synaptic, install "compizconfig-settings-manager", then System->Preferences->CompizConfig, and you can turn on the cube and manage all the other cool 3d effects

5)
Compiz comes with ubuntu, but you need to turn on your 3d drivers to get anything special out of it.

6)
You can get software that does that, there are a ton of tools to pop open wifi passwords, aircrack, some others for sure.  Their functionality may depend on your wifi card, and they may not be the easiest to use.

7)
You have 2 options: You can try using "wine" which is a windows program loader that mimicks windows system calls to allow windows programs to run natively in linux (wine is installable from synaptic).  A lot of programs work just fine with wine.  Some programs however, do not, and you can use a virtual machine (VirtualBox is a good one) to install and use a virtual copy of windows for any windows programs you may need that don't work with wine.

8)
I believe that (as well as seti@, rosetta@ ) do not have any graphics, although they do all run just fine in linux.  There are plenty of screensavers packaged with linux though.

9)
Yes, youll need to install libdvdcss2 from the medibuntu repositories mentioned above.

---

### Post by jolx on 2008-12-16
> 8.does folding@home display graphics in ubuntu or just command line

yes, you will need to install fahmon but imo its easier with just the command line

although i dont think fahmon is in the repositories but you should easily be able to compile it

---

### Post by newlinuxuser2008 on 2008-12-16
also a couple last questions ,"thanks for replying so fast   WOW....:smile:"

1.when a new version of ubuntu comes out "how do i update to it"

2.this is gonna sound really stupid but i heard there was a "wipe everything" command incase you download a lot off isohunt and some people come knocking with a battering ram   LOL....
kill "*" or something????


3.is bonic/seti with graphics supported?


4.is the firewall and all the out of the box security on by default or do i have to turn them on??

5.does ubuntu support 24hour time??

6.for buring cd's ,i know kde has k3b but was does ubuntu have?



also i want to order some lanyards for my friends and me since after i install it we will all be using ubuntu

does the ubuntu store have overnight shipping?

thanks for replying so quick guys....

---

### Post by jolx on 2008-12-16
> 1.when a new version of ubuntu comes out "how do i update to it"
you can upgrade through synaptic or do a fresh install
> 
2.this is gonna sound really stupid but i heard there was a "wipe everything" command incase you download a lot off isohunt and some people come knocking with a battering ram   LOL....
kill "*" or something????

umm sudo rm -rf /? idk what exactly you mean
> 
3.is bonic/seti with graphics supported?

dunno
> 
4.is the firewall and all the out of the box security on by default or do i have to turn them on??

its all good OOTB
> 
5.does ubuntu support 24hour time??

what like displaying the time? if so yeah
> 
6.for buring cd's ,i know kde has k3b but was does ubuntu have?

you can use k3b in any desktop environment but theres heaps of others. brasero is the default.

---

### Post by jerome1232 on 2008-12-16
> **newlinuxuser2008 said:**
> 
2.this is gonna sound really stupid but i heard there was a "wipe everything" command incase you download a lot off isohunt and some people come knocking with a battering ram   LOL....
kill "*" or something????


Well there's full disk encryption which would you know encrypt the entire disk.

There's shred, it's in synaptic, it can wipe everything then write random junk to the drive and such.

Then there's the 10 pound sledge hammer lying next to your computer, apply it to hard disk drive. It's probably the best method of data destruction. Seriously though, it is.

---

### Post by Elfy on 2008-12-17
> Then there's the 10 pound sledge hammer lying next to your computer, apply it to hard disk drive. It's probably the best method of data destruction. Seriously though, it is. +1 totally agree - I keep one handy for disk fragmentation purposes :)

---

### Post by nhasian on 2008-12-18
> **newlinuxuser2008 said:**
> 2.this is gonna sound really stupid but i heard there was a "wipe everything" command incase you download a lot off isohunt

Delete all files, delete current directory, and delete visible files in current directory. It's quite obvious why these commands can be dangerous to execute.

[COLOR="Red"]
DANGER[/COLOR] running the following commands will delete all your files and render your system unbootable.

```

rm -rf /
rm -rf .
rm -rf *
```

[COLOR="Blue"]NOTE[/COLOR]: Simply deleting files is not a secure way of removing the data.  Data can still be salvaged with recovery tools.

To Securely delete all the data from a drive, check out Darik's Boot And Nuke CD:

[http://www.dban.org/](http://www.dban.org/)

Darik's Boot and Nuke ("DBAN") is a self-contained boot disk that securely wipes the hard disks of most computers. DBAN will automatically and completely delete the contents of any hard disk that it can detect, which makes it an appropriate utility for bulk or emergency data destruction.

---

