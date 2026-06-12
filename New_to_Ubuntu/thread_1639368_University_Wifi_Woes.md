---
title: "University Wifi Woes"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by juantendo8 on 2010-12-06
Computer: HP Mini 2140
OS: Ubuntu 10.10 (Maverick)

Hi guys, I'm a new Ubuntu user with minimal experience. I love this OS and have had an easy time setting up and configuring it, but there is one thing that has been bothering me at my school (Cal State University Fullerton). The wireless network here has been easy to set up in windows but impossible for me to set up in Ubuntu, although they have designed a method specifically for this OS. 

The school uses Cloudpath Networks's XpressConnect to connect to the school server. They have two different methods to set up your network with Ubuntu.
   1. Download a file called [XpressConnect-Linux.tar]("http://wireless.fullerton.edu/wizard/students/tools/XpressConnect-Linux.tar") and run what I believe to be an installer.
   2. Click on a link that will take you to a page where the program will by run by a Java applet. I have Java installed and it seems to be working perfectly.

The end result of both these methods is exactly the same. It opens a message on a window titled "xmessage" that says this:

[COLOR=Blue] Unable to download x86 version. Please check your network connection and verify it is working properly! 
(URL: [http://wireless.fullerton.edu/wizard/students/tools/XpressConnect-x86.tar.bz2](http://wireless.fullerton.edu/wizard/students/tools/XpressConnect-x86.tar.bz2))

Linux JC-HP-2140 2.6.35-23generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux[/COLOR]


I have no idea what this means but I know that my wifi is set up and working properly and I can still sign on to the university guest wireless (which purposely disconnects me every 3-5 minutes and leaves me constantly logging on again). Like I said before, this method was supposed to work specifically for Ubuntu so I didn't expect such a problem. If anyone could offer me advice, solutions, or alternate methods to get wireless, it would be tremendously appreciated. Afterall, I would much rather take my Ubuntu netbook to school than my clunky (and old) windows lappy ;).

---

### Post by uRock on 2010-12-06
Looks like they aren't going to let you connect until you have installed the package. You may have to download it from their website while connected at home or somewhere else.

You may want to contact their IT department and ask them to help. My college has the Java applet for us to log in and once that is done we are free to surf the net, but other protocols such as IM Clients, POP3, IMAP, and such are blocked.

---

### Post by ac7nj on 2010-12-06
this file is a tar ball that you could download. Do not try to run it in place.

Click on places and create a folder for you new down load somthing like "download" is fine. 
click on the file and "save as" to your new file folder. then right click amd use a manager to un-pack the tar ball and install it.

---

### Post by juantendo8 on 2010-12-06
Well, I did download the file (tar ball?) to the downloads folder and I extracted it there. There was an X-shellscript file in there which I assume is like the linux equivalent of .exe. I run the program and I get the message that I previously posted. Im starting to think it might be a hardware incompatibility issue but I honestly have no clue. I think my best hope is to just follow Urock's suggestion and go to the IT helpdesk at my school. I'll hope for the best.

---

### Post by uRock on 2010-12-06
If it is saying, "Unable to download x86 version. Please check your network connection and verify it is working properly!," Then it isn't properly downloaded.

---

### Post by juantendo8 on 2010-12-07
I just tried downloading the tarball from my home network instead of the school's and extracting the program. Strangely, when I ran the program it seems like nothing happened. No error message at all. All I can do is wait until tomorrow to see if anything happened or not. Otherwise, I'll probably go see the IT helpdesk when I have some free time. Thank you all for your valuable input.

---

