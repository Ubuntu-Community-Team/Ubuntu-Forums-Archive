---
title: "appearence problems HELP!!!"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by HarvesterOfSorrow on 2010-10-27
if anyone can find out why the apperance settings stay on extra that would be great because ubuntu has a problem saving my settings for the visual effects 
Thanx 
-Joekickass :guitar:

---

### Post by fly-by-night on 2010-10-27
This might help:

[http://ubuntuforums.org/showthread.php?t=1538466&page=2](http://ubuntuforums.org/showthread.php?t=1538466&page=2)

[quote=Vanderfurff]
Configuring visual effects

Press System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects to change basic options relating to visual effects.

    * Select None to provide a simple desktop environment without any effects.
    * Select Normal to provide a good balance between attractiveness and performance.
    * Select Extra to provide an aesthetically pleasing set of graphics.


When you select an option, it may take several seconds for the change to be applied. During this time, your screen may flicker briefly.
Once the settings have been applied, a dialog box will appear asking you to either keep the new settings or to revert to your previous settings. If you find that the new settings work correctly, then click Keep Settings. Otherwise click Use Previous Settings. If you do not select anything for 20 seconds the system will return to your previous settings.[/quote]

---

### Post by amjjawad on 2010-10-27
Are you following the same procedure that fly-by-night posted?

---

### Post by HarvesterOfSorrow on 2010-10-27
well i tried all that and the problem is it just wont save the setting when i click on extra in the visual effects it just goes back to normal and yes i have clicked on keep settings and it dose...until i close and open the visual effects tab open again

---

### Post by amjjawad on 2010-10-27
> **JoeKickA$$ said:**
> well i tried all that and the problem is it just wont save the setting when i click on extra in the visual effects it just goes back to normal and yes i have clicked on keep settings and it dose...until i close and open the visual effects tab open again

Okay, I'm confused now. Do you want to choose "Extra" or it's stuck on "Extra" and can't be changed to another option?

---

### Post by alenn on 2010-10-27
> **JoeKickA$$ said:**
> well i tried all that and the problem is it just wont save the setting when i click on extra in the visual effects it just goes back to normal and yes i have clicked on keep settings and it dose...until i close and open the visual effects tab open again

can you set it on "none", if you can do that then your graphic card has a small amount of memory

---

### Post by DooM55 on 2010-10-27
> **JoeKickA$$ said:**
> if anyone can find out why the apperance settings stay on extra that would be great because ubuntu has a problem saving my settings for the visual effects 
Thanx 
-Joekickass :guitar:

this problem from VGA card try update :popcorn:

---

### Post by HarvesterOfSorrow on 2010-10-27
well im going to try and update my vga card i have an nvidia 9500 gt so i know i have the power to run extra but i cant get it off none

---

### Post by HarvesterOfSorrow on 2010-10-27
> **DooM55 said:**
> this problem from VGA card try update :popcorn:
did the update didn't work...this is a real head scratcher for me

---

### Post by amjjawad on 2010-10-27
> **JoeKickA$$ said:**
> did the update didn't work...this is a real head scratcher for me

1- What version of Ubuntu do you have? 10.10? 10.04? or which one?

2- Please check the attached screen shot and confirm whether it's similar to your case that you are stuck on "NONE" and you can not change it.

3- How did you try to update? maybe it's already updated and you don't need any update.

4- Did you try to restart your machine?

5- Please, reply the above questions so that we could help you more :)

---

### Post by HarvesterOfSorrow on 2010-10-27
> **amjjawad said:**
> 1- What version of Ubuntu do you have? 10.10? 10.04? or which one?

2- Please check the attached screen shot and confirm whether it's similar to your case that you are stuck on "NONE" and you can not change it.

3- How did you try to update? maybe it's already updated and you don't need any update.

4- Did you try to restart your machine?

5- Please, reply the above questions so that we could help you more :)

i have ubuntu 10.10

yes it is i am stuck on none and i cannot change it 

i updated my drivers when i first installed ubuntu a couple days ago and i let ubuntu do the update 

