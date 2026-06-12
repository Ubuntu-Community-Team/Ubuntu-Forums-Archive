---
title: "How to create a top-level menu (above the existing menus) in Ubuntu 10.04?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by rocksockdoc on 2010-08-27
**How do we create a TOP-LEVEL menu** (above or even with "Applications") in Ubuntu 10.04?

When I edit "*System->Preferences->Main Menu*", I can easily add a new menu item **BELOW** one of the 6 "Applications" sub categories (i.e., **below** "Accessories", "Graphics", "Internet", "Office", "Sound & Video", & "Universal Access); but how do we add a menu **at or above** the "Applications" category.

For example, I prefer to have a menu at the same level of "Applications" named, say, "My Programs". Or, if that is too difficult to do with Ubuntu, at least have my own menu system just below "Applications", i.e., add a 7th category called, say, "My Programs". 

Then, below "My Programs", I could have my logical menu hierarchy, e.g., 
My Programs -> Archivers -> {Zip, PDF, RAR, etc.}
My Programs -> Browsers -> {Firefox, Tor, Chrome, etc.}
My Programs -> Calendars -> {Sunbird, QOrganizer, Evolution, etc.}
etc.

There MUST be a way to add a user-defined set of menus at the top level; but what is it?

[B]How do we add a menu either at the "Applications" level or just below it?

HERE IS A PIC OF THE DESIRED RESULT (on Windoze):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169583&stc=1&d=1284588772[/IMG]
[/B]

---

### Post by Frogs Hair on 2010-08-28
You could install the GnoMenu  and add desired apps to favorites.   [http://gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93056](http://gtk-apps.org/content/show.php/GnoMenu+-+consolidated+menu+for+gnome?content=93056)

---

### Post by kerry_s on 2010-08-28
what? you can drag & drop where you want or use the up/down buttons, so i'm not sure what your saying.

---

### Post by rocksockdoc on 2010-08-28
> **kerry_s said:**
> what? you can drag & drop where you want or use the up/down buttons, so i'm not sure what your saying.

Maybe I'm wrong, but the drag-and-drop and up-down is constrained BELOW the second level (essentially making it the third level only that is easily customizable with drag and drop). 

The first level is "Applications"; the second level is "Accessories" (or any of the others mentioned), while only BELOW that, at the third level, is the drag and drop working for me.

Or, maybe I misunderstand? (I hope so.)... 

Will try the second suggestion but figured I'd respond to this one first. 

Thanks for the help... it might be that I don't understand ...

---

### Post by kerry_s on 2010-08-28
actually i don't understand.

applications is the menu. which is on the bar. are you trying to creat a menu like that?

if so, right click the panel-> add to panel-> application launcher
drag the whole menu you want to the panel

---

### Post by rocksockdoc on 2010-08-28
> **kerry_s said:**
>  right click the panel-> add to panel-> application launcher
drag the whole menu you want to the panel

I'm glad you showed me how to "copy" a top-level menu item because it allows me to create a new top-level menu, albeit if it's a copy I can change it (which is what I want to do); but if it's a link to the original menu, e.g., "Accessories", then the idea won't be useful.

I don't mind if starting with a "copy" of a menu is how I create the TEMPLATE menu; but then I want to make it my own, e.g., "My Accessories", and then put in it a sub menu (Archivers, Browsers, Calendars, Databases, Editors, Financials, Games, etc.) and then below that sub menu are the actual links to the executables (e.g., "Accessories->Editors->Photo->{Gimp, F-Spot, Fotoxx, etc.}.

The point is I have a well thought out menu system that I wish to implement and it's not (yet) obvious to me the proper way to implement a well thought out menu hierarchy. Thanks for your tip though as it helped me create a top level menu (now the problem is creating the menu hierarchy below that top level).

---

### Post by kerry_s on 2010-08-28
no, i only used accessories as a example. use main menu to create the menu you want, use the application launcher to add it to the panel.

---

### Post by rocksockdoc on 2010-09-01
> **kerry_s said:**
> no, i only used accessories as a example. use main menu to create the menu you want, use the application launcher to add it to the panel.

Thanks Kerry.
I don't know what "main menu" is nor what the "application launcher" is, so that sentence won't make any sense to me until I do some more research.

You'd think this would be intuitive ... creating a menu from scratch ... but it's not so I'll need to do more research. It's too bad it's not as easy as in Windows where all you do is create a series of cascading folders in a certain directory and voila! 

You have a menu. 

At the bottom of those cascading folders, you simply add a link to the executable and you're done. 

It apparently isn't anywhere near that easy in Ubuntu ... so I'll do some more digging.

thanks anyway.

---

### Post by kerry_s on 2010-09-01
i'm sure you'll figure it out, i moved to mac os x so i can't do detailed pics for you.
i'm taking a ubuntu break till unity netbook is ready.

---

### Post by StrungOut101 on 2010-09-01
> **kerry_s said:**
> actually i don't understand.
 
applications is the menu. which is on the bar. are you trying to creat a menu like that?
 
if so, right click the panel-> add to panel-> application launcher
drag the whole menu you want to the panel
 thanks :) helped me

---

### Post by rocksockdoc on 2010-09-15
> **StrungOut101 said:**
> thanks helped me

May I see a screenshot of your new menu?

What I'm trying to have is "Applications" and another menu right next to it (e.g., "My Applications".

For example:
My Applications->Archivers->{various archivers like gzip, etc.)
My Applications->Browsers->{various browsers like chrome, etc.}
My Applications->Calendars->{various calendars like sunspot, etc.}
My Applications->Databases->{various databases like google earth etc.}
My Applications->Editors->{various editors like vi, etc.}
My Applications->Finance->{various financial programs like ttax, etc.}
My Applications->Games->{various games like supermario, etc.}
etc.

In "Applications", I let the OS determine what goes where; but in "My Applications", I control it myself, making sure it makes sense to me.

For example, in "Applications", they have the screenshot tool in "Accessories" yet the editing tool in "Graphics" and they have all the editing tools munged up in "Graphics". It's a mess. 

I learned from the Windoze side to not even try to clean up messy operating system defaults. You just leave them alone. What you do is make a parallel menu which the operating system doesn't touch and that you control.

So I'd have, for example:
My Applications->Editors->Text Editors -> vi, vim, gedit, etc.
My Applications->Editors->Picture Editors -> F-Spot, Gimp, X-Paint, etc.
My Applications->Editors->Video Editors-> (I'm not sure what video editors)
etc.

[B][COLOR=DarkRed]To anyone who says this is easy and they've done it, can you show me a simple screeenshot of your "My Applications" hierarchical menu next to your "Applications" menu at the top level?

[COLOR=Black] HERE IS A PIC OF THE DESIRED RESULT (this is on Windoze):[/COLOR]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169583&stc=1&d=1284588772[/IMG]
[/COLOR][/B]

---

### Post by kerry_s on 2010-09-15
:lolflag: is it really that big of a deal?

i'm not using any panel menu.

---

### Post by rocksockdoc on 2010-09-15
> **kerry_s said:**
> i'm not using any panel menu.

Yes. It's a very big deal.

For the past decade, I've had a wonderfully organized file system hierarchy.
I install my programs into that hierarchy, I save my installation zip files into the same hierarchy (different location, same hierarchy), I modified the menus so that they reflected the same hierarchy. All three locations are the same hierarchy. One that makes sense. AT least it makes total sense to me (which is all that matters).

My hierarchy doesn't use brand names. It doesn't use "accessories" or "system" or "misc" or "util" or any of those ubiquitous yet meaningless catch-all categories for people who can't figure out what a program actually does. 

Anyway, yes, it's a big deal. 

Here is a screenshot of my current menu (which is the Ubuntu default). What I'm trying to do is create a single menu like I did on the Windoze side of the world. It shouldn't be all that hard to do (it's just a menu for heaven's sake). 

How hard can it be to create menus on Ubuntu? I'm missing something very very basic I'm afraid. 

Anyway, I do appreciate your help. Here is what I have on my screen right now:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169584&stc=1&d=1284589961[/IMG]

---

### Post by rocksockdoc on 2010-09-15
To clarify the goal (which I can't imagine everyone not wanting but hey, that's just me):

A) In Windoze, the "Programs" menu soon becomes a mess because every program installs, shall we say, their crap, into that menu. I used to fight all that crap, but, after a while, I just gave up. I leave the "Programs" menu all alone.  

B) I simply create my own top-level menu at the same level as the crapped'up Programs menu. My menu system has a hierarchy such that an editor of pictures is in a different hierarchy than an editor of videos but they're both editors.

