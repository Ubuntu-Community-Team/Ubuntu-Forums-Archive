---
title: "help me with this command?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by kingchipo on 2009-02-11
Well i found the drivers for my sound card and i have the commands i need but i keep getting these errors

For command:
       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .
and im getting error:
```
cp: cannot stat `/downloads/alsa-*': No such file or directory
dustin@dustin-desktop:/usr/src$        cd /usr/src
dustin@dustin-desktop:/usr/src$        mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
dustin@dustin-desktop:/usr/src$        cd alsa
bash: cd: alsa: No such file or directory
dustin@dustin-desktop:/usr/src$        cp /downloads/alsa-* .
cp: cannot stat `/downloads/alsa-*': No such file or directory

```

Why am i getting these errors?

Do i need to replace somthing? it seems to be a directory problem?

---

### Post by kingchipo on 2009-02-11
ok ive worked it down to 1 command

cp /downloads/alsa-* .

gives me the error:

cp: cannot stat `/downloads/alsa-*': No such file or directory

---

### Post by skymera on 2009-02-11
You can't make a directory in /usr/src unless you use sudo

sudo mkdir

And /downloads/alsa-*/ doesnt exist by the looks of it.
Is it typed correctly? case sensitive

---

### Post by Tony Flury on 2009-02-11
Where are you getting those string of instructions from ?

the instructions seem to be assuming that the /downloads/alsa-* directories exists, where clearly they don't.

The error message is tell you exactly that.

this suggests to ma that the instructions that you are trying to use are either incorrect (and would never work), or are specific to a particular type of system, and would need to be adapted to make them work for you.

---

### Post by kingchipo on 2009-02-11
Alright im getting these commands from this site..

[http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330]("http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330")

---

### Post by kingchipo on 2009-02-11
I think im just not executing these commands correctly?

---

### Post by kingchipo on 2009-02-11
OK 

Heres a summary of what ive gotten up to now

im trying to create the /download directory in

/usr/src/alsa

and i enter the command:

mkdir /downloads

and i get the error message:

mkdir: cannot create directory `/downloads': File exists

Yet when i type 

cp /downloads/alsa-* .

i get :

cp: cannot stat `/downloads/alsa-*': No such file or directory

---

### Post by kingchipo on 2009-02-11
anyone please?

---

### Post by tarps87 on 2009-02-11
The cp /downloads/alsa-* . command is copying any files/folders in /downloads/ which begin with alsa-
The instructions should like they want you to cp the file/folder you have downloaded in the /usr/src/alsa/ directory.
To do this replace /downloads/ with the path to you download, probably
~/Downloads/
or
~/Desktop/
(note it is case sensitive)

the . tell it to copy to the directory you are currently in, so cd to
/usr/src/alsa/

This is a root(admin) owned directory so you will need to use sudo to write to it. Sudo gives that command/process root/admin rights

So the command should be
```
cd /usr/src/alsa/
sudo cp /[i]pathToDownaload/alsa-* .
```

Note: you should leave it at least a day before bumping

---

### Post by nothingspecial on 2009-02-11
You`ve already got a directory called downloads in /usr/src/alsa.

It doesn`t look like you`ve got a directory that begins with alsa- though.

I`ve got 15 mins. If you can copy and paste the instructions you are following now perhaps I can help. Your link doesn`t work for me.

---

### Post by kingchipo on 2009-02-11
Make a directory to store the alsa source code in:

       cd /usr/src
       mkdir alsa
       cd alsa
       cp /downloads/alsa-* .

Now unzip and install the alsa-driver package:

       bunzip2 alsa-driver-xxx
       tar -xf alsa-driver-xxx
       cd alsa-driver-xxx
       ./configure --with-cards=cmi8330 --with-sequencer=yes ; make ; make install


heres the set of instructions there giving me

Thanks a bunch carp ill get right on trying them

..sorry for bumping so often i just only have this computer for about 10 more hours and need to get it fixed fast

---

### Post by handydan918 on 2009-02-11
One possible cause of that message is having the directory in question directly "below" you. IOW,
/home/username/directoryinquestion

if you attempt to do ```
cp /directoryinquestion <target>

```
you will get an error, because of the leading slash. It should look like ```
cp directoryinquestion <target>

```

HTH!

---

### Post by kingchipo on 2009-02-11
> **handydan918 said:**
> One possible cause of that message is having the directory in question directly "below" you. IOW,
/home/username/directoryinquestion

if you attempt to do ```
cp /directoryinquestion <target>

```
you will get an error, because of the leading slash. It should look like ```
cp directoryinquestion <target>

```

HTH!

i dont understand 

```
cp /directoryinquestion <target>

```
I still dont understand

[http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330](http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330)

THose are the instruction im trying to do to install a soundcard of mine...

---

### Post by tarps87 on 2009-02-11
What he means is copy command has two parameters
cp *source* *target*
*source* is the directory or file you want to copy
*target* is where you want the directory of file to be copyed to

Any path beginning with / is a path from the root/base of the filesystem, if there is no leading / it is from you current location in the file system
e.g.
If you are in /home/fred/
and you type
cp /aFile.txt /home/fred/files/
This will copy a file call aFile from the root of the file system (/) to /home/fred/files/
cp /aFile.txt files/
This will have the same effect as you are already in /home/fred

You can type pwd to find out which directory you are in

Have you downloaded the required file, if so where have you downloaded it to?

---

### Post by kingchipo on 2009-02-11
tarps i think my problem is im not filling in the correct places for example on the command

You have 

cp /downloads/alsa-* .

Now i understand so far that "/downloads" is the target of the function and 

Alsa-* is the output of the function? so to speak correct?

if you could visit this link...

[http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330](http://www.alsa-project.org/main/index.php/Matrix:Module-cmi8330)

Thats the page im trying to get through im simply trying to follow directions of not a linux user and have very little exsperience...

---

### Post by tarps87 on 2009-02-11
cp /downloads/alsa-* .

target(file to copy or in this case the files) = /downloads/alsa-* (where you put the files you have downloaded)
destination = '.'  (the location you currently are in)

From this page:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
you will need to download three packages:
[LIST]
[*]driver
[*]lib
[*]utils
[/LIST]

To make things easier download these files to the desktop, now type
```

cd /usr/src/alsa/
sudo cp ~/Desktop/alsa-* .
```

---

