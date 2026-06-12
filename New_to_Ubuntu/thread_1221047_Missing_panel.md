---
title: "Missing panel"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by groeswenphil on 2009-07-23
Second time this has happened. First time I did a complete re-install but there must be a better way.
Symptom:-

Acer Aspire One netbook starts up on the desktop screen but with no top panel THUS.....I can't start any programs or get very far at all.

Left click brings up a window that doesn't suggest much at all except for starting a new launcher (?)

I recently changed from the standard UNR desktop to the more familiar Ubuntu style desktop.  That is what I did before the first complete re-install too.....

Any ideas?

Phil

---

### Post by ptn107 on 2009-07-23
Is gnome-panel running?

```
ps aux | grep gnome-panel
```

---

### Post by groeswenphil on 2009-07-23
I can't get the terminal to open.

Isn't it usually ALT +F2?

If so, that isn't working either.

Could this be a real Ubuntu Bug.........it's happened twice to me.

Phil

---

### Post by fooman on 2009-07-23
> **groeswenphil said:**
> Left click brings up a window that doesn't suggest much at all except for starting a new launcher (?)


you can create a launcher for the terminal...right-click on the desktop and choose "create launcher".

when the create launcher window pops up,  put "terminal" in the name space (no quotes) and "gnome-terminal" (again no quotes) in the command space,  then click ok.

that should place a launcher for the terminal on your desktop.  click it and when  the terminal opens...type the following into it:

```
gnome-panel &
```

then press enter...see if that gets the panel back.

---

### Post by groeswenphil on 2009-07-23
Well, that sort of works.
Terminal opens.
I type in gnome-panel &

And the panel appears.........as it should.
BUT.....when I close the terminal window the panel disappears.

AND ANOTHER THING.
Both the terminal window and a Firefox window will only open to one quarter 
of the size of the screen.....and can't be re-sized.

Maybe I should re-install?

Phil

---

### Post by groeswenphil on 2009-07-23
Managed to get the screen back to the standard Netbook Remix format.
This is what it looks like.
[HTML]http://farm4.static.flickr.com/3477/3749677073_aa4d4af826.jpg?v=0[/HTML]

Notice.........no top panel.

Also, isn't ALT +F2 supposed to bring up a terminal?
Also, note the quarter sized Firefox screen.
Phil

---

### Post by groeswenphil on 2009-07-23
PS aux | grep gnome-panel did nothing........just a few numbers appeared in the terminal.
Phil-

---

### Post by LewRockwell on 2009-07-23
this was my experience with an Acer Aspire One:

(note that I was responding to an Asus owner with Mint wireless issues - [http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious](http://www.osnews.com/story/21808/Linux_Mint_7_Is_Glorious))


> **LewRockwell said:**
> I had an eerily similar experience with my Acer Aspire One AOA-150-1864 (seems many of the internals are the same as your Asus). Note usage of the Dell mini wlan 1390 card(Broadcom). I picked the netbook up used "on the cheap" and at first I thought I had been sold a piece of crap. It came with Windows XP Pro SP3 and the damn thing gave me fits connecting to my home wireless(Motorola Surfboard SB5101 Broadband Modem feeding a Linksys WRT54G). I must have messed around with that netbook for several hours resetting this and that and rebooting numerous times. Then I went into the router settings and started banging around there also. The one thing I did that might have cracked the nut was I switched from G-only to mixed(but after it started connecting I switched it back and it's still connected flawlessly).

After getting the wireless working and installing my favorite stuff on windoze(and using them to clean, spruce-up, and defrag windoze) I then set about partitioning the 120GB hard drive using a LiveCD of Puppy Linux(Gparted) via an internal cd-rom drive I had laying around and one of these gadgets which, I must say, no tech or hobbyist should be without([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)).

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

After the partitioning ritual(reducing the windoze partition in several smaller steps with the obligatory reboot into windoze between each reduction so checkdisk could do it's thing and so I could defrag with each reduction) I installed Puppy Linux and was pleased that it worked very well from the get-go(Puppy installation slipped the Grub bootloader in place also). Then it was off to the races to install Ubuntu 9.04 Jaunty Jackalope (full version) which also went without any problems at all. It took a minimal amount of time and fiddling to get it working with the wireless.

Of course there was the minor editing of the grub's menu.lst to get it looking "just right" and a couple of reboots into each system, but I must say that I am pleased with the performance and overall experience. I've also reserved five more partitions for future *nix distros as well.

One note with respect to the 8.9 inch display...it's small and it bothers my eyes more quickly than the bigger screens. I plugged it's VGA output into a nice 17 inch monitor I have on the tech bench and it looked great and was easy on my eyes.

I'd imagine using this little guy to drive a big monitor and, with a wireless keyboard and mouse assisting, it being a reasonably energy-efficient alternative to the regular desktop monsters consuming hundreds of watts unnecessarily.

.

of course, my regular LiveCD of full version Jaunty had been used successfully several times previously so I knew I had a good burn

why did you start a new thread on this?

I think you should just install the full version and not the UNR

.

---

### Post by jaqrah on 2009-07-23
By any chance do you have Compiz enabled?

Compiz and UNR do not play nice together.  The problems you describe are some of the problems I and others have experienced when using UNR and Compiz.

---

### Post by LewRockwell on 2009-07-23
slightly off topic but super cool anyway

[http://www.ubuntumini.com/2009/05/become-command-line-commando.html](http://www.ubuntumini.com/2009/05/become-command-line-commando.html)

.

---

### Post by FeTTo on 2009-11-03
has anyone found the issue? im having the same problem after upgrading from 9.04 to 9.10. i was good since the day 9.10 came out till today. I tried to hook up GI Joe from my laptop to my DLP tv via PC connection. First time doing so on 9.10. Gave me an error that it cannot configure the screen. I tried this about 10 times figuring it might work ( yeah i wish) and then after this i noticed the laptop starting to slow down, the panel bar, 1 by 1 had icons dissappearing from it. Then the bottom task bar moved up top and overlapped the top task bar. Now i just have a blank grey bar on teh top of my screen. It takes me about 15 times of logging in then control alt backspace over and over before i can get the desktop to load. I do gnome-panel in terminal and it just says 

"steve@steve-laptop:~$ gnome-panel &
[2] 6714
steve@steve-laptop:~$ Cannot register the panel shell: there is already one running."

is there a way to end that panel and start over? Before when i had both panels overlappinig i right clicked and turned autohide off and this problem started. Right now i just have rythm box in the left corner, and its moving up and down like the panels are fighting with each other over who gets to be on top. WTF help 
"

---

