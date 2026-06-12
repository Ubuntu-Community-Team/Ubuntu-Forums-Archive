---
title: "installing java 6"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by entropy7 on 2009-11-04
Hi-

Trying to install java 6 jre and plugin on Ubuntu 8.
Went to synaptic and searched for java6, but nothing was there.

typing java -version gives:

Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) Client VM (build 1.5.0_13-b05, mixed mode, sharing)

entered:
sudo aptitude update

then entered:
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font

lots of activity occurs but then says:
Couldn't find any package whose name or description matched "sun-java6-bin"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-font"

Downloaded all three packages, but I'm not sure if or where I should put
them.  did a sudo chmod 777.

still no good.

---

### Post by fooman on 2009-11-04
have you tried synaptic (system > administration > synaptic package manager)?

open it and search for sun

scroll through the results, check off and choose "mark for installation" the packages you are looking for.

hope that helps.

---

### Post by iansane on 2009-11-04
enable multiverse in the repos in synaptic and it should show up as sun-java6-jre and sun-java6-jdk if you want the java development kit too.

---

### Post by wmcbrine on 2009-11-04
What is "Ubuntu 8"? 8.04? 8.10?

Sun Java was, until recently, unfree. Make sure you have the multiverse repository enabled. (That's where I'm seeing it on my 8.04 system, but technically that's Ubuntu Eee, not Ubuntu; I assume it's the same on straight Ubuntu, but I'm not sure.)

---

### Post by mkvnmtr on 2009-11-04
If you are not finding it in the package manager you need to go to software sources and enable the repositories. I use all of them except the source code ones. Then you might wish to enable the medibuntu repository to wiew films. A simple google search ant the community docs page will tell you how.

---

### Post by entropy7 on 2009-11-04
the version is 8.04.

in the lower left corner of synaptic are 5 buttons:
sections, status, origin, custom filters, search results.

clicking "origins" brings up selections on left side, one of which is:

us.archive.ubuntu.com/multiverse

I assume this is what is meant by "multiverse". There do not seem to be any
Java packages coming up when this is selected, though.

---

### Post by fooman on 2009-11-04
in the top of synaptic,  click settings > repositories

when the "software sources" box opens...look under the "ubuntu software" tab and put a check next to the first 4 choices (main-universe-restricted-multiverse),  then click close.

you will see a warning that the repos have changed and need to be updated,  click close on that as well.

back in synaptic,  click on "reload"....when it finishes refreshing,  search for the sun packages again and you should find them.

---

### Post by entropy7 on 2009-11-05
thanks,  that did it!!

---

