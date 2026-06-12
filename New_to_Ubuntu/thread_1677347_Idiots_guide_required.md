---
title: "Idiots guide required"
date: 2011-01-28
forum: New to Ubuntu
---

### Post by R Trotter on 2011-01-28
Hello all. I am a recent convert to Ubutu 10.1. I am trying to get the soft keys and pen working on my HP Compac tc4200. I also cant find an on screen keyboard. I have done a couple of searches and found lots of posts about writing lines of code. This is all a little above me. Can anyone out there give me a step by step please?

Rod

---

### Post by ikt on 2011-01-28
> **R Trotter said:**
> Hello all. I am a recent convert to Ubutu 10.1. I am trying to get the soft keys and pen working on my HP Compac tc4200. I also cant find an on screen keyboard. I have done a couple of searches and found lots of posts about writing lines of code. This is all a little above me. Can anyone out there give me a step by step please?

Rod

Heya, welcome to ubuntu community :)

> **R Trotter said:**
> I also cant find an on screen keyboard.

[https://help.ubuntu.com/community/Accessibility](https://help.ubuntu.com/community/Accessibility)

> On-screen Keyboard

Ubuntu includes the onboard on-screen keyboard, a lightweight text-entry application, extensible through macros, scripts and custom layouts. 

To run just head into [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") (Applications > Accessories > Terminal) and type 'onboard' without the '', and it should run.

Getting the stylus working seems a bit more difficult, I'll hope someone else knows a bit more than me :)

---

**To have onboard autostart on login** create a small bash script called .onboard_start.sh and save it to your /home:

Applications > Accessories > Terminal 

gedit .onboard_start.sh

copy the code below and paste into the file. Save and close

#!/bin/bash
sleep 10 && onboard;

This would start onboard after 10 seconds after you login. The delay can be changed but 10 is pretty fast anyway.

Then back in terminal do:

chmod a+x .onboard_start.sh

Now, add it to your startup programs (menu: system->preferences->startup applications).Note, path to script is /home/>your user name/.onboard_start.sh

---

### Post by R Trotter on 2011-01-28
Cheers much appreciated. So i can only access the keyboard through the terminal? Do you know if i am able to tie the keyboard to one of the soft keys that are currently inactive?

---

### Post by alzie on 2011-01-28
To create a launcher for the keyboard, right click on the top panel and select "add to panel"

Click on "Custom Application Launcher"

Leave the "type" as application, enter a name you want to call the application and type onboard in the command space.  Click ok.

You should see a new icon on the top panel now.  Clicking it will launch the on screen keyboard.

I hope this helps.

---

### Post by R Trotter on 2011-01-29
Job done. Cheers guys

---

