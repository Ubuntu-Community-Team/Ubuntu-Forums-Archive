---
title: "Window/Workspace switching."
date: 2010-11-11
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2010-11-11
How do I make it look pretty?  I was watching a video about workspaces and he can bring all 4 workspaces on the screen and Ive seen people switch between them with it looking like a cube, and I think having them cycle through like a roll of film.  I tried to change my visual effects but it always switchs back to none.  I am on 10.04.


This is what Im talking about for reference. [http://www.youtube.com/watch?v=PgLK8eYAg0A&feature=related](http://www.youtube.com/watch?v=PgLK8eYAg0A&feature=related)

---

### Post by llamabr on 2010-11-11
[http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+compiz+cube&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+compiz+cube&ie=utf-8&oe=utf-8)

---

### Post by shadow120 on 2010-11-11
my desktop goes back to none too with mine its because my graphics card is old and not supported.  if your using an older computer you might be out of luck but post what you have and someone might have a better idea about that.  all the effects your talking about can be done with compiz

---

### Post by DarrenMR415 on 2010-11-11
I have a fairly new Toshiba Satallite.  Plus I have no idea how to see what I have with Ubuntu.

---

### Post by shadow120 on 2010-11-11
this should tell you what video card you have
```
lspci | grep VGA
```

did you check to see if theres any hardware drivers available under system > administration > hardware drivers?

---

### Post by DarrenMR415 on 2010-11-11
> **shadow120 said:**
> did you check to see if theres any hardware drivers available under system > administration > hardware drivers?


3d-accelerated proprietary graphics driver for ATI cards.  That might be helpful eh?:lolflag:

---

### Post by PPPilot on 2010-11-11
Open a terminal and type in the following.  ```
sudo lshw
```Hit return. You will be asked for your password. As you type it in you will not see anything. This is normal. Hit return. You will get a list of all hardware in your machine.  Copy it and post it here and I'm sure someone can help.....

---

### Post by DarrenMR415 on 2010-11-11
I updated that driver and it seems to be working.  I have compiz installed and stuff is looking fancier.  Thanks for the help.

---

