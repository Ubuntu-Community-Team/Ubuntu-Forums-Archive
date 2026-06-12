---
title: "alt + codes"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by Blue Summer on 2011-04-11
On Window$ I could use alt+ 132, 148 and 152 (I think) to use the swedish characters when I'm typing in msn, the internet or what ever, so I was just wondering how I can add that functionality to ubuntu? Thanks in advance :)

---

### Post by ChipOManiac on 2011-04-11
I Think IBus Has This Feature, But You Can Also Use The Keyboard Layout Option... <<http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu>>

---

### Post by Blue Summer on 2011-04-11
Cheers, having a look into it, wondering if there's a way to bind the 3 swedish keys to 1,2 and 3 on my numlock keypad.
öäå

---

### Post by Vaphell on 2011-04-11
while upgrading keyboard layout is more convenient you can enter any char with its unicode number, after ctrl+shift+u (_u_ shows up)
ä - _u_0064
å - _u_0065
ö - _u_00f6

---

### Post by rosencrantz on 2011-04-11
If you want to go beyond Ubuntu's layout selection, you can always try xmodmap for further customisation.
This should be a comprehensive tutorial
[http://blacketernal.wordpress.com/set-up-key-mappings-with-xmodmap/](http://blacketernal.wordpress.com/set-up-key-mappings-with-xmodmap/)
although I have no idea why the author chose that charming utterly readable grey-on-black colour scheme...

---

### Post by corncob on 2011-04-11
I use "compose key sequences" ([http://www.hermit.org/Linux/ComposeKeys.html](http://www.hermit.org/Linux/ComposeKeys.html) or google it for a better list).  System > Preferences > Keyboard > Layouts > Options > Compose Key Position.  I use the Left Win key but it gives you other choices.  If you want to make a ö, type [COMPOSE KEY]+o+", a ñ is [COMPOSE Key+~+n, etc.  It doesn't matter which order they're in.

---

### Post by GrouchyGaijin on 2011-04-11
> **Blue Summer said:**
> On Window$ I could use alt+ 132, 148 and 152 (I think) to use the swedish characters when I'm typing in msn, the internet or what ever, so I was just wondering how I can add that functionality to ubuntu? Thanks in advance :)

You can set an additional layout from System > Preferences > Keyboard.  Add Swedish then under options you can set a hot key to switch between layouts.  I use the Windows key.

Are you in Sweden?

---

### Post by TeoBigusGeekus on 2011-04-11
[Relevant.]("http://answers.yahoo.com/question/index?qid=20100922210904AAdAwYl") :biggrin:

---

### Post by Blue Summer on 2011-04-11
> **corncob said:**
> I use "compose key sequences" ([http://www.hermit.org/Linux/ComposeKeys.html](http://www.hermit.org/Linux/ComposeKeys.html) or google it for a better list).  System > Preferences > Keyboard > Layouts > Options > Compose Key Position.  I use the Left Win key but it gives you other choices.  If you want to make a ö, type [COMPOSE KEY]+o+", a ñ is [COMPOSE Key+~+n, etc.  It doesn't matter which order they're in.


Hi mate, got the compose key position ticked for left win key, just wondering how I define it now?


TeoBigusGeekus... LOLOLOL

GrouchyGaijin - Nah, I'm English, just trying to learn some swedish and it's a pain trying to get the letters in when talking to my friend. I've changed language to swedish but it's a whole different placement with question marks etc

---

### Post by corncob on 2011-04-12
> **Blue Summer said:**
> Hi mate, got the compose key position ticked for left win key, just wondering how I define it now?


Now that you have the compose key set, hit it (don't hold it down) and, if you want an å, hit [a] then [*] -- it doesn't matter in what order.  You can get Umlauts (or whatever they're called in Swedish) by typing the letter and quotation marks like so: [COMPOSE] [u] ["] gives you an ü.  € (I believe they use the Euro) is c and =, etc.
I find it to be quite intuitive and don't use it much but I printed my list of compose key sequences from [http://download.oracle.com/docs/cd/E19683-01/806-4743/6jdq6q2n7/index.html](http://download.oracle.com/docs/cd/E19683-01/806-4743/6jdq6q2n7/index.html) .  A Google search gives you many more choices.

---

