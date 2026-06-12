---
title: "Flash 10 problems. Should I install Flash 9?"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Epilonsama on 2008-12-10
Nice tutorial, I wanna ask you something, I have flash 10 installed on my machine but is lagging to much when I watch videos on youtube, is that a problem with flash 10, if so is there a way to install flash 9 on my intrepid system?

---

### Post by Het Irv on 2008-12-10
Flash 10 is vastly better than Flash 9 and much easier to install... if you want to I guess you could try, but I think the problem stems more from the fact that Full Linux Support for Flash didn't start till 10.

---

### Post by Keen101 on 2008-12-10
I had problems with flash 10 lagging as well when i installed it with the .deb file from adobe. But, it works great when installed like this:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by aysiu on 2008-12-10
I moved this out of the Psychocats tutorial updates thread, since it is more of a support request. I haven't had problems with Flash 10 in Intrepid, but it's definitely worth a shot for you to try Flash 9. Which method did you use to install Flash 10?

---

### Post by zvacet on 2008-12-10
@ **Keen101**

It is not same as Adobe flashplugin.You will see that if you try to install adobe-flashplugin from synaptic.To get it to the synaptic add this to your source list

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

( you can replace hardy with itrepid if you use it)

save and close file.

```
sudo apt-get update
```

In synaptic you will find adobe-flashplugin and when you install it flashplugin-nonfree will be removed.

---

### Post by Epilonsama on 2008-12-11
> **aysiu said:**
> I moved this out of the Psychocats tutorial updates thread, since it is more of a support request. I haven't had problems with Flash 10 in Intrepid, but it's definitely worth a shot for you to try Flash 9. Which method did you use to install Flash 10?

Sorry about hijacking your thread, about my method of install I tried using the one from the repo, and also tried downloading it directly from adobe, both of them lagged to much.

---

