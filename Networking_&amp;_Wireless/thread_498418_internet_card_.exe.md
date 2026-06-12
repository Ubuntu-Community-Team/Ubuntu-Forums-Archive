---
title: "internet card .exe"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by Lunatrix on 2007-07-11
hey guys i need some more support.


ok i just started over my ubuntu. fresh,clean the works. now  i want to install my wireless internet card driver:[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/itemid,33/id,list_b/)

(^^look at number 27 for all the info you will probably need^^)

i need unwine after i install unwine, is there any other configuration that i need to do after i install unwine to actually get the scripts to my wireless driver .exe? thanks guys

---

### Post by Lunatrix on 2007-07-11
#
Card: Belkin F5D7001 Highspeed Wireless 128Mbps Desktop Network Card

    *
      Chipset: BCM4306
    *
      pciid: 14e4:4320

---

### Post by Lunatrix on 2007-07-11
lol wow. i went to sleep for 11 hours to find nothing. thats not cool

---

### Post by Lunatrix on 2007-07-12
bump. anything?

---

### Post by yota on 2007-07-12
Hi, have you tried the bcm43xx opensource driver?

It works flawlessly for me, to install it do the following:
-install fwcutter: sudo apt-get install bcm43xx-fwcutter
-download the wireless card firmware from here: [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o)
-install the firmware (cd to the folder where the firmware is): sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o
-reboot

-if you update the kernel, repeat the procedure

Hope this helps!

---

### Post by Lunatrix on 2007-07-12
do i need to download fwcutter from somewhere?

---

### Post by felin on 2007-07-12
As noted above

> sudo apt-get install bcm43xx-fwcutter

---

### Post by Lunatrix on 2007-07-12
E: invalid operation bcm43xx-fwcutter

---

### Post by Lunatrix on 2007-07-12
woops my bad i didnt put install in there but i still kant get it

E: couldent find package bcm43xx-fwcutter

---

### Post by Lunatrix on 2007-07-12
so what should i do?

---

### Post by yota on 2007-07-12
Have you enabled the "universe" repository?

If you don't know what I mean take a look about installing software in ubuntu at: [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

And at the "Enabling extra repositories" section in particular.

---

### Post by Lunatrix on 2007-07-12
that picture he shows in that enabling extra repositories it looks different then mine. so i wasent able to anable them. now what should i do?

---

### Post by yota on 2007-07-12
In Synaptic go to settings/repositories, then check the box to make it look like in attached image.

Edit: mhh... I've looked at the image provided in the previous link, it's not that different after all: what about using a little imagination? ;-)

---

### Post by Lunatrix on 2007-07-12
ok, i did that now what?

---

### Post by yota on 2007-07-12
Retry the procedure described in my first post, now it should work since bcm43xx-fwcutter is contained in the universe repository (that you have just enabled).

A hint: copy and paste commands to avoid mistypes, in particular the fwcutter command uses backticks which can be easily confused with apostrophes (` and ').

---

### Post by Lunatrix on 2007-07-12
i cant copy and paste because thats the computer im trying to get the internet on. im on my labtop now.

---

### Post by Lunatrix on 2007-07-12
im still getting an error in terminal when i try to install fwcutter.

E: couldent find package bcm43xx-fwcutter

---

### Post by yota on 2007-07-12
> **Lunatrix said:**
> i cant copy and paste because thats the computer im trying to get the internet on. im on my labtop now.

Oh, that's a problem. apt-get (1st command) will try to download the package from internet and if the box is not connected will fail.
Can't you use a wired connection? 
Before the apt-get command get in sync with the repo with 'aptitude update' when you're online.

Otherwise you'll have to download fwcutter manually and move it to the unconnected box.

---

### Post by Lunatrix on 2007-07-12
this topic is all about me gettin wireless internet. if i could use a wire i dont think i would want to install my wireless card...kan you get me a download that i can get for fwcutter, and put it on a disk and install it on my computer?

---

### Post by yota on 2007-07-12
> **Lunatrix said:**
> this topic is all about me gettin wireless internet. if i could use a wire i dont think i would want to install my wireless card...kan you get me a download that i can get for fwcutter, and put it on a disk and install it on my computer?

Hey! I didn't want to do a thread hyjacking! ;-) I was only asking if you could use a wired connection for the time needed to make the wireless work.
And by the way I can use a wired one and prefer to use the wireless just for freedom of movement...

Letting apt-get do the work is FAR more easy than installing things by hand; anyway at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) you can find the urls for all ubuntu packages.
fwcutter is at [http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/feisty/utils/bcm43xx-fwcutter)
(download the .deb of your platform, I suppose it should be "i386")

once you have the .deb package you can take it to the pc and install with 'sudo dpkg -i *packagename*.deb'
Once it's installed we can resume the procedure.

---

### Post by Lunatrix on 2007-07-12
k, thnx.i would and me and my dad has been doing layouts and stuff to put a cable throught my walls and stuff to get a wired connection. i wasent trying to be mean lol sorry

---

### Post by Lunatrix on 2007-07-12
i guess that worked except for the terminal part, linux is not really good.

---

### Post by yota on 2007-07-12
Which command? What do you think about pasting some errors? If we will be able to get this damn card working I expect a medal at least! (let's say two one gold for me and one silver for you ;-) )

Linux is indeed very good (IMHO), but it can be quite hard to be understood and learnt...  Don't confuse quality with ease.

Anyway I have to go now, I suppose that if you reread the posts carefully you can spot the problem by yourself. You have all the needed information now, if not a bit of googling can help.

See you tomorrow!

---

### Post by eki_yu on 2007-08-28
Go to the System - Administration - Synaptic Package manager, click on Search, type bcm43xx-fwcutter, when found select it and install. 

Download  [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o) , and save it to your home folder

Open terminal, type:

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` wl_apsta.o

and reboot.

Of course, have Ethernet cable plugged in (for the installation needs files from the internet)

---

