---
title: "Coming from Windows... Tips?"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by kesre on 2009-01-19
Hey
I got Ubuntu on my laptop about a month ago - I realized that I'm so used to Windows doing stuff on its own, and not giving me any option otherwise, that I don't know if theres anything I should do with partitions, undervolting, backups, etc. that would either increase my computer's efficiency, heating problems, or chance of surviving crashes and hardware problems

Also, if there are specific features in Ubuntu that I should know about, or anything that you think would be useful. 

(like for instance, I never suspended because I thought it was like Windows Standby - little did I know that Ubuntu can suspend and unsuspend in 5-7 seconds... and consume much less power)

Thanks

---

### Post by candtalan on 2009-01-19
Welcome!
The basic thing - although it might seem a bit obvious in hindsight - you bought a PC with Windows already on it, and learned Windows by using it whether you wanted to or not, and you will learn what you need from Ubuntu - by using it.

If you are happy and continuing to use Windows then there is not much urgency for you to use Ubuntu. That is ok, depending on what your motives are. Although it might be a good idea to gently try out functions that you would need in Ubuntu if Windows suddenly failed, so that you would be in some way ready and a bit familiar with Ubuntu, which would probably still available in that situation.
hth

---

### Post by Kellemora on 2009-01-19
Hi K

Recently in another post I compared Windows to Linux like as if they were cars.

Windows is like the Family Sedan, complete with Automatic tranny and computer controlled Idiot Lights in the dash, one size fits all, with no optional accessories.

Ubuntu is more like a Ferrari, Stick Shift, Posi-traction, full instrument console in the dash, and a Major Power plant under the hood.  Plus every option imaginable is available if you want it!  You CAN set the timing and fuel ratio, just how you want it for the way YOU drive!

If you've never driven a stick before, especially with some horsepower under the hood, there will be a learning curve!
But once you can handle your machine, you RULE the Road!

As the others have said, take your time and learn things, they ARE different than Winders, AND most things are LOGICAL TOO!

TTUL
Gary

---

### Post by Paul Miller on 2009-01-19
My advice is to not be afraid of breaking stuff.  Undoubtedly at some point you will want to tweak your computer, and one of those tweaks will inevitably break something.  That's to be expected.  It's a learning experience. Most of the time, the friendly folks on this forum can help you fix it.

My second bit of advice would be to put /home on its own partition.  This makes it *much* easier to do a full reinstall, because you don't have to worry about it erasing your data.  (Of course, you should have anything important enough to worry about backed up already -- you do, don't you?)

Other than that, enjoy Linux and Ubuntu!

---

### Post by Cresho on 2009-01-19
> **Kellemora said:**
> 
Ubuntu is more like a Ferrari, Stick Shift, Posi-traction, full instrument console in the dash, and a Major Power plant under the hood.  Plus every option imaginable is available if you want it!  You CAN set the timing and fuel ratio, just how you want it for the way YOU drive!


I am going to correct you on this one.  Ubuntu is an unassembled Ferrari.  Once it is assembled, you will never ever look back.  It is a fun car to drive.

what is windows? :)  I already forgot how to boot into it.  Ahh!  yes!  here it is.  I pulled the hardrive out.

---

### Post by albinootje on 2009-01-19
> **kesre said:**
> 
Also, if there are specific features in Ubuntu that I should know about, or anything that you think would be useful. 


Welcome to Planet Ubuntu! :)

I think it is good to realise that whenever a new Ubuntu release is out, that you do *not* have to upgrade.
If you're using 8.04, which is a LTS release, stick to that until the next LTS is coming out.
Unless.. you really think you need never software which is not available via backports.

And if you're interested, read some background information about Linux and open source software, here's just a few quick random pages :

