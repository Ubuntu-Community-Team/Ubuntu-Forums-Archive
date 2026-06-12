---
title: "about .sh files"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by mreipr on 2010-08-11
[SIZE=4]Hi there....just installed lucid lynx 10.04.
 Total newbie on all this Linux macroworld
My question is ( probably for the 11,000th time):
How the make an .sh file executable ?

Looking forward for moron-proof answers.
[/SIZE]

---

### Post by inameiname on 2010-08-11
Right click the 'sh' file and select Properties, and under the Permissions tab, select "Allow executing as a program"

---

### Post by linux18 on 2010-08-11
your text is too large it hurts my eyes!

anyway, back to being serious, its a simple process:

1) grab a shell script, like this one:

```
 
#!/bin/bash
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```2) save it to a text file and rename the file yourscript.sh

3) goto a terminal and type chmod +x yourscript.sh

4) then execute by typing ./yourscript.sh

---

### Post by mastablasta on 2010-08-11
had the same quesiton, but now i know.

---

### Post by theboxseat on 2010-08-11
> **inameiname said:**
> Right click the 'sh' file and select Properties, and under the Permissions tab, select "Allow executing as a program"

And if you have not got access....

open terminal:

# gksudo nautilus

------This will open an "explorer like" window with super user rights
------Right click the 'sh' file and select Properties, and under the ------Permissions tab, select "Allow executing as a program"

;)

---

### Post by inameiname on 2010-08-11
Good addition to point out, theboxseat.

---

### Post by MooPi on 2010-08-11
I actually don't make my .sh scripts executable. I just open a terminal and ```
sh myexe.sh
```
Keeps me from accidentally executing while in the file manager.

---

### Post by jtarin on 2010-08-11
.sh,it is already executable.

---

### Post by MooPi on 2010-08-11
> **jtarin said:**
> .sh,it is already executable.

A casual click of the mouse doesn't execute though.

---

### Post by bodhi.zazen on 2010-08-11
> **jtarin said:**
> .sh,it is already executable.

Yes and not.

You can execute a .sh if you have permissions to read the file if you call it with sh

```
sh script.sh
```

But you need the file to be executable to call it directly

```
./script.sh
```

In addition , if you keep such scripts in ~/bin or /usr/local/bin (depending if you want user or global access) the script will be on your PATH.

In general "executable" means the permissions have been set to execute the script

```
chmod a+x script.sh
```

---

