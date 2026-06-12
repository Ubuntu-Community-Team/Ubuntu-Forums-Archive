---
title: "[SOLVED] Command to add repositories?"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by J03y on 2009-08-03
Hi,
I was wondering if there's a command to add repositories.

---

### Post by oldsoundguy on 2009-08-03
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by coldReactive on 2009-08-03
Might want to check this:

[http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html](http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html)

---

### Post by drs305 on 2009-08-03
There is actually a "sister" page to the one oldsoundguy posted, specifically for the command line:
[https://help.ubuntu.com/community/Repositories/CommandLine]("https://help.ubuntu.com/community/Repositories/CommandLine")

---

### Post by J03y on 2009-08-03
> **coldReactive said:**
> Might want to check this:

[http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html](http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html)
I was already in that page, but it says that I need to backup the original file. And I just want to add a repository to the original source.list

---

### Post by drs305 on 2009-08-03
> **J03y said:**
> I was already in that page, but it says that I need to backup the original file. And I just want to add a repository to the original source.list

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak  # Backup
gksudo gedit /etc/apt/sources.list  # Open for editing and add applicable entry

```

The format is:
> 
*deb address codename section*

Example: 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy  multiverse

---

### Post by slakkie on 2009-08-03
> **J03y said:**
> I was already in that page, but it says that I need to backup the original file. And I just want to add a repository to the original source.list

making a backup is not that difficult to do:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
nano /etc/apt/sources.list
# edit edit edit

```

---

### Post by J03y on 2009-08-03
> **coldReactive said:**
> Might want to check this:

[http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html](http://www.ubuntugeek.com/addrepo-easiest-way-to-add-apt-repositories.html)
Thanks! :)

---

### Post by J03y on 2009-08-03
> **drs305 said:**
> ```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak  # Backup
gksudo gedit /etc/apt/sources.list  # Open for editing and add applicable entry

```
Im planning on making a script to do everything so I wont have to do it manually cause its a real pain doing it manually every time I re-install Ubuntu.

---

### Post by slakkie on 2009-08-03
Ok, check out this script:

[http://www.zoef-pc.nl/zooi/multimedia.sh](http://www.zoef-pc.nl/zooi/multimedia.sh)

Here we add medibuntu repo's for multimedia stuff. But why not make a sources.list file, put it online somewhere and do this:

sudo wget [http://your.domain.tld/our/sources/sources.list](http://your.domain.tld/our/sources/sources.list) /etc/apt/sources.list

And, why would you reinstall Ubuntu so many times that you need such a thing anyways?

---

### Post by drs305 on 2009-08-03
> **J03y said:**
> Im planning on making a script to do everything so I wont have to do it manually cause its a real pain doing it manually every time I re-install Ubuntu.

Yeah, we strayed from the original "command line" requirement.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.`date +%F`
echo "deb address codename section" | sudo tee -a /etc/apt/sources.list

```

---

### Post by J03y on 2009-08-03
> **slakkie said:**
> making a backup is not that difficult to do:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bk
nano /etc/apt/sources.list
# edit edit edit

```
I know I've already done that before. This may sound weird but I actually feel more secure not making a backup cause last time I did that, when I was adding repositories I kinda got confused and added the repositories in the wrong file and messed up Ubuntu. :?

---

### Post by J03y on 2009-08-03
> **drs305 said:**
> Yeah, we strayed from the original "command line" requirement.

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.`date +%F`
echo "deb address codename section" | sudo tee -a /etc/apt/sources.list

```
Thanks! :)

---

### Post by egalvan on 2009-08-03
> **J03y said:**
> This may sound weird but I actually feel more secure **not making a backup** cause last time I did that,
 when I was adding repositories I kinda got confused and **added the repositories in the wrong file** and messed up Ubuntu. :?

How can making a back-up, then choosing the wrong file to edit,
be related? :)

If you gave the back-up the wrong name, then you should get into 
the habit of always using a standard extension, such as bak.

or add a '~' to the name... 
on my system, this turns it into a 'backup file" type.

gedit always makes backups, names them with the '~' added on, which show as "back-up file".

---

### Post by J03y on 2009-08-03
> **egalvan said:**
> How can making a back-up, then choosing the wrong file to edit,
be related? :)

If you gave the back-up the wrong name, then you should get into 
the habit of always using a standard extension, such as bak.

or add a '~' to the name... 
on my system, this turns it into a 'backup file" type.

gedit always makes backups, names them with the '~' added on, which show as "back-up file".
Maybe I put in the wrong terms. By "messed up" I meant that I felt that my Ubuntu installation had a lot of files and just didn't want to add more "useless files" to the collection. Felt that it had a lot of garbage inside and just wanted it to stay clean :) lol

---

### Post by sisco311 on 2009-08-03
if you want to add more than a line, then:
```
cat << EOF | sudo tee -a /etc/apt/sources.list
deb addrs1 codename section
deb addrs2 codename section
EOF

```

---

### Post by J03y on 2009-08-03
Thanks I already solved it :) . So how do I mark it as solved?

---

### Post by drs305 on 2009-08-03
> **J03y said:**
> Thanks I already solved it :) . So how do I mark it as solved?

At the bottom right of the thread you can select the "Edit tags" button and add a "solved" tag. You can also rename the original post via Edit, Go Advanced, and  adding [SOLVED].

---

### Post by egalvan on 2009-08-03
> **J03y said:**
> Maybe I put in the wrong terms. By "messed up" I meant that I felt that my Ubuntu installation had a lot of files and just** didn't want to add more "useless files" to the collection.** Felt that it had a lot of garbage inside and just wanted it to stay clean :) lol

Wow, then I better not tell you that my system shows
469,522 items, totaling 393.5GB !! :D

---

