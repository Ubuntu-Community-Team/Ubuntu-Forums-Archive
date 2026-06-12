---
title: "A Simple Suggestion"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by Eiji Takanaka on 2011-03-13
[LEFT]Hi there!

I've just thought of an idea which might help a few people out, perhaps its already been thought of perhaps not. Basically if your like me then you have done a fair bit of tweaking to your system, simple things here and there. Now when you come to upgrade chances are that subtle tweakage might get lost in the wash, proverbially speaking of course. 

Now what i try and make an effort to do is log any tweaks i might do to the system in a simple text file, so that when the next version of ubuntu comes out i have the ability to get my system back to its 'original' state. More and more with Ubuntu peoples systems will become (i suspect) more and more unique and tailored to the individual. Now what might be needed perhaps is the ability to log these changes manually in some sort of program, so that upon upgrading to a new version of ubuntu these 'customised settings' are incorporated into the upgrade. You could then easily 'load-in' your customised settings. As simply as loading them into a program. This would save doing it manually ala reading the text file and altering your settings as you remember them.

Just an idea. I wonder if any one knows if such a prgram allready exists? Or what the scope for creating one might be. I suppose you could enter your changes as some sort of script right? so that the system then reads 'your customised script' and alters the system to your preference. This 'custom script' could then be taken with you and inserted into other linux machines e.t.c on an sd card/whatever medium. 

Any thoughts on the idea?  More than welcome =) 

Eiji Takanaka (7G-Operator)
[/LEFT]

---

### Post by Eiji Takanaka on 2011-03-13
bump?

---

### Post by wilee-nilee on 2011-03-13
There are several methods, you can do daily backups or when ever you want with rsync, and a handful of others, you can clone it, there is a log in home that has all the installs, you can make a script in synaptic that list all the installs. Your not getting an answer as your not asking for a how to.:)

Personally I just clone my setups with clonezilla, and fresh install every time.
[http://clonezilla.org/](http://clonezilla.org/)

This is actually pretty well covered in what you seek. I only know clonzilla and using rsync to sync daily ISO test releases though.

---

### Post by pi3.1415926535... on 2011-03-14
Shell scripts do work for this, though it means knowing the command line command for all of the modifications.

---

### Post by mcduck on 2011-03-14
I always log any interesting tweaks I make into a text file. Wouldn't be much of a problem to turn it into a shell script, although there are some GUI tweaks as well (I could probably just use gconftool-2 to handle them).

It really isn't much of a trouble to do this, especially when I really don't bother logging minor tweaks I know I'll be able to repeat myself, or that will move to new systems easily by just copying the setting files from my home directory.

This far I've never needed to run all of them, but it's nice to have such log around. Come to think of it, I should probably sync it to Ubuntu One... ;)

---

### Post by HermanAB on 2011-03-14
Well, it is always a good idea to make backups of /home and /etc.

Digital data doesn't really exist, unless you have at least two copies of it...

---

### Post by Eiji Takanaka on 2011-03-14
Hi again,

Thanks for reading and taking the time to reply all.

O.k  yeah i'm not so much talking the cloning of the entire system here  wilee-nilee dude, more perhaps the 'customisation' of ones system to  operate as one requires. 

I think this individuality and  'uniqueness' almost of each persons system is something important and i  can see it playing perhaps an important part further into the future, as  more people start to adapt to an open source way of life. 

I  imagine any simple mods can be done with regard to importing settings  (desktop layout/compiz/windows/backgrounds e.t.c) relatively easily. (If  not perhaps there is a way to save these to a simple shell script,  which can be 'loaded' onto any other system, pretty sure this must of  already been done). 

I'm talking about large changes to the  system, for example i have been tatting around with ubuntu stuidio a  while back it meant importing a specific kernel (real-time), and then  altering various audio config settings so as to increase performance as  required. 

Before now i've had to manually download and compile wifi drivers to get my wifi working. 

As  i said i try to keep a manual log file (just a simple .txt) of these  changes, but as you learn more and more you (or i:P) tend to tweak more  and more stuff on the system i find. Simple stuff until you have your  system running the way you want it.

I truly do think this ability  to customise fully your own system will be a massive massive thing in  the near future. But because in open source your running from a similar  base so to speak, the potential to then upload your own settings onto  other systems is increased i would of thought. You could then simply  load in your unique settings ala a sd card or future tech of your  choice. Or as was aforementioned upload to the cloud, so that the  settings are attainable at any point any from any linux system. It is  this ability of having own unique customised computer settings (in  general) that could create a continuation and provide a sense of  familiarity with whichever system you might find yourself to be working  on. 

Anyways im side-tracking.

Bascially i'm thinking  short-term, about maybe a program that can log changes to  scripts/configurations those sort of tweaks, make a note of  dependencies/modules required. save it as a script. Which can then be  transcribed onto a different workstation.

I suppose something super simple to start as a test.

I  know what im describing sounds very much like the synaptic and in a way  thats what im talking about. But with synaptic your talking actual  programs, and not the actual 'universal configuration' or workings of  the files that you are using, which you may of tweaked. 

Basically  a list of the tweaks you might have done to your system in a script so  that whenever you went on a different linux system its as simple as  running a shell script and it automatically downloads any files you  might need/sets the configuration of each program as you so desire that  sorta thing. 

Im talking major customisability and also minimal effort haha.

Maybe from now on putting any changes i do into a text file which can then be run as a script might be the way forward.

But  if there is a way to get a gui (yeah boo hiss i know) so as to improve  usability for those who are still finding their way around that will log  the changes made to a universal system configuration file of sorts...

Who  knows just bouncing a few ideas around really, not looking for a  specific answer or anything, more just suggesting stuff i guess...But if  we can get this script onto a small device which is then carried  around, and maybe im a bit of a dreamer but im thinking, a pda of sorts,  like the i-phone that people have on them, which carries these unique  settings..then you walk into a house and the settings automatically send  themselves to the workstation in your house (wifi or bluetooth  whatever). Or simply the ability to upload the settings onto the system  you will be working on. easily and simply. We are assuming most  developed countries have pretty darned fast broadband, so the uploading  pda can be super small and merely tells the connected system what to  download and from where and then what customisations to do to what  files. It could be mega small even.

I'm talking complete customisation script almost. 

This  ability to log changes made in a way which can then be transcribed into  a universal custom script, and run on whichever system would be kinda  cool i think.

Any ideas...or as the mighty Johnny 5 would say.....

inpuuuutttttttttttttttttttttttttttttttttt?? 

haha ;)

---

### Post by hotrod6657 on 2011-03-14
> **Eiji Takanaka said:**
> Hi again,

This  ability to log changes made in a way which can then be transcribed into  a universal custom script, and run on whichever system would be kinda  cool i think.


It would be cool, I'll admit, but I think a universal customization application might be tough...

For one, it would almost mandate than nothing in the new OS was different than the one you're transitioning from.  Just look at the number of times people start threads saying that something used to work on their old version of Ubuntu but doesn't work after upgrading to the new version.

---

### Post by Eiji Takanaka on 2011-03-14
Hmm this is true.... which is why the custom script might also include a download link to any dependencies/modules that might be required in order to properly implement the script. In a similar way that apt-get downloads required dependencies also. When changes are logged in the 'program' not only are the individual file change/customisations documented to script, but as are the current modules in place required to run it. 

maybe....

---