yes i restarted my machine

---

### Post by HarvesterOfSorrow on 2010-10-27
i have ubuntu 10.10 

i restarted my machine 

i am stuck on none like described in the photo 

i updated my card recently and i let ubuntu do it

---

### Post by amjjawad on 2010-10-28
> **JoeKickA$$ said:**
> i have ubuntu 10.10

yes it is i am stuck on none and i cannot change it 

i updated my drivers when i first installed ubuntu a couple days ago and i let ubuntu do the update 

yes i restarted my machine

When you restart your machine, the problem is still there, right? nothing changed, correct?

Try to run this from Terminal:

```
gnome-appearance-properties
```

Let's see what will happen.

---

### Post by HarvesterOfSorrow on 2010-10-28
yes problem still exists after i restart my machine and i typed in the command line the command you sent and it didnt change my problem

---

### Post by HarvesterOfSorrow on 2010-10-28
> **amjjawad said:**
> When you restart your machine, the problem is still there, right? nothing changed, correct?

Try to run this from Terminal:

```
gnome-appearance-properties
```Let's see what will happen.

joekickass@joekickass-P31-DS3L:~$ gnome-appearance-properties 

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

tried that this is what i get but the appearance settings window dose open

---

### Post by HarvesterOfSorrow on 2010-10-29
by the way its me JoeKickA$$ i just had to change my username

---

### Post by tajiknomi on 2010-10-29
> **HarvesterOfSorrow said:**
> joekickass@joekickass-P31-DS3L:~$ gnome-appearance-properties 

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

tried that this is what i get but the appearance settings window dose open


[SIZE=2]I think you haven't installed a **suitable Driver** for your Graphics-Card,thats y it not opening you Appearance-Menu..[/SIZE]


[SIZE=2]Check it out... sys>Adm>hardware drivers...[/SIZE]..perhaps it work

---

### Post by amjjawad on 2010-10-29
> **HarvesterOfSorrow said:**
> joekickass@joekickass-P31-DS3L:~$ gnome-appearance-properties 

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5225): Gdk-CRITICAL **: IA__gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

tried that this is what i get but the appearance settings window dose open

It could be a bug. I'm trying to google it and I found this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/518368](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/518368)

I know it's for 10.04 but it could be the same bug in 10.10. If it's not a bug then it's your driver and if it's not your driver (you said you update to the latest one) then I have no clue what's wrong. Perhaps someone else could figure it out. These are the possible causes I'm thinking about, either it's a bug or your driver.

---

### Post by tajiknomi on 2010-10-29
[SIZE=2][I]The link which is mentioned by "AMJAWAAD" ,i have read it out and at last i have see a comment which is....

"[/I][/SIZE]                 [SIZE=2]I was able to solve the problem. It is probably related to unadvised partial upgrades I and others did. Explanation:[/SIZE]
 [SIZE=2]At least in my installation two packages (libgnome-[/SIZE][SIZE=2]window-[/SIZE][SIZE=2]settings1  2.30.0-0ubuntu3 and capplets-data 2.30.0-0ubuntu3) were being held back  from updating. Both are probably dependencies of the current  gnome-control-[/SIZE][SIZE=2]center package, which consequently, I figure, was also being held back, even though aptitude apparently didn't report so.[/SIZE]
 [SIZE=2]I had to force the installation of these two packages. It resulted in  the uninstallation of the ubuntu-desktop metapackage and then of  gnome-control-[/SIZE][SIZE=2]center, which is part of ubuntu-desktop; so after updating libgnome-[/SIZE][SIZE=2]window-[/SIZE][SIZE=2]settings1 and capplets-data I simply had to reinstall ubuntu-desktop. gnome-appearanc[/SIZE][SIZE=2]e-properties works fine now.[/SIZE]

        
[SIZE=2][I]"

Good-Luck..
[/I][/SIZE]

---

