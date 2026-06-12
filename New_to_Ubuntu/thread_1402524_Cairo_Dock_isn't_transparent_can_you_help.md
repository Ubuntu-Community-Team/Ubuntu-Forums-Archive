---
title: "Cairo Dock isn't transparent can you help?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by verachion on 2010-02-09
I have just installed cairo dock 2.1.3-2. When I launch it I get a huge balck square around the dock, its not trasparent like it should be,is  there a setting I need to go to to make it transparent/

---

### Post by NCLI on 2010-02-09
> **verachion said:**
> I have just installed cairo dock 2.1.3-2. When I launch it I get a huge balck square around the dock, its not trasparent like it should be,is  there a setting I need to go to to make it transparent/

It sounds like you have compositing disabled. Try going to System->Preferences->Appearance->Visual Effects then choose either "normal" or "extra."

---

### Post by elliotn on 2010-02-09
I have the same problem, my is transparent but u can see where the lines, it just cant be like rocket dock on windows

---

### Post by verachion on 2010-02-09
> **NCLI said:**
> It sounds like you have compositing disabled. Try going to System->Preferences->Appearance->Visual Effects then choose either "normal" or "extra."

I have the visual effects turned on, I went in to dock preferences system and changed the composite to transparent and that worked, but now I get a right angle line at the top left and a line on the bottom as shown here

---

### Post by fabounet on 2010-02-09
this is maybe the window's whadow.
what is your window manager ?

---

### Post by verachion on 2010-02-09
> **fabounet said:**
> this is maybe the window's whadow.
what is your window manager ?

I am using ubuntu 9.10

---

### Post by tom.swartz07 on 2010-02-09
> **verachion said:**
> I have the visual effects turned on, I went in to dock preferences system and changed the composite to transparent and that worked, but now I get a right angle line at the top left and a line on the bottom as shown here

You have drop shadows on.

Open up CompizConfig settings manager (or install and open it if you dont have it) and select window decoration.

There should be a line for shadows. click the add button, then click invert. next click grab, and click your cairo dock. apply apply apply, and you should be all set.

Ive attached pics for you to follow along.

---

### Post by fabounet on 2010-02-09
also, if you run Compiz, you don't need to activate the fake transparency in the dock.
It sounds like you did both (but maybe I've just misunderstood).

---