[http://en.wikipedia.org/wiki/Linus_Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds)

Watch the Fry video : [http://www.gnu.org/fry/](http://www.gnu.org/fry/) 
( From here: [http://www.fsf.org/](http://www.fsf.org/) )

[http://en.wikipedia.org/wiki/Richard_Stallman](http://en.wikipedia.org/wiki/Richard_Stallman)
[http://en.wikipedia.org/wiki/Mark_Shuttleworth](http://en.wikipedia.org/wiki/Mark_Shuttleworth)

---

### Post by donkyhotay on 2009-01-19
The two things I've found that throw people off when converting to linux are

1: root access
If you don't know what that is read this [http://brajeshwar.com/2008/linux-root-power/](http://brajeshwar.com/2008/linux-root-power/). With windows you have full administrative access over everything all the time, although convenient this leaves your system wide open to viruses (which is why mac and linux don't do that). It may seem that typing a password in to do administrative tasks is annoying but it's for your own protection. If you're ever uncertain if something you are doing will damage your system or not just remember, "without my password the worse that can happen is trashing my personal files". 

2: installing software
With windows to install programs you eiher go online, download the installer, and install the program; or you go to the store, buy a disc, and install the program. Be aware with linux that will not happen. Although there are exceptions (and some of the exceptions can be frustrating) over 90% of all software you will ever need/use are located within the repositories which can be easily accessed through synaptic. 
Once you get used to these two things most of the rest of the things commonly done (minimizing/maximizing, copy/paste, etc.) are similar enough that you'll be fine. Admittedly doing administrative tasks like configuring hardware, working with file permissions, etc. are very different (and any experience you have doing admin tasks on windows will not help you) but unless you're interested in tweaking your system or run into a problem it's most likely something you're not going to have to worry about.

---

### Post by Dumbestcrayon on 2009-01-19
The best think you can do is to back up Ubuntu. I get it where I want it and I back up the important files. (much like the C:\Windows folder of Windows but you can actually read, write and execute from it).

I did this..

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
What this backup does is tar.gz up all of your system files and if you mess something up you can just untar it and everything will be how you left it. I wen't one step further and partitioned out 7gb and put the backup on it just incase something else happens.

PERFECT way to back up your system. Like said above, don't be afraid to mess something up or ask questions. If somebody tells you to run XXX command. Ask what it means. Find out exactly what you're doing so that you'll know in the future. If you mess something up you can fix it (mentioned in the link above).

Hope this helps.

---

### Post by mrbiggbrain on 2009-01-19
As a fellow newbie, i wish people would have told me about the following commands.

**su**  - used to switch users under a shell. so you could have a shell for dave and joan under tims xwndows session.

**sudo** - super user do, allows you to do things as root, however i can stress anough that you should use root only for things you must, as a newbie its better to see if you can do without, before doing, the worst that can happen without root privliges is the destruction of your own files...with.... everything can go poof.

**chown** - allows you to change who owns something, mainly folders. so that you then have full rights without sudoing :-) 

ls - listas files  and folders, has options for hiden files, hiden folders.

**./*some-script.s*** - dont forget the dot in front of your scripts, many a linux newbie has taken 2 minuts writing there first script to spend hours wondering why
```

# my-script.s

```

doesnt work :-/ 

**rm -r **- this little commands removes not just files, but is recursive and can delete folders, i spent 2 days before relizeing i needed the -r
[B]
cd ../../../../sources/[/B] - this one looks wierd, ../ means your previous directory, so ../../ is 2 directorys back and ../../../ means 3 back. 

tab is your command line ... freind ....

say i typed
```

# ./my-
```

will fill in the rest for me.... so i might get

```
#./my-script.s
```

if nothing happens hit tab again and youll get a list of every last file that could possibly have come up

maybe 

my-script.s
my-non-script.s
my-txt.txt

edit:

note this would also work if i say
```

source /home/nick/Documents/cheese/do
```

and then hit tab

or 

```
source ../../../../../../do
```

and hit tab

and is context sensitive, so
```

cd Doc

[tab]
```

might give you 
```

cd Documents/
```

---

### Post by albinootje on 2009-01-19
> **mrbiggbrain said:**
> As a fellow newbie, i wish people would have told me about the following commands.

**su**  - used to switch users under a shell. so you could have a shell for dave and joan under tims xwndows session.


Perhaps it's good to mention that :
```

su -

```
itself won't work by default on Ubuntu since the root account is disabled.
An example for using someone else's account in a terminal would be :
```

su - adrian

```
This would only be useful to do command line things, as starting any X application after using "su - username" is gonna fail.

For the OP, see also here : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldos2er on 2009-01-19
You might want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by txcrackers on 2009-01-20
Got one that I've not really seen mentioned before:

When installing software, remember that it won't necessarily be found in the "menus." Server software, a lot of utilities, etc. are **only** accessible from the command-line or other system-level access (e.g. service management). E.g. you can't start/stop Apache from the applications menu.

---

### Post by kesre on 2009-01-20
> **txcrackers said:**
> Got one that I've not really seen mentioned before:

When installing software, remember that it won't necessarily be found in the "menus." Server software, a lot of utilities, etc. are **only** accessible from the command-line or other system-level access (e.g. service management). E.g. you can't start/stop Apache from the applications menu.


yeah I've noticed that... is there a way I can list programs/commands in terminal?

---

### Post by HavocXphere on 2009-01-20
I've learned that patience is a vital ingredient in learning linux.;)

---

### Post by tegnoto89 on 2009-01-20
Google is a good friend, and the forums and documentation are your best buddies in the whole world.

SO far in my experience, I can do everything I did in windows (and more) after just a little tinkering.  Granted, I have to use wine to play games and such, but other than that, I've really come to like ubuntu a lot.

---

### Post by kesre on 2009-01-20
Thanks all, this is very helpful - keep it coming (and feel free to mention more advanced stuff, cool configuration settings, etc.)

I definitely recognized the potential of Ubuntu when I was looking to get rid of windows. I only wish I knew more programming so I could run my own scripts + change things around a bit more as I wanted...

The nice thing is that, since not everything is graphical (especially things needing sudo) I'm being forced to learn shell/bash commands (<=which is the correct term?)

Thanks for the ../../../ and tab - that'll save me a lot of time =D


backup... hehe, never actually done one - too much of a pain in windows - running one script though... I love Ubuntu. =D
hmm, didn't know about /home in a new partition... that'll be my next project =D

Also didn't know about the LTS - does that stand for Latest Stable? (and I don't suppose I can downgrade from 8.10, still keeping files, programs, and configuration?)

As for downloads... .debs are my best friend right now - though I've had some experiences ./configure-ing make-ing and make install-ing...

Now, for repositories/sources for synaptic and "Add/Remove" are there any other sites I can add <- I'm looking for some cool games or programs... I liked Freecol, but it keeps going buggy on me. Also, Billiards-GL doesn't even open for me =(

know of any good RTS / Strategy games?

---

### Post by Facetious Falcon on 2009-01-20
> **kesre said:**
> Thanks all, this is very helpful - keep it coming (and feel free to mention more advanced stuff, cool configuration settings, etc.)

I definitely recognized the potential of Ubuntu when I was looking to get rid of windows. I only wish I knew more programming so I could run my own scripts + change things around a bit more as I wanted...

The nice thing is that, since not everything is graphical (especially things needing sudo) I'm being forced to learn shell/bash commands (<=which is the correct term?)

Thanks for the ../../../ and tab - that'll save me a lot of time =D


backup... hehe, never actually done one - too much of a pain in windows - running one script though... I love Ubuntu. =D
hmm, didn't know about /home in a new partition... that'll be my next project =D

Also didn't know about the LTS - does that stand for Latest Stable? (and I don't suppose I can downgrade from 8.10, still keeping files, programs, and configuration?)

As for downloads... .debs are my best friend right now - though I've had some experiences ./configure-ing make-ing and make install-ing...

Now, for repositories/sources for synaptic and "Add/Remove" are there any other sites I can add <- I'm looking for some cool games or programs... I liked Freecol, but it keeps going buggy on me. Also, Billiards-GL doesn't even open for me =(

know of any good RTS / Strategy games?

LTS is long term support. It means support and updates are held for longer periods than the non LTS versions. 

If you're looking for some nice stuff try compiz-fusion, it makes Vista look outdated. There should be some guides on google but it's easy to install from the synaptic package manager.

I like executable scripts which is very useful I have a button at the top which when pressed backs up certain files to my secondary hard disk and if plugged in, backs up to my USB memory stick. Pretty useful, something that would be annoying to do in windows.

Also, if you're worried about security of certain files the latest version of Ubuntu (8.10) comes with in built encryption tools which allows you to encrypt using 128bit AES security. Yet again, there should be many guides from searching google as to how to set it up but it's pretty simple.

Screenlets are another useful tool as well, I can search wikipedia, google etc from my desktop although it's more for aesthetics than anything.

---

### Post by donkyhotay on 2009-01-20
A very useful script I have in my menus is
```
rm -fr home/%username%/.local/share/Trash
```
with the menu entry set to use gksudo. This is useful for emptying the trash with root access for those times when you've thrown something away you don't have permission to. This happens to me quite frequently when compiling programs from source and using 
```
sudo make install
```
as all of the various object files created are owned by root and when I'm done I forget about it, drag it to the trash, and then can no longer empty my trash due to lack of permissions.


//edit: %username& of course is my actual username I use when logging onto my system, I just put it this way as an example. You don't want to use ~ as it will then go to roots home directory which isn't what I want.

---

### Post by vmatherly on 2009-01-20
I have converted quite a few users over to ubuntu. The one question I seem to get a lot is what about anti virus. To which I happily reply "forget about it , you dont need it anymore" :-).

---

### Post by 4E.Kipper on 2009-01-20
i recently switched. i cant say mucn more than whats been said. ubuntu is now my default on my laptop on desktop. (its the only thing on my desktop)

i;ve found this usefull, its a google search, that searches for ubuntu (i dont know how else to describe it)

[http://www.google.com/coop/cse?cx=001461844748502826593:hh-ikmexth4](http://www.google.com/coop/cse?cx=001461844748502826593:hh-ikmexth4)

its VERY usefull. it does search loads of other linux sites aswell. i've manged to solve most of the little niggles i;ve come across using that search,

---

### Post by boostedtsi on 2009-01-20
I would probably like linux as a whole more if they got rid of all the required command line interactions...
I did not like the command line in Win 3.1, or anything since. Now I care for it even less when there certainly is not a real need for it if the proper GUI interface can be had.

---

### Post by donkyhotay on 2009-01-20
There are many things that are more easily done through the CLI then through the GUI. For example when helping people install a specific program it's easier to tell them to copy/paste
```
sudo apt-get install flashplugin-nonfree
```
then it is to say, go to synaptic, click the refresh button, do a search for flashplugin, make certain it's not the one with the extrasound option, click the little white box just left of the name, select 'mark for installation', accept any dependency messages that appear, click apply. I know some people claim GUI is better, some claim the CLI is better, personally I think they both have strengths and weaknesses and I use both depending on what I'm trying to do. I don't think you will ever get rid of the CLI in linux like they try to do with windows and osX just because in many ways it *is* easier (once you're used to it). Especially when you're giving out free tech support on an online forum.

---

### Post by Facetious Falcon on 2009-01-20
> **boostedtsi said:**
> I would probably like linux as a whole more if they got rid of all the required command line interactions...
I did not like the command line in Win 3.1, or anything since. Now I care for it even less when there certainly is not a real need for it if the proper GUI interface can be had.

They each have their pros and cons which is why I never understood why windows has essentially removed theirs.

For example I use the commands a lot to make executable scripts which allows a huge amount of customization

---

### Post by donkyhotay on 2009-01-20
> **Facetious Falcon said:**
> They each have their pros and cons which is why I never understood why windows has essentially removed theirs.

For example I use the commands a lot to make executable scripts which allows a huge amount of customization

It exists, but it's hard to find and harder to use (use windows CMD after getting used to linux BASH and it'll drive you nuts). It's useful for performing certain tasks (like CACLS especially) but they try to drive you to the GUI so much that adminning a windows box (running actual services like DHCP, DNS, apache, etc.) is much harder then adminning a linux box without a GUI on it. Admittedly this isn't applicable for the 'average' user that just needs to check his Email and browse the web but thats what the GUI is for.

---

### Post by boostedtsi on 2009-01-20
It is just a personal preference that I like doing things through the GUI over command line. In all honesty I try to avoid the command line as much as possible. I have to deal with it enough in a server OS that by the time I get home I simply cannot stand it any more, I just want to click through and not have to remember all the commands and switches.

---

### Post by kesre on 2009-01-20
> **donkyhotay said:**
> ...much harder then adminning a linux box without a GUI on it...

what exactly can you do on a linux box w/o a GUI on it?
(I'm actually interested in trying it out (CTRL+ALT+F2), but I don't know what I would do in the shell environment...)

---

### Post by donkyhotay on 2009-01-20
> **kesre said:**
> what exactly can you do on a linux box w/o a GUI on it?
(I'm actually interested in trying it out (CTRL+ALT+F2), but I don't know what I would do in the shell environment...)

Almost anything you want, generally I use the CLI for administrative tasks (installs, configuring hardware/software) and the GUI for regular usage (web browsing, Email, games). But there are web browsers (lynx), text editors (vi, emacs, nano), torrent clients (rtorrent), and a bunch of other stuff available for the CLI. If you are really interested in learning I would recommend doing a google search. The best way to learn is to just use it. I'm not that great with the CLI since I only use it for tasks that are harder with the GUI but technically you can do just about anything.

---

### Post by PaulTR on 2009-01-20
Heh, I just switched to running Linux from Windows this last week and happened on this thread :) You guys are awesome <3 I've only had to reload Ubuntu once so far, so yay *glad he backed everything up on an external*

---

### Post by The Cog on 2009-01-20
> **kesre said:**
> yeah I've noticed that... is there a way I can list programs/commands in terminal?

You could use the command completion in bash. Just get a command prompt and type **<Tab><Tab>y**

---

### Post by mrbiggbrain on 2009-01-21
> **boostedtsi said:**
> I would probably like linux as a whole more if they got rid of all the required command line interactions...
I did not like the command line in Win 3.1, or anything since. Now I care for it even less when there certainly is not a real need for it if the proper GUI interface can be had.


ok then take a folder filled with 10,000 files, then give me a list of only the files larger then 100mb, but less then 200mb, in .iso format, last edited today.

now someone generally talented in the art of shell could definetly do this, most GUI interfaces couldnt even dream of this.

im not saying i know the command off the top of my head, its quite a few pipeing operations, and a few shell tricks... but to try and say any operations is simple given the correct gui is a little premature... the entire point of the shell is that you can do anything, through pipeing, and manipulation of outputs.

GUI's are great, but they are limited by there creators, and the way the creators intend them, they are a toy car, the shell is a box of legos, one piece is useless, but as you add more and more pieces you can build things much better, larger, and more complex then a car... and noone ever said you cant just build a factory (shell script) to simply manufacture cars.

---

