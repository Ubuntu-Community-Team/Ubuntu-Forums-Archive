---
title: "Proplems with software center &quot;java 6 runtime&quot;"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by rupp on 2010-03-30
I am trying to install java 6 runtime.  At first I was getting a message saying manager was busy but I did sudo dpkg --configure -a  now its starts the download and stops a 3% and says the installation or removal of software package failed.

Details " E: wasn't able to locate a file for the sun-java6-jre package. this might mean you need to manually fix this package. (due to missing arch):

one other note I tried to install java from terminal useing

sudo apt-get install sun-java6-bin sun-java6-jre   

 But at the end it had like and over lay of my terminal that was asking me to hit ok but it would not let me type of mouse over it so I think maybe its hung up.

---

### Post by lidex on 2010-03-30
Here you go :
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by somethingkindawierd on 2010-03-30
I had a similar problem where the terminal overlay came up and I could not active the 'ok' button. I had to tab focus to the 'ok' button so when I hit enter it activated the button.

---

### Post by rupp on 2010-03-30
Thanks Lidex and Something,

after trying a few more things I got
ezra@system1:~$ [COLOR=Red]apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/COLOR]
:

that got me to this thread [COLOR=Lime]www.ubuntuforums.org/showthread.php?t=1424441&highlight=open+lock+file&page=2 
[/COLOR]
so I searched for broken package in synaptic file manager and found java was broken.  after trying to remove it I got this message 

[COLOR=Red]E: sun-java6-jre: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.[/COLOR]   

I can not install it so I don't know how I am going to reinstall it

---

### Post by rupp on 2010-03-31
Thanks again for your help.  

I was able to repair the package in synaptics and I think it is okay.   I am posting my terminal just in case it might help someone "I doubt it"

ezra@system1:~$ sudo apt-get install sun-java6-bin sun-java6-jre
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ezra@system1:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ezra@system1:~$ cd /var/lib/dpkg
ezra@system1:/var/lib/dpkg$ sudo fuser -u ./lock
ezra@system1:/var/lib/dpkg$ cd ~
ezra@system1:~$ ^C
ezra@system1:~$

---

