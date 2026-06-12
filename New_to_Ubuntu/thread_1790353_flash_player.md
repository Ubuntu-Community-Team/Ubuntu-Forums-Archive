---
title: "flash player"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Bunny12391 on 2011-06-24
flash player stopped working after my last update. i tryed to download the new flash player but it told me i couldn't install it due to broken packages

---

### Post by dFlyer on 2011-06-24
Try these from a terminal in this order.

sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade

I've got the recent flash release installed with out a problem.

---

### Post by SunnyRabbiera on 2011-06-24
also try flash-aid for firefox, it patches up things nicely.

---

### Post by Bunny12391 on 2011-06-24
a number of packages failed to download and im still getting the same error

---

### Post by SunnyRabbiera on 2011-06-24
again try flash aid [Go here]("https://addons.mozilla.org/en-us/firefox/addon/flash-aid/")

---

### Post by Bunny12391 on 2011-06-24
> **SunnyRabbiera said:**
> also try flash-aid for firefox, it patches up things nicely.
i dont know what flash aid is or how to use it

---

### Post by SunnyRabbiera on 2011-06-24
> **Bunny12391 said:**
> i dont know what flash aid is or how to use it

Its very simple, its an add on for firefox.
Ever install an add on for firefox?
its real simple, just click the big green thing that says "add to firefox" in the link I gave you
restart firefox when prompted to and we can take it from there

---

### Post by dFlyer on 2011-06-24
If your running 11.04, start ubuntu software center, under edit select software sources enter you password and select other sources and make sure canonical partners is selected. If it's not select it, and try my past post terminal command again.

If your not running 11.04 what version are you running.

---

### Post by SunnyRabbiera on 2011-06-24
> **dFlyer said:**
> If your running 11.04, start ubuntu software center, under edit select software sources enter you password and select other sources and make sure canonical partners is selected. If it's not select it, and try my past post terminal command again.

If your not running 11.04 what version are you running.

another good idea.
Also there a few more tools they can install if needed.

---

### Post by Bunny12391 on 2011-06-24
> **dFlyer said:**
> If your running 11.04, start ubuntu software center, under edit select software sources enter you password and select other sources and make sure canonical partners is selected. If it's not select it, and try my past post terminal command again.

If your not running 11.04 what version are you running.
im pretty sure im running 10.04

---

### Post by SunnyRabbiera on 2011-06-24
> **Bunny12391 said:**
> im pretty sure im running 10.04

10.04, thats good... my advice is stay with it as its stable

Anyhow did you try my suggestion yet?

---

### Post by Bunny12391 on 2011-06-24
> **SunnyRabbiera said:**
> Its very simple, its an add on for firefox.
Ever install an add on for firefox?
its real simple, just click the big green thing that says "add to firefox" in the link I gave you
restart firefox when prompted to and we can take it from there
it still isnt working

---

### Post by Bunny12391 on 2011-06-24
i ran the flash aid wizard three times and it still doesnt  work

---

### Post by SunnyRabbiera on 2011-06-24
> **Bunny12391 said:**
> it still isnt working

the flash aid install needs a few things to get it working.
If you dont see a button that looks like a red circle with the letter f in it this means that the flash aid install neess you to manually add its icon.
If so its a simple fix:
Firstly right click on your main toolbar (where your back, forward, address bar etc are)
click on "customize" and try to find the flash aid button in your list within the customization window and simply add it to your tool bar by drag and drop.
after its in your toolbar you can close out the customization window and hit that button.
Click on "wizard mode" and in the pulldown menu at the top make sure it says "adobe stable" and when that happens click on "next", you will have to hit "next" for a few more times until the final page where you hit "finish"
If you have issues tell us but if you see a terminal window asking for your password you are good to go, just type in your password in the terminal when prompted and follow any remaining steps.
Its real easy to use :D

---

### Post by Bunny12391 on 2011-06-24
you i didat  exact thing four times and it still doesnt work. i have no idea why its not working

---

### Post by SunnyRabbiera on 2011-06-24
> **Bunny12391 said:**
> you i didat  exact thing four times and it still doesnt work. i have no idea why its not working

Hmm...

Well did you try the official flash download install?

Are you using 64bit?

---

### Post by Bunny12391 on 2011-06-24
im using 32bit when i try the official flash download it fails to download all of the packages and wont install

---

### Post by SunnyRabbiera on 2011-06-24
> **Bunny12391 said:**
> im using 32bit when i try the official flash download it fails to download all of the packages and wont install

How did you install it originally?

Maybe its time to try the ubuntu-tweak method

---

### Post by Bunny12391 on 2011-06-24
i just clicked download and then install when it was done, nothing special. all i wanted to do was watch the new meet the medic video from tf2 :(

---

### Post by SunnyRabbiera on 2011-06-25
> **Bunny12391 said:**
> i just clicked download and then install when it was done, nothing special. all i wanted to do was watch the new meet the medic video from tf2 :(

all from the adobe site I assume.
Well this is a drawback to trying the windows way of things here on linux, in windows you usually install flash by installing a file.
Here its similar but different in many respects.
You may want to install a package called ubuntu restricted extras, in your menu's there is something called "ubuntu software center"
use this to install the package "ubuntu restricted extras"

there is a guide here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

this mainly covers 11.04 but the same basics apply.
Its very simple to use

---

### Post by Bunny12391 on 2011-06-25
> **SunnyRabbiera said:**
> all from the adobe site I assume.
Well this is a drawback to trying the windows way of things here on linux, in windows you usually install flash by installing a file.
Here its similar but different in many respects.
You may want to install a package called ubuntu restricted extras, in your menu's there is something called "ubuntu software center"
use this to install the package "ubuntu restricted extras"

there is a guide here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

this mainly covers 11.04 but the same basics apply.
Its very simple to use
i figured it out. i guess i was missing some other plug-in

---

### Post by SunnyRabbiera on 2011-06-25
> **Bunny12391 said:**
> i figured it out. i guess i was missing some other plug-in

Possibly.
Youtube did have java at one time, I dont know if thats the case now though.
Just keep in mind when installing packages in the future to use the software center or synaptic.

---

