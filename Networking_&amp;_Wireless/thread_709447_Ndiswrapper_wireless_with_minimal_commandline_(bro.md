---
title: "Ndiswrapper wireless with minimal commandline (broadcom 43** cards -hp/dell)"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by myddewji13 on 2008-02-27
So your all pumped up about installing ubuntu...you can't wait to try out the crazy desktop effects...theres just one problem though....u have no internet!!!...arrgh...I know exactly how you feel...

This guide is for:

-people unfamiliar with the command line/terminal 
-people who want to do things the easy 'gui' way (aka windows converts...like me)
-people who have read all over the forums and internet to figure out how to fix their wireless woes and tried all sorts of 'copy paste commands' to get ndiswrapper working
-people who are about to give up...

This guide assumes:

-you have a clean install of ubuntu 7.10 
-you have internet (via ethernet cable - pref high speed)
-you are frustrated

Basically I've decided to write this guide after spending 3 weeks trying to get my wireless working...at the end of the day/weeks it was actually a very easy task... frustrating to get there but easy...

So we are starting off with a new install...if you have messed with ubuntu (aka configured it)...reinstall...write down what you did to make it easier if you want certain settings back.

Steps:

1) connect ethernet cable...turn on computer...boot into ubuntu ...ensure internet is working

2) open synaptic package manager 
system-->Administration-->Synaptic Package Monitor

3)hit ctrl+f and search for ndiswrapper (make sure the search is set to 'description and name)

you should get 3 entries:
1)ndisgtk
2)ndiswrapper-common
3)ndiswrapper-utils-1.9

install all of them by ensuring all are checked off and hitting apply 
(not if the box is dark it is already installed)

4)Find some wireless drivers
-look for your card on the forums...find a link for wireless drivers...make sure they are for your card... 
-4310 is NOT THE SAME as 4311, this was the biggest problem i had...i was always trying to install the wrong drivers...
-if you download a file it may need to be extracted - install cabextract from synaptic
-you need two files - a .inf as well as a .sys file (named bcmwl5.inf for my card - note the bcmwl6 files are for vista and usually dont work in ubuntu)

5) Go to applications-->accessories-->terminal 

copy in the following

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

hit enter...leave the terminal running in the background for now..

6)Go to system-->administration ...at the bottom there should be a new entry titled 'windows wireless drivers'..open..

7)find your files (the .sys and the .inf file) ...drag the .sys file into the windows wireless driver window...you will get an error asking you for the .inf file...drag in the .inf file...

8) if it works your windows wireless window should state hardware present:yes ...if not.. you have the wrong drivers...keep looking!!!!
(note if you have an hp laptop it is my personal experience that the hp drivers off of the hp website suck/do not work...try using drivers off the dell website...)

9)configure your network ..you can do this by hitting the configure network button in the 'windows wireless drivers window'

10)DO NOT FORGET THIS STEP - go back to terminal and copy paste in the following command:

```
sudo gedit /etc/modules
```

a new window (text file) will open...at the bottom there is a list of names...add ndiswrapper to this list (do not misspell) 
save file...reboot to ensure everything is working... TA DA your done

Notes: 
-this is my first ever help tutorial post... the reason i am writing this is because when i tried to look for methods to fix my computer i could not find an easy method...rather i ended up taking bits and pieces from different tutorials/posts...

-this is a windows to linux newb help guide...i am completely new to linux...this is how i got it done so this should work for you too

-if there is another tutorial similiar to this..let me noe.. ill gladly delete my post..

-note i did this on my hpdv2708ca laptop (hpdv2700 or hpdv2000 laptop series...im not sure..the labels on my laptop conflict)with a BROADCOM BCM4310 card ...as prev stated the hardest part was finding the right drivers.
drivers:
[http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

---

### Post by K.Mandla on 2008-02-27
Moved to Networking and Wireless.

---

### Post by myddewji13 on 2008-02-28
all right...if anyone needs help...post on this thread...if not...oh well it'll go to the land of the lost threads....

---

### Post by myddewji13 on 2008-02-28
ok...just posted a link to broadcom 4310 drivers...im not sure if they are the same ones as mine...but i think they're the ones i used...

---

### Post by fsanarsil on 2008-04-24
Thanks for your guide it's been a lot of help however, I'm still having a problem getting my wireless set up. When I try and run windows wireless drivers, the window appears for a second and then disappears, the program closes as soon as I open it. I'm new to linux so I'm not really sure what could be causing this, any help would be appreciated.

~

---

