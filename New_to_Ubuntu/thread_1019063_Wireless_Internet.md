---
title: "Wireless Internet"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Noodler13 on 2008-12-22
i recently downloaded and mounted the ubuntu live cd to try out, but am having trouble connecting to my local network, im using a:
Linksys Wireless-G PCI Adapter (model no. WMP54G if thats of any use) 

im hoping there is some sort of autodetect funtion, and the problem is just a resolvable compatability issue, right?

any help would be appreciated.

thanks in advance.

---

### Post by igknighted on 2008-12-22
Can you post the output of the command 'lspci'?  Even cards with the same model # can have different chips in them, so that will tell us what you need to get yours to work.

---

### Post by Noodler13 on 2008-12-22
> **igknighted said:**
> Can you post the output of the command 'lspci'?  Even cards with the same model # can have different chips in them, so that will tell us what you need to get yours to work.

do i have to do that in linux or can i do it in windows? ill have to reboot obviously if in ubuntu

---

### Post by igknighted on 2008-12-22
> **Noodler13 said:**
> do i have to do that in linux or can i do it in windows? ill have to reboot obviously if in ubuntu

In Ubuntu.  Do you have a wired connection you can plug into for a little while?

---

### Post by Noodler13 on 2008-12-22
im afraid not, the modem is one floor below me and i have not enough wire to reach

---

### Post by Noodler13 on 2008-12-22
i put in ispci but is just said unknown command (im suposed to do this in terminal right?) what am i doing wrong?

---

### Post by igknighted on 2008-12-22
> **Noodler13 said:**
> i put in ispci but is just said unknown command (im suposed to do this in terminal right?) what am i doing wrong?

that was a lower case "L", not an "i".  'ls' for list, and pci for the devices on the PCI bus.

---

### Post by Noodler13 on 2008-12-22
command not found. i tried it by itself, i tried it with 'these things' around it. technology hates me if you havent noticed

---

### Post by igknighted on 2008-12-22
Don't use quotes.  Did you leave everything lowercase?  Case matters in linux (eg, lspci!=Lspci)

---

### Post by Noodler13 on 2008-12-22
yep, i also tried it in and out of caps, i tried every variation imaginable almost

could it have something to do with me using a live cd as opposed to the full thing (to my understanding it is a stripped version of the whole shebang)

---

### Post by metallicamike on 2008-12-22
try going to the connection applet (two monitors in the top) and right click and hit manual configuration. then go to wireless and set it to automatic configuration.

---

### Post by igknighted on 2008-12-22
> **Noodler13 said:**
> yep, i also tried it in and out of caps, i tried every variation imaginable almost

Thats really weird.  Thats part of the core cli commands, and should never be uninstalled.  You definitely tried:```
lspci
```and not```
ispci
```like you typed above?

---

### Post by Noodler13 on 2008-12-22
:mad:> **igknighted said:**
> Thats really weird.  Thats part of the core cli commands, and should never be uninstalled.  You definitely tried:```
lspci
```and not```
ispci
```like you typed above?
jesus christ im dumb. ive been leaving out the i. arg. 
ok it output an assload of info, i scanned it for anything that sounded network card-ie... didnt see anything at a glance

---

### Post by igknighted on 2008-12-22
Try filtering it... 'lspci | grep Net' and 'lspci | grep net'

---

### Post by Noodler13 on 2008-12-22
all in one line? or do the vertical lines mean a new entry?

---

### Post by igknighted on 2008-12-22
> **Noodler13 said:**
> all in one line? or do the vertical lines mean a new entry?

no, the vertical lines are <shift> + \.  You need those in there.  I listed 2 commands because I don't know if your card would have the N capitalized or not.

---

### Post by Noodler13 on 2008-12-22
ok,
when i capitalize i get:
Network controller: broadcom corporation BCM4306 802.11b/g wireless Lan controller (rev 03)

when i didnt capitalize i got something from nvidia which is way out, no mention of wireless in it either.

---

### Post by Noodler13 on 2008-12-22
so im assuming that the first one is the one we need to examine right? how do i make it work

---

### Post by igknighted on 2008-12-22
Download the following file and put it on your linux desktop: wget [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then run the following commands on the linux terminal (one at a time):

```
cd Desktop
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```

---

### Post by Noodler13 on 2008-12-22
im getting an error when i put in the second line, "no file exists" you're telling me to type it as a .bz2 but i noticed that it is .tar after the other .tar
as in:
broadcom-wl-4.150.10.5.tar.tar

---

### Post by Noodler13 on 2008-12-22
so do i just type it in like i said it appeared, and continue?

---

### Post by Noodler13 on 2008-12-22
well i went with it anyway and it worked it seemed, until the command: 
sudo b43-fwcutter -w /lib/firmware wl apsta_mimo.o

i get

sudo: b43-fwcutter: command not found.

also, sorry for the triple post

---

### Post by Noodler13 on 2008-12-22
i was told to type a bunch of stuff into terminal, until the last one i had to do which was:

sudo b43-fwcutter -w /lib/firmware wl apsta_mimo.o

and i get:

sudo: b43-fwcutter: command not found.

whats the matter here?

---

### Post by adult swim on 2008-12-22
can you post a link to where you are getting the instructions?

---

### Post by nhasian on 2008-12-22
you are not specifying the full path of b43-fwcutter.

if your not sure where it is type

```
sudo updatedb
```

then

```
locate b43-fwcutter
```

---

### Post by Noodler13 on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=1019063&page=3](http://ubuntuforums.org/showthread.php?t=1019063&page=3)

an old thread i made that sunk into the depths of the forum

---

### Post by overdrank on 2008-12-22
Please do not create multiple threads on the same subject. threads merged :)

