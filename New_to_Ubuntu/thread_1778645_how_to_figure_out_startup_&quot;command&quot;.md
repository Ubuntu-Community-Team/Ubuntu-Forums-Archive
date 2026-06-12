---
title: "how to figure out startup &quot;command&quot;"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by smcrossman on 2011-06-09
This seems like such a basic thing...  I have several apps that I would like to start up when the system starts up in Ubuntu (currently a dual boot w/Win 7; one in 64 bit one in 32).

I have them placed on either panels or they are on the Launcher, or if those fail I can find them in Applications.  My problems is I don't know what to enter for the command to start the app.  I'm also having this issue trying to add Application Launchers to the desktop.  Is there a way to identify the command when looking at the files for the application?  (You know like in windows you would link to the .exe file....) 

I recall sometime in the past month I came across a blog type thing that told you how to add launchers to your launcher bar in Unity, but I cannot for the life of me find it again.  

I am currently using Startup Applications in System/Preferences to do this. I am willing to go into terminal and alter the actual file, but if I can do it without actually editing the code I prefer that way.

---

### Post by jtarin on 2011-06-09
Sometime just the name of the app will start it. [You might be interested in this.]("http://www.ubuntu-corner.com/2011/05/slingshot-application-launcher-from-elementary-team-in-ubuntu-11-04-2/")

---

### Post by robbiemacg on 2011-06-09
Hi,
If I understand your question correctly, you're interested in determining what to input for a 'command' when adding an application to your Startup Apps (System Settings > Startup Application > Add)?
I'd usually point to an executable file in **/usr/bin** or a desktop config file in **/usr/share/appliactions**.

If you don't feel like scrolling through a giant list you can always open a terminal emulator and do something like this:
```
robbiemacg@robbiemacg-desktop:~$ ls /usr/share/applications | grep fire
[COLOR=Red]fire[/COLOR]fox.desktop

```
Now I know that there's a desktop config file that'll launch Firefox located in **/usr/share/applications/firefox.desktop**.
There might be other methods to achieve your ends, but this is how I've done things in the past, and my efforts have met with success.

robbiemacg

---

### Post by ajgreeny on 2011-06-09
If the app in question is a GUI and not a terminal only application, you can find the command to run it from the desktop menu editor (alacarte).

So if you're using unity use the command **alacarte** in terminal to start the editor and navigate to the application in question, then click on the Properties button and you will see the command box.  Copy that into the startup applications command box.

Simple!

Even more simple could be using the command ```
which <*applicationname*>
```If you're not sure of the name, start with the first few letters of the app name and hit tab; a single name may appear after a first tab or a list of options may appear after a second tab press, eg, if I use ```
which ala
```a list of **alacarte** and **alarmclock** appears after two tab presses.

---

### Post by ngubk on 2011-06-09
The easiest way is to open /usr/share/applications. Right click on the app you want to start with Ubuntu and copy that command. See how easy that is :))

---

### Post by ajgreeny on 2011-06-09
> **ngubk said:**
> The easiest way is to open /usr/share/applications. Right click on the app you want to start with Ubuntu and copy that command. See how easy that is :))
That's clever!!

I never thought about that way, as I always use the straight one word command of the executable's name.

I shall remember that one!.  Many thanks.

---

### Post by smcrossman on 2011-06-09
thanks...lots of ways to go! I'll play around with them and see which seems to fit best for me!  I knew that there was some simple way...but I was totally lost!  Basic thing that anyone tweaking should know!

---

### Post by robbiemacg on 2011-06-09
Report back and let us know how it goes... and remember to please mark this thread solved if your questions been managed to your satisfaction. :D

---

### Post by smcrossman on 2011-06-10
> **robbiemacg said:**
> Report back and let us know how it goes... and remember to please mark this thread solved if your questions been managed to your satisfaction. :D

I like the usr/share/applications. The alacarte seems to take me mostly to the menu, and I haven't been able to master the which command, especially with multiple word names.  Probably will keep playing with it. Generally if I tab it might pull up the name. If I double tab it either does nothing (I'm still trying to fine tune keyboard settings) or it lists everything and the kitchen sink (I'm guessing it's some complete file directory, I just haven't figured out which one because it's listing things like which and whichis)

One tip for any other newbies....I had earlier gotten a tip on putting a "shortcut" or launcher on the desktop to list all my installed applications.  I can use that instead of terminal to navigate to the list you get in usr/share/applications. Then right clicking gives me the command!  I don't remember if I asked that question or just viewed it because it sounded useful. I think that you right click on desktop to make a location launcher and then go to usr/share/applications in the location box. does that seem about right folks? Since I seem to be installing a lot of apps and don't want to add them all to the launcher bar while I'm testing to find what I want to use this "shortcut" (windows term) or "launcher" (linux term) seemed like a good way to find things I've installed or to look before installing something new.

---

### Post by jtarin on 2011-06-10
9 times out of 10 it will normally start with just the name....firefox,gimp,inkscape etc...some you have to be a litle more creative...like Open Office Word Processor (oowriter) short and sweet.

---

### Post by smcrossman on 2011-06-10
> **jtarin said:**
> 9 times out of 10 it will normally start with just the name....firefox,gimp,inkscape etc...some you have to be a litle more creative...like Open Office Word Processor (oowriter) short and sweet.


That is just so LOGICAL and simple.  One of the things I'm truly appreciating about Ubuntu vs Windows.  Problem is that so many things in my life have trained me LOGICAL isn't valid or won't work, I'm undoing a lot of brainwashing here! ;)

---

