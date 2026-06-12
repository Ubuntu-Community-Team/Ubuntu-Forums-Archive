---
title: "first timer - a few questions"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by indup on 2010-09-28
ok i installed ubuntu via windows installer on my laptop so now i have dual boot windows and ubuntu.
i have a monitor connected to my laptop which i use as my main work/viewing screen and the laptop screen is used as a secondary screen and is always on. a few questions please:

1) when i first booted after the install the ubunt welcome screen was in the pinky sort of colour with 'ubuntu' in small letters with the 5-6 dote underneath. in subsequent boot ups the 'ubuntu' writing has been magnified 3-4 times the size; i was just wondering what that was about?

2) i had a bit of a problem getting the dual screen set up initially the way i want it (monitor main screen and laptop second screen). more through trial and error and just hoping for the best i have achieved this but ever since i have i can no longer acess the monitor settings as i get a 'randr extension missing' message or something like that. do i need to sort that out or can i just leave it?

3) most of my time is spent web browsing and i use firefox like i did on windows but i have noticed that since using ubuntu my eyes will start to hurt after about an hour whereas using windows i could spend all day on firefox and not have this problem.

4) is it possible while i am still figurng out ubuntu to simultaneously have ubuntu and windows running,for eg. ubuntu on my main screen and windows on my laptop screen?

thanks

---

### Post by madmax75 on 2010-09-28
> **indup said:**
> 

1) when i first booted after the install the ubunt welcome screen was in the pinky sort of colour with 'ubuntu' in small letters with the 5-6 dote underneath. in subsequent boot ups the 'ubuntu' writing has been magnified 3-4 times the size; i was just wondering what that was about?

I believe this is a bug. After installation Ubuntu shows the boot splash screen in the wrong resolution. I have that too on my laptop, but I don't mind since it is there just for a few seconds after all :rolleyes:

> 3) most of my time is spent web browsing and i use firefox like i did on windows but i have noticed that since using ubuntu my eyes will start to hurt after about an hour whereas using windows i could spend all day on firefox and not have this problem.

This has maybe something to do with the fonts Firefox is using? :confused: I know there was an "ugly default Firefox font problem" in the earlier versions of Ubuntu, but I myself haven't noticed this (my first Ubuntu was 8.04).

Can't say anything about the other problems, sorry...

---

### Post by Dustin2128 on 2010-09-28
> **indup said:**
> 
4) is it possible while i am still figurng out ubuntu to simultaneously have ubuntu and windows running,for eg. ubuntu on my main screen and windows on my laptop screen?

thanks
well, something you might try is installing a virtual copy of windows (if you have install discs) on virtualbox. It basically runs the windows machine inside a window that you can minimize or maximize and use as a full computer, minus any strenuous gaming. You can even use seamless mode to give your ubuntu install a taskbar above your gnome panel. But I don't know the specs of your laptop, and running 7 or vista will almost certainly take up half or more of your ram. XP runs fine on around 368 Mb of RAM though, so that's much more practical.

---

### Post by uRock on 2010-09-28
Hello and welcome to Ubuntu Forums,

Being that ubuntu doesn't have to be registered, you should run it in a virtualbox inside of Windows. In order to install Windows in a VBox within ubuntu, you'd have to have a install disk from MS, as the restore disk will most likely not work in a VBox.

It is normal for the boot splash to get ugly after installing the graphics driver, but it works fine.

I am the opposite with the visual problems you are having with Firefox in ubuntu. You can change the Firefox theme by visiting this link; 
[http://www.getpersonas.com/en-US/persona/1303](http://www.getpersonas.com/en-US/persona/1303)

Regards,
uRock

---

### Post by Dustin2128 on 2010-09-28
> **uRock said:**
> 
I am the opposite with the visual problems you are having with Firefox in ubuntu. You can change the Firefox theme by visiting this link; 
[http://www.getpersonas.com/en-US/persona/1303](http://www.getpersonas.com/en-US/persona/1303)
I don't think personas will make much of a difference in viewability (no font or button changes). [https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/) provides themes with many other modifications.

---

### Post by indup on 2010-09-28
thanks for everyones replies i think ill try to just get use to ubuntu for the time being the virtualbox method seems a bit complicated for me.

i just experienced a problem i could do with some help with.

th cursor just froze on the border of both screens and wouldnt move with the mouse or with any method i tried and all the computer keys became unresponsive even the shut down button, only thing i could think to do was to turn the power at the wall socket and had to restart my computer. anyone know what happened at if it should happen again what can i do instead of turning off the power from the mains. this happened immediately after i downloaded and chose to use the moomex theme, i dont know if that had anything to do with it.
thanks

---

### Post by s1wood on 2010-09-29
I get a similar problem, though in my case the cursor moves but nothing happens when I click it.
 I still haven't found an answer but  the tip I was given helps: if your keyboard is working hold down Alt + SysRQ and type (This is the difficult bit) REISUB. This should restart your computer. 

Susan

---

### Post by indup on 2010-09-29
thanks but when it happened the keys completely froze aswell the only thing i could think to do was turn the power off at the mains. (obviously this aint good for my computer)>

---

### Post by uRock on 2010-09-29
> **Dustin2128 said:**
> I don't think personas will make much of a difference in viewability (no font or button changes). [https://addons.mozilla.org/en-US/firefox/themes/](https://addons.mozilla.org/en-US/firefox/themes/) provides themes with many other modifications.
Changing the background of the Firefox Tool bars can make a great difference. Would it hurt to make recommendations without shooting down someone else's?> **indup said:**
> thanks for everyones replies i think ill try to just get use to ubuntu for the time being the virtualbox method seems a bit complicated for me.

i just experienced a problem i could do with some help with.

th cursor just froze on the border of both screens and wouldnt move with the mouse or with any method i tried and all the computer keys became unresponsive even the shut down button, only thing i could think to do was to turn the power at the wall socket and had to restart my computer. anyone know what happened at if it should happen again what can i do instead of turning off the power from the mains. this happened immediately after i downloaded and chose to use the moomex theme, i dont know if that had anything to do with it.
thanks
Is this problem still happening or was it a one time thing? 

Is moomex a firefox theme or persona?

---

### Post by sandyd on 2010-09-29
> **indup said:**
> ok i installed ubuntu via windows installer on my laptop so now i have dual boot windows and ubuntu.
i have a monitor connected to my laptop which i use as my main work/viewing screen and the laptop screen is used as a secondary screen and is always on. a few questions please:

<snip>

2) i had a bit of a problem getting the dual screen set up initially the way i want it (monitor main screen and laptop second screen). more through trial and error and just hoping for the best i have achieved this but ever since i have i can no longer acess the monitor settings as i get a 'randr extension missing' message or something like that. do i need to sort that out or can i just leave it?

**Did you activate anything in System -> Administration -> Hardware drivers by any chance?**

3) most of my time is spent web browsing and i use firefox like i did on windows but i have noticed that since using ubuntu my eyes will start to hurt after about an hour whereas using windows i could spend all day on firefox and not have this problem.

