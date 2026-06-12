---
title: "Ubuntu/gnome desktop theme editor"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by apollothethird on 2010-11-21
Does anyone know how to make minor changes to an Ubuntu Desktop theme?  I’ve spent a couple of days looking for a Theme editor but can’t find one.

Actually the Dust Theme is perfect except that I can’t see the words on the Menu bar in the unselected windows.  They are too dark.  I’m trying to find a way to lighten up the menu bar.

I can see the menu bar differently if I use the Customize option to change the Window Border, but that’s too drastic, as I lose the charm of the Dust theme (the 3d window border effect).

I would think it might be a simple matter of locating an xml file and changing the menu title bar color.

Anyway, any info on editing themes would be great.  Since someone is creating the themes I’m sure an editor exist somewhere.  I’m just having bad luck finding one.

Thanks in advance for feedback.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Hippytaff on 2010-11-21
Is it this your looking for

system -> preferences -> appearance 

? :-)

---

### Post by apollothethird on 2010-11-21
> **Hippytaff said:**
> Is it this your looking for

system -> preferences -> appearance 

? :-)

No.  That is the option that I described that will allow you to change the themes or modify the Window Border which will to a different boarder theme which will destroy charm of my selected theme.

I'm hoping for a way to make a very minor change.  In this case to only change the color of the title bar, and specifically the title bar of the Dust theme.  I have used the method that you mentioned for days.  It won't allow the minor adjustment I'm trying to make.

Of course if there is a theme editor around somewhere, a person would be able to make any change.

Thanks for the tip.  But unless I'm missing something, it doesn't have a feature to only change the shade of the menu bar and leave everything else untouched.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Hippytaff on 2010-11-21
I'm not sure, but the package ubuntu-tweak might have that option, other than that I don't know - sorry :-)

---

### Post by apollothethird on 2010-11-21
> **Hippytaff said:**
> I'm not sure, but the package ubuntu-tweak might have that option, other than that I don't know - sorry :-)

Thanks!  I'm exited about the prospect.  I'll let you know how it goes.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-22
Hippytaff.  Thanks again for the ubuntu-tweak suggestion.  It's a great tool that has lots of goodies for the Ubuntu's visual.  

However, I spent a good part of the day trying to figure out a way to modify the theme and specifically the shade of the title bar, but it doesn't include anything like that as part of the package.

For some reason it appears that making fine changes to the gnome/Ubuntu themes is a very closely guarded secret.

If someone discovers something, or knows something, please share the information with us.  I see the question asked all over the internet, but I don't see any working solutions.  Just themes provided by a few select who has apparently joined the exclusive club.

I'll post back my findings if I discover something.

Thanks again for everyone who has read this thread and pondered the thought.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by koleoptero on 2010-11-22
Another tool that has many UI options, although it might be a bit complicated, is gnome-color-chooser.

Run in terminal:
sudo apt-get install gnome-color-chooser

Then run it by the same command (it will also be in the menus somewhere).

---

### Post by dkjMusic on 2010-11-22
I too have looked far and wide and found no GUI-based editor for metacity themes that runs. I believe there is a real need for one.

I'm also a fan of the Dust theme. I like the fact that its wider borders on the side allow easier "grabbing" to resize the window.

IF the change you want to make is inside the window borders, e.g., menu bar, button colors, etc., then run System/Preferences/Appearance/Customize.../Controls and try the different options there until you find one you like. I'm using Dust with ellanna Controls to really brighten up Dust's colors within the borders.

---

### Post by koleoptero on 2010-11-22
> **dkjMusic said:**
> I too have looked far and wide and found no GUI-based editor for metacity themes that runs. I believe there is a real need for one.

I'm also a fan of the Dust theme. I like the fact that its wider borders on the side allow easier "grabbing" to resize the window.

IF the change you want to make is inside the window borders, e.g., menu bar, button colors, etc., then run System/Preferences/Appearance/Customize.../Controls and try the different options there until you find one you like. I'm using Dust with ellanna Controls to really brighten up Dust's colors within the borders.

The metacity theme is not responsible for the menubar, only the titlebar and the borders.

---

