---
title: "No Ctrl + X Command?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Zeptinune on 2010-02-22
Sorry if this is the most noobiest question you've ever seen here but there doesn't seem to be a Ctrl + X command in Linux..

I can do a Ctrl + C & Ctrl + V.
Both work fine, so I can copy and paste, but I can't cut with just a keyboard shortcut. Is 'Cut' different in Linux? I also did a google and a search here but no one has had to ask the question ever hahahaa!

I guess there is a first for everything. Thanks for any and all help.

---

### Post by kellemes on 2010-02-22
Ctrl-X works for me..
have you maybe changed your keyboard-shortcuts or something?
From what situation or software-environment are you trying to cut?

---

### Post by Zeptinune on 2010-02-22
Umm well I am using a Finnish Keyboard.
I haven't changed any of the shortcuts as far as I know. It has just never worked. Don't know why its never worked and copy and paste have.

Umm I'm just trying to cut and paste a folder to another folder. (Well that is usually the case but sometimes I try to cut and paste text in documents) I guess I just got fed up with it not working and came here.

I don't know if or why a Finnish keyboard would make a difference as to why just 'cut' isnt working.

---

### Post by lockalidiot on 2010-02-22
I also use Finnish keyboard and ctrl+X works just fine.

---

### Post by Zeptinune on 2010-02-22
Hmm that's odd :/
Well I haven't messed with any of the shortcuts.. and the others work ok.
*Checks System > Preferences > Keyboard shortcuts*

None of the commands are in there..

Is there a terminal command for binding a keystrokes to 'cut' ?

---

### Post by kellemes on 2010-02-22
> **lockalidiot said:**
> I also use Finnish keyboard and ctrl+X works just fine.

Maybe you can help @Zeptinune ;-)
1- You have a physical Finnish Keyboard? So.. the placements of keys on this keyboard is Finnish?
2- Have you setup your system to use a Finnish Layout?

---

### Post by lockalidiot on 2010-02-22
Probably there is. Now we have to wait that one of these gurus stops by and tells us noobs what it is.. :p
I propose that in the mean time you try to set the shortcut via System -> Preferences -> Keyboard shortcuts.

By the way, I see you have Finland/Australia as your location. Do you speak and write finnish, or are you just related to some?

EDIT: Sorry kellemes, we were writing at the same time.

1. Yes.
2. Yes.

---

### Post by mcduck on 2010-02-22
Have you checked that you have a correct keyboard *model* in the System/Preferences/Keybaoard?

It's not enough to have just the layout you wish to sue, if the keyboard model that's set doesn't have the right amount of keys, for example. (if you can't find the exact mdel you ave in the list, "Generic 105-key" works fine for Finnish layout.

Also, does the X key itself work?

..and finally, are yoy sure you haven't set the Ctrl-X as keyboard shortcut either in System/Preferences/Keybaord Shortcuts or in Compiz settings+ If you set such shortcut it will override any default purpose for the same keys... Checking Gnome's own keybaord shortcuts should be simple, but for Compiz shortcuts you might just want to test if switching to Metacity solves the problem (press Alt-F2 and run "metacity --replace"). If that solves the problem then go through all the Compiz plugin settings to find which one has the shortcut defined (If switching to Metacity makes no difference then just Alt-F2 and run "compiz --replace" to get Compiz running again).

---

### Post by Zeptinune on 2010-02-22
In the keyboard shortcuts menu there isn't any shortcuts that have any of the commands like Ctrl + V for paste etc. It's just got a bunch of other shortcuts there.
My keyboard layout is set to Generic 105-key (Intl) PC and the layout is set to Finland.
Every key works fine, without any problems at all, this is the only command that doesn't seem to want to work at all. It worked fine on windows, but when I swapped over to ubuntu it doesn't want to work now.

Off the record, I am an Australian, I have no blood ties or any ties for that matter to Finland. Ever since I was 8 I sort of fell in love with Finland from a tv commercial. Cliché I know. I've been learning Finnish since I was 10. My parents have supported me for the last 9 years, I learned in school for 4 years and then studied like mad for the last 5 years self teaching and just watching lots of movies and reading lots of books. Helmiä ja Sikoja etc. :)

I have a house in Finland that I am renting and I travel back and forth between Finland and Australia. At the moment I am in Australia, so I set my status to Finland/Australia because sometimes I am there. On another forums an Admin got 'annoyed' (for lack of a better word) that I set my status to Finland and that my I.P showed I was in Australia. After coming back to Aust. It's complicated.

Sorry if that history lesson bored you. :D

I checked a few more settings and well I can't seem to find anywhere to assign a new key combination to cut. Keyboard shortcuts doesn't show me anything and as far as I know my keyboard is set up correctly. EDIT: X key works fine :D no problems or issues with any of my keys. My computer is quite new. I got it from Finland last summer :)