My Apps -> Editors -> Picture -> {Gimp, XPaint, etc.}
My Apps -> Editors -> Video -> {VideoEdit, XVideo, etc.}
My Apps -> Editors -> Text -> {vi, vim, gedit, etc.}
My Apps -> Editors -> Html -> {Frontpage, Backpage, etc.}
My Apps -> Editors -> Hex -> {hexedit, edithex, etc.}

All I want is my one menu in Ubuntu 10.04. It shouldn't be difficult at all. I should just edit a configuration file or a set of pointers such that I can create a hierarchy:

My Apps -> Archivers -> {gzip, arcc, etc.}
My Apps -> Browsers -> {Firefox, Chrome, Safari, etc.}
My Apps -> Calendars -> {Sunfox, Sunbird, calmanager, etc.}
My Apps -> Databases -> {Google Earth, MapQuest, etc.}
My Apps -> Editors -> {Picture, Video, Text, Html, Hex, Pdf, etc.}
etc.

[SIZE=2][COLOR=DarkRed]**Can you help me find where I can find a tutorial for creating such a simple top-level menu in Ubuntu?**[/COLOR][/SIZE]

Note: [SIZE=1]*Please don't let the fact the menus are on the side confuse you as there is a very good reason for side menus (up/down real estate on a compact portable PC is precious and menus should not impinge on that important space).*[/SIZE]

