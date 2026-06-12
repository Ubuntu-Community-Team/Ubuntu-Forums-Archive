---
title: "I have Gimp, is Gap included? or how to get it?"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by Ubunser on 2010-01-30
I have Gimp, but realized I need Gap. And I have no idea how to get it. Looked in synaptic and add/remove - there's nothing by the name Gap or something that's not the Gap I mean.

---

### Post by spiky001 on 2010-01-30
it,s in synapic pacage manaer, system, administration hope thats what you want

---

### Post by Tahakki on 2010-01-30
The package you want is gimp-gap. Type:

```
sudo apt-get install gimp-gap
```

---

### Post by Ubunser on 2010-01-30
> **spiky001 said:**
> it,s in synapic pacage manaer, system, administration hope thats what you want

I typed 'gap' in termianl it said it wasn't installed, so I installed it through terminal. When finished I closed the terminal. But no Gap appered in no menu. So I went again to terminal and typed 'gap'. This time it said "   Loading the library. Please be patient, this may take a while.
" After waiting 20 minutes I ran out of patience, what's more weird the computer seems absolutely idling as I see system monitor shows no CPU activity att all, not even the slightest like moving the cursor. So I closed the terminal despite the warning that a there's one active process. 
Like, this all sucks like crazy. I don't like this. I just need Gap

---

### Post by Ubunser on 2010-01-30
I just opened Gimp and found new tab in menu bar called "Video" - is this Gap?

---

### Post by Tahakki on 2010-01-31
Possibly, isn't it an animation add-on?

---

### Post by houseworkshy on 2010-01-31
It is in the repositories but not under the name "gap" is is called "Gimp gap".  If you search for gimp on its own then you will find it in a rather large list of things which can be added to gimp.  Before searching look at your software sources.  As you are going to use synaptic anyway the logical route to them is :- System>Administration>Synaptic Package manager>settings>repositories>third party software.  Make sure that all the empty boxes except source code are checked.  Then close and reload as prompted, then use the search and you should find them.

---

