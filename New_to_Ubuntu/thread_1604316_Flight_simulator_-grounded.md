---
title: "Flight simulator -grounded"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by Eddison on 2010-10-23
Hullo,

Really like the open source flightsim; flightgear but I'm going to commit murder if I can't get it working :)
This is a stupid and easy to fix problem, but not if ya don't know how to fix it?? I want to add a folder of some aircraft to the main program, and this is what i am supposed to do..

[LIST=1]
[*] Open Terminal and log in as root
[*] Navigate to /usr/share/Games/FlightGear/Aircraft
[*] Extract your aircraft file into the folder
[*] Start up flight gear. Your aircraft should show up in the launcher
[/LIST]
Tried to set up a new user with great permissions, messing around with the root folder- i had to reinstall ubuntu.
Please HELP! assume your talkin to a cmplete IDIOT thanks!

Eddison

---

### Post by sgosnell on 2010-10-23
Don't add a new user, that won't help.  Don't change the permissions.  Root owns everything in the /usr hierarchy, and always will.  To make any changes to any folder/file other than your home, use sudo before the command.  Sudo makes you a temporary superuser, and you can do what you need to do.  You can also bork the system, so be careful with it.  Linux assumes you know what you're doing, and will let you do whatever you want if you use sudo.  In Ubuntu, you don't need to log in as root, just use sudo.  For what you want to do, use ```
cd /usr/share/Games/FlightGear/Aircraft
sudo tar -xf aircraft_file 
``` where aircraft_file is the filename of the tarball you want to extract.  That should do it.

---

### Post by Eddison on 2010-10-23
Hi,
Thanks for helping..
ok i got into the /usr/share/games/FlightGear/Aircraft folder, now i have to place this file in there, which is on my desktop R22_20080503.zip
This isn't a tarball? I tried sudo tar -xf R22_20080503.zip but i am not i that directory?
I'm totally confused now lol!

---

### Post by sgosnell on 2010-10-24
You need to use ```
sudo tar -xf /home/user/Desktop/R22_20080503.zip 
``` where user is your username.  You have to tell tar where the file is.

Or you can do it the GUI way, and enter ```
gksu file-roller
``` to open the archive manager as root, and use it to navigate to the file, open it, and have it extract the contents to the folder you need it to go to.  Gksu says to run a graphical program as superuser.  If you have the proper extensions installed, you can use the file manager to go to the file, right-click on it, and select Open as Administrator.  I'm not running Ubuntu right now, so I can't recall the exact script extensions you need.  I'm running Linux Mint Debian Edition, and that comes standard.

---

### Post by Eddison on 2010-10-24
Haloo !

Thanks sgosnell, that worked a treat !! I got me a core i7 with gtx 460 card 6gb ram an its the flight sims that are suffering now, not my pc lol!
Using ubuntu for 6 months now, an i love it!! but its great to be able to do things like this with it.
Now all i have to do is find a tutorial on the archive manager !!

kind rgrds
Ed.

---

### Post by Eddison on 2010-10-24
Just adding a note to above..
The aircraft file was a Sikorsky-76C.zip file. this didn't extract too good for me, so i right clicked it, then extracted it to desktop, then right clicked it again, and compressed the aircraft file to a tar.gz type of file.
Then using the terminal window i typed in cd /usr/share/games/FlightGear/Aircraft This is where i wanted to add aircraft like a Sikorsky to FlightGear. 
Writing this as extracting files into folders is a handy skill to have when using ubuntu.

Now as sgosnell suggested, I extracted the file I wanted into the aircraft directory of FlightGear like this;
sudo tar -xf /home/eddison/Desktop/Sikorsky-76C.tar.gz
don't forget to use any caps you see.
eddison is the username of my computer, it could be ubuntu or whatever you named your computer, but 'eddison' will need to be replaced with whatever username you have. If you want to see this, click on 'places' at the top of the screen, then click on 'home folder' now look at the very top of the window that pops up, above file edit view and go. 

Eddison

---

### Post by sgosnell on 2010-10-24
How does the S76C (which variation is it?  C, C+, C++?) fly on the sim?  It's a dream to fly as a real aircraft, but I've never tried it on a PC sim, just the Flight Safety Level D full-motion sim at West Palm Beach.  That one is very realistic, but it should be for the millions of dollars they spent building it.

---

### Post by Eddison on 2010-10-24
Can't seem to get that sucker to work- the Sikorsky S76 i mean. I am using R22 flight sim instead. I flown the real thing, and its really really good. Very similar, except without the large food blender above you lol! Sims are tricky in that it can be hard to judge distance from the ground, so i usually hover over to the airport to practice hover etc.
Compared to the real deal its excellent- for a computer model. I like the rotorway, but what I really want is this;
[http://www.vertical-aviation.com/](http://www.vertical-aviation.com/)
Thats why its a pity the sim aircraft S51 and the S76C are not working, as the humming bird is based on the old S52, and the S51 is the closest I can get in a sim. 
I want to build one of these things, maybe with an LS 7 engine or jet engine mmm nice.

---

### Post by Eddison on 2010-10-27
I have a question for experienced users, but when i play the game Flightgear, after about half an hour, the sound starts to cut in and out. 
At first i thought i fried the sound chip on the motherboard, or the northbidge or something.
I have a new gigabyte ud7 motherboard, quad core i7 chip, 6 gigs of triple channel ram, a GTX 460 graphics card, and Ubuntu 10.10.
Is there some sort of buffer that fills up, or overruns?
Thanks for helping.

Ed.

---

### Post by sgosnell on 2010-10-27
Are you running Pulseaudio?  That can be problematic, IME.  It's also hard to remove from Ubuntu.  It's also possible that it's a hardware problem, with heat causing expansion of connectors or something else, resulting in a poor connection.

---

### Post by Eddison on 2010-10-27
Thanks for the reply. Pulseaudio? have no clue what I am running lol! I know the mobo uses realtek controller. It was a clean install of ubuntu 10.10 on new motherboard.
Funny thing thing is the temps look great. I have a baram cpu cooler with 2 120mm fans stuck either side of it. One pulling one pushing. The case has 120mm fan, and two fans on the graphics card. Temps are about 30 degrees centigrade on the cpu- its not overclocked, and system temp is never over 38-40 degrees centigrade. 
Quite unnerving thinking the sound chip is frying- 

Running the flight sim for half an hour, then the sound deteriorates. Now if I exit the program, and leave the computer to idle, and cool, then start flightgear again, it is like it starts where it left off- sound cutting in and out, like it is a chip getting hot.
If I turn off the computer immediately, and restart, flightgear has no sound probs for another half an hour?? checking system health, when the sound goes-the weather is fine! Also, after running FG, and I play video, the sound in that is corrupt also- restarting cures it all??
I'm not too bothered, if I have to restart, but only like hot chips in a sandwitch, not in my nice pc.

Ed.

---

### Post by sgosnell on 2010-10-28
I wasn't suggesting that a chip was overheating, just a connector somewhere.  The temp inside the computer is certainly rising after some time, as everything heats up, and the metal of a connector can be expanding very slightly, resulting in a poor connection.  If the audio is built into the motherboard, that likely isn't the problem, but if you have a separate soundcard, you might try reseating it.  

Pulseaudio is a software package for audio.  It can cause problems in some cases.  It's installed by default in Ubuntu.

---

### Post by 3rdalbum on 2010-10-28
A lot of problems attributed to Pulseaudio are actually caused by OpenAL, the directional sound library. If Flightgear uses OpenAL by default, try configuring it NOT to use OpenAL.

Choppy sound usually indicates OpenAL at fault. No sound or "late" sound indicates Pulseaudio at fault.

---

### Post by migs73 on 2010-10-28
> **Eddison said:**
> 

Now as sgosnell suggested, I extracted the file I wanted into the aircraft directory of FlightGear like this;
sudo tar -xf /home/eddison/Desktop/Sikorsky-76C.tar.gz
don't forget to use any caps you see.
 

Once you have typed 'sudo tar -xf' into the terminal, just drag the file from the desktop into terminal and terminal will auto fill the destination. Saves you typing it wrong!

---

### Post by sgosnell on 2010-10-28
Or just press the Tab key after typing the first few letters of the file, which autocompletes the entry.  If it won't autocomplete, then there are multiple files with the same start, and you can type another letter or more, and then get autocomplete.

---

### Post by Eddison on 2010-10-30
Open AL? i hope that is the problem, but the computer is still alive, and that is the main thing. I'll have to dig into some of the flightgear files to find it. As I mentioned, it is affecting other apps as well- thanks for that 3rdalbum 

> Once you have typed 'sudo tar -xf' into the terminal, just drag the file  from the desktop into terminal and terminal will auto fill the  destination. Saves you typing it wrong!> Or just press the Tab key after typing the first few letters of the  file, which autocompletes the entry.  If it won't autocomplete, then  there are multiple files with the same start, and you can type another  letter or more, and then get autocomplete.This is really fantastic advice guys, i didn't know that could be done. It's kinda offputting to learn about this, especially when you have type everything, and Linux is a bit of a curve. Great!


Eddison
[URL="http://ubuntuforums.org/member.php?u=61044"]
[/URL]

---

