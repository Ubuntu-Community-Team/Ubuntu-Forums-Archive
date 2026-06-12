---
title: "Removal or complete removal ? THAT,is the ??"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by faron45 on 2009-04-01
I need to know the difference between "mark for removal" & "mark for complete removal".If I check something "mark for complete removal" does that take the entire program  out of my synaptic repositories or is there just little extras lying around on your pc if you don't mark something for complete removal ?

---

### Post by oldos2er on 2009-04-01
Complete removal means all program files including config files (usually "dot" files in your home directory) are uninstalled. Removal deletes everything but the config file.

---

### Post by bodhi.zazen on 2009-04-01
removal = remove the binary, the program

complete removal = remove  program + config files + documentation (man pages) + everything else.

Typically complete removal does NOT remove config (dot or . ) files in your home directory however.

---

### Post by faron45 on 2009-04-01
> **bodhi.zazen said:**
> removal = remove the binary, the program

complete removal = remove  program + config files + documentation (man pages) + everything else.

Typically complete removal does NOT remove config (dot or . ) files in your home directory however.
 Okee-dokee...let me ask this then everybody.....if I were to select "complete removal" & were to go into "synaptic package manager"sometime down the line...would I be able to find that program in the manager still ? That's I suppose what I'm worried about.

---

### Post by bodhi.zazen on 2009-04-01
> **faron45 said:**
> if I were to select "complete removal" & were to go into "synaptic package manager"sometime down the line...would I be able to find that program in the manager still ? That's I suppose what I'm worried about.

yes.

---

### Post by faron45 on 2009-04-01
> **bodhi.zazen said:**
> yes.

Thank you all very,very much for all your help.Now,if someone can tell me how to do this too...[damn newbies] I shalll mark this thread as "solved".
 Darnit...how DO you mark a thread as "solved" ?
 And...THANKS again !!

---

### Post by stchman on 2009-04-01
I was under the impression that that Complete Removal was like apt autoremove where it also removes unused dependencies.  I have found that Complete Removal does not remove ~/.xxxxx folders in the users home folder.

---

### Post by egalvan on 2009-04-01
In a "how-to" I read the following:


**To completely remove a package and leave no trace of it you would use the apt-get –purge remove command.**
```
sudo apt-get –purge remove* package-name*
```


Is this correct?
I have not experimented with this yet.

ErnestG

---

### Post by snova on 2009-04-01
> **egalvan said:**
> In a "how-to" I read the following:


**To completely remove a package and leave no trace of it you would use the apt-get &#8211;purge remove command.**
```
sudo apt-get &#8211;purge remove* package-name*
```


Is this correct?

Yes. The difference is just that --purge will remove configuration files, without that option it will leave them intact (good if you changed them, I guess).

I believe "Complete removal" is analogous to this option.

Also, it won't exactly leave "no trace", as the package manager will never touch files in your home directory- so if the program leaves per-user config files there, they will remain.

---

