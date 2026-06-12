---
title: "network card issue, im totally lost"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by archangel2187 on 2008-08-18
Ok so im not compleatly new to linux but i would like to start off by asking anyone who replies to please do so in a step by step, talk to me like a 2 year old fashion as i never know where im not going to be capable of filling in the blanks. OK here goes....

I had ubuntu hardy heron from the live cd 8.04 i believe it was installed on my computer. from the moment i installed it it worked fine... internet and everything was automaticly picked up and running. it was great....then one day i decided that i wanted to reformat my drive as i was going to upgrade my graphics card and just wanted to start a fresh ubuntu as i was moving from ati, to nvidia. OK here is where it gets weird. I was using a Asus P5GC-MX/1333 mobo.. this has not changed the only hardware configuration that has changed in my system is a new graphics card and new powersupply. NOTHING ELSE.... Nothing to do with the onboard network card....again i stress NOTHING..

I used the same live cd to install hardy heron again and low and behold i can't get the damn internet to work for nothing. run these fourms up and down and i can't find a single thing that helps me. i have found several that say they are using the same mobo as me and that i need to download this file called atl2.ko.tar.gz or something like that. so i have downloaded several renditions of it across these forms.. i unpack the file
and run terminal for a gksudo nautilus.. browse to /lib/etc...../drivers/net/ and put the file here.. then i run the terminal script that everyone says to run. and i get a error like improper module......etc.. i am at a total loss,


my desktop is compleatly useless without internet so will someone please explain how to make this crap work in little baby steps PLEASE... 

And for the guys working on ubuntu... I LOVE LINUX but this is the perfect example of why people aren't flocking to linux over windows....so gotta get to work on that (double click .exe, check yes, next, next, next, install...) way of doing things.. can't be that hard if microsoft managed it lol... just saying lol.. but anyway someone please help me out im dieing here...

and just in case you need to know i running 2.6.24-16-generic kernel...

thanks in advance

---

### Post by mellowd on 2008-08-18
One question, have you tried with the old graphics card again and does it work? If so it sounds like a slight conflict with the new one

---

### Post by Loaded.len on 2008-08-18
Might be a long shot, but it's worth a try for a quick fix... reset your BIOS defaults.

It will force an ESCD update

---

### Post by jarrettgold11 on 2008-09-05
Ever Want free stuff but you cant afford it? Then join prize rebel now! In order for you to get a game like GTA 4 or a free Wii or even a PS3 all you have to do is fill out surveys and get points easy as that. No more getting up and having to buy stuff. Get it right in the privacy of your home and for FREE!!! Join now at         


            [http://www.prizerebel.com/index.php?r=507390](http://www.prizerebel.com/index.php?r=507390)   
              
                          Thats Right 

            [http://www.prizerebel.com/index.php?r=507390](http://www.prizerebel.com/index.php?r=507390)

---