---

### Post by Noodler13 on 2008-12-22
> **overdrank said:**
> Please do not create multiple threads on the same subject. threads merged :)

well what good is one at the bottom of the pile... neverthe less, i need some help here

---

### Post by adult swim on 2008-12-22
whenever you ran the command tar xjf broadcom-wl-4.150.10.5.tar.bz2, did it make a new folder on your desktop named broadcom-wl-4.150.10.5?

---

### Post by Noodler13 on 2008-12-22
you bet it did, it just seems either the guy had a typo in his command or something

---

### Post by adult swim on 2008-12-22
run these three commands ```
cd Desktop

cd broadcom-wl-4.150.10.5/driver

sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
``` and then copy and paste all of the output that they  return here

---

### Post by Noodler13 on 2008-12-22
the only output i get is:

sudo: b43-fwcutter: command not found

---

### Post by adult swim on 2008-12-22
what does this return?
```

cd 

whereis b43-fwcutter
```

---

### Post by Noodler13 on 2008-12-22
all i get is:

b43-fwcutter:

---

### Post by adult swim on 2008-12-22
you need to run
```
sudo apt-get install b43-fwcutter
```  it may set up your wireless when you install it.  if it doesnt then you can succesfully run the commands ```
cd Desktop

cd broadcom-wl-4.150.10.5/driver

sudo b43-fwcutter -w /lib/firmware wl_apsta_mimo.o
```  post back if you run into problems.

---

### Post by Noodler13 on 2008-12-22
now im getting:
cannot open input file wl_apsta_mimo.o

---

### Post by adult swim on 2008-12-22
whenever you installed b43-fwcutter did it ever ask you to fetch firmware?

---

### Post by Noodler13 on 2008-12-22
yeah, but that required an internet connection, which obviously i dont have at my disposal at the moment (in case your wondering im on a laptop running windows, linux better be worth all this trouble)

---

### Post by igknighted on 2008-12-23
It's just new and different.  My old laptop was the same way, and once you know what to do (like anything else, i suppose) it's really easy.  I'd go through the steps in a couple minutes.  But at first when it's all greek, it seems terribly complex and counter-intuitive.

Now that you have b43-fwcutter installed, you can run the command that failed before.  Make sure that you are in the proper directory first, though.

---

### Post by Noodler13 on 2008-12-23
thats what i just did. and i got the last error message i did. i apparently dont have the firmware for b43-fwcutter, because i need to connect to the net for that

---

### Post by igknighted on 2008-12-23
> **Noodler13 said:**
> thats what i just did. and i got the last error message i did. i apparently dont have the firmware for b43-fwcutter, because i need to connect to the net for that

You can get it here: [http://packages.ubuntu.com/intrepid/b43-fwcutter](http://packages.ubuntu.com/intrepid/b43-fwcutter)

---

### Post by Noodler13 on 2008-12-23
okay thanks, now what do i do with them once theyre on my computer (there was 2 versions there one called ati64 and some other one, i chose the otherone because im not using an ati64 bit processor, this was the proper choice i assume.)

---

### Post by igknighted on 2008-12-23
> **Noodler13 said:**
> okay thanks, now what do i do with them once theyre on my computer (there was 2 versions there one called ati64 and some other one, i chose the otherone because im not using an ati64 bit processor, this was the proper choice i assume.)

You should just be able to double click that to install.

And yes, I would assume that the i386 (standard, 32bit ubuntu) is what you are using.

---

### Post by adult swim on 2008-12-23
once you put it on the computer, double click the icon and it shoudl install b43-fwcutter.  it will probably ask you if you want to fetch the firmware but choose no since your internet isnt up yet.  then go back and run those commands.

---

### Post by Noodler13 on 2008-12-23
failed to install, a quick scan of terminal says it tried to connect to the internet... this is ridiculous, i tried to do that other command again for the hell of it, no dice. the only way to get this crap to work is to get a super long ethernet cable into the back of my tower.

---

### Post by Noodler13 on 2008-12-23
im not going to lie, this is really putting me off of linux. i though ubuntu was suposed to be "linux for humans" not humans with the patience of a saint

---

### Post by adult swim on 2008-12-23
im not sure why it wont install on your computer.  i just deleted my wireless driver and installed it with no internet connection without any problems.

---

