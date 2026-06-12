---
title: "Help installing Ubuntu on an old computer."
date: 2009-07-08
forum: New to Ubuntu
---

### Post by The Jinx on 2009-07-08
Hi,

I'm currently interested in installing Ubuntu on a really old computer. Since it is a really old computer I would like it just to have LXDE for its window manager. My goal is just to have it use abiword and playing mp3s off of a usb drive.

The specs are as followed:

Intel Celeron 633mhz (socket 370)
192mb SDRam
**1.5gb HDD**
Integrated Graphics [intel i810]

I notice some users with similar specs installing the CLI version of Ubuntu and building up from there, I guess that is what I am aiming for, but I have no idea on how to do that.

Thank you,
Jinx

---

### Post by wojox on 2009-07-08
Hey jinx check this guys site out good stuff:

```
http://www.psychocats.net/ubuntu/minimal
```

---

### Post by The Jinx on 2009-07-08
does anyone know what I install to get LXDE, i don't want IceWM

---

### Post by QIII on 2009-07-08
[http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

But, honestly...

Don't be so h*ll bent for leather that you HAVE to have Ubuntu.  

You can always come back to it, but you can try any number of other lightweight Linux distros.  Just saying it is worth driving a few other cars before you buy.

---

### Post by The Jinx on 2009-07-08
> **QIII said:**
> [http://wiki.lxde.org/en/Ubuntu](http://wiki.lxde.org/en/Ubuntu)

But, honestly...

Don't be so h*ll bent for leather that you HAVE to have Ubuntu.  

You can always come back to it, but you can try any number of other lightweight Linux distros.  Just saying it is worth driving a few other cars before you buy.


Yea I know, I was planning to install Arch Linux, but wanted to get more familiar with terminal and editing conf files first. I've also looked at DSL before and just didn't like how bland it looked. I was following puppy linux since the beginning but I dont know its just something about Ubuntu that keeps me coming back.


Another quick question, Do you think 1.5gb is enough for Ubuntu, Swap space, LXDE, Abiword, maybe Totem and Codecs?

---

### Post by earthpigg on 2009-07-08
> **The Jinx said:**
> 
Another quick question, Do you think 1.5gb is enough for Ubuntu, Swap space, LXDE, Abiword, maybe Totem and Codecs?


ill uninstall as much as possible on my toy virtualbox arch install - excluding the apps you listed - and see how much hard drive space it uses. im bored, and you have me curious now :P

---

### Post by The Jinx on 2009-07-08
Thank you for going out of your way to check, it is much obliged

---

### Post by earthpigg on 2009-07-09
bleh, internet is slow today.

it may be a little close. keep in mind this is on arch, not ubuntu. also keep in mind that i started with a bunch of crap installed and removed as much as i could... i probably have some junk left that i could get rid of.

i used the slim login manager.

openbox window manager was giving me issues i didn't feel like resolving (my mouse cursor was invisible), so i went ahead and used icewm with lxde.

abiword and totem have a _lot_ of gnome dependencies that are rather large - you could go cloud-style, using google docs, and skip that package to save 150 mb.

i picked the midori web browser, 70 mb.

docs.google.com in midori returns a page telling you your browser isn't compatible. docs.google.com_**?browserok=true**_ seems to make google docs run just fine - i did not do extensive testing, but it seemed ok.

(copy/paste between desktop and virtualbox isn't working for some reason, sorry for the lack of code output.)

its a tight fit, but df -h / returns _**1.2gb used**_. if you use a _**100 mb swap file**_, that will leave _**200 megs free**_.

ditching totem and abiword (can still use google docs) will free an additional 150 mb of hd space.

flash (youtube) is another 20mb installed.

flashplugin, mplayer, and jre which together 'should provide everything you need' (according to the legendary arch wiki) total 217 mb.

if it all fits (abiword, totem, jre, flashplugin, mplayer, lxde, midori), it will be just barely, and without swap space.

ditch totem, save 100mb.

ditch abiword and rely on google docs, save 100mb.

ditch mplayer and jre, save 200mb.

pick what you want to axe....

...and you will need to run pacman -Scc frequently _**if**_ you keep the software up to date. this will mean no downgrading packages and a less stable system _**if**_ you update the software once it is installed and working. what i would do: once it is all installed and working, run pacman -Scc and then never update anything again. this is not a machine that we care about some esoteric and theoretical security vulnerability existing on.... stability is more important to us, here.

free -m is returning 68 megs used at desktop with 1 terminal window open... midori is another 3 megs, abiword another 1.1.

---

### Post by earthpigg on 2009-07-09
the arch wiki is known to be the best around.

Arch beginners guide:
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

Arch install guide: (not so beginner oriented -- the beginner's guide covers the same stuff.)
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

while reading up, keep wikipedia and google on two other tabs in case there is a term you are unfamiliar with that pops up.

take your time and read carefully. if you screw up, no biggie... start over or check for typos. 

one piece of advice i will give you:

if you want the whole 'root' thing to be handled the way it is in ubuntu with 'sudo bla bla bla', then what you want to do is create a new user, give the new user admin privileges, and install/configure 'sudo'. i leave it to you to discover how to do this.


you will have quite a sense of accomplishment once your project is done, i'm sure.

---

### Post by Warren Watts on 2009-07-09
Here's a HOW-TO I wrote that will allow you to build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop:


[HOWTO Build and install a compact (+/-) 1GB Xfce Based Ubuntu Desktop]("http://ubuntuforums.org/showthread.php?t=549958")

The HOW-TO is almost two years old at this point, but it should still work just fine...

---

### Post by The Jinx on 2009-07-09
I would like to thank all that has commented and helped me out on this thread thus far. 

I think I will follow the steps provided on this site [[http://www.psychocats.net/ubuntu/minimal]](http://www.psychocats.net/ubuntu/minimal]) as provided by Wojox, but I have some questions regarding what to install after the base system is done. And after this goes well, I will be on my way to Arch Linux.

The website provides some packages they recommend but I am unsure of which of those packages I would really need if I install LXDE. The provided recommendations are as followed:

sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic
sudo /etc/init.d/gdm start

For example, I don't think I will need **icewm **and **xterm**, if I plan on using LXDE right? Furthermore, I don't think will be going online with this computer after I do all the updates so I wouldn't need **firefox **and if I install packages through terminal would I still need **synaptic**?

---

### Post by Cheesemill on 2009-07-09
You could also check out [CrunchBang]("http://crunchbanglinux.org/").
It's based on Ubuntu with the OpenBox window manager.
The lite version should install on 1.5GB.

---

### Post by The Jinx on 2009-07-09
okay so I've tried to install the minimal ubuntu but it failed to detect my pci network cards, does anyone have any ideas on how i should proceed, i've tried two different ones, and while i was running off of a regular livecd i was able to get online with them so i am lost on what to do.

---

### Post by LewRockwell on 2009-07-09
> **The Jinx said:**
> okay so I've tried to install the minimal ubuntu but it failed to detect my pci network cards, does anyone have any ideas on how i should proceed, i've tried two different ones, and while i was running off of a regular livecd i was able to get online with them so i am lost on what to do.

it's very strange that they would work with the LiveCD but not after it's installed?

perhaps your installation was so "minimal" that the networking stuff got left out?

.

---

### Post by The Jinx on 2009-07-09
perhaps I should rephrase my post, I was **unable **to finish installing the minimal ubuntu due to the fact that I was not able to connect to the internet. Yet i was able to get online with a LiveCD

---

