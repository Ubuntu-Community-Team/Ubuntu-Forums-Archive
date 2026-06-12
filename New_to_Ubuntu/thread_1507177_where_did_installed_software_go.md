---
title: "where did installed software go"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by stormchaser2063 on 2010-06-11
Good Morning and go CHICAGO BLACKHAWKS!!!


ok, now i dont really want to say this is an annoying issue, but it really is. I downloaded or installed a weather app using the ubuntu software center yesterday and it says its installed.... but for the life of me, i cannot find it. I believe the name of the app was wmdockmaker weather + or something close to that name (im using my apple powerbook at the local starbucks now so cant really look up the name of the app.) but where the h*** did the app go?

im running ubuntu 10.04 on my desktop and thats where i wanted this app to go since i am a storm chaser and weather applications are important to me. also does anyone know of a good weather radar program/application that will run on ubuntu 10.04 since gr level x wont?

thanks have a great day and congratulations to the CHICAGO BLACKHAWKS!!


im going to their parade and rally this morning so hopefully i can find my post when i get home!

---

### Post by Ichido on 2010-06-11
What I do when this happens to me is to first test to see if the software is installed by typing the name of the software in a Terminal Window.
If this works, then I Create a Launcher in my Top Panel or on the Desktop.

Right Click on the Top Panel and choose Add to Panel. Then Custom Application Launcher and choose Add.
On the Desktop, Right Click and choose "Create Launcher".
Fill in the following:

TYPE: Application in Terminal
NAME: Call it what you want.
COMMAND: "Name of Program"

Usually after a reboot or some updates, the Program will appear in the Applications Drop-down Menu.

PS I wasn't rooting for the Blackhawks be they were/are the Best Team!

---

### Post by Peter09 on 2010-06-11
in a terminal try
 
```
locate wmdockmaker 
```
 
if should tell you where it is.
 
Also, if you cannot remeber the exact name try
 
```
 
locate wm

```
 
and instead of enter hit the tab key (autocomplete) it will show all options which fit wm.

---

### Post by _Mark_ on 2010-06-11
[ATTACH]160069[/ATTACH]

See attached screenshot, I think that was what the OP downloaded, in which case it is a widget to be used for the Windowmaker dock so it won't be seen unless you have that installed also

---

### Post by manishsarkhel on 2010-06-11
1...>search in ubuntu software centre by the first few letters of the application name

2...>just press alt+f2
type the first few letters of the application name.....

if the above 2 do not work then you can download a useful application for it....

3...>then you can download a useful application which can find other applications

first update ubuntu by pasting the following in the terminal(accessories->terminal)

sudo apt-get update

then type your password

after update

type sudo apt-get install xfce4-appfinder

to install xfce4 application finder

---

### Post by stormchaser2063 on 2010-06-12
well that works... right clicking on the bar worked. nice to know that there are other ways to find programs/apps that are missing too you guys are the best. too bad that i cant find a gr level 3 radar program substitute that will run on ububtu though... any ideas


Go HAWKS.... stanley cup repeat in 2011

---

