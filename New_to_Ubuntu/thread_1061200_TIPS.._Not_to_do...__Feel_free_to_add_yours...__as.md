---
title: "TIPS.. Not to do...  Feel free to add yours...  as in &quot;Why I had to reinstall&quot;..."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-05
Don't download Linux stuff with an old dell in a Windows OS... It seems to seriously mess things up...  Download it a different machine, or apply for the free CD...

Never run a cleanup code, nor cleanup-software, immediately after a new Ubuntu install, before you've installed all the necessary updates and peripherals...
The cleanup could take-out items that aren't set solidly...  You'll be reinstalling Ubuntu...

Never place a Windows software installer on Ubuntu's desktop...  You probably won't be able to delete it from trash.. from the desktop if you're lucky...

Don't even think of Wine-installing PhotoPlus in Ubuntu...  You'll regret it big-time...  You'll be reinstalling Ubuntu...

Never ever try to install WinWall in Ubuntu...  WhooH!..







[next time an strange Absolutely HUGE bear-sized Pit-Bull is meandering your way, and comes right up to you with its beady little eyes staring right through you.. Shout a strong meaningful sudden "HEAL!!".. and when it parks itself beside you, rub its neck and shoulder, while saying "Good puppy!"...]

---

### Post by racie on 2009-02-05
While uninstalling or installing Ubuntu through Wubi, disable all firewalls.


It screwed up my computer when I forgot to.  =P

---

### Post by jerome1232 on 2009-02-05
Well I have to say I've never been able to destroy an install past the point of repair yet, everytime I've reinstalled it was because I wasn't happy with my partitioning scheme. 

So I finally switched to using LVM to make repartitioning everything something I could easily do from a live cd :).

I think the most common thing I've seen on these forums is chmoding or chowning /, now that's a reinstall ;)

---

### Post by donkyhotay on 2009-02-05
Not being careful with the directory specified when doing
```
sudo rm -fr /path/to/directory
```
I've accidently wiped out my /sbin that way. Oh, and even though this is a list of things *not* to do I suppose I should mention to NEVER run the command above unless you know exactly what are doing because although it's useful and necessary it times you can easily (as previously mentioned) really @#$% your system bad.

---

### Post by jimv on 2009-02-05
> Don't download Linux stuff with an old dell in a Windows OS... It seems to seriously mess things up... Download it a different machine, or apply for the free CD...

Your machine had a unique problem.  You can't extrapolate that to include all Dells.  That's ridiculous.
> 
Never run a cleanup code, nor cleanup-software, immediately after a new Ubuntu install, before you've installed all the necessary updates and peripherals...
The cleanup could take-out items that aren't set solidly... You'll be reinstalling Ubuntu...

That doesn't even make sense.  Software is installed as soon as it's done installing.  There is no waiting for it to "set solidly".

> Never place a Windows software installer on Ubuntu's desktop... You probably won't be able to delete it from trash.. from the desktop if you're lucky...

Another unique problem that you had.  Ubuntu doesn't care what kind of file something is.  If it's not deleting it when you tell it to, you were probably using sudo/root when you placed the file there, and thus your regular account didn't have sufficient permissions to delete it.
> 
Don't even think of Wine-installing PhotoPlus in Ubuntu... You'll regret it big-time... You'll be reinstalling Ubuntu...

There is nothing that you could install in WINE that would ever necessitate a reinstall of Ubuntu.  Delete your /home/you/.wine folder and you're good to go.

---

### Post by DonaldJ on 2009-02-05
> **jerome1232 said:**
>  "I've never been able to destroy an install past the point of repair yet..."




You The Man!...

---

### Post by estyles on 2009-02-05
Don't use chown or chmod on system directories.  I know you want to have rights to read/write everything on your whole system, but you won't get what you want, and nothing will work right.

I never chown'd my whole drive, but I did chmod a+rw my /var directory because a power outtage had severely borked my /var partition and I thought that the reason my install couldn't write to /var was because of write permissions.  Luckily, removing the /var partition fixed the problem and Ubuntu could create it's own hierarchy for /var.  I wouldn't have been so lucky if I had chmodded the /bin directory, frex...  :p

---

### Post by drumfire420 on 2009-02-05
RTFM
seriously, read anything you can about what you're doing before doing it (and try to have it handy while doing it).  if you're pressed for time
 A) this is when you WILL make mistakes and
 B) skimming through it helps too

now that that's out of the way

when you download anything important (like a live CD) run some checksum on it after downloading AND after burning.  It will save you a TON of headaches!  you CANNOT assume things will download and burn correctly.  It takes all of 5 min to check, just get in the habit and do it.

---

### Post by DonaldJ on 2009-02-05
Things to never do...


Never sweep the floors with the tower running...  
The floating dust will be sucked-in by the fans...
Dust in fan bearings heats up, turns to carbon, and abrades bearings like fine sandpaper...  Oil doesn't fix a chewed up bearing... Oiling a wrecked bearing is like adding oil to a car engine that blew because it ran out of oil...

Never park a tower close to a heat source..  it will suck in the heat, and heat what it supposed to be cooling...

Never leave a PC plugged-in during a violent lightning storm...

Never drink liquids over a keyboard.. unless you really enjoy puzzles...

Never close up tower case without first having picked it up, and given it a little shaking, to ensure there aren't any loose metal things resting on the M-board...

