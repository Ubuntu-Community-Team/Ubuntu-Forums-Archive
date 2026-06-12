---
title: "Dealing with spaces in Command Line"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Dreigo42 on 2010-01-25
Been using Ubuntu and variants for about a year now and I am starting to learn the Terminal but I just can't seem to get the hang of spaces in folder names. I have a folder I named "Disk Images" in /home/*user*/Documents/Disk Images/ but I can only cd as far as Documents. when I try [ cd Disk Images] I get [bash: cd: Disk: No such file or directory]. Can anyone tell me what I'm doing wrong so I can beat my head on my keyboard?

---

### Post by ankspo71 on 2010-01-25
hi, any of these commands should help.
```
/home/user/Documents/Disk\ Images/
"/home/user/Documents/Disk Images/"
'/home/user/Documents/Disk Images/'
```the backwards slash tells the terminal that the following space should be treated as a space in a directory path, not as a space used to separate a second command.
Hope this helps.

---

### Post by beauty. proletariat on 2010-01-25
I'm newer than you but maybe putting inverted commas will help?

like this:

 /home/*user*/Documents/'Disk Images'/

also try

' /home/*user*/Documents/Disk Images/'

lol this comes from knowledge of cmd though

---

### Post by LuisGMarine on 2010-01-25
Yeah a rule of thumb when using Linux is to always use under scores for spaces.  

To access your folder replace the space with a "\"

for example:

```
cd /home/Downloads/awesome\ movies
```

If you can navigate to it using nautilus and change the folder name to something that uses underscore as the space =P

---

### Post by freak42 on 2010-01-25
Hi

try pressing tab to auto expand your pathnames on the command line.. it helps ALOT especially with spaces in the names.. so try typing

cd /home/user/Documents/Disk[TAB] 

and it should expand your path (expect if there are of course multiple directories there that start with Disk.

hth

---

### Post by Paqman on 2010-01-25
+1 for tab autocomplete. Sod typing out the whole path.

Personally I would type:
```
cd ~/Do<TAB>/Di<TAB>
```

---

