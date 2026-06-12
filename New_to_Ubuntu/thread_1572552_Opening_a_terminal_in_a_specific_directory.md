---
title: "Opening a terminal in a specific directory"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by gaurish108 on 2010-09-11
Hi,

I am using Ubuntu 10.04. I wanted to know if there was anyway to configure my computer open a terminal in a specific folder by doing just a right click inside/on the folder. 

Some of my folders have long and convoluted names and even with the Tab completion key it becomes irritating to do cd again and again....

If some one could sugges a method or a shell script I will be grateful. I am relatively new to Ubuntu so please if possible provide a detailed explanation.....Thank you very much:)

---

### Post by hhlp on 2010-09-11
nautilus-open-terminal is a proof-of-concept Nautilus extension
which allows you to open a terminal in arbitrary local folders.

```
sudo aptitude install nautilus-open-terminal
```

right click in nautilus open in terminal in the specific folder

---

### Post by gaurish108 on 2010-09-11
Hi I just installed nautilus-open as you suggested but cannot see '''nautilus open anywhere'
even in the righ-click menu in a folder. 

Is there sth elementary I am missing/ not done?

---

### Post by jtarin on 2010-09-11
> **gaurish108 said:**
> Hi I just installed nautilus-open as you suggested but cannot see '''nautilus-open-terminal'
even in the righ-click menu in a folder. 

Is there sth elementary I am missing/ not done?
I would say so...the name of the extension is nautilus-open-terminal......you asked for "open a terminal in a specific folder"....that's what you get....right click menu "Open in a Terminal". You might have to logout and back in to see it.

---

### Post by dcsoldschool53 on 2010-09-11
I was just researching this command last night, and it does work. What you were suppose to do after you installed.

sudo aptitude install nautilus-open-terminal

in the terminal, was to also type in the command

killall nautilus

This would have rebooted nautilus. Then when you would have reopened nautilus, and right click on a folder, you would have seen it.

---

### Post by jtarin on 2010-09-11
Yes that is another way to do it, but brevity is the soul of wit when posting.

---

### Post by gaurish108 on 2010-09-11
Thank you, this worked perfectly.!!!!

---

### Post by inameiname on 2010-09-11
There's also a brand new option besides open in terminal if desired, a built-in Nautilus terminal:

[http://www.webupd8.org/2010/09/nautilus-embedded-terminal-gets.html](http://www.webupd8.org/2010/09/nautilus-embedded-terminal-gets.html)

---

### Post by Jazzy_Jeff on 2010-09-11
Here is a link for you also:

[http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html](http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html)

---

### Post by jtarin on 2010-09-11
I don't like that one...its in the way and according to the originator...> There is one catch though: currently there is no way to disable the embedded terminal (like a keyboard shortcut to toggle the terminal on/off) so if you install this, you'll always have a terminal embedded into Nautilus. But you can however set it to only show up for certain folders you set.That's a deal breaker for me.

---

### Post by inameiname on 2010-09-11
My link and Jazzy_Jeff's link are about the same nautilus-terminal. Mine be the latest, which if you checked out, it states there is now a toggle added to it to enable hiding it as default. Of course, there are a few other bugs that are currently being worked on. But it's a great new idea that has never been this far into actually being a Nautilus Terminal.

---

### Post by DaGeek247 on 2010-09-11
mark it as solved if this worked!

---

### Post by bodhi.zazen on 2010-09-11
> **Jazzy_Jeff said:**
> Here is a link for you also:

[http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html](http://www.webupd8.org/2010/09/nautilus-terminal-embeds-terminal-into.html)

That is cool, thanks for the link.

---

### Post by jtarin on 2010-09-11
Konqueror had this feature ages ago....don't know if it still does. I can remember using it in Mandrake 5 or 6. What goes around comes around.

---

