---
title: "I literally started using ubuntu 15 minutes ago..."
date: 2010-11-25
forum: New to Ubuntu
---

### Post by u-noob-tu on 2010-11-25
And i have no idea what im doing. However i can safely say that i am happy i got rid of windows on my laptop and tried ubuntu linux. But i know almost nothing about it. Thats where you guys come in. I need to know the basics, no, the BASICS of the basics. I am so new at this, i havent even turned on wifi yet (my dads asleep, and only he knows the password). Anyway, i want to know what the coolest software is, the best settings, the best everything. I can already say that ubuntu looks much more coherent with itself when compared to windows. 

By the way, i am running ubuntu 10.10 (something meerkat, right?). Looking forward to having a lot of fun here. 

Ryan

---

### Post by Hippytaff on 2010-11-25
Welcome to the world of ubunut :-)

have a look at this - [http://ubuntuclips.org/collections_2.html](http://ubuntuclips.org/collections_2.html)

and there is lots more :-)

---

### Post by garvinrick4 on 2010-11-25
#Look in my signature and there is a .pdf book that is nice to go through.
#Here is a link for post installation:[Main Page -]("http://ubuntuguide.org/wiki/Main_Page") another is below:
Just click on your 10.10 Maverick Meerkat.
[http://www.my-guides.net/en/guides/linux/199-ubuntu-maverick-meerkat-1010-post-installation-guide](http://www.my-guides.net/en/guides/linux/199-ubuntu-maverick-meerkat-1010-post-installation-guide)

---

### Post by thebarisaxkid on 2010-11-25
Definitely look at what Happytiff showed.

Once you start learning,  you will get the hang of things pretty easily.  

As for wifi, look under System, then Administration, and look for additional drivers. Here you will have some drivers for certain hardware in your computer.  You'll have to connect your laptop (I'm assuming it is a laptop) to the internet via ethernet.  Then you can activate the drivers.  Choose your wireless driver, then the recommended version of the Graphics card.  

Have fun learning, and congrats on making the switch!

---

### Post by NightwishFan on 2010-11-25
Welcome and please have fun! Some stuff you should certainly check out in the software center:

Stellarium - Planetarium
Compizconfig-settings-manager - Desktop Effects
Compiz-Fusion-Plugins-Extra - More Desktop Effects
Battle For Wesnoth - Game
Nexuiz - Game
Gimp - Image Editor
Frozen Bubble - Game
Banshee - Media Player
Gnome-do - Launcher
Docky - Dock