---

### Post by kerry_s on 2010-09-15
i've always hated deep menus like that.

what i use to do was just drop everything to a side panel.

like this. simple 1 click access.

---

### Post by rocksockdoc on 2010-09-15
> **kerry_s said:**
> what i use to do was just drop everything to a side panel

Of course menus are "to each his own" so you're welcome to put everything on a side panel. 

But I have probably at least a hundred programs stored, and I know where every single one of them belongs. I couldn't fit them on a panel and besides, panels take too much space on my tiny laptop screen (that's why my menus are on the side in the first place). 

Nobody could fit hundreds of programs on a side menu and make any sense of it. Just my editor menu has probably twenty five programs alone. My hardware menu has another fifty. (Actually I think I have something like 200 programs installed.).

Anyway, the point is that I can keep track of all my installed programs perfectly easily because they're all in a logical location. They're not stored by brand name nor in a useless clump like "utilities". 

They are exactly where they belong. By function.

Anyway, the exact nature of the menu system isn't really what we need to argue here.

In Windoze, you can trivially create a menu hierarchy with a batch file, e.g., 
```

 mkdir -p /menu/archiver/{winzip,izarc,7zip}
 mkdir -p /menu/browser/{chrome,firefox,ie,safari}
 mkdir -p /menu/cleaner/{ccleaner,avast,avg,swb}
 mkdir -p /menu/database/{google_earth,magellen,skywatch}
 mkdir -p /menu/editor/text/{vi,vim,nedit,notepad}
 mkdir -p /menu/editor/pic/exif/{exifer,noexif,exify}
 mkdir -p /menu/editor/pic/touchup/{blemify,cleanup,makeup}
etc.

```And then you just copy in the symbolic links to the executables into the appropriate menu directories {which I've symbolically shown with the braces}.

So there MUST be something similar for creating entire menu hierarchies on Ubuntu, right?

QUESTION:
[COLOR=DarkRed]**On Ubuntu, where is this MENU HIERARCHY that I can create with a text file?**[/COLOR]

---

### Post by QLee on 2010-09-16
rocksockdoc, I do understand what you are stating, you want things organised the way you are used to dealing with them and that seems reasonable. I do know that because of inherent differences between Windows and Ubuntu it sometimes can make sense to adapt ones personal style to a new choice of operating system. It does take a while to learn new things.

When I read your question, and I don't know the answer, I gave it some thought. I know from the GNU/Linux filesystem hierarchy that, /etc,  Contains  configuration  files  which  are local to the machine, So, I looked in there and found a folder (directory) called /menu. See if your install has a folder /etc/menu, and, if it does, does it also have a readme file in the folder? If it does, is there anything useful for you in it? If not, does usr/share/doc/menu, have anything useful?

---

### Post by kerry_s on 2010-09-16
> In Windoze, you can trivially create a menu hierarchy with a batch file, e.g., 
Code:
 mkdir -p /menu/archiver/{winzip,izarc,7zip}
 mkdir -p /menu/browser/{chrome,firefox,ie,safari}
 mkdir -p /menu/cleaner/{ccleaner,avast,avg,swb}
 mkdir -p /menu/database/{google_earth,magellen,skywatch}
 mkdir -p /menu/editor/text/{vi,vim,nedit,notepad}
 mkdir -p /menu/editor/pic/exif/{exifer,noexif,exify}
 mkdir -p /menu/editor/pic/touchup/{blemify,cleanup,makeup}
etc.
And then you just copy in the symbolic links to the executables into the appropriate menu directories {which I've symbolically shown with the braces}.

i think i know a way you can do that. install "file-browser-applet" add it to your panel, create your "menu" folder & sub folders.
then just "middle click hold drag & drop-> link here" your applications(/usr/share/applications) to the folders you want.(a little tip: if you hold ctrl & select your programs, you can drag them all in 1 go)
add the path to the applet.

this is just a quick slap together, to get a pic for you.

---

### Post by col48 on 2010-09-16
rocksocdoc
Fully sympathise.  I don't organise things in exactly your way but mine has a similar philosopy.  In Windoooos, I left directories like Programs and MyDocuments empty (similarly Inbox and Outbox and Sent Mail in Outlook Express) and moved things elsewhere - which also meant it was easy to see when files had been put there "by default".  Ubuntu is more logical so I am less radical but I am still more inclined to find (non-executable) files by nautilus than by any other method.  I don't seem to lose files, as some people do!

It's an instance of what I call ops - Other People's Software.  Somehow it never seems to be quite as sensible as I would be:  see, there's not even a smiley which has it's tongue in its cheek to put here!

All power to your elbow!

---

### Post by rocksockdoc on 2010-09-16
> **QLee said:**
> I do understand what you are stating, you want things organised the way you are used to dealing with them

Good observation. But this is only true if I delete the second part of the sentence, i.e., "you want things organized".

It really doesn't matter what I'm used to (I've been on operating systems since PDP 11 days and IBM 1130's). I'm used to a lot. I've learned over the decades that I should know where EVERY program & data file resides that I put on that system willingly.

< rant > All I want is what everyone should want ... which is a menu system that fits my a logical hierarchy (and, yes, having a category such as "Accessories" or "Utilities" or "Misc" is, IMHO, a copout, best left for those who aren't concerned about organizing a program menu by what the program actually does). < / rant >

I thank you for your help!

I will take ALL your advice and follow up as that's the only way we're going to solve this problem, for me, and for anyone else who wishes to maintain a logical menu hierarchy (the actual logic doens't matter as that should be left up to the user ...).[/quote]


> It does take a while to learn new things.
Yes. Indeed. I've learned dozens of OS's over time. But nowadays, it should be almost trivial to create and maintain a menu of your own choosing. I'm positive Ubuntu can do it. I realize MOST people don't do it, which is why the knowledge is a bit hard to come by ... but when I finally do figure it out (with your help), I'll write up a tutorial for others to benefit, as always.

>  See if your install has a folder /etc/menu, and, if it does, does it also have a readme file in the folder? 

The only thing in that folder is the following README:

```

README:
In this directory, the system administrator can install menufiles to
override the menu files provided by Debian in /usr/lib/menu, /usr/share/menu
and /usr/share/menu/default.

The filename should be the name of the package that it is overriding,
and may contain as many lines and menu entries as necessary.

Please run 'update-menus' after changing or adding files.

For more info, please read /usr/share/doc/menu/html.

```

In /usr/share/doc/menu/html is an index.html of the "Debian Menu System" which I will read after I post this response. Thanks for the tip ... 

> does /usr/share/doc/menu, have anything useful?

In there are some files, and this README:
```

README - menu
-------------

menu is a menu-generator originally made for Debian. It provides an
update-menus program to generate menus for different providers of menus
(both window managers and console applications like pdmenu).

Menu files are placed in /usr/share/menu by packages. update-menus then reads
these files and passes them to install-menu which generates a menu specified
by a menu-method (placed in /etc/menu-method).

The full documentation for menu can be found in doc/menu.txt.gz or
doc/menu.html/

```

So, while I was hoping for a tutorial on how to create your own menu outside of the "Applications" menu (so that the OS won't mess it up), it looks like I have to start at ground zero, figure out how the menus work, and then create my own.

Wish me luck! :)

---

### Post by rocksockdoc on 2010-09-16
> **col48 said:**
>   In Windoooos, I left directories like Programs and MyDocuments empty 

Exactly what I did! Actually, a decade or so ago, I tried to relocate "My Programs" to, for example, "c:\bin" since I was well versed in SunOS at the time (having since become rusty). But after a few years of trying to CONTROL the horrid Windows "My Documents" and "My Programs" mess, I just decided to NEVER install anything in either of those locations, and to just let them fill up with inadvertent crap. 

Since then, I've had MANY PCs, and migrating data and programs is a cinch since I can wholly ignore the crap in "My Documents" and in "Program Files" (none of which I installed) and even in the huge "Windows" folder. 

I also follow this philosophy with the "Programs" menu. So many installation programs put crap into that menu, and organize themselves by brand name (what an idiotic system) that I just don't even look at or touch the "Programs" menu. It's trivial (in Windoze) to create a separate menu hierarchy (they're just folders) pointing to executables (they're just symbolic links, i.e., shortcuts) that it's a crime if anyone doesn't have their own menu system in Windoze.

In summary, it's actually VERY EASY to manage Windoze if you first create:
```

C:\data (put all your data files here in your own organized hierarchy)
[COLOR=DarkRed]C:\repository (put all your installation zip files here for backup & re-use as needed)
C:\menu (put your own logical menu system here; they're just folders)
C:\bin (put your programs here, in a logical functionally based organization)[/COLOR]

```

Bear in mind the wonderful benefit:
- The hierarchy of repository is the same as bin is the same as menu!

This wonderful functional hierarchy can last you for decades (updated over time), and many many operating systems. It really doesn't matter WHAT functional organization you use ... all that matters is you keep your installers, your menus, and your binaries in that organizational system and you will live happily ever after. :)

> I don't seem to lose files, as some people do!Me too! I never lose program binaries or data files. Not because I have a good memory but because I know where, functionally, I would put them. THAT's the benefit of a logical system. Linux (like UNIX, SunOS, Solaris, etc.) has a vastly more logical file system than Windoze does, but, still, that default menu is illogical as all hell.  :(

It would be great if we could just create a folder hierarchy (or a text file) and that becomes a new menu system (alongside the old menu system). 

**All it needs other than the folder hierarchy or text file is the final pointer to the symbolic link which is the executable to bring up at the end of the menu.**
[SIZE=2][B][COLOR=DarkRed]
Having a locial menu-editing system is a pretty simple concept ... So simple and logical ... that I must be optimistic and BELIEVE that it exists on Ubuntu. I just have to find it! :)[/COLOR][/B][/SIZE]

---

### Post by rocksockdoc on 2010-09-16
I should summarize:

I'm not looking (any more) to edit the EXISTING Ubuntu menu structure (as that seems to be overly complex and there is little experience in doing that since most users apparently don't have their own logical program hierarchy to fit the menu to).

What I simply want to figure out is how to create a new menu, next to the existing menus, that DOES have my logical menu hierarchy.

I'm optimistic that we can figure this out and anyone who follows will benefit.

---

### Post by col48 on 2010-09-16
ref last sentence of post 20....
No problem.  Good luck.

I remember the 1130 too.  I think it had 8k of memory of which a good chunk was permanently taken up by the OS and the Fortran II compiler.  It was amazing what could be done with what was left.  Those were the days!

---

### Post by QLee on 2010-09-16
[QUOTE=rocksockdoc]...
Yes. Indeed. I've learned dozens of OS's over time. But nowadays, it should be almost trivial to create and maintain a menu of your own choosing. I'm positive Ubuntu can do it. I realize MOST people don't do it, which is why the knowledge is a bit hard to come by ... but when I finally do figure it out (with your help), I'll write up a tutorial for others to benefit, as always.[/QUOTE]
OK, with that level of experience, you are well aware that things that are, not trivial when they are different from what you already know, sometimes become trivial when you have knowledge and experience.



[QUOTE=rocksockdoc]The only thing in that folder is the following README:
...
For more info, please read /usr/share/doc/menu/html.
[/code]In /usr/share/doc/menu/html is an index.html of the "Debian Menu System" which I will read after I post this response. Thanks for the tip ... 
....[/QUOTE]

Well it did show you how the menu is generated.

You asked for a way to do it and I tried to give you the documentation you need to learn. I hear that you want someone to give you a step-by-step that gives you the kind of custom menu you want but, as you have found out, it may not yet exist. I look forward to reading the tutorial that you'll now produce.

rocksockdoc, you're not the only person around here with years of experience and some of us don't consider the particular "lack" you have detailed to be a real problem for the way we do things, I have never needed to organise as you have detailed. Of course, with GNU/Linux a user can choose to do things many ways, some require learning first.

A small piece of advice, when posting for help try to avoid rants as much as possible, many times the people who could help you most will just pass on a thread where the poster is ranting about how Ubuntu can't do "xxx". It is very common for new users to keep referring back to how Windows does things, it isn't necessarily better, usually it's just different but help threads can become bogged down when people start arguing about better and best.

---

### Post by QLee on 2010-09-16
[QUOTE=rocksockdoc]...
**All it needs other than the folder hierarchy or text file is the final pointer to the symbolic link which is the executable to bring up at the end of the menu.**[/Quote]
Perhaps something like the, !include, in the documentation?
[SIZE=2][B][COLOR=DarkRed]
[/COLOR][/B][/SIZE][QUOTE=rocksockdoc][SIZE=2]**[COLOR=DarkRed]Having a locial menu-editing system is a pretty simple concept ... So simple and logical ... that I must be optimistic and BELIEVE that it exists on Ubuntu. I just have to find it! :)[/COLOR]**[/SIZE][/QUOTE]
Did you look through the various packages available to Ubuntu but not included by default because of CD size limitations?

---

### Post by rocksockdoc on 2010-09-19
**What I'm looking for is a "hello world" style tutorial for creating your own logical menu.**

Once any of us have that, we can efficiently modify it to our heart's content.
*Since none seem to exist, I'll kick it off (but I'm still far from the final goal).*

[SIZE=3][COLOR=DarkRed]**Here is a simple-to-follow cut-and-paste DIY to create a new menu item in Gnome**[/COLOR][/SIZE]

* Again, this is nowhere near where we need to be but it's an initial start.*

```


0. Resize any image to 48x48 pixels, e.g., with Gimp, saved as /tmp/foo.png:
   GIMP: Image->Scale Image->48x48
   GIMP: File->Save As->/tmp/foo.png

   This picture will be your menu item icon.
 
[SIZE=1]   *See note 1 about acceptable file types.*[/SIZE]

1. Copy that png icon to the pixmaps directory:
   $ sudo cp /tmp/foo.png  /usr/share/pixmaps/.

2. Create a script, /tmp/foo.sh that edits your foo list, for example:
   $ vi /tmp/foo.sh

    pushd ~/tmp
    vi ~/tmp/foo.txt
    popd

3. Copy that script to a location in your path, e.g.:
   $ sudo cp /tmp/foo.sh  /usr/local/bin/.
   $ sudo chmod 755 /usr/local/bin/foo.sh

4. Create a new text file for your menu entry, saved as /tmp/foo.desktop
   $ vi /tmp/foo.desktop

    [Desktop Entry]
    Encoding=UTF-8
    Name=Run the foo program
    Comment=This is the foo program 
    Exec=/usr/local/bin/foo.sh
    Icon=foo
    Terminal=true
    Type=Application
    Categories=Application;Office;

[SIZE=1][I]    See note 2 about acceptable file names.
    See note 3 about the severe limit on logical categories.[/I][/SIZE]

5. Place that new text file into the menu directory:
   $ sudo cp /tmp/foo.desktop  /usr/share/applications/.

6. OPTIONAL: If required, kill and restart your menus:
   $ sudo killall gnome-panel

7. You should now see your icon and a new menu entry on the Gnome panel:
   Applications->Office->[ICON] Run the foo program

8. Hovering over that entry should display your comment:
    "This is the foo program".

9. Clicking on that menu item should execute foo.sh:
    This should bring up foo.txt in the vi text editor.

10. Modify the various parts to creates (very limited) menus as needed.


```NOTES:

[LIST]
[*] Note 0: If you organize your menus differently than Gnome defaults (and  you almost certainly do), you'll need much MORE of a head start than this simple DIY.
[/LIST]
 

[LIST]
[*] Note 1. The pixmap file must be a PNG file.
[/LIST]
 

[LIST]
[*] Note 2: Strangely, the file name is apparently restricted to all lowercase characters & it must end with ".desktop".
[/LIST]
 

[LIST]
[*] Note 3: The Gnome menu system is apparently severely limited to just these categories:
[LIST]
[*]          Applications->Accessories === Application;Utility;
[*]          Applications->Games === Application;Game;
[*]          Applications->Graphics === Application;Graphics;
[*]          Applications->Internet === Application;Network;
[*]          Applications->Office === Application;Office;
[*]          Applications->Programming === Application;Development;
[*]          Applications->Sound & Video === Application;AudioVideo;
[*]          Applications->System Tools === Application;System;
[*]          Applications->GNOME === Application;GNOME
[*]          Applications->GTK === Application;GTK
[*]          Places->??? where is this located ???
[*]          System->Preferences === Settings;
[*]          System->Administration === Settings;System;
[/LIST]
 
[/LIST]
 
[SIZE=3][COLOR=DarkRed]**Still needed:**[/COLOR][/SIZE][SIZE=3]
A) How to add **hierarchy**, [SIZE=2]e.g., Applications->Graphics->Editors->foo.sh[/SIZE]
B) How to add **categories**, [SIZE=2]e.g., Applications->Editors->{Graphics,Text,Video,etc.}[/SIZE]
C) How to a add **top-level menu**, [SIZE=2]e.g., Apps->{Archivers,Browsers,Calendars,etc.}[/SIZE][/SIZE]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=169974&stc=1&d=1284915868[/IMG]

---

