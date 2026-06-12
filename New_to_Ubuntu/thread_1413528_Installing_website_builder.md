---
title: "Installing website builder"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by Glen007 on 2010-02-22
Hello,
Newbie here.
I need to build a website using a WYSIWYG program as I have no HTML experience.
I have Serif on CD which I loaded to my desktop, but I'm having trouble installing it.
When I try "**sudo chmod a+x whateveryourfileiscalled.bin**, hit enter and then **./whateveryourfileiscalled.bin**."
As soon as I hit enter after the first line I get  "(sudo) pass word for bob" and nothing happens when I try typing, no text comes up in Terminal.
The website builder file name is z-sfwpx2.bin
Bear in mind this is the first time I've used Terminal as well.
Any help is much appreciated.
Thank you.

---

### Post by arochester on 2010-02-22
As far as I know Serif (Pageplus SE?) is a Microsoft Windows program and not a native Linux program. I think you need to use a Linux program like...KompoZer

---

### Post by ajgreeny on 2010-02-22
Some Serif windows apps will work in wine, so it's worth looking at the winehq site to see what their database of apps that work says about it.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by tom.swartz07 on 2010-02-22
> **Glen007 said:**
> Hello,
Newbie here.
I need to build a website using a WYSIWYG program as I have no HTML experience.
I have Serif on CD which I loaded to my desktop, but I'm having trouble installing it.
When I try "**sudo chmod a+x whateveryourfileiscalled.bin**, hit enter and then **./whateveryourfileiscalled.bin**."
As soon as I hit enter after the first line I get  "(sudo) pass word for bob" and nothing happens when I try typing, no text comes up in Terminal.
The website builder file name is z-sfwpx2.bin
Bear in mind this is the first time I've used Terminal as well.
Any help is much appreciated.
Thank you.

Why dont you try Eclipse? its made for Ubuntu, and its really nice for beginners!

[http://www.eclipse.org/](http://www.eclipse.org/)

---

### Post by sandyd on 2010-02-22
> **Glen007 said:**
> Hello,
Newbie here.
I need to build a website using a WYSIWYG program as I have no HTML experience.
I have Serif on CD which I loaded to my desktop, but I'm having trouble installing it.
When I try "**sudo chmod a+x whateveryourfileiscalled.bin**, hit enter and then **./whateveryourfileiscalled.bin**."
As soon as I hit enter after the first line I get  "(sudo) pass word for bob" and nothing happens when I try typing, no text comes up in Terminal.
The website builder file name is z-sfwpx2.bin
Bear in mind this is the first time I've used Terminal as well.
Any help is much appreciated.
Thank you.
the password doesnt show up for security reasons.
rest assured however, that your password is being entered.

---

### Post by thefoolisme on 2010-02-22
You could look in the following places for other linux based apps for web design.  i've used Nvu before, but there's Bluefish, and some others.  I know there's other lists, but this could help you get started if you don't want to try installing serif in Wine.

[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html#3](http://www.linuxrsp.ru/win-lin-soft/table-eng.html#3)

[http://www.desktoplinux.com/news/NS2844646285.html](http://www.desktoplinux.com/news/NS2844646285.html)

---

### Post by dmaxel on 2010-02-22
> **carlee said:**
> the password doesnt show up for security reasons.
rest assured however, that your password is being entered.^--- What she said. Even though you're typing, the characters will stay completely hidden so you don't even see those little stars/dots.

---

### Post by sandyd on 2010-02-22
> **dmaxel said:**
> ^---  What she said. Even though you're typing, the characters will stay completely hidden so you don't even see those little stars/dots.

the actual bug discussing this sudo no-asterisk problem is here: 

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/194472)

---

