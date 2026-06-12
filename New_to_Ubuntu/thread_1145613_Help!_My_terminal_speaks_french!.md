---
title: "Help! My terminal speaks french!"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Mariane on 2009-05-01
Hi, 

I just did an upgrade and dist-upgrade. 
I lost my kde in the process and had to install 
it from gnome. Then KDE opened after a reboot and 
things don't seem too bad except my terminal was 
white on black and spoke french. 

I found how to set it back to black on white text. 
But not how to make it speak english. The rest 
looks OK (The "control center" is called 
"control center" and not "centre de control"). 

Mariane

---

### Post by sylvainrb on 2009-05-01
> **Mariane said:**
> Hi, 

I just did an upgrade and dist-upgrade. 
I lost my kde in the process and had to install 
it from gnome. Then KDE opened after a reboot and 
things don't seem too bad except my terminal was 
white on black and spoke french. 

I found how to set it back to black on white text. 
But not how to make it speak english. The rest 
looks OK (The "control center" is called 
"control center" and not "centre de control"). 

Mariane

Is the rest of KDE in French as well or is it just the terminal that is in French and the rest in English? I know there is an option at login to choose among many languages so try that and see what happened...

If you receive any system messages put their output in here and I can translate them for you...

Hope this helps a little :)

---

### Post by Mariane on 2009-05-04
The rest of kde is in English. Only the terminal 
speaks French. 

Example: I type
```
ls -zz
```
It says:
```
ls: option non reconnue " --zz "
Pour en savoir davantage, faites " ls --help "
```

OK, it means ls has no such option as --zz. I 
thought so. But some of the stuff is not that 
easy to understand, when it's in French... 

I am getting no particular error messages. 

Mariane

---

### Post by Vonnick on 2009-05-04
This would be a good opportunity to learn French! :guitar:

---

### Post by Didius Falco on 2009-05-04
Try this:

1. Open Terminal

2. Go to the **Terminal** menu (second menu from the right)

3. Click Set **Character Encoding/Add or Remove **(third choice down/bottom choice)

4. Change the language

5. Say "Au Revoir" to the French output

I hope this helps....

---

### Post by Malalo on 2009-05-04
> **Didius Falco said:**
> Try this:

1. Open Terminal

2. Go to the **Terminal** menu

3. Click Set [B]Character Encoding/Add or Remove
[/B]
4. Change the language

5. Say "Au Revoir" to the French output

I hope this helps....

This wont work as French has the same character encoding as English...
I did what you suggested and didn't find French anywhere in that list.
The problem is elsewhere.

---

### Post by Didius Falco on 2009-05-04
Hmmm - I am intrigued now. To the Google!!

What is it set on now? I'm using Unicode - UTF8 and it's in US English.

---

### Post by Mariane on 2009-05-04
I don't have these options, I have :
Settings / Encoding / 
Then a list of encodings. The one ticked is just 
called default. I'm using kde, maybe this is why 
I don't have the same options as you. 

The *menus* are in English. 

And it's not just the terminal. I installed 
gnusound because I couldn't get audacity to play 
a sound, and the *menu names* (top row) are in 
English while the *menu options* (when you click on 
a menu name) are in French. 

This is ***, excuse my French... 

Mariane

---

### Post by Malalo on 2009-05-04
Perhaps the Terminal is different in Gnome and in KDE.

Try searching [here]("http://docs.kde.org/kde3/en/kdebase/faq/configure.html#id2537826"), perhaps it will help...

---

### Post by LowSky on 2009-05-04
I have never heard of this before... it seems very odd indeed.

---

### Post by Didius Falco on 2009-05-04
This is a couple of years old, but it's worth a look:

[http://ubuntuforums.org/showpost.php?p=2282079&postcount=1](http://ubuntuforums.org/showpost.php?p=2282079&postcount=1)

KeeperOS said (In part):

> Hi, today I installed Kubuntu on a VM (after Ubuntu, just to check and compare) and just for the hell of it I chose Greek for the system language. After the installation I tried to change it back to English; sure enough, I went to System Setings -> Regional and Language and chose US English as the primary language (simply moved it on top of Greek on the Languages list).

However this only does half the job, it does change some (most?) dialogs and menus back to english but several aspects of the system (including most annoyingly the Konsole Terminal) remain in Greek.

- Is there a way to completely change the system language post-install or do I have to reinstall the OS in order to change that?
**EDIT-_SOLUTION_**_: Found it: One must go under system -> Language Support -> Default Language._

---

### Post by Mariane on 2009-05-04
Thank you. I tried. I did:
bash
export LANG=en

And in Control Center the language is said to be 
US English. 

The problem seems to be spreading, now even the 
menus in FreeCell are in French... I should never 
have done this dist-upgrade... Never... 

I don't dare to open a spreadsheet. I mostly use 
.csv, and if the numbers are interpreted as French 
I'm <excuse my French again>. 

The French write their numbers in a weird way, to 
say 0.1 they write 0,1 so just imagine what such 
a change can do to a spreadsheet... 

Please help. I'll try anything. 

Mariane

---

### Post by Didius Falco on 2009-05-04
You could try Localepurge. It's a script that deletes all the language files except the ones you select. Perhaps by purging everything but the default locale you'd be able to stop this from happening.

It's in Synaptic, but I'd install it from a terminal shell, so you can configure it right away. Up/Down arrows scroll through the installed languages, space bar marks the keepers, then when you are done tab down to start it.

As a bonus, it will automatically purge language files other than your choices from future package downloads.

I have it on my system and haven't noticed any ill-effects from it.

```
sudo apt-get install localepurge
```to install it from the term...uhh, Konsole.

I hope this fixes it for you....

On Edit: It's been a while, but I think I had to either log out and back in, or possibly reboot. It should tell you.

---

### Post by Mariane on 2009-05-04
Reply related to:

EDIT-SOLUTION: Found it: One must go under system -> Language Support -> Default Language.

Doesn't seem to exist under KDE so I went to Gnome 
and - guess what - the whole Gnome is French :confused: 

I couldn't find it at first because I was looking 
for "Support de langage" and it turned out to be 
something or other "linguistic". There it was 
written that the default language was French and 
it told me "Your favorite language is not completely 
installed, do you want to install it now?" 

The possible options were "Yes" and "Remind me 
later", no way of answering "It is NOT my favorite 
language". 

Anyway, thank you very very much. My KDE is now 
in English! Hurray! 

I just hope next dist-upgrade it won't turn into 
Chinese :P 

Mariane

PS: Now THIS is utterly amazing. Getting rid of the French 
also sorted out audacity. This works again too.

---

### Post by Didius Falco on 2009-05-04
Excellent!! I'm almost afraid to ask, but have you opened one of the spreadsheets?

If you would, please, mark this thread as solved by editing your first message, hitting the **Go Advanced** button and typing solved at the front of the thread title. It'll offer you several variations to choose from as you are typing. Then simply save the edit and it'll make it easier to find for the poor soul who does have a language other than their own to fix.

Why do I suddenly feel like listening to a lot of Edith Piaf? <G>

---

### Post by Docaltmed on 2009-05-04
If there is a "Most Entertaining Thread of the Week" award, this one ought to win it.
=D>

---

