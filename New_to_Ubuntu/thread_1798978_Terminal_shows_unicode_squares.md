---
title: "Terminal shows unicode squares"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by sebas9854 on 2011-07-06
So today I got home, turned on my PC, booted Ubuntu 11.04, all normal...

...then opened the terminal, and to my surprise: everything (yes, everything: [http://i.imgur.com/L5OQn.png](http://i.imgur.com/L5OQn.png)) has turned into unicode squares

Any ideas?

Thanks

---

### Post by mikejonesey on 2011-07-07
lol how cool, what happens when you try n export a new PS1, is there anything unterward in the profile... i'm guessing the prob is before there though as all char...

also is it the same in tty1 Ctrl+Alt+F1 or is it just in gnome-terminal?

---

### Post by sebas9854 on 2011-07-07
> **mikejonesey said:**
> lol how cool, what happens when you try n export a new PS1, is there anything unterward in the profile... i'm guessing the prob is before there though as all char...

also is it the same in tty1 Ctrl+Alt+F1 or is it just in gnome-terminal?


I don't really know what a PS1 is =P.

I did try copying all the text it gave me and pasting it into t Libre Office Writer (text edit gives me the unicode squares as well), and it gave me real characters which made sense, so I don't really know what is happening, also: It's just gnome terminal, not tty1

---

### Post by mikejonesey on 2011-07-07
lol was about to say where is the menu bar... unity lol

goto Terminal->Set Character Encoding and select ASCII

ps, PS1 = the info you see before you get typeing ie: username, hostname and in linux the current dir (older | some other unix based systems suppress the cur dir by default, so you have to rely on pwd), the PS1 is set in the profile in etc, i was guessing you had modded that or somthing before to get a funny char that made the rest go odd...

makes more sense that the wrong char enc is setup somewhere in gnome-terminals settings specially as tty1 is fine...

---

### Post by sebas9854 on 2011-07-08
> **mikejonesey said:**
> lol was about to say where is the menu bar... unity lol

goto Terminal->Set Character Encoding and select ASCII

ps, PS1 = the info you see before you get typeing ie: username, hostname and in linux the current dir (older | some other unix based systems suppress the cur dir by default, so you have to rely on pwd), the PS1 is set in the profile in etc, i was guessing you had modded that or somthing before to get a funny char that made the rest go odd...

makes more sense that the wrong char enc is setup somewhere in gnome-terminals settings specially as tty1 is fine...

There is no ASCII on the options, not even on the "Add or Remove...", also, the PS1=same squares.

Also, I found something funny, if I select all the text on the terminal, copy it and paste it on the Libre Office Writer it gives me the text that should be there in the first place.


Also, what do you mean by "lol I was about to say where is the menu bar..." I never mentioned any menu bars :P

Halp!

---

### Post by mikejonesey on 2011-07-08
> Also, what do you mean by "lol I was about to say where is the menu bar..." I never mentioned any menu bars :razz:

in the screenshot there is no menu, look for unicode instead of ascii then...

---

### Post by sebas9854 on 2011-07-12
Still nothing, any ideas?

---

### Post by AlphaLexman on 2011-07-12
Can you type anything into the terminal ??

Can you read what you typed ??

Even if you can't read it, do commands such as '**ls**' produce any output ??

If so, try this...
```
bash --debugger --noprofile --norc
```

---

### Post by sebas9854 on 2011-07-13
> **AlphaLexman said:**
> Can you type anything into the terminal ??

Can you read what you typed ??

Even if you can't read it, do commands such as '**ls**' produce any output ??

If so, try this...
```
bash --debugger --noprofile --norc
```



The terminal works perfectly, I mean, it's fully functional, except, obviously, because of this inconvenience, what you told me to try gave me this:
```
hotch@Hotch:~$ bash --debugger --noprofile --norc
bash-4.2$ 
```

Also, '**ls**' gave me ```
Back	   Downloads	     jre1.6.0_26	      Public	  Videos
Backups    examples.desktop  jre-6u26-linux-i586.bin  swt.jar
Desktop    installer.log     Music		      Templates
Documents  jd_unix_0_9.sh    Pictures		      Ubuntu One

```

Maybe that'll help?


Thank you in advance.

---

### Post by mikejonesey on 2011-07-13
maybee... in your .bashrc

export LANG=en_GB.utf8
export GDM_LANG=en_GB.utf8

if that does not work can you tell me the out come of running; "gnome-terminal --disable-factory"...

if any of this works we can update your profile settings...

---

