---
title: "Where is the Main Menu?"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by g d on 2011-05-11
I'm using 11.04 that I downloaded and installed yesterday on an older mini ITX system (pentium m, 1GB RAM...). I left everything at their default settings.

I've used Ubuntu before and there's typically a menu across the top of the screen and it seems to be missing. All I get is a dock type strip down the left side of the screen with a few apps in it. I've searched and while I've found others with this issue, the solutions haven't worked for me. Some will say things like  "check System > Preferences > Main Menu" - but that's just my problem, I don't have a "System" menu to be able to get to anything. This is extremely frustrating.

Has the Main Menu gone away in v.11? If not, how do I turn it on?

Thanks

---

### Post by jtfolden on 2011-05-11
Yes, the prior menu system (and desktop environment) as used in earlier versions of Ubuntu is being retired in favor of what you see now. You should have an icon on the Dock that brings up your listing of Apps now.

Alternatively, you can log out and choose "Classic..." as your session but this will be going away with the next release.

---

### Post by Paqman on 2011-05-11
> **g d said:**
> 
Has the Main Menu gone away in v.11?


Yes, but in the dock on the left you've options to search fro either files or applications. Everything that used to be in the menu can be found that way. You can add things to the dock permanently by right clicking on their icon (when they're running) and selecting "keep in launcher".

> 
If not, how do I turn it on?


Log out and select "Ubuntu classic" from the session menu at the bottom of the screen when you go to log in. However, the next version of Ubuntu won't have this option available, so it's worth getting used to the new interface.

---

### Post by drs305 on 2011-05-11
It takes some learning and getting used to, but the launcher has a lot of advantages. Right click on any app in the launcher and you can make it permanent, even when the app is closed.

Another quick way to launch apps and files is to use the bottom two icons (Applications & Files). Clicking on them brings up the most recently used ones, and access to others as well as a search bar.

---

### Post by grahammechanical on 2011-05-11
1) Click on the icon of a folder and then move the mouse pointer to the top panel. What do you see?

2) click on the shut down icon. Do you see System Settings at the bottom of the menu list? Have you looked in there?

3) In the Launcher (left side panel) right click on the icon of a plus sign (+) inside a magnifying glass. Do you see the menu list?

Regards.

---

### Post by g d on 2011-05-11
> **jtfolden said:**
> Yes, the prior menu system (and desktop  environment) as used in earlier versions of Ubuntu is being retired in  favor of what you see now. You should have an icon on the Dock that  brings up your listing of Apps now.
 
 Thanks for clarifying that.

> **Paqman said:**
> Yes, but in the dock on the left you've options  to search fro either files or applications. Everything that used to be  in the menu can be found that way. You can add things to the dock  permanently by right clicking on their icon (when they're running) and  selecting "keep in launcher".

 So there's some icons in the dock already,  and I can click on the zoom icon (magnifying glass with a +) to get a  few more. That seems extremely more difficult than the old way.  Previously they were shown in a list that was all easy to see. Now  there's a pile of just a few HUGE icons. I don't care about ones I don't  have installed - is there a way to shut that off?

Is there a way to make it just a simple list? Even if I click See more  results... I get a huge grid with a ton of wasted space. Is there a way  to make the icons smaller? Apple tried this same thing when they  released Stacks and quickly found that people hated it so they added a  list view. That's what I'd prefer..

> Log out and select "Ubuntu classic" from the session menu at the  bottom of the screen when you go to log in. However, the next version of  Ubuntu won't have this option available, so it's worth getting used to  the new interface.

Thanks. I'll try to find some way to make this current version work.


> **grahammechanical said:**
> 1) Click on the icon of a folder and then move the mouse pointer to the top panel. What do you see?

File, Edit, View, Go...

> 2) click on the shut down icon. Do you see System Settings at the bottom of the menu list? Have you looked in there?

Wow, I never would have thought to click on the shutdown icon to find System Settings. That will come in handy.

> 3) In the Launcher (left side panel) right click on the icon of a plus sign (+) inside a magnifying glass. Do you see the menu list?
.

Not a list, but a grid.

Thanks to all for your input. As a UI designer for 15+ years, I get rather frustrated with UI's that aren't intuitive.

---

### Post by drs305 on 2011-05-11
> **g d said:**
> Is there a way  to make the icons smaller?

If it isn't already installed, install ccsm:```

