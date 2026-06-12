---
title: "iBus, Anthy, and Katakana."
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-09-27
So, I had ubuntu install Japanese support when it was installing itself. I don't really know how, but this does not seem to have included any way to actually write japanese. iBus did list anthy and one other system of input. However, as anthy was not actually installed I have no idea how I was able to write anything in it. Still, installing anthy has greatly improved it, but for two problems:

1)I have no idea how to switch between hiragana and katakana.
2)The font looks abysmal and I do not know how to change it.

If you'd be so kind as to help me out, I'd appreciate it.

---

### Post by olfsj on 2010-10-07
The way I have set it up is like this:

First, install *ibus-anthy* (maybe you have that already). Then in *System settings* -> *IBus Preferences*, go to the tab *Input Method*, and remove all input methods you have there. Then add *Japanese - Anthy* as your only input method. 

To have IBus start correctly on login, you also need to go to *Administration* -> *Language Support*, then on the first tab *Language* choose IBus as *Keyboard input method system*.

Then when you want to write in Japanese, press Ctrl+Space and Anthy will be activated. Just write and you'll see hiragana show up. If you want katakana or kanji instead press Space to convert, pressing repeatedly if the first choice is not the one you wanted, pressing Enter to select it. 

As for fonts, that's more complicated to get set up nicely, and unfortunately I don't quite remember what I did there.

---

### Post by YannBuntu on 2010-12-21
This is an old thread but it may help you : [http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)

---

### Post by Pressondude on 2010-12-24
I am also having this problem. I installed the packages anthy and ibus-anthy, but I get no response when I hit the spacebar. On Jaunty (my last install), I had no problems getting SCIM to work. iBus changes my typing to hiragana without a problem, but gives no response when I hit the spacebar.

---

### Post by YannBuntu on 2010-12-24
Did you install the "ibus-anthy " package ?

also, you have to hit Ctrl+Space, not only Space.

---

### Post by Pressondude on 2010-12-24
I meant "space" to change from hiragana to katakana/kanji. I rebooted and now everything seems fine...

---

### Post by Cho_cho on 2011-04-10
Hello!

I installed all the packages and changed my language settings properly but the Anthy bar doesn't show up when I press ctrl+space. I tried changing the shortcut in the ibus preferences section but it still doesn't work. 

What could be the problem?
Thank you!

---

### Post by temporos on 2011-04-10
> **Cho_cho said:**
> Hello!

I installed all the packages and changed my language settings properly but the Anthy bar doesn't show up when I press ctrl+space. I tried changing the shortcut in the ibus preferences section but it still doesn't work. 

What could be the problem?
Thank you!

When you open the iBus preferences, there should be two Anthys for you to choose: "Anthy" and "Anthy (m17n)."  I know most people here use the m17n IME, but that won't work on my machine for some reason.  Try using the regular "Anthy" IME.  That one seems to work for me.

---

