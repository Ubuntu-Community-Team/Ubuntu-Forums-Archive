---
title: "having kismet problem (any other wardriving programs with an easier install?)"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by Dnerd on 2009-05-15
I don't know what it means when I get "....no" on some things (as seen in my screenshot here: 

I'm using this guide here: [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

At section 2a. it says:
 * Download Kismet from [http://www.kismetwireless.net/download.shtml](http://www.kismetwireless.net/download.shtml)
    * Run ``./configure''.  Pay attention to the output!  If Kismet cannot
      find all the headers and libraries it needs, it won't be able to do
      many things.
**    * Compile Kismet with ``make''**

The bolded part is the part which I cannot do, presumably because I'm getting "....no" on those. 

I've searched around but all I can find was that there is/was a package installer for it which did it easily, but I cannot find it now. The only one which shows up on the package installer is SWScanner, but it's not working and I'm not even sure if it does what I need it to do anyways.

Please help me... I just need to get the SSID of one router and I'll be happy.

---

### Post by MegaJim on 2009-05-15
Why not use Kismet version in the repository?

---

### Post by t0p on 2009-05-15
You can install kismet very easily, using the command

```
sudo apt-get install kismet
```

But if you really really want to compile it from source (maybe because the version in the repos is too old?) I advise you to check out [this guide]("https://help.ubuntu.com/community/CompilingEasyHowTo") to compiling.  If you don't understand what compiling is all about, you won't be able to solve any problems that arise.  But don't fret: the guide I linked to explains it very nicely.

Personally, I prefer using **Backtrack** for wardriving/wifi security issues.  I've got Backtrack3 on a live usb stick (thanks to UNetbootin).  But Backtrack4 has been released so maybe you'd prefer that?  (Backtrack is not a program, it is a linux operating system that comes with a wide selection of software useful for wardriving/messing with wifi/all kinds of security issues.)

---

### Post by Dnerd on 2009-05-15
Thanks. Do I just type that in or do I have to specify a directory? It would be on my desktop. I will switch to my Ubuntu partition and try this out in a minute. Thanks!

---

### Post by PhilMize on 2009-05-15
you may need the source i cant rem last time i used kismet... im pretty sure all you need to do is type that...

sudo apt-get install works for installing anything through terminal instead of synaptic....

---

### Post by Dnerd on 2009-05-15
Woah, I'm not even sure how it's doing this, but this is cool. Does the 'sudo' part make it search online for applications?

---

### Post by MegaJim on 2009-05-15
Just type it into a terminal and it will be installed in the usual place (/usr/bin/kismet...) then type in

```
man kismet
```

to read the manual and setup your wireless device

---

### Post by MegaJim on 2009-05-15
> **Dnerd said:**
> Woah, I'm not even sure how it's doing this, but this is cool. Does the 'sudo' part make it search online for applications?

sudo gains you root permissions (this is needed to install software) then the apt-get program connects to the internet to download the necessary files and install them in the system

---

### Post by Dnerd on 2009-05-15
Thanks! 

Now I have an entirely different problem.. using it.. >_>

Normally I'm the go to guy for computer problems, but I got bored and decided to try expanding my knowledge to Linux, starting with Ubuntu, and now I feel like I did 10 years ago when I first started using Windows.

What I'm trying to do is view the SSID of a hidden network. I see that the main option seems to be "capture" but whenever I try to use it, it tells me I have to set up an interface. I go to the preferences --> capture but there's nothing in the box for me to use. What do I need to do? It's ok if you don't know the answer or something, I'll try looking around for how to do it. 

Thanks for helping me get this far.

---

### Post by MegaJim on 2009-05-15
Have you configured your wireless device in /etc/kismet/kismet.conf ?

---

### Post by Dnerd on 2009-05-15
No. I just found out that I had to. I don't know how to find my wireless card information because the website no longer has it for sale and I can't see the specifications anymore. It's a compaq presario CQ50. I'm just about to call it a day because it seems like I'm doing everything wrong or screwing up some kind of way all for one SSID..

---

### Post by Dnerd on 2009-05-15
Well I just found this: **Network Card**                                          Integrated 10/100 Ethernet LAN                                                                                    **Wireless Connectivity**                                          802.11b/g WLAN
but I'm pretty sure I need more than that.

---

### Post by MegaJim on 2009-05-15
in a console:

```
sudo lshw -C network
```

it will list what cards are detected

then add the appropriate line to kismet.conf (readme here: [http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml))

e.g. my conf has a line like:

```
source=bcm43xx,wlan0,broadcom
```

---

### Post by Dnerd on 2009-05-15
..

---

### Post by Dnerd on 2009-05-15
That's what I get

---

### Post by MegaJim on 2009-05-15
the file should be located at /etc/kismet/kismet.conf

you can use the locate command to find files from the terminal, e.g. to find a file called jump, you would use

```
locate jump
```

its often easier (if you're expecting a lot of results) to pipe them through a command like "more" which will present them page-by-page, e.g.

```
locate jump | more
```

if you aren't getting any results, the located database is probably out of date, update it with the command

```
sudo updatedb
```

---

### Post by MegaJim on 2009-05-15
in order to edit the file, you need to open it in a text editor, the easiest is gedit

```
sudo gedit /etc/kismet/kismet.conf
```

you need the sudo to gain write permissions over the file

---

### Post by Dnerd on 2009-05-15
Alright, it came up and I changed the suiduser=yournamehere to suiduser=dee and the source to source=bcm43xx,wlan0,broadcom

If that's it, can I just run Wireshark (as root) and have it work? Or do I have to do something else?

btw, is there anyway to keep this from signing me out every 2 minutes?

---

### Post by MegaJim on 2009-05-15
Wireshark is a different program with different setup to Kismet.  Once you've setup your card in kismet.conf you can start the program with

```
sudo kismet
```

If you want to add a capture device in Wireshark, click capture -> interfaces, then click start next to the networking device you want to listen with.

---

### Post by Dnerd on 2009-05-15
ok Thanks, but now it says that I need to have a version of my drivers which support monitor mode.. I guess I'll look up how to find those out when I get home.

---

