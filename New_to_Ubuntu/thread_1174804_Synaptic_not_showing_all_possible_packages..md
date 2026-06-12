---
title: "Synaptic not showing all possible packages."
date: 2009-05-31
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-05-31
Alright, this is the story:

I started with Intrepid about 3 months ago. When Jaunty came out, I upgraded, got all the programs I wanted(Banshee, Kdenlive, a few others) all through Synaptic. 

About a week ago, something happened that involved me reinstalling 8.10, because I was having issues and was too lazy to do searching around and fix it, seeing as I barely had anything on the computer. I backed it all up, blah blah blah. Anyways, upon trying to reinstall all the programs I wanted again, I found that they are not listed in synaptic anymore. Now, I am a total n00b when it comes to installing via Terminal, so I was a little annoyed. I decided I wanted to upgrade back to Jaunty, and maybe that was part of the issue. I have done that. The programs I want are still unavailable in Synaptic. I couldn't even find Kino on the list.

I am thinking its something with the way it filters, but I don't really know where to start. Any help is appreciated!

---

### Post by pbpersson on 2009-05-31
In Synaptic, when you go to Settings-->Repositories, are they all checked?

Which packages appear in Synaptic (and also what you can install from the command line) is determined by what repositories you are searching. 

This is also controlled from System-->Administration-->Software Sources

---

### Post by RAZRBAKK on 2009-05-31
All are checked.

---

### Post by unutbu on 2009-05-31
Open a terminal and run
```

sudo apt-get update
```
This will refresh the database of available packages.

If that does not fix the problem, please post your 
/etc/apt/sources.list

---

### Post by RAZRBAKK on 2009-05-31
> **unutbu said:**
> Open a terminal and run
```

sudo apt-get update
```
This will refresh the database of available packages.

If that does not fix the problem, please post your 
/etc/apt/sources.list

Thank you, sir!

---