### Post by apollothethird on 2010-11-22
> **koleoptero said:**
> Another tool that has many UI options, although it might be a bit complicated, is gnome-color-chooser.

Run in terminal:
sudo apt-get install gnome-color-chooser

Then run it by the same command (it will also be in the menus somewhere).

Thanks.  I'm still looking at it.  After a couple of hours I notice that it's a nice tool.  It had many options, but it's missing the option to change the tile foreground or background.  It appears to have everything else covered.

It's the unselected window title bar that I can't see on one of my computers and have a hard time seeing on the others.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-22
> **dkjMusic said:**
> I too have looked far and wide and found no GUI-based editor for metacity themes that runs. I believe there is a real need for one.

I'm also a fan of the Dust theme. I like the fact that its wider borders on the side allow easier "grabbing" to resize the window.

IF the change you want to make is inside the window borders, e.g., menu bar, button colors, etc., then run System/Preferences/Appearance/Customize.../Controls and try the different options there until you find one you like. I'm using Dust with ellanna Controls to really brighten up Dust's colors within the borders.

Thanks Dkjmusic.  That's was the first thing I looked at weeks ago.  I still revisit it from time to time to make sure I'm not missing anything.  It's very hard to believe that you can't change the shade of the title bar.

I don't have any problems seeing the controls.  Changing the controls is very easy.  However, the problem is the title menu.  That's the area just above the controls.  I can't see the text in the title bar (the area just above the controls that tells the name of the window or application running.  There isn't enough contrast.

It's called the Windows Border in the customize theme configuration.  Changing that will lose the Dust feature which you describe as very convenient.

I'm still looking and very open for any ideas on how to be able to modify this element.