**See if changing the color/temperature settings and the gamma helps.**

thanks
.

---

### Post by indup on 2010-09-30
> **uRock said:**
>  Is this problem still happening or was it a one time thing? 

Is moomex a firefox theme or persona?

 just happened once so far and i think moomex is a theme  thanks

---

### Post by indup on 2010-09-30
> **sandyd said:**
> .

 no i idnt activate anything i jusy went to the monitor sectting and got the error message.  now that its been a couple of days the screen wiewing problem is not so bad now although the screen isnt as sharp as when using windows. thanks

---

### Post by adwhitenc on 2010-09-30
> **Dustin2128 said:**
> well, something you might try is installing a virtual copy of windows (if you have install discs) on virtualbox. It basically runs the windows machine inside a window that you can minimize or maximize and use as a full computer, minus any strenuous gaming. You can even use seamless mode to give your ubuntu install a taskbar above your gnome panel. But I don't know the specs of your laptop, and running 7 or vista will almost certainly take up half or more of your ram. XP runs fine on around 368 Mb of RAM though, so that's much more practical.


As he said, virtualbox is the best bet for this, however, make sure to download the proprietary version and install the guest additions if you want seamless mode. Also, make sure your memory is large enough to handel windows and ubuntu at one. Also, as a warning, installing vista or 7 under virtualbox allows Microsoft to deactivate your disc. Be careful with that.

---

### Post by indup on 2010-09-30
its been a couple of days now and im finding it a bit of a struggle. windows just seems a whole lot easier.  i tried to install skype- couldnt do it (x816 message or something like that).  when i connect my n900 it only recognises one type of memory and not the other where my personal files(pics,sounds,wallpapers,etc) are.  been trying to install themes from the web- about half of them work the others dont.  same with apps/programs, some just dont work when i click on them (nothing happens),dont know why.

---

### Post by SeijiSensei on 2010-09-30
> **indup said:**
> same with apps/programs, some just dont work when i click on them (nothing happens),dont know why.

Don't install software randomly from the web; use the software management tools that come with Ubuntu.

The underlying philosophy of Ubuntu and other Linux distributions is very different from that of Windows.  Because all the software in Ubuntu is open-sourced, it can be freely redistributed by Ubuntu itself.  It's very rare that you need to install a program that's not already available from the Ubuntu software "repositories."  Unlike Windows, where nearly all software is provided by third parties, that situation is quite rare when it comes to Linux distributions.  For the time being, you should stick to the software that's available via your software installer.  You'll be amazed at the array of programs available at your fingertips for free.

---

### Post by adwhitenc on 2010-09-30
> **indup said:**
> its been a couple of days now and im finding it a bit of a struggle. windows just seems a whole lot easier.  i tried to install skype- couldnt do it (x816 message or something like that).  when i connect my n900 it only recognises one type of memory and not the other where my personal files(pics,sounds,wallpapers,etc) are.  been trying to install themes from the web- about half of them work the others dont.  same with apps/programs, some just dont work when i click on them (nothing happens),dont know why.
Try installing wine at [http://www.winehq.org/](http://www.winehq.org/)
 you can run most windows apps on that

---

### Post by fugaki on 2010-09-30
> 3) most of my time is spent web browsing and i use firefox like i did on windows but i have noticed that since using ubuntu my eyes will start to hurt after about an hour whereas using windows i could spend all day on firefox and not have this problem.

Make sure you check the video settings, if you have the resolution or refresh rate off, I have seen it flicker in an odd way, I'm sure this could give you a headache if you stared at it long enough.

---

### Post by indup on 2010-10-01
ok things are going from bad to worse here. i cant log onto the internet now tried starting firefox nothing happening and any program that requires access to the internet doesnt work. all i can think that might have caused it is the automatic update of apps from the app centre,(dont know if that caused the problem though?).

---

