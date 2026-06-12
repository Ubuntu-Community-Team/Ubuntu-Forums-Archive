---
title: "Oh MY god. My fonts are destroyed ! :("
date: 2010-10-12
forum: New to Ubuntu
---

### Post by dihan91 on 2010-10-12
**I tried to replace some fonts in ubuntu 10.10 maverik meerkat and now all my fonts are boxes**
I' gonna cry.
**** what did I do?
please tell me how can I revive the fonts. **How to reset this??**
now i'm on my pc using windows 7:(:(:(:([IMG]http://imgur.com/F6feG.png[/IMG]

---

### Post by ft-Orchard on 2010-10-12
Click on &#9633;&#9633;&#9633;&#9633;&#9633; than on &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
Then see if &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633; is checked.

Of not, than start "gconf-editor" and search for &#9633;&#9633;&#9633;&#9633; > &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
And change the value of &#9633;&#9633;&#9633;&#9633;&#9633;&#9633; to "&#9633;"

If that does not work: try these commands: 

```

mv ~/.gconf/desktop/gnome/interface/%gconf.xml ~/.gconf/desktop/gnome/interface/%gconf.old.xml 
mv ~/.gconf/apps/nautilus/preferences/%gconf.xml ~/.gconf/apps/nautilus/preferences/%gconf.old.xml 
mv ~/.gconf/apps/metacity/general/%gconf.xml ~/.gconf/apps/metacity/general/%gconf.old.xml

```

---

### Post by sikander3786 on 2010-10-12
Try reinstalling the fonts.

```
sudo apt-get install --reinstall --purge fontconfig fontconfig-config
```

If it doesn't work from the terminal, from the login screen you can press Ctrl + Alt + F1. That will give you a console. Login using your credentials, execute the above command and then press Ctrl + Alt + F7. Login and see if it worked.

---

### Post by kerry_s on 2010-10-12
> Click on &#9633;&#9633;&#9633;&#9633;&#9633; than on &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
Then see if &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633; is checked.

Of not, than start "gconf-editor" and search for &#9633;&#9633;&#9633;&#9633; > &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
And change the value of &#9633;&#9633;&#9633;&#9633;&#9633;&#9633; to "&#9633;"

:lolflag:

---

### Post by coffeecat on 2010-10-12
It's possible that the fonts selected in the fonts tab of the Appearance window have been uninstalled or renamed. Have a look at my post #2 in this thread:

[http://ubuntuforums.org/showthread.php?t=1567700](http://ubuntuforums.org/showthread.php?t=1567700)

That was for someone who had set their application font to dingbats. :-k But it might work for you if the above is the problem.

---

### Post by dihan91 on 2010-10-12
> **ft-Orchard said:**
> Click on &#9633;&#9633;&#9633;&#9633;&#9633; than on &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
Then see if &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;bo&#9633;&#9633;&#9633;&#9633;&#9633; is checked.

Of not, than start "gconf-editor" and search for &#9633;&#9633;&#9633;&#9633; > &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
And change the value of &#9633;&#9633;&#9633;&#9633;&#9633;&#9633; to "&#9633;"

If that does not work: try these commands: 

```

mv ~/.gconf/desktop/gnome/interface/%gconf.xml ~/.gconf/desktop/gnome/interface/%gconf.old.xml 
mv ~/.gconf/apps/nautilus/preferences/%gconf.xml ~/.gconf/apps/nautilus/preferences/%gconf.old.xml 
mv ~/.gconf/apps/metacity/general/%gconf.xml ~/.gconf/apps/metacity/general/%gconf.old.xml

```

sorry sir can you believe I am only seeing some boxes on the first few lines of ur post, didnt you write in english?
for example you wrote:
[B]"Click on &#9633;&#9633;&#9633;&#9633;&#9633; than on &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
Then see if &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;bo&#9633;&#9633;&#9633;&#9633;&#9633; is checked.

Of not, than start "gconf-editor" and search for &#9633;&#9633;&#9633;&#9633; > &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
And change the value of &#9633;&#9633;&#9633;&#9633;&#9633;&#9633; to "&#9633;"
"[/B]  
but i am seeing boxes after the word 'click on', 'than on', 'if' 

I'm useless i think.
can u help further?

---

### Post by ft-Orchard on 2010-10-12
Nahid, did you try this?

(open terminal with CTRL_ALT+T)
```

sudo mv ~/.gconf/desktop/gnome/interface/%gconf.xml ~/.gconf/desktop/gnome/interface/%gconf.old.xml 
sudo mv ~/.gconf/apps/nautilus/preferences/%gconf.xml ~/.gconf/apps/nautilus/preferences/%gconf.old.xml 
sodu mv ~/.gconf/apps/metacity/general/%gconf.xml ~/.gconf/apps/metacity/general/%gconf.old.xml

```And then restart your linux?

If that does not work, try:
```

sudo apt-get install --reinstall --purge fontconfig fontconfig-config 
```If that does not work, try:
[http://ubuntuforums.org/showthread.php?t=1567700](http://ubuntuforums.org/showthread.php?t=1567700)

---

### Post by kerry_s on 2010-10-12
> **dihan91 said:**
> sorry sir can you believe I am only seeing some boxes on the first few lines of ur post, didnt you write in english?
for example you wrote:
[B]"Click on &#9633;&#9633;&#9633;&#9633;&#9633; than on &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
Then see if &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;bo&#9633;&#9633;&#9633;&#9633;&#9633; is checked.

Of not, than start "gconf-editor" and search for &#9633;&#9633;&#9633;&#9633; > &#9633;&#9633;&#9633;&#9633;&#9633;&#9633;&#9633;
And change the value of &#9633;&#9633;&#9633;&#9633;&#9633;&#9633; to "&#9633;"
"[/B]  
but i am seeing boxes after the word 'click on', 'than on', 'if' 

I'm useless i think.
can u help further?


that part was the joke, he's just playing with you. :lolflag:
your fonts are all box's, get it?

---

