---
title: "Where is Search and Indexing?"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by mvalviar on 2009-05-25
I used to be under System>Admin>Search and Indexing in intrepid. I can't find it anywhere in Jaunty. Where is it now?

---

### Post by mprince on 2009-05-25
You may have to add it using the Menu editor... which should be in *System>Preferences>Menu editor*

Press Alt+F2 and type *tracker-preferences* which should bring it up.

---

### Post by philinux on 2009-05-25
> **mvalviar said:**
> I used to be under System>Admin>Search and Indexing in intrepid. I can't find it anywhere in Jaunty. Where is it now?

Not installed by default. You'll have to install it from synaptic/add remove or via terminal.

---

### Post by Sceiron on 2009-05-25
> **mvalviar said:**
> I used to be under System>Admin>Search and Indexing in intrepid. I can't find it anywhere in Jaunty. Where is it now?

Hm, dont you have "Search for files..." Under "Places" in your menu.
If that's what you are looking for?

---

### Post by mvalviar on 2009-05-26
> **philinux said:**
> Not installed by default. You'll have to install it from synaptic/add remove or via terminal.

Why did they decide not to install it by default? Its kinda neat. I'm missing the "all in one deskbar" applet too. I forgot what it's called. Anyway thanks this is the answer I was looking for.

---

### Post by andrew.46 on 2009-05-29
Hi mvalviar,

If you ever decide to go to the 'dark side' and use the very powerful linux search commands you will come across 'find'. You can take it for a spin now by searching your 'home' for all of your mp3s:

```
find $HOME -iname '*.mp3'
```

Not what you are looking for now but perhaps in the future?

Andrew

---

### Post by mvalviar on 2009-05-29
No, biggie I'm a basher. It's for my wife she's used to point and click and she fond of the deskbar applet in Hardy and Intrepid.

---

### Post by andrew.46 on 2009-05-29
Hi mvalviar,

> **mvalviar said:**
> No, biggie I'm a basher. It's for my wife she's used to point and click and she fond of the deskbar applet in Hardy and Intrepid.

I understand completely. My wife has instructed me to keep my 'linux thing' to my *own* computer so you are a step ahead of me there :-).

Andrew

---

### Post by Viva on 2009-05-30
The tracker and deskbar applet are still in the repos. I love the deskbar too:)

You could also try Beagle as an alternative to tracker.

---