sudo apt-get install compizconfig-settings-manager
```

Now you can play with Unity. Press the system icon (upper left), then type *compiz*. You will see an icon for it appear. CLick it. If you think might refer to it often, right click the icon in the left menu and select 'Keep in Launcher'. 

Now, to answer your question: Once you've opened it, look in the Desktop section, Ubuntu Unity Plugin. Double Click, then Experimental, launcher icon size. It only shrinks to 32, but it seems a lot smaller than the default.

---

### Post by wildmanne39 on 2011-05-11
> **g d said:**
> I'm using 11.04 that I downloaded and installed yesterday on an older mini ITX system (pentium m, 1GB RAM...). I left everything at their default settings.

I've used Ubuntu before and there's typically a menu across the top of the screen and it seems to be missing. All I get is a dock type strip down the left side of the screen with a few apps in it. I've searched and while I've found others with this issue, the solutions haven't worked for me. Some will say things like  "check System > Preferences > Main Menu" - but that's just my problem, I don't have a "System" menu to be able to get to anything. This is extremely frustrating.

Has the Main Menu gone away in v.11? If not, how do I turn it on?

Thanks

Hi, also you can do what I did I installed the awn launcher and installed a menu applet to let me have a list of available programs. just like it use to be in gnome.

---

### Post by g d on 2011-05-11
That wasn't installed but I installed it. It doesn't seem to do quite what I'm looking for. When one clicks on the Applications icon in the Launcher, the flyout that appears is what I have a problem with. I would prefer it simply show the applications I have installed, and all of them, in list view - something similar to the way it used to work, how a folder in the OS X Dock works, how the Apple Menu in Classic Mac OS worked, how the Start menu in Windows works/ed...

The icons are the same size, no matter the size of the icons in the launcher. By default it only lists the first five application icons. It uses the whole screen to do this. I would like the entire "Apps Available for Download" section to go away. It takes up a third of the space. Same with Most Frequently Used.

I know I can also search for apps in the same window, but that assumes I know the name of the app I'm looking for.

The end result I would like is two clicks to every application.

Thanks

---

### Post by compmodder26 on 2011-05-11
Unfortunately, if you want to have the same menu you are used to, you're going to have to do what others said and switch to the "Ubuntu Classic" desktop on the login page.  You could alternatively install something like avant window navigator that offers a main menu

---

### Post by beew on 2011-05-11
> **g d said:**
> That wasn't installed but I installed it. It doesn't seem to do quite what I'm looking for. When one clicks on the Applications icon in the Launcher, the flyout that appears is what I have a problem with. I would prefer it simply show the applications I have installed, and all of them, in list view - something similar to the way it used to work, how a folder in the OS X Dock works, how the Apple Menu in Classic Mac OS worked, how the Start menu in Windows works/ed...

This is the dreadful dash, it is a 'feature' of course.

> 
I know I can also search for apps in the same window, but that assumes I know the name of the app I'm looking for.
Yeah, and it is kind of lame to tell people that Unity is great because you can use search like we are told in so many threads. It amounts to admitting that the cartoon menu sucks for finding and opening applications as it would take n clicks instead of just 2. Now if search is the intended way to find applications why do they spend so much time on the cartoon menu? And why do you need to open the dash (the flyout thing) to activate search? A button that when click will show a small search box would be suffice (like Synapse, a third party search launcher you can install in Unity)

> The end result I would like is two clicks to every application.

ThanksMove back to 10.10 or use the classic desktop.

---

### Post by DocShaman on 2011-05-19
Yeah its definitely taking some getting used to for me. 

Keyboard shortcuts helped me immensly. To search I mash the windows key. But I tend to like dual hand navigation but not typing. So I love using keyboard shortcut + clicks but tend to dislike searching.

SUPER (aka windows)key+type in a few letters e.g. "term"+enter launches the first one. 
[SUPER]+"term"+[enter]

Also like you I prefer to see everything at times, especially because I can never remember what Ubuntu calls things. So I can click on the (+) icon in the main icon menu (left) or via keyboard shortcut SUPER+A (mnemonic A=Applications?). Then there are two things of note took me a bit to notice once it opens. First, I can click on the "See 99 more results" in the header of the Installed section. Second the dropdown in the search bar to narrow the results. 

This site was decent for shortcuts and gives a nice desktop background for reference.
[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

Im my case, I just installed bitdefender via a community doc but it doesn't tell you how to run it or launch the gui unless I missed it. So I found the "main menu" config in System Settings and its shown there. But when I search or look in the app's it's not found so i'll have to find that but I wanted to comment in case it helps.

And thanks to whomever posted the shutdown>system settings tip. How many times have I overlooked that one!

Doc

---

### Post by wildmanne39 on 2011-05-19
> **DocShaman said:**
> Yeah its definitely taking some getting used to for me. 

Keyboard shortcuts helped me immensly. To search I mash the windows key. But I tend to like dual hand navigation but not typing. So I love using keyboard shortcut + clicks but tend to dislike searching.

SUPER (aka windows)key+type in a few letters e.g. "term"+enter launches the first one. 
[SUPER]+"term"+[enter]

Also like you I prefer to see everything at times, especially because I can never remember what Ubuntu calls things. So I can click on the (+) icon in the main icon menu (left) or via keyboard shortcut SUPER+A (mnemonic A=Applications?). Then there are two things of note took me a bit to notice once it opens. First, I can click on the "See 99 more results" in the header of the Installed section. Second the dropdown in the search bar to narrow the results. 

This site was decent for shortcuts and gives a nice desktop background for reference.
[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

Im my case, I just installed bitdefender via a community doc but it doesn't tell you how to run it or launch the gui unless I missed it. So I found the "main menu" config in System Settings and its shown there. But when I search or look in the app's it's not found so i'll have to find that but I wanted to comment in case it helps.

And thanks to whomever posted the shutdown>system settings tip. How many times have I overlooked that one!

DocHi, I am going to give you the background with the shortcuts and if you look below this text you will see four useful guides for unity, that you can click on to check out.:)

---

### Post by wildmanne39 on 2011-05-19
> **DocShaman said:**
> Yeah its definitely taking some getting used to for me. 

Keyboard shortcuts helped me immensly. To search I mash the windows key. But I tend to like dual hand navigation but not typing. So I love using keyboard shortcut + clicks but tend to dislike searching.

SUPER (aka windows)key+type in a few letters e.g. "term"+enter launches the first one. 
[SUPER]+"term"+[enter]

Also like you I prefer to see everything at times, especially because I can never remember what Ubuntu calls things. So I can click on the (+) icon in the main icon menu (left) or via keyboard shortcut SUPER+A (mnemonic A=Applications?). Then there are two things of note took me a bit to notice once it opens. First, I can click on the "See 99 more results" in the header of the Installed section. Second the dropdown in the search bar to narrow the results. 

This site was decent for shortcuts and gives a nice desktop background for reference.
[http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts](http://askubuntu.com/questions/28086/unity-keyboard-mouse-shortcuts)

Im my case, I just installed bitdefender via a community doc but it doesn't tell you how to run it or launch the gui unless I missed it. So I found the "main menu" config in System Settings and its shown there. But when I search or look in the app's it's not found so i'll have to find that but I wanted to comment in case it helps.

And thanks to whomever posted the shutdown>system settings tip. How many times have I overlooked that one!

DocHi, I am going to give you the background with the shortcuts and if you look below this text you will see four useful guides for unity, that you can click on to check out.:)
Sorry for got to attach the background.

---

### Post by bdoe on 2011-05-19
If you find, like I did, that you and Unity are a match made in hell, there *are* other alternatives you can try. You could give KDE a try via Kubuntu. Or, if you want something more lightweight that resembles Gnome, there's a new-ish Ubuntu derivative called Lubuntu, which uses the LXDE Desktop Manager. LXDE is perfect for those who are newly transitioning from Windows, as it has a very similar look-and-feel, but it is also great for Gnome veterans looking for something fast and streamlined.

---

### Post by Seth Mould on 2012-02-15
[QUOTE= In the Launcher (left side panel) right click on the icon of a plus sign (+) inside a magnifying glass. Do you see the menu list?

Regards.[/QUOTE]

I can't see the magnifying glass.

It's really annoying when I go for the Back button in Firefox and go too far, opening the Launcher or Applications menu or whatever else you call it (can't we all sing from the same hymn sheet?)

---

### Post by grahammechanical on 2012-02-15
@Seth Mold. This is an old thread and the Op has received the help that he requested. Why are you resurrecting it?

What version of Ubuntu are you using? The suggestions here were for 11.04. The advice about the icon with the magnifying class in the Launcher is only applicable to 11.04 because that icon was removed in 11.10.

The design of the standard Ubuntu desktop interface (Unity) is moving forward. There are improvements/differences Ubuntu 12.04 which will be released at the end of April.

I am running 12.04 development branch right now and I can tell you that when I have Chromium or Firefox maximized and I move the mouse to the back button the Launcher does not reveal. This is because I have set the Launcher to only reveal or come out when the mouse pointer goes to the left edge of the screen and not when the mouse pointer goes to the top left of the screen.

I can also adjust the pressure that is needed when putting the mouse pointer to the left edge of the screen so that it is not too sensitive or too insensitive. These are things that we can adjust in 12.04.

I accept that Linux/Ubuntu is under constant development. I expect things to improve over time.

Regards.

---

### Post by Frogs Hair on 2012-02-15
You can add a menu applet to unity 11.04 if you wish . [http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

---

### Post by Seth Mould on 2012-02-15
> **grahammechanical said:**
> @Seth Mold. This is an old thread and the Op has received the help that he requested. Why are you resurrecting it?

What version of Ubuntu are you using? The suggestions here were for 11.04. The advice about the icon with the magnifying class in the Launcher is only applicable to 11.04 because that icon was removed in 11.10.



Thanks, and apologies for farting in church. I added to the thread because it put a noobie question into a pertinent thread, rather than raising another dumbass thread. I'm on 11.10. 

I must try harder.

---

### Post by Seth Mould on 2012-02-15
> **Frogs Hair said:**
> You can add a menu applet to unity 11.04 if you wish . [http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray](http://ubuntuguide.net/classic-menu-indicator-applet-in-ubuntu-11-04-unity-system-tray)

Thank you, but I want to keep my v10.11 'vanilla', and solve problems without tweeks.

---

### Post by oldos2er on 2012-02-16
This thread seems to be going nowhere fast, so I've closed it.

Seth Mould, it's to your advantage to start a new thread, especially where a newer version of Ubuntu is concerned. Also most people don't look for new questions in old threads.

Thanks for your understanding.

---