### Post by Omnomnom on 2010-10-29
Like Taji said, if you click on the top bar System, then click Additional Drivers, then let it do the work and follow everything it does. Then restart your computer, boot into normal Ubuntu mode by pressing enter if it's already highlighted, if it isn't, use the arrow keys to navigate down or up to it, then let it boot, if the writing is a little big don't worry, that's a bug that should hopefully be fixed in the next release, which is due next year. So when it's done, type in your password if needed to connect to your wireless, then go to System > Preferences > Appearance > Then wait for that to load if it doesn't instantly, then click on the Visual Effects tab. First click on normal, if that works then feel free to click on Extra. An easy way to see if Extra was applied is to move the window arround, if it wobbles, it's worked! You can edit settings on the CompizConfig settings window, which you can find in the Ubuntu software centre. Note that the changes might take a few seconds to apply, especially if you have a slow computer, so give it 10 or so seconds when you try and turn on extra or normal. Hope I helped.

---

### Post by HarvesterOfSorrow on 2010-10-29
> **tajiknomi said:**
> [SIZE=2][I]The link which is mentioned by "AMJAWAAD" ,i have read it out and at last i have see a comment which is....

"[/I][/SIZE]                 [SIZE=2]I was able to solve the problem. It is probably related to unadvised partial upgrades I and others did. Explanation:[/SIZE]
 [SIZE=2]At least in my installation two packages (libgnome-[/SIZE][SIZE=2]window-[/SIZE][SIZE=2]settings1  2.30.0-0ubuntu3 and capplets-data 2.30.0-0ubuntu3) were being held back  from updating. Both are probably dependencies of the current  gnome-control-[/SIZE][SIZE=2]center package, which consequently, I figure, was also being held back, even though aptitude apparently didn't report so.[/SIZE]
 [SIZE=2]I had to force the installation of these two packages. It resulted in  the uninstallation of the ubuntu-desktop metapackage and then of  gnome-control-[/SIZE][SIZE=2]center, which is part of ubuntu-desktop; so after updating libgnome-[/SIZE][SIZE=2]window-[/SIZE][SIZE=2]settings1 and capplets-data I simply had to reinstall ubuntu-desktop. gnome-appearanc[/SIZE][SIZE=2]e-properties works fine now.[/SIZE]

        
[SIZE=2][I]"

Good-Luck..
[/I][/SIZE]

how do you do a force install? can you give me a step by step on what you did to solve your problem?

---

### Post by HarvesterOfSorrow on 2010-10-30
thanks man got it

---

### Post by Omnomnom on 2010-10-31
Glad we helped! You should change the thread tag to [SOLVED] so it can help other people who may have this problem.

---

### Post by Omnomnom on 2010-10-31
So did we help or..?

---

### Post by HarvesterOfSorrow on 2010-10-31
ya you guys helped alot thanks 

p.s how do i switch it to solved?

-travis :guitar:

---

### Post by amjjawad on 2010-10-31
> **HarvesterOfSorrow said:**
> ya you guys helped alot thanks 

p.s how do i switch it to solved?

-travis :guitar:

Thread Tools.

---

### Post by kakila on 2010-12-10
Hi
I tried to uninstall and re-install the libraries mentioned but the problem is not solved.
I do not really know how to force an update.
Also, could you tell the versions that are supposed to work?
I have
libgnome-window-settings1 2.32.0-0ubuntu2
capplets-data 2.32.0-0ubuntu2

Thanks

---

### Post by amjjawad on 2010-12-10
> **kakila said:**
> Hi
I tried to uninstall and re-install the libraries mentioned but the problem is not solved.
I do not really know how to force an update.
Also, could you tell the versions that are supposed to work?
I have
libgnome-window-settings1 2.32.0-0ubuntu2
capplets-data 2.32.0-0ubuntu2

Thanks

I'd suggest you start a new thread and please, make sure to describe the problem in an easy-to-understand way and also don't forget to mention your system configuration/specifications :)

---

### Post by kakila on 2010-12-10
Ok,
Problme posted in
[http://ubuntuforums.org/showthread.php?p=10222738#post10222738](http://ubuntuforums.org/showthread.php?p=10222738#post10222738)

---

