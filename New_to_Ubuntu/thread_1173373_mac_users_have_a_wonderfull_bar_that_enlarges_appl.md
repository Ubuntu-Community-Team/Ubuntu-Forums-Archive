---
title: "mac users have a wonderfull bar that enlarges applications can we do this"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by blake7 on 2009-05-29
mac users have a wonderful bar at the bottom of the screen that enlarges applications logos when you pass the mouse over the icon.  which i think is fantastic  efficient and beuifull.

can we do this on ubuntu if so how so or is their something  similure

i hope this is not to negative on ubuntu, which i love with a passion, i would just like it to be the best of the best


thank you for your time

---

### Post by anarchyinc on 2009-05-29
It's called AWN-manager or something to that effect. Attached to Gnome but works with others. Memory hungry eye candy.

---

### Post by tlois on 2009-05-29
have you tried setting compiz to use windows preview?  i think that is what you are talking about.  you have to have compiz settings manager.

---

### Post by |{urse on 2009-05-29
there is an alternative to awn that isnt memory hungry at all! Its called wbar and it's sole dependancy is imlib2.

[http://code.google.com/p/wbar/](http://code.google.com/p/wbar/) <---- nab it here

extract that then 

./config
make
sudo make install

*run these commands from the terminal while in the directory where you extracted wbar of course*

the bar can be launched by simply typing "wbar" in your fav terminal emulator

now if you wish to configure your bar all you need to do is edit 

gedit /home/username/.wbar

once wbar is restarted it will reflect the changes you have made in the config file

-or-

you can install this easy to use wbar configuration interface

[http://www.ihku.biz/wbarconf/wbarconf_0.7.2-1_i386.deb](http://www.ihku.biz/wbarconf/wbarconf_0.7.2-1_i386.deb)

Anyways, its a lot faster than bloated awn. And it more closely emulates the physics of the 0sx bar imho.

---

### Post by blake7 on 2009-05-29
have you tried setting compiz to use windows preview? i think that is what you are talking about. you have to have compiz settings manager.



sorry what is compiz and where do i find it

thank you

---

### Post by blake7 on 2009-05-29
thank you |{urse

i get starting on that not sure how easy that going to be im not a computer kind of guy.

but will try 


thabnk you for all your suggestions

and have an nice eving

---

### Post by Viva on 2009-05-29
The zoom feature in awn is awful, so that is not what the op wants. Install cairo-dock instead.

---

### Post by anarchyinc on 2009-05-29
Compiz isn't the solution to your question, it is another window manager. Nothing but pure eye candy to entertain your friends, worth testing out later. Haven't personally tried Wbar but either that or the fatter AWN should do what you are requesting.

---

### Post by blake7 on 2009-05-29
./config
make
sudo make install


sorry but how do i sudo make install that

---

### Post by Tibuda on 2009-05-29
You better use the deb package. A lot easier than compiling.

---

### Post by blake7 on 2009-05-29
just tryed that does not work says that i have the wronge opener appucation

arrrr
how do i do it the other way and why is it not strait forword

cheers

---

### Post by |{urse on 2009-05-29
thank you daniel, im so used to compiling everything i didt even look for a deb ;)

[http://code.google.com/p/wbar/downloads/detail?name=wbar_1.3.3_i386.deb&can=2&q=](http://code.google.com/p/wbar/downloads/detail?name=wbar_1.3.3_i386.deb&can=2&q=)

---

### Post by blake7 on 2009-05-29
sorry it says 

Error: Dependency is not satisfiable: wbar

what does that mean and how do get it to work


thnk  you

---

### Post by blake7 on 2009-05-29
what is compiling

thank you

---

### Post by |{urse on 2009-05-29
okay sorry to confuse, install the deb above first and then the deb for the configuration utility from my first post second

---

### Post by blake7 on 2009-05-29
errr sorry it now says 

tmp/wbar_1.3.3_i386-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

what this and change to what 


thank you for your time

---

### Post by |{urse on 2009-05-29
compiling is the process of running the source code through a compiler instead of installing a pre-built package.

---

### Post by Viva on 2009-05-29
Are you looking for something like [this]("http://taufanlubis.files.wordpress.com/2008/06/kibadock-gutst00.png")?

You can download cairo dock [here]("http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=16259")

---

### Post by |{urse on 2009-05-29
when you download that deb you should have the option to open it with gdebi package installer

---

### Post by blake7 on 2009-05-29
yea that is the baby

is what im doing going to be that good??

cheers

---

### Post by |{urse on 2009-05-29
Viva, your first link was to a picture of Kiba-Dock not cairo-dock. cairo-dock doesnt look that nice ^^

---

### Post by blake7 on 2009-05-29
no it says

tmp/wbar_1.3.3_i386-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

what the fluff does that mean


cheers and sorry for the use of the world fluff hope no one has fluff problems  lol

---

### Post by Viva on 2009-05-29
> **blake7 said:**
> yea that is the baby

is what im doing going to be that good??

cheers

Yes, just make sure you have desktop effects enabled. Download cairo-dock and cairo-dock plugins from the link I posted before and install them. Then open it from Applications->System Tools->Cairo Dock(You'll have two cairo docks there, use the OpenGl one if you have a good graphic card).

If you want something much lighter, but without the parabolic zoom effect, install avant-window-navigator. It supports other effects like 3d turn and is much easier on resources.

---

### Post by |{urse on 2009-05-29
lmao no problem, just save the .deb to your desktop or wherever and right click on it. if gdebi doesnt open it on the "open" item in your menu then right click and select "open with"

type "gdebi" in the custom command field.

LOL OR

open a terminal.

sudo apt-get install wbar

---

### Post by Viva on 2009-05-29
> **|{urse said:**
> Viva, your first link was to a picture of Kiba-Dock not cairo-dock. cairo-dock doesnt look that nice ^^

Pretty sure that is cairo dock. I can get a screen from my own system if you want. It looks even better with customizations.

---

### Post by tlois on 2009-05-29
the latest cairo dock is great.  you have to have compiz to run it.  sounds like you want eyecandy- i like it too!

you need to install compiz from synaptic.  also install compiz manager. then you have to install both the cairodock and cairodock plugins packages.  

i have tried most of the docks.  they play with each of my computers differently, so you can try awn, cairo dock, whatever to see which one you prefer.  i have one computer that cairo dock just doesn't work smoothly on, so used awn with that one.  i like docks and having what i want right there.

[http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=13311](http://developer.berlios.de/project/showfiles.php?group_id=8724&release_id=13311)

---

### Post by |{urse on 2009-05-29
Viva, if you read the original post, the dock we were talking about that was so memory hoggish was AWN (which stands for avant-window-navigator).

---

### Post by |{urse on 2009-05-29
> **Viva said:**
> Pretty sure that is cairo dock. I can get a screen from my own system if you want. It looks even better with customizations.


[http://taufanlubis.files.wordpress.com/2008/06/kibadock-gutst00.png](http://taufanlubis.files.wordpress.com/2008/06/kibadock-gutst00.png) <--- THAT IS THE LINK YOU POSTED LOL

note the obvious title "kibadock"

---

### Post by Viva on 2009-05-29
> **|{urse said:**
> [http://taufanlubis.files.wordpress.com/2008/06/kibadock-gutst00.png](http://taufanlubis.files.wordpress.com/2008/06/kibadock-gutst00.png) <--- THAT IS THE LINK YOU POSTED LOL

note the obvious title "kibadock"

That guy got the names wrong. He says kiba dock, but provided instructions for installing cairo-dock

---

### Post by blake7 on 2009-05-29
thank you alll

---

### Post by Viva on 2009-05-29
Did you manage to install any of the docks mentioned?

---

### Post by |{urse on 2009-05-29
Viva ah righton! lmao this thread got very confusing real quick, Enjoy your dock, whichever you picked Blake ^^

---

### Post by fabounet on 2009-05-29
I confirm it's Cairo-Dock ;-)

---

