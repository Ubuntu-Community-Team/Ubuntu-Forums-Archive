---
title: "Help with wireless connection"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by mollyc on 2005-07-06
Hi everyone-- this is my first post here.  Last week I had a very bad Windows experience, and decided it is more trouble than it is worth.  I have wiped my laptop clean and installed Ubuntu.  I am a brand new newbie and don't know much beyond basic commands.

How do I get ubuntu to "see" my wireless adapter?  I have opened Device Manager and found the card.  The information below says Device Unknown, Capabilities Unknown.  How can I change that?

Best wishes,
Molly

(p.s.  If there is a button at the bottom of the screen, please let me know.  I can't see it because my screen resolution defaults to 800 x 600.  I did go to preferences-- screen resolution, but 800 x 600 was as high as it went.  Another issue.)

---

### Post by rachii on 2005-07-06
welcome to ubuntu!!!  both of your issues are very common.  (its all just a matter of configuring ubuntu to work with your computers setup.) so if you search these forums you'll find your answers everywhere for both of your issues

but in short:
 for the wireless it sounds like you need to install the drivers.  do you have a cd with the wireless drivers on it, or can you download the ones speciific for your wireless cards model?  
ubuntu comes with the tool ndiswrapper   which manages your wireless card
this is a command prompt tool.  so if you right click on the desktop and click on open terminal, you will get a command line to work with.  

this thread has a compilation of howto's from the forums, check the ndiswrapper one to get your wireless setup
[HTML]http://ubuntuforums.org/showthread.php?t=31094&highlight=index+howtos[/HTML]

and if you  just do a search for 'resolution' or something like that you can find your other answer

enjoy

---

### Post by mollyc on 2005-07-06
Hi Rachii--  linksys does not provide drivers for linux unfortunately.  I will look for more info on this ndiswrapper.

I have searched for "resolution" but I haven't found much that applies.

---

### Post by rachii on 2005-07-06
yeas, sorry.   you use the windows drivers (i think i used the xp drivers).  just save them somewhere that you will remember. then in a command line type```
ndiswrapper -i filename.inf
``` replacing filename with the name of your driver (it is the .inf file).  like with my linksys...on the disc there was a driver folder and then inside there was another folder with my driver.  i just copied that folder to my home directory and then in the command line navigate to that folder.

cd - changes the directory
ls  - lists the files in the current directory
pwd -  tells you the address of your working directory...where you are

then do the ndiswrapper code above
to see if if installed correctly do```
ndiswrapper -l
``` and it will "list" the installed drivers/cards.

that should get you started with your wireless

---

### Post by rachii on 2005-07-06
(a second post, to refer to your second issue)

if you open up another terminal and type```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```(this will copy the file and make a backup in case we mess up the original)  sudo gives you super user permission allowing you to edit this file which is read only. it will ask for your user password. then do```
sudo gedit /etc/X11/xorg.conf
``` now we can fix your resolution issue.

scroll down towards the bottom and notice where all of the resolutions are listed under section "screen" and subsection "display.  what do you have listed?  there might be different "depths" .  on one of them just add the resolutions you want (following the format numberxnumber in quotes)  then just copy those values for all the other "depths".  for example, a snippet from my xorg.conf:
```
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
```
(i had to add the two higher resolutions in order to use them)

hit save and restart X (the graphical display manager) to do this hit ctrl+alt+backspace.  then log back in and you should be good to go, and under system-preferences  you should be able to select a different resolution now

---

### Post by mollyc on 2005-07-07
Hi Rachii-- thank you so much for taking the time to answer my questions.

I downloaded ndiswrapper and got it on my laptop..  then followed both your instructions and the instructions from the HOWTO index.  Unfortunately I couldn't get either to work.  

It's probably something very easy, I just don't know what I'm doing.

From the ndiswrapper folder, when I type in sudo make install, I get the message "Can't fine kernel sources in /lib/modules/2.6.10-5-386/build; give path to kernel sources with KSRC=<path> argument to make


Regarding the screen problem.  Oddly enough, I opened up my xorg.conf file and found that the *only* screen resolutions in there were 1024x768, which is what I want.  Maybe the problem is something else?  The background picture seems to be showing with high resolution, it is the windows and taskbars that appear too large and distorted.

Maybe I just need to re-install ubuntu?

Very confusing.  Thank you again for your time.

---

### Post by tbasten on 2005-07-07
Hey Molly,

Welcome to Ubuntu forums.

In regards to your resolution, ubuntu often installs only a few resolutions. I am not sure but i think it only installs the resolutons that will work. You can try adding "1280x1024" into your xconf.org file. restart your GUI by pressing alt+cntrl+backspace if id doesnt work press alt+ctrl+-

In regards to reinstalling ubuntu, there is no real need for it. Thats the best part about ubuntu is that u install it once and thats it. Unlike windows, if something bad goes wrong u have to reinstall it,

Regards, tbasen

---

