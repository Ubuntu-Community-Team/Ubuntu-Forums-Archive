---
title: "Just installed Ubuntu and LOVING it!"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by killtheaquitted on 2010-01-28
Hi all,

Just signed up to the forum, and I wanted to share my first Ubuntu experience and ask a few newbie questions. Here's how I came to Ubuntu. 5 years ago, I bought my wife a low end laptop to do some basic web browsing & doc editing in the living room while watching tv. The laptop was running XP and was pretty slow out of the box. Well, 5 years is like 100 tech years and the laptop has been basically unusable for the past year (even after a complete HD wipe and XP reinstall). Lately, she had been bugging me that she wanted the laptop back, and I figured the only way I could revive it was going to linux. Now, I have no experience with linux (or ubuntu) but I consider myself a low level computer geek, so I figured I was up to the task. I don't know how many of you have wives out there, but after running the boot disks of ubuntu and netbook remix, I went with remix because my wife got excited because it looked "cute" and the fonts were "pretty." 40gb HD on the laptop with a belkin 8071 v1 wifi card. wiped XP and installed in less than 45 minutes. I booted it up and expected basically nothing to work (drivers) and much didn't. I cruised some how-tos and got overwhelmed with the programming language. So I clicked system test just to see what wasn't functioning, and by some ubuntu miracle, that test cured everything that was broken (wifi, hardware, sound!!!) Now I have a resurrected laptop that boots in about 15 seconds and is faster than the first day it came out of the box.

List of awesome improvements:
-faster boot time
-faster program load times
-the laptop runs about 5xs cooler temp wise
-does everything my wife wants in a simple interface
-goodbye computer viruses
-OPEN SOURCE!!!!

Questions:

1. I have looked around and I have yet to come up with a definitive answer regarding the necessity of firewalls and antivirus. I DL'ed firestarter and feel that I am good, but any feedback is helpful

2. What are everyones' must have programs from the repositories? 

3. Is there any way to get a "my computer" type launch program

4. Is there a "how linux is structured for dummies" guide anywhere? It is like a foreign language coming from windows. 

5. I understand that remix is just a pretty cover on regular ubuntu. Is there a quick and dirty way to switch to regular ubuntu so I can have access to the full ubuntu experience.

I am sure I will have more questions as I get used to the new OS, and I will try to answer other's questions when I can. LONG LIVE THE PENGUIN!

---

### Post by tom.swartz07 on 2010-01-28
> **killtheaquitted said:**
> Hi all,
......
Questions:

1. I have looked around and I have yet to come up with a definitive answer regarding the necessity of firewalls and antivirus. I DL'ed firestarter and feel that I am good, but any feedback is helpful

2. What are everyones' must have programs from the repositories? 

3. Is there any way to get a "my computer" type launch program

4. Is there a "how linux is structured for dummies" guide anywhere? It is like a foreign language coming from windows. 

I am sure I will have more questions as I get used to the new OS, and I will try to answer other's questions when I can. LONG LIVE THE PENGUIN!


Glad to hear youre having a great time so far!

This thread is bound to get a few responses, so let me try to be one of the first to welcome you to the forums!

The easiest way to turn on your firewall is to open a terminal (applications>accessories>terminal) and type the following```
sudo ufw enable
```
It will ask for your password, just type it but nothing will appear- thats normal.


I have a TON of programs- but I would suggest Ubuntu-Tweak. It features many neat little changes that you could do to your system, it also includes some great programs.


As far as "My Computer", Ubuntu Tweak will cover that also for you. Theres an option to add the computer and trash, etc all to your desktop.