Thanks again for the time and interest.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by 101011010010 on 2010-11-22
Hello. 
I think it will be slightly easier to change the colour of the inactive window titlebar text, rather than the colour of the titlebar.
Open up a root nautilus window (type "gksu nautilus" in a terminal). Be careful any mistakes can cause problems.
Navigate to /usr/share/themes/Dust/metacity-1.
Make a backup of "metacity-theme-1.xml" just incase.
Open metacity-theme-1.xml with "gedit" 
Go to line 54 and change the colour (#727262) to the colour that you want.
Save the change, close the windows, log out and back in and that should be it.
I hope this is what you were looking to change.
(Updates to the Dust theme will reset the change)
A.

---

### Post by dkjMusic on 2010-11-22
You said:

> **koleoptero said:**
> The metacity theme is not responsible for the menubar, only the titlebar and the borders.

Then you said:
It's the unselected window title bar that I can't see on one of my computers and have a hard time seeing on the others.

So either I'm confused or it **is** a Metacity theme editor you need.

Do you need to lighten the menubar or the titlebar? I'm thinking you want to lighten the buttons and title on the inactive title bar. I'll try to help if I can figure out what you need.:D

---

### Post by apollothethird on 2010-11-22
> **dkjMusic said:**
> You said:



Then you said:
It's the unselected window title bar that I can't see on one of my computers and have a hard time seeing on the others.

So either I'm confused or it **is** a Metacity theme editor you need.

Do you need to lighten the menubar or the titlebar? I'm thinking you want to lighten the buttons and title on the inactive title bar. I'll try to help if I can figure out what you need.:D

Let me give you and example to try to help you to understand what I'm saying.

I refer to the menu bar as the area that says:

File Edit View (etc...)

I refer to the title window (which I may have referred to as the titlebar) as the space above that with Text information about what is running.

On some applications such as Virtual Box, it brings up the name of the application.  On some applications it brings up other information, such as Nautilus will bring up the name of the folder you have opened.

I have no problem seeing what I refer to as the Menu bar on all of my computers.  However on one of them I can't see the information on the status bar (in the inactive window).  If you look closely at an inactive window you'll see that "File Edit View" is a different font shade than the information that is just above that (in the same inactive window).

Does it still appear confusing what I'm saying?  Maybe someone else can look at an inactive window in the default dust theme and help me with better words to explain the problem that I'm seeing and describing.

Please keep in mind that people's eye sight and the shades they can recognize is different.  The shades might have lots of contrast for one person and not enough for another, as in my case (with the inactive window).

I believe this is known, and this is the reason most OS' theme environments have tweaks in this matter.

By the way, other items in this separate title bar include the Minimize and Maximize buttons.  I can't see them either.  But I can use them because I can tell relatively where they are.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-22
> **101011010010 said:**
> Hello. 
I think it will be slightly easier to change the colour of the inactive window titlebar text, rather than the colour of the titlebar.
Open up a root nautilus window (type "gksu nautilus" in a terminal). Be careful any mistakes can cause problems.
Navigate to /usr/share/themes/Dust/metacity-1.
Make a backup of "metacity-theme-1.xml" just incase.
Open metacity-theme-1.xml with "gedit" 
Go to line 54 and change the colour (#727262) to the colour that you want.
Save the change, close the windows, log out and back in and that should be it.
I hope this is what you were looking to change.
(Updates to the Dust theme will reset the change)
A.

Thanks, A.  I was able to change the background Font the way you mentioned.  I had tried that before, but I thought copying the theme to my ~/.theme area would take precedence over the glove one.  I have a “Dust” them in my ~/.theme area.

Do you know of a way to make the one in my area become effective so that I can leave the system wide defaults for other users?

At present I’m forcing everyone on the system to have my deviant choice.

Thanks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by 101011010010 on 2010-11-22
Hi again,
I don't really use the ~/.themes & /.icons folders, I thought that items placed in them would over-ride the usual themes aswell. 
Just a thought, I wonder if having Dust in two places is causing the problem.
If you goto ~/.themes and rename the Dust folder Dust-MM. Now open Dust-MM, right click on the Dust file,choose Properties, open the Permissions tab and put a tick in the "Allow executing file as program" box (this allows us to open the file Dust with Gedit).

Now open Dust file with Gedit and change the name to Dust-MM where required. It should look something like this:-
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Dust-MM
Comment=Ubuntu Dust-MM theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Dust-MM
MetacityTheme=Dust-MM
IconTheme=Humanity-Dark
CursorTheme=DMZ-White
ButtonLayout=maximize,minimize,close:
```Now hopefully the Dust-MM should work. Don't forget to make sure the change that you want is in the ~/themes folder.:)
If not I'm having a look myself,thought it might help in the future. So if this doesn't work let us know and maybe somebody with more knowledge might be able to help.

When you go into Appearances Dust-MM appears and can be selected.

A.

---

### Post by koleoptero on 2010-11-22
So it IS the titlebar, sorry, that you can only fix by editing the metacity theme. On the other hand I remember ubuntu usually had the opacity of the inactive titlebar semitransparent on the previous versions. If that is the issue then:

Press alt+f2 and run gconf-editor. Then navigate from the tree on the left to apps -> gwd. Then on the right you'll see the active and inactive decoration opacity. Set them both to 1. If they were already at 1 then it's the colour of the decoration that's the problem which, I'm sorry to tell you, you'll have to edit by hand by editing those files the people mentioned above.

---

### Post by apollothethird on 2010-11-22
> **koleoptero said:**
> So it IS the titlebar, sorry, that you can only fix by editing the metacity theme. On the other hand I remember ubuntu usually had the opacity of the inactive titlebar semitransparent on the previous versions. If that is the issue then:

Press alt+f2 and run gconf-editor. Then navigate from the tree on the left to apps -> gwd. Then on the right you'll see the active and inactive decoration opacity. Set them both to 1. If they were already at 1 then it's the colour of the decoration that's the problem which, I'm sorry to tell you, you'll have to edit by hand by editing those files the people mentioned above.

Thanks for the input.  I appreciate another program to have in my arsenal to learn about.

The titlebars, neither the active nor the inactive is semitransparent.

Also, there isn't an option on the right when selecting gdm.

I'm currently working with trying to make a per-user change to the Dust theme by modifying a copy placed in the users ~/.theme area.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by koleoptero on 2010-11-23
Well sorry for the tons of off-topic replies, I'm glad I at least helped you learn about a couple of tools. :)

Also in that last post I say gwd not gdm :)

---

### Post by apollothethird on 2010-11-23
> **koleoptero said:**
> Well sorry for the tons of off-topic replies, I'm glad I at least helped you learn about a couple of tools. :)

Also in that last post I say gwd not gdm :)

Hi, Koleoptero.  Your post, as well as all the post, have been very helpful.  I have found them to be very much on topic.  While there doesn't seem to be a public theme editor available for the gnome desktop theme (or one that anyone appears to know of) the various method of tweaking the theme and environment is invaluable to me.

I really appreciate all the input.

Thanks also for clarifying my misread of your gwd.  I find the options you mentioned under the gwd.  The options confirms as I mentioned that the opacity if 1.

Many thinks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by koleoptero on 2010-11-23
> **apollothethird said:**
> Hi, Koleoptero.  Your post, as well as all the post, have been very helpful.  I have found them to be very much on topic.  While there doesn't seem to be a public theme editor available for the gnome desktop theme (or one that anyone appears to know of) the various method of tweaking the theme and environment is invaluable to me.

I really appreciate all the input.

Thanks also for clarifying my misread of your gwd.  I find the options you mentioned under the gwd.  The options confirms as I mentioned that the opacity if 1.

Many thinks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Well the theme editing in gnome is mostly done by editing the appropriate text files. It's not hard to understand if you have some basic experience with coding, at least if you just want to change some aspect of a theme.

But it's easier to go to gnome-look.org and install a theme you like better. There are various gtk 2.0 themes that look great, as there are metacity themes too.

All the themes you install will be either in your /home/*your_username*/.themes/ folder, or in the /usr/share/themes folder if you installed them with some script or ppa or .deb file. You can just delete them drom there if you want, or go inside its files and tinker with it. If anything goes wrong with tinkering then just change theme and you're fine. :)

---

### Post by apollothethird on 2010-11-23
> **101011010010 said:**
> Hi again,
I don't really use the ~/.themes & /.icons folders, I thought that items placed in them would over-ride the usual themes aswell. 
Just a thought, I wonder if having Dust in two places is causing the problem.
If you goto ~/.themes and rename the Dust folder Dust-MM. Now open Dust-MM, right click on the Dust file,choose Properties, open the Permissions tab and put a tick in the "Allow executing file as program" box (this allows us to open the file Dust with Gedit).

Now open Dust file with Gedit and change the name to Dust-MM where required. It should look something like this:-
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Dust-MM
Comment=Ubuntu Dust-MM theme
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Dust-MM
MetacityTheme=Dust-MM
IconTheme=Humanity-Dark
CursorTheme=DMZ-White
ButtonLayout=maximize,minimize,close:
```Now hopefully the Dust-MM should work. Don't forget to make sure the change that you want is in the ~/themes folder.:)
If not I'm having a look myself,thought it might help in the future. So if this doesn't work let us know and maybe somebody with more knowledge might be able to help.

When you go into Appearances Dust-MM appears and can be selected.

A.

Hi, A.  Your method worked!  I had a lot of problems.  I don't know what caused the problems.  But for a long time it didn't work.  I kept going over the steps, and eventually the ability to change themes stopped working.  No matter which one I selected, the theme didn't change.

On a new day, I rebooted the machine and voila, it worked!  The local per-user configuration works.  I'll now change the /usr/share/themes/Dust one back to the backup configuration.

Thank!

While I was hoping to locate an editor, this workaround solves my immediate issue (to be able to read the inactive title windows).  I'll mark the topic as solved.  If I discover a theme editor, I'll come back and update the topic.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2010-11-23
> **koleoptero said:**
> Well the theme editing in gnome is mostly done by editing the appropriate text files. It's not hard to understand if you have some basic experience with coding, at least if you just want to change some aspect of a theme.

But it's easier to go to gnome-look.org and install a theme you like better. There are various gtk 2.0 themes that look great, as there are metacity themes too.

All the themes you install will be either in your /home/*your_username*/.themes/ folder, or in the /usr/share/themes folder if you installed them with some script or ppa or .deb file. You can just delete them drom there if you want, or go inside its files and tinker with it. If anything goes wrong with tinkering then just change theme and you're fine. :)

Thank.  It appears that we were typing the same conclusion at the same time.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

