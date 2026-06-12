---
title: "How do i completely remove wine?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by mr.big_gun on 2009-03-15
i messed up something with wine when i was doin something in the terminal by tryin to get it to pick up my dvd drive. it wont run and when i removed the program and installed it again i get the same thing.  it will install and but it wont run any of the programs.  i have tried deleting the wine folder to get the wine folder out of my applications list on my desktop but i cant get rid of that either. please help!!!

---

### Post by rafac24 on 2009-03-16
You uninstalled Wine already by Synaptic?? 

System-> Administration-> Synaptic Package Manager
Type 'wine' in the search bar and mark for complete removal.

Also, to remove it from your Menu, you're gonna want to open the Main Menu Settings:

System-> Preferences-> Main Menu
Then just uncheck Wine from the bottom of the list.

---

### Post by mr.big_gun on 2009-03-16
yes i did uninstall it with the synaptic package manager
and do u know if, if i sound dumb its because im a noob, there is a way to reset the scripts or whatever tells it what to do. i had a problem with virtualbox and i just had to recompile the program. or something like that
it will install i just cant get anything to work in it.

---

### Post by Gannon8 on 2009-03-16
Try:
```
sudo apt-get purge wine
```

That should get rid of all the configuration files associated to wine. You may have to reinstall wine however.

It would be nice if WINE had a reset feature. It would be great for testing software.

---

### Post by mvalviar on 2009-03-16
```
sudo apt-get --purge remove wine
rm -rf ~/.wine 
```

---

### Post by mr.big_gun on 2009-03-16
i just tried what u said gannon8 and it worked perfect  thank you very much. your are awesome!

---

### Post by mr.big_gun on 2009-03-16
new problem lol i kinda deleted the applications folder so now i cant see what i have installed
is there a way to get it back? i just tried to reinstall and it didn't work

---

### Post by mvalviar on 2009-03-16
If you did run "rm -rf ~/.wine" you removed the virtual c drive and there is no way to restore it. If you removed the program navigating to it in nautilus (the file explorer) and deleting it maybe it is still under trash. Simply restore it.

Remember that ~/.wine or /home/username/.wine is your virtual windows machine.

---

### Post by billgoldberg on 2009-03-16
When deleting stuff it's better to use autoremove instead of remove.

So I would use:

```
sudo apt-get autoremove wine --purge
```

---

### Post by MrWES on 2009-03-16
What't the difference between remove and autoremove ?

---

### Post by billgoldberg on 2009-03-16
> **MrWES said:**
> What't the difference between remove and autoremove ?

autoremove removes dependencies that got installed (aptitude style).

---

### Post by MrWES on 2009-03-16
> **billgoldberg said:**
> autoremove removes dependencies that got installed (aptitude style).


Ahh...good to know for the command line -- thanks.

---

