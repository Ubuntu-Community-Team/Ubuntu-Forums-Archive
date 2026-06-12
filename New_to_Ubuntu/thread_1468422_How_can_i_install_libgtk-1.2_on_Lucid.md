---
title: "How can i install libgtk-1.2 on Lucid?"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by Gustavo Daniel on 2010-05-01
Hi, i'm trying to install Canon iP1300 printer, following this instructions: [http://ubuntuforums.org/showthread.php?p=3450617](http://ubuntuforums.org/showthread.php?p=3450617), but, when i try to install  libgtrk-1.2, with:

$ sudo apt-get install libgtk-1.2

happens:

E: Impossível achar pacote libgtk-1.2

and in Ubuntu packages, only have for Dapper, Hardy, Intrepid and Jaunty. Nothing about Lucid.

So how can i install libgtk-1.2?

[s]Sorry for the bad english![/s]

---

### Post by zer0pulse on 2010-05-04
Not sure about you but this worked for me.

Download these files (i386 when you're given a choice).
[http://packages.ubuntu.com/hardy/libgtk1.2-common](http://packages.ubuntu.com/hardy/libgtk1.2-common)
[http://packages.ubuntu.com/hardy/libglib1.2ldbl](http://packages.ubuntu.com/hardy/libglib1.2ldbl)
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

"hardy" is the 8.04 version of ubuntu, if you need something newer replace it with "intrepid" or "jaunty".
Karmic (9.10) and Lucid (10.04) don't seem to have packages built, but the 8.04 packages work for me on 10.04.

Go to a Terminal, and type these commands for each file in the order listed above.
sudo dpkg -i --force-architecture <file you downloaded>

Hope that helps!

---

### Post by jvc26 on 2010-05-04
[http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all) would suggest that the last libgtk1.2 was in Jaunty... is there a reason you have to use an old library?

Were you to have to you could manually download the old Jaunty packages from packages.ubuntu which would probably work.
J

---

### Post by xumuk37 on 2010-05-04
sudo apt-get install gtk* if you vant it for Lucid. this will download and install all libraries with dependencies.

---

### Post by zer0pulse on 2010-05-04
> **jvc26 said:**
> [http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=all&section=all) would suggest that the last libgtk1.2 was in Jaunty... is there a reason you have to use an old library?


My point was that they're old libraries anyway so it wouldn't be necessary to install the latest, so why not use the last LTS (hardy) for what you need it for?
In my case I was trying to install a game ([Uplink]("http://www.introversion.co.uk/uplink/") by [Introversion]("http://www.introversion.co.uk/")) that wouldn't get past the install script because it complained about not having libgtk1.2

Like I said, it worked for me, so it might work for him.

---

### Post by Eddie Lee on 2010-06-25
Hello, Im having the same problem, I need to install Wolf: ET 2.55 which I can only find in a .run file, I execute the file and I get that same error, I want to try the solutions provided here but since Im fairly new to linux I dont know if installing previous versions of this file will override or cause any problems with my current version libgtk2 (in Lucid Lynx)and any other programs using it, if I install it (and I get issues regarding it), can I just simply remove it using $ rm libgtk-1.2?, or how could I fix it should it give me any problems.

Thank you for your time

---

### Post by Perfect Storm on 2010-06-26
> **Eddie Lee said:**
> Hello, Im having the same problem, I need to install Wolf: ET 2.55 which I can only find in a .run file, I execute the file and I get that same error, I want to try the solutions provided here but since Im fairly new to linux I dont know if installing previous versions of this file will override or cause any problems with my current version libgtk2 (in Lucid Lynx)and any other programs using it, if I install it (and I get issues regarding it), can I just simply remove it using $ rm libgtk-1.2?, or how could I fix it should it give me any problems.

Thank you for your time

libgtk1.2 will not override libgtk2
If you install the .deb package you can simple remove them via synaptic package manager.

---

### Post by Eddie Lee on 2010-06-26
> **Artificial Intelligence said:**
> libgtk1.2 will not override libgtk2
If you install the .deb package you can simple remove them via synaptic package manager.

Great, thanks for responding so quickly :D

---

