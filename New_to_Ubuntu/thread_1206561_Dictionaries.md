---
title: "Dictionaries"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2009-07-07
I would like to install two dictionaries but on reading previous previous threads the ones listed appear to be only spell checkers for open office , whereas all I would like is just a plain straightforward dictionary for doing single word translations . I have looked in package manager but am confused by the various  " aspell , myspell , ispell , dict " etc. Thanks.

---

### Post by Arup on 2009-07-07
The best dictionary is Stardict which is equivalent of Windows WordNet. You can add a huge range of dictionaries to it from their site, it has voice pronouciation, clipboard scan etc. I find it to be an excellent offering for Linux and Windows. Its in the repos.

---

### Post by Mornedhel on 2009-07-07
Aspell, Ispell and Myspell are spell checkers.

The dict-freedict-* packages provide translation dictionaries that you can use with a dictd daemon through the gnome-dictionary application, or any client for dictd.

The simplest translation dictionary setup with dictd is to install any dict-freedict-* package you need, dictd to have a local daemon, and configure gnome-dictionary to use localhost as a server.

Other solutions exist.

---

### Post by ex-wirecutter on 2009-07-07
Many thanks for your help .

---

### Post by ex-wirecutter on 2009-07-07
Just need a little further help in setting up local host as source , not too sure about " port " and " host name " Thanks

---

### Post by LewRockwell on 2009-07-07
> **ex-wirecutter said:**
> Just need a little further help in setting up local host as source , not too sure about " port " and " host name " Thanks

different topics need individual threads please

.

---

### Post by Mornedhel on 2009-07-07
The host name would be "localhost" and the port should be kept default, 2628.

---

### Post by ex-wirecutter on 2009-07-07
Thats what I needed , many thanks again .

---

### Post by wpshooter on 2009-07-07
> **Arup said:**
> The best dictionary is Stardict which is equivalent of Windows WordNet. You can add a huge range of dictionaries to it from their site, it has voice pronouciation, clipboard scan etc. I find it to be an excellent offering for Linux and Windows. Its in the repos.

When you say this has voice pronunciation, what does that mean ?

I installed this Stardict and when I press on the symbol that says voice pronunciation, I get no sound/audio feed back, am I supposed to ?

P. S. - I just went in an looked at the setup/preferences and both sound and pronounce word are checked/enabled, still no sound !!!

Thanks.

---

