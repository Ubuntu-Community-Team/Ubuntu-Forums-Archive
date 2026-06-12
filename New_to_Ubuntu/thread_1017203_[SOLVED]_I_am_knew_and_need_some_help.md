---
title: "[SOLVED] I am knew and need some help"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Scytes on 2008-12-20
Hi, I am only into these for two weeks, I don't know much but I do know enough to see that the "sudo apt-get update" is not downloading all my repositories. Here is what it looks like.




Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US                                                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US                                                                                                             
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US                                                                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US                                                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US                                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                                                                                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                                                                                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 378B in 40s (9B/s)
Reading package lists... Done




Can anyone please help me with this?

---

### Post by howefield on 2008-12-20
What's wrong with that ?

---

### Post by StevenHarper on 2008-12-20
that command updates the list

to update on the command line:

```
sudo apt-get upgrade
```

There is a nice GUI you know in 

System | Administration | Update Manager

---

### Post by Scytes on 2008-12-20
Yes I tried that to, when I do that it doesn't download them either.

---

### Post by StevenHarper on 2008-12-20
Could you open Synaptic package manager

System | Administration | Synaptic package manager

From its menu

Setting | Preferences

Then in the Network TAB check your network is correct.

Also please try the update in Synaptic package manager and post any errors here

Steve

---

### Post by Zeedok on 2008-12-20
I'm not sure that that is a problem - the same thing happens when I "sudo apt-get update".

Can you install everything you want to?  When a repo doesn't load properly the reload window in synaptic "times out", ie you will know.  

If that ever happens, you can check that you are using the best mirror - in Synaptic open Settings - Repositories.  Then in the "Download from" drop down list select "Other".  A window pops up with heaps of mirrors available.  On the right hand side is a button "Select Best Server", push that and it will find the fastest and best mirror for your location.

Enjoy.:P

---

### Post by Scytes on 2008-12-20
So the only issue could be that the mirror I am trying isn't the right one for me to download it from? and also could this cause issues with the x server when using wine?

---

### Post by Zeedok on 2008-12-20
> **Scytes said:**
> could this cause issues with the x server when using wine?

Don't think so.  What actually happens when you "reload" in synaptic??

---

### Post by jmszr on 2008-12-20
Scytes,
        Did you happen to notice that all the Ign (Ignore) were suffixed with Translation-en_US. Not to worry - you're getting all your updates.

---

### Post by kansasnoob on 2008-12-20
I'm not at all sure you have any problem. But go to System > Administration > Software Sources. this is mine;

[ATTACH]97094[/ATTACH]

[ATTACH]97095[/ATTACH]

[ATTACH]97096[/ATTACH]

The second screenshot will not look like yours, but it would really help to know what works and what doesn't work.

What is Ubuntu not doing to suit you?

---

### Post by Scytes on 2008-12-20
The Translation-en_US. fails when I use synaptic reload.

---

### Post by jmszr on 2008-12-20
Scytes,
         I found this thread:[http://ubuntuforums.org/showthread.php?t=903214](http://ubuntuforums.org/showthread.php?t=903214) ,the reason it's ignored is that there is nothing to update. There is also a code if you feel the need to check.

---

### Post by Skip Da Shu on 2008-12-24
> **jmszr said:**
> Scytes,
        Did you happen to notice that all the Ign (Ignore) were suffixed with Translation-en_US. Not to worry - you're getting all your updates.

Yea, yea... but I've been seeing this for a good year now...Why is it and is there anyway to make it go away.. the "Translation-en_US" errors that is?

Thanx, Skip

---

### Post by hyper_ch on 2008-12-24
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

