---
title: "update error"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by enoac on 2009-02-22
i dont know what i did, but when i try to use the update manager or the add remove programs thing i get this message 


'E:Type '--2009-02-18' is not known on line 1 in source list /etc/apt/sources.list.d/mebiduntu.list, E:The list of sources could not be read.'
 
what should i do?

---

### Post by geirha on 2009-02-22
To start, post the content of /etc/apt/sources.list.d/mebiduntu.list. It's complaining that there is something in that file it doesn't understand.

---

### Post by Perfect Storm on 2009-02-22
> **geirha said:**
> To start, post the content of /etc/apt/sources.list.d/mebiduntu.list. It's complaining that there is something in that file it doesn't understand.

Open the terminal and do this;
```
cat /etc/apt/sources.list
```

post the output of it.

---

### Post by enoac on 2009-02-22
how do you post the output?

---

### Post by Perfect Storm on 2009-02-22
copy and paste;

When you run the command;
```
cat /etc/apt/sources.list
```
in the terminal, it will spit out alot of output. Mark it and post it here.

---

### Post by shifty_powers on 2009-02-22
put the above into a terminal. then highliht the output, press control+shift+c and paste it into code tags...

---

### Post by geirha on 2009-02-22
The file called /etc/apt/sources.list.d/medibuntu.list is of more interest than /etc/apt/sources.list though, since it specifically mentions that file. You can open it in the regular text editor as well if you prefer to not use the terminal.

---

### Post by enoac on 2009-02-22
um.... whats a code tag? and where do i find it?

---

### Post by geirha on 2009-02-22
> **enoac said:**
> um.... whats a code tag? and where do i find it?

After you have pasted the data from the file into the text-box of the forum, mark the text you just pasted and click the # icon near the top right of the text-box. (if there's no # icon, click the "Go Advanced" Button.

---

### Post by enoac on 2009-02-22
here is what it spits out with cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse[CODE]
```[/CODE]

---

### Post by clive littlewood on 2009-02-22
Hi

The code tag is on the reply page (the hash sign)

Press this and put your copied text between the signs.      :D

Clive

---

### Post by geirha on 2009-02-22
/etc/apt/sources.list looks fine. Could you post /etc/apt/sources.list.d/medibuntu.list as well?

---

### Post by enoac on 2009-02-22
> **geirha said:**
> To start, post the content of /etc/apt/sources.list.d/mebiduntu.list. It's complaining that there is something in that file it doesn't understand.

here is what it the output is of /etc/apt/sources.list.d/mebiduntu.list ```
--2009-02-18 00:54:51--  http://http//www.medibuntu.org/sources.listd/intrepid.list%20-o%20/etc/apt/sources.list.d/mebiduntu.list%0Asudo%20apt-get%20update%0Asudo%20apt0get%20instal%20medibuntu-keyring%20&&%20apt-get%20update%0Asudo%20wget%20http//www.medibuntu.org/sources.listd/intrepid.list
Resolving http... failed: Name or service not known.
wget: unable to resolve host address `http'
```

---

### Post by geirha on 2009-02-22
Yes, the wget command you used when adding the medibuntu repository failed and instead put an error message in the file. Try it again:

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

```

Alternatively, you can open the file in a texteditor with ```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
``` and replace the content of the file with the content of the page at [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) (This is what the wget command does)

---

### Post by enoac on 2009-02-22
this is the output of sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

```
wget: /etc/apt.sources.list.d/medibuntu.list: No such file or directory

```

and just changing the stuff in the file with the text editor didn't work either.

---

### Post by enoac on 2009-02-22
so i typed it in wrong. but when i corrected it i got this 



--2009-02-22 11:58:38--  [http://www.medibuntu.org/sources.list.d/interpid.list](http://www.medibuntu.org/sources.list.d/interpid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-02-22 11:58:44 ERROR 404: Not Found.

---

### Post by JohnFH on 2009-02-22
Strange as the server doesn't report that error to me.  Anyway the contents of that file (intrepid.list) is:

```

## Medibuntu - Ubuntu 8.10 "intrepid ibex"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ intrepid free non-free
#deb-src http://packages.medibuntu.org/ intrepid free non-free

```

Put the above text either into the /etc/apt/sources.list file or a new file (call it medibuntu.list) and put the new file into /etc/apt/sources.list.d/

---

### Post by enoac on 2009-02-22
even with that i still get the same error. is there a way to just completly remove that repository? or would that not fix it?

---

### Post by enoac on 2009-02-22
ok i got it fixed. i had to go in and delete all the files related to it and then remove it from the sources list. so it works now. thanks for all your help!

---

