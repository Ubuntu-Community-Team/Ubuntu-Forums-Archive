---
title: "Changing Keyboard Layout failure"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by emmiesix on 2011-06-24
My boyfriend is Greek, and as I am slowly learning the language I would like to be able to type some Greek characters in (mainly) our skype conversations and also perhaps libreoffice, firefox, and email (thunderbird).

I went ahead and installed the modern greek lanuage pack, and added the panel notification for keyboard layout.

When I go and select Greek, it shows a dot next to it.

I have then gone to type in: emacs, gedit, libreoffice, skype, and firefox.  NO GREEK CHARACTERS.  If I click on "keyboard layout" it shows me a greek layout, but (as you can see clearly right now) I'm still getting roman characters.

I have searched all over, I cannot figure out why this basic switch does not work. :(  Ubuntu is failing me, sadly.

---

### Post by Sealbhach on 2011-06-24
Try in the menu System/Preferences/Keyboard

There's a gui there for choosing keyboard layouts. Make sure too that you select the keyboard layout at the login screen (gdm). Just logout and check that you have that set to whatever layout you want to use.
.

---

### Post by emmiesix on 2011-06-24
Thanks for the reply.

There are two problems:

1) The Greek Keyboard doesn't work, even if I choose it from System-Preferences-Keyboard or at login.

2) I don't really want to choose greek at login, because I can barely speak/understand it.  What I want is to be able to switch to a greek keyboard on the fly (with the mouse or a key pattern) so I can type, e.g., "good night" in greek, but keep all the displays etc in English.

---

### Post by luca5am on 2011-06-24
If you have two layouts set in you system>preferences>keyboard, then you can easily switch from one to another with the following shortcut (unless you change it from its default value):
shift+caps lock
I use it because I use two layouts too.
The top layout in system>preferences>keyboard will be the one loaded at start-up

---

### Post by idoitprone on 2011-06-24
i giving you general command in shifting layout

```
setxkbmap gr
```
change gr to us for english


> My boyfriend is Greek, and as I am slowly learning the language i guess people learn things to get closer lol

---

### Post by emmiesix on 2011-06-25
Thanks, that works!

In case anyone else is looking for something similar, make sure to type 
```
setxkbmap us
```

first, and keep the terminal open... this way you can switch back and forth just by pushing "up" twice plus enter.  I'm sure there is a more elegant way out there but this works for now. :)

---

### Post by ellaivarios on 2011-06-28
> **emmiesix said:**
> My boyfriend is Greek, and as I am slowly learning the language I would like to be able to type some Greek characters in (mainly) our skype conversations and also perhaps libreoffice, firefox, and email (thunderbird).

I went ahead and installed the modern greek lanuage pack, and added the panel notification for keyboard layout.

When I go and select Greek, it shows a dot next to it.

I have then gone to type in: emacs, gedit, libreoffice, skype, and firefox.  NO GREEK CHARACTERS.  If I click on "keyboard layout" it shows me a greek layout, but (as you can see clearly right now) I'm still getting roman characters.

I have searched all over, I cannot figure out why this basic switch does not work. :(  Ubuntu is failing me, sadly.


Jersus Christ, Virgin Mary, Holly Spirit, and Zeus...
 I hate it when people ask a simple question and they get a cluster farm (lol) of random messages and responses:

Here you go (I'm Greek-Canadian, I am an expert at doing what you ask)

1. Go to System>Preferences>keyboard
2. Click on the layouts Tab.
3. Make sure you have your default keyboard layout at the very top (mine  is USA); probably a good idea if English is your default language to  leave it that way.
4. click on "Add"
5. choose country "Greece", variants "Greek"
6. click "Add"
7. Click on "Options"
8. Select "Keys to change layout"
9. Choose the keyboard combination of your choice that will switch  between your English layout and the Greek layout (if you add more  languages it will cycle through them, but Ubuntu couldn't be worse than  Microsoft in preventing you from adding more than 4 keyboard layouts...  anyway) I use Ctrl+Shift, others prefer Shift+Alt.
10. click "Close" to go back to the main menu.
11. click on "Keyboard model", and find your keyboard model (on the top  choose a vendor, on the bottom, choose a model for your keyboard -- it's  easier if you have a laptop -- make sure it looks the same, not that  the model matches only), and press "ok"
12. Click on "Apply System-Wide"

you are done.
Now if you want to type in Greek just type your keyboard combination  (i.e. Ctrl+Shift or whatever) and then after you are done using Greek,  type your keyboard combination again to switch back to English.


I hope you are still with your Greek boyfriend!
Go visit Greece. Don't worry about the Propaganda by all the american  media about the Greek crisis and all that. (sorry if you are american -  the US government is super corrupt),  It's all made up cos they wanna  take down the Euro. When you go there to an island in Greece or  wherever, you'll see it's paradise, and the economy is more or less  fine, save for the dumn communists and anarchists who go on strikes cos  the CIA pays them bug bucks... Anyway, I'm just venting...

Good luck.

---

