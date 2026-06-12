---
title: "How to Lock down Ubuntu"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by buncey on 2010-06-23
[LEFT]All I am new to Linux / Ubuntu so please bare with me if these questions are simple or answered elsewhere.
 

Background:

I work for a small company of 40-50 users and we are thinking about going thin-client as our desktops are 6-4 years old and currently running XP SP3, which run slow as it is. (without thinking of the nightmare and costs of going to Win 7).
 

We are thinking about going to a thin-client solution as it will be cheaper and we will not need to replace our machines anytime soon.
 

I have been tasked with trying to get a test desktop working.
 

My initial idea was a locked down desktop what will only allow you to connect to our WCP though the browser, I have done this successfully with Windows XP (However with licensing costs, I thought a Linux OS would be better for the desktop thin-clients)

 
Question:
 

Can Ubuntu be locked down so that all it allows is the user to access just 1 URL (My WCP) through a browser? 
 
Ideally like the software Sitekoisk does to Windows, turning it into a terminal, because as long as the users can connect to our WCP it will be fine.
 
 

Can Ubuntu be locked down in such a way?
 

Is there an Open source software you can think what can do this with Ubuntu(linux)?
 

Or am I barking up the wrong tree completely and if so can you point me in the right direction?

 
Linux Noob[/LEFT]

---

### Post by bwallum on 2010-06-23
If you are running machines using XP then you will get a definate performance improvement simply loading up Ubuntu. You get a rich environment, you can read and edit all your MS Office stuff, you'll have no licence fees to pay and you can get a demo machine up and running in 2 hours max. This forum will help out with any issues on the way. No need to go thin client.

If you do still want to go thin client have a look at the minimalist Ubuntu, check that you can network boot from a server (Ubuntu server is free too) using your existing hardware and you can restrict your browser as much as you like (Firefox is the default browser in Ubuntu at the moment). But why?

This is an old thread [https://help.ubuntu.com/community/ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto") which shows it can be done. I'm sure if you go thin client then this forum will be on hand to help out. With all the money your company will be saving you could even consider a small donation to the Open Software Foundation.

Good luck whichever way you go.

---

### Post by buncey on 2010-06-24
[FONT=Calibri][SIZE=3]Thank you for your prompt reply.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I will have a look at the thinclienthowto[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]The reason I would like to lock down Ubuntu, is that I also have to get a Internet Kiosk up and running [/FONT][FONT=Wingdings][FONT=Wingdings]L[/FONT][/FONT][FONT=Calibri]. Were all the user is able to do is access the web, no viewing files, no saving,. Just web access? Any ideas on that?[/FONT][/SIZE]

---

### Post by Paqman on 2010-06-24
> **buncey said:**
> Any ideas on that?

IIRC, KDE has a "kiosk mode" built in.

---

### Post by bwallum on 2010-06-24
Could you explain a bit more about the hardware environment please. 

What are the input devices? E.g. touch screen, keyboard, mouse, usb stick....
What are the output devices? E.g. printer, monitor, usb stick...

EDIT
The reason I ask is that you can restrict Users System>Administration>Users and Groups, set up a user and try the advanced settings. You can then auto login to that user with System>Administration>Login Screen. It may contribute to the solution.

---

### Post by matchett808 on 2010-06-24
I looked at this at one point making the user re-login  after 1 hour (it was for a library) where the computer overwrote the /home/user partition every login...

---

### Post by buncey on 2010-06-24
[COLOR=black][FONT=Verdana]The Hardware is mainly Lenovo S50’s. 2.4ghz Celeron processer, 512MB ram[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Inputs (keyboard, mouse, usb)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Output (speakers, monitor, printer)[/FONT][/COLOR][COLOR=black][FONT=Times New Roman][/FONT][/COLOR]
[COLOR=black][FONT=Verdana]---[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I.e. When user logs on (generic log-on)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Goes straight to browser, (they cannot close browser or open any other applications).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The machine will be only for internet use.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana](Input usb, as request for people to upload images to social networking websites)[/FONT][/COLOR]

---

### Post by bwallum on 2010-06-25
Try this link

[http://locutusweb.asw15.org/index.php?topic=80.0](http://locutusweb.asw15.org/index.php?topic=80.0)

You use lubuntu and Chromium here, auto loading Chromium.

---

### Post by bwallum on 2010-06-25
> **bwallum said:**
> Try this link

[http://locutusweb.asw15.org/index.php?topic=80.0](http://locutusweb.asw15.org/index.php?topic=80.0)

You use lubuntu and Chromium here, auto loading Chromium.

This may not work, here is the 'knife and fork' method:

1) Create a user called guest (if none exists) System>Administration>Users and Groups

2) Create a file called chromium.desktop in /home/guest/.config/autostart

3) Paste the following to that file:

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Name=chromium
Name[gb]=Chromium
Comment[gb]=Systemmonitor
Exec=chromium
Icon=chromium.png
Terminal=false
Type=Application
X-MultipleArgs=false
Categories=GTK;Archiving;Utility;
StartupNotify=true

That should work.

EDIT
The above was learnt from sixpack75 on freenode #lubuntu
You may like to access this information source. Open an account with freenode then start chat (from top right envelope icon) and enter room "#lubuntu" without the quotes. You may need to let chat connect up before the room option becomes active (a minute at most)

---

### Post by grg3 on 2010-10-19
While Lubuntu is nice, it may be easier to lockdown gnome. Check out these two sites for ideas:

[http://jacob.steelsmith.org/content/ubuntu-kiosk-based-910](http://jacob.steelsmith.org/content/ubuntu-kiosk-based-910)
[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

---