Never go touching your fingers to the chips on a M-board while its powered up... A bit of static hitting them is like lightning hit you...

Never plug-in or unplug things from a tower while it's running, except USB's and RCA audio plugs...  You can fry a logic board, from "cross-pin static"...

If you've got a cord chewing pet wandering around the home.. boil-up a bottle of cayenne to a paste.. add a squirt of mace defender, and a tsp of saffron...  Boil it down, and paint it on wires.. especially if you have a pet rabbit...  Pet bunnies can chew through a cord, electrocute themselves, ignite the carpet, and burn the house down...  Not a good idea for nail-biters, it's so Hot, it might make a kid's bum "fall-off"...

If when you sit at the PC, and touch the mouse or keyboard, the screen flickers.. change your chair from a plastic chair to a wooden chair, and go down into the basement, and check to ensure that the building's electrical ground-wire isn't green corrosion...  If it is seriously green, get out the tools, remove the connection, clean it to shiny metal, reinstall it back tight, then spray it with clear paint... Then buy an AC-outlet polarity tester...

If your Internet connection fails every week.. find the cable entry to the building... If its cold, it means there's cold air leaking through the wall where the cable hole was drilled, which means when it's cold outside the inside connectors build-up moisture, and corrode... If you see the slightest bit of white corrosion on a cable connector, replace both cable ends...  You'll need a cable connector crimper.. A couple dollars from a "dollar-store" or liquidation center... 30-bucks from the tools stores...
If your internet connection fails a lot on dial-up.. check the wall sockets for green corrosion.. If you see any, change the wall unit... 50-cents at a cheap store... 5-bucks at a regular store... 50-bucks for the telephone company to change it...

Never drop a nextec lighted keyboard...

Never drop a cheapy flash drive...

Never trust a flash drive to be your permanent backup...

Never leave the CD door open when not in use...

Never power-up a piece of electronics that was brought-in from below zero temperatures without letting it warm-up for at least half an hour... Always wrap cold electronics in plastic bags, outside before bringing them into a warm moist-air building...  It prevents moisture from collecting on the internal components...  Most electronics really don't like running in water.. Some more than others...  This is why so many car-stereos die in winter... Warm up the vehicle before switching them On...

---

### Post by OutOfReach on 2009-02-05
Never try editing an important file without knowing EXACTLY what you are doing.

^ That's how I b0rked my wireless and had to reinstall. I was a noob at the time, I didn't know what exactly I was following (from a tutorial) and I didn't know how to fix it... I was trying to bridge my internet from my laptop to my 360...

---

### Post by DonaldJ on 2009-02-06
I'm guessing that it's a bad thing to run any cleaner before doing a reboot... You could have installed an update that hasn't been properly set, which could wipe out critical segments of packages and codes, and cause any number of weird glitches...  And from the little I've experienced with Ubuntu cleaners, I found they do speed-up the OS a little bit, but they seriously damage it too... Maybe the system should be run as it is, and not gutted and raped, like I had so much fun doing with Windows junk...

It doesn't seem that the user can speed-up the Ubuntu system merely by uninstalling things, like games and unwanted softwares, like you could in a Windows OS...  Every-time I uninstalled Ubuntu's games the OS seemed to act a little damaged..?  I like games in my PC as much as I enjoy "falling face first in barn-mud".. I do not like playing interactive cartoons anymore...  Maybe I should just leave the OS as it came, and stop trying to make it better, when I really don't know what the h I'm dong in there yet...

Also it seems that a few downloads in the downloads-list cause conflicts and glitches in Ubuntu..?  I wish I knew which ones are OK to install, without having to go through all the grief of trying to repair a conflict mess that I foolishly invited into my machine...

This install I'm gonna try to keep my claws and fangs off it for a month, and just run Ubuntu like it is, till I'm sure of what I'm adding and subtracting...

---

### Post by marcgh on 2009-02-06
NEVER forget common sense when installing or deleting any file or directory.

NEVER confirm if you are not sure, ask advice (we have top forums here for help)

and finally: I will NEVER again do major updates or Kernel updates without backing up all data first.

---

### Post by nothingspecial on 2009-02-06
Ah but I think you may miss the point.

Never do anything on your main system that you don`t understand fully ...... but ....... seek out and old, toasted, cheap laptop; install some distro on it and have a good ol' chown, chmod, rm etc about on it. You will have to reinstall a few times but there`s nothing like breaking your box and attempting to fix it. Best way to learn in my opinion.

---

### Post by DonaldJ on 2009-02-06
Good point...   

I'll add a little twist to it.. If you find you've killed the OS, and your next play must be to reinstall the OS.. why not get right into it and see what serious damage you can really do to it for an hour... 
If you have a backup computer, you can search-out suggestions and cures to the messes you did, and try to repair some of it... That's when you really learn a lot, fast...  Be like a kid cut-loose in a candy factory...

---

### Post by DonaldJ on 2009-02-14
Never install "Gnome Apt Software Manager" in Ubuntu"...  Big mistake!..
I kills the window's top tool-bar, and kills right-click, and causes a tremendous Mess in the OS...  Uninstall it, and reboot, should fix it..  It did for me,  but it might have left a little damage...

___________________________________


So.. How do I exchange my four green coffee beans, and one ripe bean, for triple-rotted cocoa beans..?
I wonders what coffee made from green beans tastes like..?  Probably extremely bitter, thinks I...

---