The best guide ive ever read was Ubuntu Beginners Guide. Heres a blog; [http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/](http://linuxowns.wordpress.com/2008/11/11/ubuntu-the-absolute-beginners-guide/)

By far the best BOOK is this: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also, just for giggles, ill post a gratuitous pic of my desktop just in case you want to see it. 

Enjoy!

---

### Post by lykwydchykyn on 2010-01-28
> 
1. I have looked around and I have yet to come up with a definitive answer regarding the necessity of firewalls and antivirus. I DL'ed firestarter and feel that I am good, but any feedback is helpful

Check under the "recurring discussions" forum.  The A/V thing always creates massive threads of the same old endless debates.  The short answer for A/V is, for the foreseeable future, none required.
A firewall is good to have running, especially if you connect to public networks or you aren't behind a router.  The firewall is built into the linux kernel, all the various firewall software you see are just front-ends to that.  The only real difference is finding one that balances ease of use with configurability.  Firestarter is good for most basic needs.
> 
2. What are everyones' must have programs from the repositories? 

I'll pass on this one, since (a) I use KDE, and (b) my hobbies are probably different from yours.
> 
3. Is there any way to get a "my computer" type launch program

The "places" menu is probably the closest equivalent.  What's missing for you?
> 
4. Is there a "how linux is structured for dummies" guide anywhere? It is like a foreign language coming from windows. 

The official documentation is really pretty good for starters:
[https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)
Besides, you're not a dummy and you know it :)

---

### Post by raktarok on 2010-01-28
Yeah! this is the attitude we need. Welcome to ubuntu and hope you keep on liking it. Personally, after making the switch to linux a year ago, I have never looked back. 

1. Yes, an antivirus program is not actually needed in ubuntu, but there's no harm in having one. and firestarter is a good choice, it serves the purpose.

2. Some of the must-have programs could be these, but I guess it changes from user to user. 

gmrun or gnome-do : ever used launchy in windows? well, these are like that, only much better. They allow you to launch programs quickly and do much much more. While gnome-do is terribly popular, not many people would put gmrun in a must-have list. I have a soft spot for the program though.

vlc or mplayer : I don't think these are available by default, so install one of them. can't live without a good media player...

wine : run windows programs. But I recommend you to use native applications whenever possible.

ubuntu-restricted-extras : a bunch of packages related to flash, java, codecs, fonts and more. Proprietary software, so some may not prefer it, but this is a necissity for many. 

Do this from a terminal to downlaoad all of them in a shot. (another advantage of ubuntu, no more clicking "Next" while installing software)

```
sudo apt-get install gmrun gnome-do vlc mplayer wine ubuntu-restricted-extras
```

Also look at ubuntu-tweak and ailurus - they can be very useful, especially to new comers.   
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
[http://www.ubuntugeek.com/ailurus-10-01-5-is-available-for-use.html](http://www.ubuntugeek.com/ailurus-10-01-5-is-available-for-use.html)

Then there are stuff like frozenbubble(a highly addictive game), supertux(heard of mario?), gloobus-preview (preview files fast and quick) etc..

3. Look at the ubuntu-tweak program, it has that option.

4. Have a look here for nice guides. 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://tldp.org/LDP/intro-linux/html/index.html](http://tldp.org/LDP/intro-linux/html/index.html)
If you really want to learn more, then rute is an excellent guide.
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)

Hope this solved your questions to some extent!

---

### Post by ptviperz on 2010-01-28
> **killtheaquitted said:**
> 
1. I have looked around and I have yet to come up with a definitive answer regarding the necessity of firewalls and antivirus. I DL'ed firestarter and feel that I am good, but any feedback is helpful

You don't need to worry about that stuff

> 2. What are everyones' must have programs from the repositories? 

This one is totally dependant on you. I couldn't live without my AWN dock, Jedit, etc. 

> 3. Is there any way to get a "my computer" type launch program

Sure, Places->Home

> 4. Is there a "how linux is structured for dummies" guide anywhere? It is like a foreign language coming from windows.

Basically, anything you download or use will be in your home directory, i.e. /home/USERNAME

Downloads? /home/USER/download
Desktop?   /home/USER/Desktop

config files are usually hidden in /home/.CONFIG, you can see hidden files by going to Places->Home and hit CTRL-H

Good luck, it's worth the time to learn it.

---

### Post by peace.gangsta on 2010-01-28
> **tom.swartz07 said:**
> 

Also, just for giggles, ill post a gratuitous pic of my desktop just in case you want to see it. 

Enjoy!

I ve posted below another [post]("http://ubuntuforums.org/showthread.php?t=1366797&page=3") of yours that I REALLY want a conky like urs ...
could you please oblige and  make that giggle into a hearty laugh and applaud by sharing the .conkyrc pleeessss [-o<

---

### Post by peace.gangsta on 2010-01-28
I ll give you an idea of how pathetic my conky is :(

---

### Post by raktarok on 2010-01-28
> **peace.gangsta said:**
> I ve posted below another [post]("http://ubuntuforums.org/showthread.php?t=1366797&page=3") of yours that I REALLY want a conky like urs ...
could you please oblige and  make that giggle into a hearty laugh and applaud by sharing the .conkyrc pleeessss [-o<

That conky looks impressive, and yeah, I would love to have the rc file too. oblige us and please post it, o great one..

---

### Post by peace.gangsta on 2010-01-28
O mighty soul 
O great one 
Come out of the dungeons 
Give us the CONKYyyyyyyyyyyyyyyyyyyyyy

---

### Post by J V on 2010-01-28
Heres part of my tips & tricks guide (pending)
> **Flash, MP3, Java**
One of the first things you should install after you start up Ubuntu is  "[ubuntu-restricted-extras]("http://ubuntuforums.org/ubuntu-restricted-extras")" (Click to install)

If you are on a 64-bit computer, you will need to install the 64-bit flash, which you can download, nice and neatly, from [adobes website]("http://labs.adobe.com/downloads/flashplayer10_64bit.html"). (Beyond the scope of this guide)

Another often-used program is "[Java]("apt://sun-java-bin")" (Click to install)

**How to run windows programs**
Most people will tell you to run windows programs through "Wine", which, by the way is [not an emulator]("http://wiki.winehq.org/Debunking_Wine_Myths#head-7c9ecddfaff60d8891414b68d74277244e7109eb"), however, it can be hard to get going, and even if you like tinkering with stuff, there are easier ways.

"[Playonlinux]("apt://playonlinux")" (Click to install) is an excellent interface for wine, which has lots of options, and lots of enhancements, including separate settings for each program, separate wine versions for each program, and even windows-like "Next next next" installers that make running windows programs a LOT easier.

Firstly though, you should check weather a program works with the wine "[AppDB]("http://appdb.winehq.org/")"

**Viruses**
Linux has no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

**Firewall**
The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.
So yeah, playonlinux, restricted extras, flash, java, clamtk/gufw only if you need them...

My computer: Places > Computer
Guide to linux > [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
Getting rid of remix: You can reinstall, or install ubuntu-desktop and remove ubuntu-desktop-remix...

---

### Post by Sealbhach on 2010-01-28
Here's a good article giving an overview of the Linux file structure:

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

Just some things to remember - 

/ is a folder, it is the root folder.

/home is a subfolder of / and is where the user's files are stored. You do not need special permissions to change anything in your /home folder but if you go above that level, you will be prompted to escalate your privileges.

/usr stands for "unix system resources" not "user".

.

---

### Post by lotharmat on 2010-01-28
I think everyone else has covered most of your questions so I'll just say:

Welcome to Ubuntu forums! :D

---

### Post by nothingspecial on 2010-01-28
To remove the netbook remix packages```


sudo apt-get remove go-home-applet human-netbook-theme maximus window-picker-applet ume-launcher desktop-switcher
```

if you want the netbook remix back just change remove for install in the command above.

---

### Post by pathfindermwd on 2010-01-28
> **tom.swartz07 said:**
> Glad to hear youre having a great time so far!

Also, just for giggles, ill post a gratuitous pic of my desktop just in case you want to see it. 

Enjoy!


Tom that is an awsome desktop!  I like the weather comment too...It's F*****G cold!

Oh, and welcome to Ubuntu, I just got here too, it's pretty cool!

---

### Post by peace.gangsta on 2010-01-28
> **Sealbhach said:**
> 
/usr stands for "unix system resources" not "user".

.
ROFL 
That reminds me i suffered with this misconception for quite sometime and i kept on looking for stewpid things innit...
F***in windows..
and please dont name mark it solved i really want that .conkyrc when the user posts it do watever you want ....:P

---

### Post by rlogan on 2010-01-28
Hiya

As already suggested Ubuntu Tweak and Restricted extras are a definite good start. From there it depends on what you want to do

Glad to see your enjoying Ubuntu

Cheers

Richard

---

### Post by lotharmat on 2010-01-28
> **peace.gangsta said:**
> ...
and please dont name mark it solved i really want that .conkyrc when the user posts it do watever you want ....:P


Why not PM the person?

---

### Post by peace.gangsta on 2010-01-28
> **lotharmat said:**
> Why not PM the person?
Cause its not only me who has been mesmerized by the conky.So it will be great if he can share with all.
But yeah I ll PM him to post on maybe this thread or I can get it from him/her and post it here meself with a screen-shot of mine:P.

---

### Post by killtheaquitted on 2010-01-28
> **nothingspecial said:**
> To remove the netbook remix packages```


sudo apt-get remove go-home-applet human-netbook-theme maximus window-picker-applet ume-launcher desktop-switcher
```if you want the netbook remix back just change remove for install in the command above.

I knew there was a quick and dirty way to swap! Thanks nothingspecial and everyone else that has replied to this thread. Quick question, where is this "terminal" everyone is referring to? I am in remix and I don't see it (maybe I am just blind). It seems like terminal is key to doing any system altering shenanigans. Thanks again!

---

### Post by tom.swartz07 on 2010-01-28
> **peace.gangsta said:**
> Cause its not only me who has been mesmerized by the conky.So it will be great if he can share with all.
But yeah I ll PM him to post on maybe this thread or I can get it from him/her and post it here meself with a screen-shot of mine:P.

Im writing up a post on how to get everything just like youve seen so far here.

Ill post back on each of the threads where it was asked with a link when its up.

ill pm you too peace.gangsta when i get it up also.

---

### Post by phillw on 2010-01-28
> **killtheaquitted said:**
> I knew there was a quick and dirty way to swap! Thanks nothingspecial and everyone else that has replied to this thread. Quick question, where is this "terminal" everyone is referring to? I am in remix and I don't see it (maybe I am just blind). It seems like terminal is key to doing any system altering shenanigans. Thanks again!

Hi and welcome to the forums.

Applications --> Accessories --> Terminal should get you there.

It *may* be different in Remix.

Regards,

Phill.

---

### Post by 416inversed on 2010-01-28
> **killtheaquitted said:**
> I knew there was a quick and dirty way to swap! Thanks nothingspecial and everyone else that has replied to this thread. Quick question, where is this "terminal" everyone is referring to? I am in remix and I don't see it (maybe I am just blind). It seems like terminal is key to doing any system altering shenanigans. Thanks again!

Nothingspecial's post only removes UNR specifics; the second part of switching to full Ubuntu from UNR is
```
sudo apt-get install ubuntu-desktop
``` which installs the desktop specifics.

Another switch from UNR is to remove 'Go Home' (the Ubuntu icon that acts like "Show Desktop") from the Gnome Panel, right-click Remove from Panel, and replace it Main Menu, right-click add to panel and choose from list.

Terminal is under Applications>Accessories>

Although I installed guake which provides a quick dropdown terminal whenever I press F12. In terminal```
sudo apt-get install guake
``` & then added it to Startup Applications in System>Preferences> add, "Guake" under name and "guake" in command, no quotes.

---

