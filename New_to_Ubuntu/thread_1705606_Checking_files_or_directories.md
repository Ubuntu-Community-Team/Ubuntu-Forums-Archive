---
title: "Checking files or directories"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by Jon Anderson on 2011-03-12
I'm told to go to /home/jbander/Downloads, so how do I do that, I assume you do it in terminal but what do you do next, I can get to home but thats it. How do I go from one directory or file or whatever they are, to another  and once I'm there what do I do to see what is in the download file. One more question if I want to change it from e.g. cow to e.g. duck how would I do that(they are just arbitrary names) how do I get rid of cow and how do I put duck in it's place.

---

### Post by Joeb454 on 2011-03-12
Changing directory in a terminal is done by ```
cd /home/user/Downloads
``` or alternatively, you can use relative paths, so when you open a terminal, simply typing ```
cd Downloads
``` would also work.

**Note:** The terminal is case sensitive, so using 'downloads' will _not_ work.

As for changing cow to duck, use **mv** ```
mv /path/to/cow /path/to/duck
``` The same note about relative paths applies here too :)

---

### Post by Perfect Storm on 2011-03-12
The use of **cd** : change directory

So if you want to change to /home/jbander/Downloads
```
cd /home/jbander/Downloads
```
or
```
 cd ~/Downloads
```


to see what's in that directory:
```
ls -a
```

---

### Post by jerome1232 on 2011-03-12
Tab completion is your friend, don't type whole names out, just get the first 2-3 characters then tap tab, it will autocomplete the name for your if there's enough characters for it to uniquely identify the directory/file you want.


ie if you had  a home folder and it contained these folders:

Downloads
Desktop
Documents
src
bin


and you wanted to cd into Desktop you can just type "De" then hit tab.

If you wanted Downloads you can type "Dow" and hit tab.

src? just type "s" and hit tab. etc....

---

### Post by PunkLV on 2011-03-12
Use this: [http://linuxcommand.org/](http://linuxcommand.org/)
Comprehensive and throughout guide of linux terminal.

---