Also here are some fun links as well:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.kubuntu.org/](http://www.kubuntu.org/)
[http://askubuntu.com/](http://askubuntu.com/)

---

### Post by madjr on 2010-11-25
Welcome!

definitely check out psychocats:
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

after you get started with that you may want some fun, new stuff, etc. with ubuntu, lots over here:

[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)

btw funny nick :p

---

### Post by 73ckn797 on 2010-11-25
A good Ubuntu search engine is here: [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)
It will be a great source for problem solving giving better results than searching within the forums using the search feature there. At least in my opinion.

---

### Post by DogMatix on 2010-11-25
Welcome to Linux. 

When you get the Wireless key from your father and get online.

Run 'System > Administration > Update Manager' and get everything up to date.

Then get stuck in. Sign up for Ubuntu One and get 2GB of free cloud storage. Fire up Gwibber and enter your Twitter and/or Facebook accounts. Check out available applications by running 'Applications > Ubuntu Software Centre'.

Have fun

---

### Post by u-noob-tu on 2010-11-26
wow... i wasnt expecting so many responses. Ive been doing a lot of looking around on the internet, and have found some cool stuff (already got compiz). After making the switch, i dont know why i put up with windows. ubuntu is spectacular!!! I love the insane amount off tweaking you can do. The quality of third party apps is great, and the free stuff, oh glorious free stuff. ubuntu just WORKS. 

anyway, thanks for the tips and links. seems ive got a lot of tweaking to do ;)

Ryan

---

### Post by gary0 on 2010-11-26
And if you break it, which you will, you get to keep both parts!
Check out medibuntu to add more cool repos by entering this into the termial:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

it will as you for your password (which you won't see as you type it).
Next do this in the terminal:

```
sudo apt-get install libdvdcss2
```

to install DVD codecs

then:

```
sudo apt-get install w32codecs
```

so you can play various formats of music / media

and finally:

```
sudo apt-get install ubuntu-restricted-extras
```

for all sorts of other essential stuff.

Have fun!
Gary.

---

### Post by The Cog on 2010-11-26
> **u-noob-tu said:**
> wow... i wasnt expecting so many responses. Ive been doing a lot of looking around on the internet, and have found some cool stuff (already got compiz). After making the switch, i dont know why i put up with windows. ubuntu is spectacular!!! I love the insane amount off tweaking you can do. The quality of third party apps is great, and the free stuff, oh glorious free stuff. ubuntu just WORKS. 

anyway, thanks for the tips and links. seems ive got a lot of tweaking to do ;)

Ryan

Glad you like it. Most important is probably to remember to use the repositories to get your software. System->Administration->Synaptic. Don't just hunt for it on the internet like a windows user would. The Ubuntu repositories have most stuff all set up right for Ubuntu. Stuff you download off the internet is possibly malware and even if not, probably needs some knowledge and effort to install.

Second, read these forums a lot. Just read the headings that catch your interest. What interests you will change from day to day, but that's good.

---

### Post by u-noob-tu on 2010-11-26
> **gary0 said:**
> And if you break it, which you will, you get to keep both parts!
Check out medibuntu to add more cool repos by entering this into the termial:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```it will as you for your password (which you won't see as you type it).
Next do this in the terminal:

```
sudo apt-get install libdvdcss2
```to install DVD codecs

then:

```
sudo apt-get install w32codecs
```so you can play various formats of music / media

and finally:

```
sudo apt-get install ubuntu-restricted-extras
```for all sorts of other essential stuff.

Have fun!
Gary.

*ERROR* BRAIN OVERLOAD! TOO MUCH INFORMATION TOO QUICKLY! 

Nah, just kiddin. Although that is a lot of code. So, what are these packages? are they like software bundles?

---

### Post by Foxheadz on 2010-11-26
I would check out gnome-look.org for pretty much any type of customization you can find.

Icons: i would take a look at faenza
gtk themes:these are the window themes 
cursor: changes your mouse pointer

And once you get comfy i would take a look into conky [http://conky.sourceforge.net/](http://conky.sourceforge.net/) and the theme for it conky colors [http://gnome-look.org/content/show.php/CONKY-colors?content=92328](http://gnome-look.org/content/show.php/CONKY-colors?content=92328)

---

### Post by sammiev on 2010-11-26
Great to hear you are having a blast. Been off and on with it for a bit now. Lately, it's really the only OS I'm using. GL :)

---

### Post by dabomb1022 on 2010-11-27
Add me on aim if you need help just message me if you want it.

---

### Post by Perfect Storm on 2010-11-27
> **u-noob-tu said:**
> *ERROR* BRAIN OVERLOAD! TOO MUCH INFORMATION TOO QUICKLY! 

Nah, just kiddin. Although that is a lot of code. So, what are these packages? are they like software bundles?

Because of legal issues etc. in some countries Ubuntu can't include these stuff default.

You can read about it here: [http://medibuntu.org/](http://medibuntu.org/)

You can get close source multimedia codecs and libdvdcss which is used to play DVD movies.

---

### Post by Locke_99GS on 2010-11-27
This was mentioned earlier, but I mention it again: Be sure to check out UbuntuOne - it is a file syncing service, but more importantly, many various parts of Ubuntu interact with it. It is already included in your Ubuntu install, you just need to start it up and create an account. It started out as a flop, but it's getting real nice; they even just started a public beta for the UbuntuOne Windows client, and the price-point for >2gb is *very, very* good.

A popular alternative to UbuntuOne for file syncing is Dropbox. Dropbox syncs Mac, Windows, and Linux, and integrates a bit with Nautilus. (your file manager) It provides a lot more free space, syncs between more OS's, syncs over the LAN and uses file deltas (up/down os fast) but it is proprietary, and the price point for additional space is a bit crazy.

Somebody also mentioned Stellarium; This is well polished bit of software for stargazers. I use it all the time to help me with my AST/APhy classes. There are other awesome softwares that do the same thing, some are even better (Celestia) but are less polished and more difficult to use.


Most applications can be discovered in the Ubuntu Software Center - You can add more by adding extra repositories. Browse through it, check some random stuff out. Don't forget to remove installed packages if you don't like them, or won't use them. With the ease of installing software, you can consume a LOT of drive space pretty quickly on accident.

If you play games, check out [http://www.ubuntugamer.com](http://www.ubuntugamer.com) and [http://www.penguspy.com](http://www.penguspy.com). 

There are a lot of Linux, (and more specifically, Debian and Ubuntu) news sites out there if you care to know what's going on. The Linux community moves very fast. My personal favourite Ubuntu specific site is [http://www.omgubuntu.co.uk](http://www.omgubuntu.co.uk), while [http://www.phoronix.com](http://www.phoronix.com) has interesting news and benchmarks on everything Linux related.



And it's unfortunate that I should even have to mention this, but I do: Never, ever, ever, **ever** run a terminal command that looks like this: "*sudo rm -rf /*" This will destroy your operating system. Some people get some cheap kick out of telling *nix beginners to run this command. Don't do it.

---

### Post by s1wood on 2010-11-27
If you will take a word of advice from another newbie: don't store any valuable data on the system while you are playing!  Then if you do manage to screw it up you can just do a clean install and start again - I speak from experience.

Susan

---

### Post by u-noob-tu on 2010-11-27
> **s1wood said:**
> If you will take a word of advice from another newbie: don't store any valuable data on the system while you are playing!  Then if you do manage to screw it up you can just do a clean install and start again - I speak from experience.

Susan

Thats too bad, but thanks for the heads up. I havent had ubuntu long enough to put anything valuable on it yet. Yeah, the temptation to tinker is irresistible right now.

---

### Post by QLee on 2010-11-27
[QUOTE=u-noob-tu] Yeah, the temptation to tinker is irresistible right now.[/QUOTE]

If you have a spare partition, or sufficient space to carve one out, one suggestion could be to do a second install for testing (playing, tinkering, making mistakes). A 10G partition should be plenty, when you format label it "tinker" or some other name that suits you and which can be identified easily. If you end up trashing it to the point it won't boot, you'd just reboot and, at GRUB select the working install partition, from which you could repair the test one or restore your backup of it or do a fresh install to the test partition. Saved me many hours of pain when I first used Ubuntu. Also allows you to easily get back to the forum and ask questions about what you did incorrectly. Just a suggestion, most users don't do this.

---

### Post by hovzio on 2010-11-27
Another good way to tinker is virtualization; vmware or virtual box are both good although I prefer vmware. This way you dont have to log out and log in any time you want to try something. The other neat thing is that the guest operating systems are given their own IP's on the network making it really easy to dable with ssh, apache, ethereal or anything like that. Aside from 3d acceleration I have been able to everything within these guest operating systems:)

---

### Post by u-noob-tu on 2010-11-27
Fortunately, my step dad is an IT guy (and a good one), so if i mess it up, he'll be there. and about tinkering, i dont do do anything until i am ABSOLUTELY SURE that nothing bad will happen. 

And by the way, linux has some AWESOME games. so far my favorites are foobilliard and warzone 2100. both are great.

---

### Post by Perfect Storm on 2010-11-27
Did I hear the word games?

Try also, free and open source:
Secret Maryo Chronicles (smc)
Wormux
Battle for wesnoth

Close source and cost:
Heroes of newerth: [http://www.heroesofnewerth.com/](http://www.heroesofnewerth.com/)
Savage 2: [http://www.savage2.com/en/main.php](http://www.savage2.com/en/main.php)

There are more but it would be better if you can narrow down your favor genre.

---

### Post by Locke_99GS on 2010-11-27
[http://www.worldofgoo.com](http://www.worldofgoo.com)

---

### Post by eeffoc on 2010-11-27
Welcome to Linux! Nice choice on making the switch -- by far the best OS and community to stand behind it. :D

---

