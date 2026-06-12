---
title: "cant install sun java 6.0 plugin"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by cormac616 on 2010-06-02
Ive tried to install sun java 6.0 plugin but its not showing an install icon on the software center.

Ive clicked on "more info" but it says: "To show information about this item, the software catalog needs updating"

Ive looked in the update manager but there are no updates.

[IMG]http://i257.photobucket.com/albums/hh215/cormacmonty/Screenshot.png[/IMG]
Any help would be appreciated.

---

### Post by Brandon Williams on 2010-06-02
If you click on 'Canonical Partners' in the sidebar, do you get a listing of items that includes, among others, 'Sun Java 6.0 Plugin'?

Also, in a terminal, run this command 'grep partner /etc/apt/sources.list'. What does the output look like?

---

### Post by gandaran on 2010-06-02
```
the software catalog needs updating
```
this message means you have to reload synaptic not look for updates, just click the reload button.
make sure you have the archive.canonical repo enabled in software sources

---

### Post by cormac616 on 2010-06-02
[IMG]http://i257.photobucket.com/albums/hh215/cormacmonty/partner.png[/IMG]

Nope its not in canonical partners tab.

---

### Post by cormac616 on 2010-06-02
> **gandaran said:**
> just click the reload button.



Where's this? sorry, im fairly new to Ubuntu, and thanks everyone for your quick response and help!

---

### Post by gandaran on 2010-06-02
> **cormac616 said:**
> Where's this? sorry, im fairly new to Ubuntu, and thanks everyone for your quick response and help!
open synaptic package manager, see the button top left corner

---

### Post by cormac616 on 2010-06-02
Nope still cant install after reloading it, the software sources seem correct? 

[IMG]http://i257.photobucket.com/albums/hh215/cormacmonty/Screenshot-1.png[/IMG]

---

### Post by gandaran on 2010-06-02
try installing using apt-get and post all the errors 
sudo apt-get install sun-java6-plugin

---

### Post by _Mark_ on 2010-06-02
Went through this last night myself, open a terminal
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
change lucid to whatever version you are running 

Then
```
sudo apt-get update && sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

That should be all the java you need

---

### Post by cormac616 on 2010-06-02
[IMG]http://i257.photobucket.com/albums/hh215/cormacmonty/Screenshot-2.png[/IMG]

---

### Post by _Mark_ on 2010-06-02
close the software centre and/or synaptic

---

### Post by gandaran on 2010-06-02
looks like some kind of problem not sure what but use synaptic to fix it, open synaptic and click the filters tab, check for any problem there like broken packages

---

### Post by _Mark_ on 2010-06-02
He is getting that error because he has either the software centre and /or synaptic open when trying to apt-get in the terminal, thats all

---

### Post by gandaran on 2010-06-02
> **_Mark_ said:**
> He is getting that error because he has either the software centre and /or synaptic open when trying to apt-get in the terminal, thats all
yes that's right, I should have known that!
he will have to close both to install using apt-get or keep one open and use it to install

---

### Post by cormac616 on 2010-06-02
Ahh thanks so much guys, got it working through Mark's method, 

Thank you all so much!

---

### Post by rmckee on 2010-06-02
i am new to ubuntu and i am tring to frostwire to work can someone help me please

---

### Post by AliceKingsley on 2010-09-06
> **_Mark_ said:**
> Went through this last night myself, open a terminal
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
change lucid to whatever version you are running 

Then
```
sudo apt-get update && sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
```

That should be all the java you need

Just wanted to give a huge thank you. I've been trying to get this to work for days.

---

### Post by _Mark_ on 2010-09-06
> **AliceKingsley said:**
> Just wanted to give a huge thank you. I've been trying to get this to work for days.

Your welcome 

:D

---

### Post by Muzicman16 on 2010-09-12
Hey guys. . .im having the same problem, ran the code like you said and it worked. but java still says my java is out of date (only version 6, update 18)

now, when the second command finished it gave me some error saying that not all the repositories could be updated and so they were either skipped or used an older version. that was fine because it let me install the java runtime. so now i just tried running the update manager to see if that would give me the current version of java and it gave me the same error and doesnt show any updates. Any ideas?

oh and one thing that i didnt do was change lucid to anything the first time, but then tried lucid lynx the second time (not sure if that makes a diffrence or what exactly you were asking me to change it to. would it be 10.04 lucid lynx?

exact error: "The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."
And in update manager after that it says: "Failed to fetch [http://archive.canonical.com/dists/lucid/Release](http://archive.canonical.com/dists/lucid/Release)  Unable to find expected entry  linx/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by Muzicman16 on 2010-09-15
help anyone?

---

