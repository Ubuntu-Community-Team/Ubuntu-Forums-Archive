---
title: "cannot configure keyboard in spanish ,it doesn't work"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by martinvirg on 2009-04-29
I xcan't xconfigurwe my keyboard in spanish.  I can't setup it for correct working, please help!!!!!:confused::confused::confused::confused:
ç
ç
ç
ç thisd ework likwe thisd ,for wexcamplew wehwen i weritwe "·I sdisdlikwe weinsdowesd visdta or sdomwething welsdew likwe that thwe kewysd put tweox charaxctwersd insdtweasd of onwe
ç               so I have to edit the spell or words

---

### Post by zvacet on 2009-04-29
Under **system>admin>language support** add support for Spanish.Afte that go to the **system>preferences>keyboard>layouts**>add Spanish and make it default.

---

### Post by Yeti can't ski on 2009-04-29
Hey there! No panic. 

I had a similar but more tragic problem. I have a laptop with Italian keyboard (very few special characters) and I needed special characters for Portuguese and German. 

Unlike Window$, in Ubuntu you can specifically adjust the outuput of every key and/or key combination.

Take a look at this thread: 

[http://ubuntuforums.org/showthread.php?t=209115](http://ubuntuforums.org/showthread.php?t=209115) 

The solution in particular is on this post, by stdragon: 

> 
 Re: problem with international characters
Hey I figured it out!

Gnome/GTK doesn't use ANY of those files. There is a built-in list of compose sequences that you cannot change.

To force Gnome to use the standard way of doing it, you have to set the input method to "xim". Do this by editing /etc/environment and adding

export GTK_IM_MODULE=xim

at the end. Now copy /usr/share/X11/locale/en_US.UTF-8/Compose to ~/.XCompose (e.g. in your home directory as .XCompose). Now logout and restart the X server and next time you log in everything will work as expected.

It might be a good idea to edit the file a bit too. I don't have a "macron" key on my keyboard so I replaced <macron> with <minus> everywhere. I also deleted all the Cyrillic, Arabic, and Greek stuff since I only wanted latin characters with accents.

If you cannot figure it out by yourself, please let me know.

---

### Post by Ganu on 2009-07-22
I just tried Ubuntu 9.04 in live CD mode. I started in English. All the experience went fantastic until I realized that my keyboard did not giving "_" from the expected key. Looking around to configure my spanish keyboard, I found the menu option to do it.
 
Unfortunaterlly, even after configuring to Spain/Spanish I was not able to make my keyboard working properly.
 
I'm in the process of deciding wether installing Ubuntu/GNU/Linux in my computer. To me this keyboard issue is a very minimum condition, and it is not a good marketing for Ubuntu, I hope the cause of the problem is in my side.
 
As I said, other than that, ubuntu first contact was superbe and I will keep trying,
 
Ganu

---

### Post by Yeti can't ski on 2009-07-22
Well, remember that the Live CD experience will never match a full install. It is supposed to just give a "taste" of Ubuntu. 

Anyway, I can ensure you that Linux (and, thus, Ubuntu) offers a level of flexibility on keyboard configuration which is usually unachievable with Window$. 

Because of some academic activities, I must use the Italian keyboard of my laptop to write the special characters of German, Portuguese and French (for instance: áéíóúàèìòùäëïöçãõâôê). With Linux I can specifically establish the output of every single key and/or key combination. 

With my Window$ computer at work, my only choice was to install the uthoHotkey plugin and write some scripts for combination keys, which is definitely not nearly as good.

The transition to Ubuntu (just as with any piece of software) requires some patience and effort, but (unless you have some very weird proprietary drivers keyboard) the keyboard issue should not be the one reason preventing you from switching.

Welcome aboard (I hope!) and let me know if you need any assistance.

---

