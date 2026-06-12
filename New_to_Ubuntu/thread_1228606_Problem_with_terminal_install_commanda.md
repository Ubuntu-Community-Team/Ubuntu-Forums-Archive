---
title: "Problem with terminal install commanda"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by samren on 2009-08-01
Hey Guys...I am an absolute newbie for linux just installed ubuntu 9.04 yesterday. Now i browsed through some sites and got a list of basic commands for linux
But..

1. I cannot install any packages using get-apt command in my linux or for that matter command sudo get-apt install vlc doesnt work either
2. I am not able to change the directory for both cases i am getting similar kind of error message which says 
could not find directory d: 
or unable to find vlc 

Kindly help

---

### Post by mapes12 on 2009-08-01
Can you install packages with System>Administration>Synaptic Package Manager?

And have you checked that you have the correct sources in System>Administration>Software Sources?

---

### Post by Mornedhel on 2009-08-01
> **samren said:**
> 1. I cannot install any packages using get-apt command in my linux or for that matter command sudo get-apt install vlc doesnt work either

Just to make sure, the command is apt-get, not get-apt.

---

### Post by Doctor Debian on 2009-08-01
> **samren said:**
> Hey Guys...I am an absolute newbie for linux just installed ubuntu 9.04 yesterday. Now i browsed through some sites and got a list of basic commands for linux
But..

1. I cannot install any packages using get-apt command in my linux or for that matter command sudo get-apt install vlc doesnt work either
2. I am not able to change the directory for both cases i am getting similar kind of error message which says 
could not find directory d: 
or unable to find vlc 

Kindly help

Just a note-

In Linux, D: is 

/media/cdrom

All dvd/usb/hard drives will be in the /media folder when you mount them.

:)

---

### Post by samren on 2009-08-01
Thanks a lot all of you

---

### Post by theozzlives on 2009-08-01
There are no drive letters in Linux, just like there are no .exe files. I think that concept was one of the hardest things to get used to, coming from DOS/Windows.

---

### Post by samren on 2009-08-01
yea...thats what i am getting confused at so can u explain me the basic architecture of linux and how to go about it....difficulty is that i am basically a construction engineer and My enthusiasm on linux and computers prompted me to take up this and explore...
Hence kindly help me in  detail...

---

### Post by samren on 2009-08-01
@maples when i tried installing using GUI i am getting the folllowing error

could not downlload all repository indexes....

No clue of wht to do now..kindly help

---

### Post by kansasnoob on 2009-08-01
One of my favorite places to start:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

Other great sources:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://users.bigpond.net.au/hermanzone/p5.htm](http://users.bigpond.net.au/hermanzone/p5.htm)

---

### Post by RomeReactor on 2009-08-01
Hi samren.

Regarding the problem with installing programs, it's possible the servers for your location are having a bit of trouble; you could wait a few hours and see if the problem clears up, or you could try setting your package managers to fetch the packages from another location. To do that, open Synaptic (System->Administration->Synaptic) and go to 'Settings->Repositories'. On the first tab to the left you should see a dropdown menu labeled "Download from:". Press it, select "Other", and on the window that pops up, press "Select Best Server"; that will automatically try to locate the most appropriate server for you.

---

### Post by samren on 2009-08-01
Dear all
Thanks for ur patience and support. when i tried to install using GUI the error said 
"proxy requires authenciation"

Kindly let me know where i can update username and pwd of my proxy server

Regards
Samren

---

### Post by RomeReactor on 2009-08-01
> **samren said:**
> Dear all
Thanks for ur patience and support. when i tried to install using GUI the error said 
"proxy requires authenciation"

Kindly let me know where i can update username and pwd of my proxy server

Regards
Samren

In Synaptic, go to "Settings->Preferences", and go to the "Network" tab. Even though it's really old, maybe [this thread]("http://ubuntuforums.org/showthread.php?t=73269") can be of help.

---