---

### Post by mcduck on 2010-02-22
> **Zeptinune said:**
> In the keyboard shortcuts menu there isn't any shortcuts that have any of the commands like Ctrl + V for paste etc. It's just got a bunch of other shortcuts there.
My keyboard layout is set to Generic 105-key (Intl) PC and the layout is set to Finland.
Every key works fine, without any problems at all, this is the only command that doesn't seem to want to work at all. It worked fine on windows, but when I swapped over to ubuntu it doesn't want to work now.

There isn't even supposed to be any options for copy/paste etc in the Keyboard Shortcuts.

What I meant that check that you haven's set any *other* shortcut to use the Ctrl-X combination. Because doing that would override the default "Cut" maning of the key combination.

Same applies to keyboard shortcuts defined for Compiz, if you set any shortcut in Compiz to use the Ctrl-X combination then that combination won't work for cutting any more.

(your keyboard layout itself is just fine, simply the fact that the X key alone works is enough to tell that for sure)

---

### Post by Zeptinune on 2010-02-22
Well I just did a really good look around my computer and I can't find anything. In that keyboard shortcuts I can't find anything there that has Ctrl + Anything.
It's all Ctrl + Alt + xxx etc.

Or Alt + xxx or something. I don't know really any other way at all to check if anything has assigned itself to Ctrl + X.

However now (without seemingly making any change on anything) I can now cut and paste text in a document. (Before I couldn't). But I still cannot cut and paste around files or folders for that matter.

Ok tested again and I can use the cut command where applicable inside of a program but for some reason it just doesn't work when I try and cut and paste a file or folder...
Computers are so strange sometimes..

Apart from setting my keyboard layout upon installation I have done nothing to modify the keyboard options at all.

---

### Post by Sir Jasper on 2010-02-22
Hi,

It doesn´t work for me either on files or folders (mcduck will surely know if it is supposed to work that way). So I right click to cut or copy or paste those.

Glad your main problem seems to be mysteriously resolved. 

My regards

---

### Post by mcduck on 2010-02-22
> **Sir Jasper said:**
> Hi,

It doesn´t work for me either on files or folders (mcduck will surely know if it is supposed to work that way). So I right click to cut or copy or paste those.

Glad your main problem seems to be mysteriously resolved. 

My regards

I must admit that I didn't *know* if cutting files in Nautilus works or not, but I just tried it and it sems to work for me...

I don't really knoe why it wouldn't work if you even got it working in other sitautions. But as a work-around, you can drag a file with middle mouse button and you'll get a popup dialog asking if you wish to copy, move or link the file to new location. So that would give you the same result as cut/paste does.

---

### Post by Sir Jasper on 2010-02-22
Hi mcduck,

Thank you for your reply which is of interest to me and may help Zeptinune. I use Thunar and I am pleased with the way it works, but I&#7743; always happy to learn from you. You have the knack of giving detailed explanations which you manage to pitch at my level of comprehension.

My regards

---

### Post by mcduck on 2010-02-22
> **Sir Jasper said:**
> Hi mcduck,

Thank you for your reply which is of interest to me and may help Zeptinune. I use Thunar and I am pleased with the way it works, but I&#7743; always happy to learn from you. You have the knack of giving detailed explanations which you manage to pitch at my level of comprehension.

My regards

your welcome. :)

I've heard a saying that if you can't explain something in easy to understand way then you don't really understand it yourself either.. Makes sense to me, so I try to keep things simple (as long as you don't mind some typos.). Although it could just be my limited English skills... ;)

Zeptinune, I tried searching all Nautilus settings in gconf and couldn't find anything that could affect cut/paste..  Does it work if you do it from the right-click menu or through the Edit-menu?

---

### Post by Zeptinune on 2010-02-23
It sure does work from the right click menu just not from the shortcut keys. I don't know why Nautilus is being stubborn. I've done some googling and I have found one such other post in another forums about this and there wasn't a single reply. It was 5 months ago on ubuntu 8.

It seems to be a shady error... I dare say could this just be a weird programming issue? A misfault of the Ubuntu distro devs :D?

---

### Post by lockalidiot on 2010-02-23
You probably just haven't sacrificed enough windows installation CDs to the spirits of Ubuntu... :P Or something... :D 

Seriously, thats a weird error.

---

### Post by Zeptinune on 2010-02-23
Aaahaha I hear that. I think I need to burn all my backups of Windows Xp cd's as well as my Vista and W7 ones :D I'll do that now.

Oh well. Don't worry about it guys, its not the end of the world. I'll just right click and do it.

---

