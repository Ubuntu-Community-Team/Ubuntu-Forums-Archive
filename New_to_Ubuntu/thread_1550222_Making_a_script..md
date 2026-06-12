---
title: "Making a script."
date: 2010-08-10
forum: New to Ubuntu
---

### Post by aidenscool09 on 2010-08-10
So, I'm making a script to help newbies compile tar.gz files. Is there a way I can it unzip the file and go to the created directory? I have made it so it unzips it, but I want to know if I can make it automatically go to the folder it extracted. Thanks in advance.

---

### Post by Ozymandias_117 on 2010-08-10
> **aidenscool09 said:**
> So, I'm making a script to help newbies compile tar.gz files. Is there a way I can it unzip the file and go to the created directory? I have made it so it unzips it, but I want to know if I can make it automatically go to the folder it extracted. Thanks in advance.

It's not very advanced, but this is the best way I can think of off the top of my head.

```
#!/bin/bash
#Ozymandias_117

if [ ! $1 ]; then
	echo "Please enter the name of the file you wish to compile"
	read FILE
else
	FILE="$1"
fi

mkdir extract_program
cd extract_program

case $FILE in
	*.tar.bz2) tar xjf ../$FILE ;;
	*.tar.gz) tar xzf ../$FILE ;;
	*.tgz) tar xzf ../$FILE ;;
	*.tbz2) xjf ../$FILE ;;
	*) echo "I don't know how to handle that file!" ;;
esac

cd `ls -l | grep d | gawk '{ print $8 }'`

if [ -e ./source ]; then
	cd ./source
elif [ -e ./src ]; then
	cd ./src
fi

./configure
make
sudo make install
```

---

### Post by Ozymandias_117 on 2010-08-10
Just tried it, and it does work, as long as all dependencies are met.

---

### Post by sandyd on 2010-08-10
> **Ozymandias_117 said:**
> Just tried it, and it does work, as long as all dependencies are met.
should add 
```

sudo apt-get build-dep [appname]
```
you can awk the appname from the name of the file

---

### Post by Ozymandias_117 on 2010-08-10
> **carlee said:**
> should add 
```

sudo apt-get build-dep [appname]
```
you can awk the appname from the name of the file

I was trying to think of a way that would also work for packages not in the repositories, but yeah, that would help if they were.

---

### Post by aidenscool09 on 2010-08-12
Cheers mate. Here is what i've got until you told me that script:
```
#!/bin/bash

clear
echo "Hello, my name is John"
(sleep 2s)
clear
echo "I'm going to help you compile a program."
(sleep 2s)
clear
echo "So, where is the package?"
 read tarball
tar -zxvf $tarball ./
```

---

### Post by Zorgoth on 2010-08-12
I do not know how the return values on ./configure work, but if there is not a way to tell if you have all the dependencies, you should query the user whether they really would to go ahead with make, since there may be missing dependencies the user wants to install that ./configure brings to their attention.

---

### Post by aidenscool09 on 2010-08-12
well could i maybe make it install dependencies if it sees a part of the text which only comes up when the dependency isn't met e.g. "not installed" and if it sees that then it will correct it.

---

### Post by Ozymandias_117 on 2010-08-12
> **aidenscool09 said:**
> well could i maybe make it install dependencies if it sees a part of the text which only comes up when the dependency isn't met e.g. "not installed" and if it sees that then it will correct it.

I had already checked to see if configure files had something in them that showed the programs that needed to be installed in a way it would be easy to retrieve them, but unfortunately, they were all different.

To be able to do this, you'd probably need to output the results of ./configure into a text file, then grep the text file for not found and awk it to get the program you need. Finally you'd have to do an aptitude search to find it.

```
#Previous code here

./configure > make_results
NEEDED_PROG=`grep "not found" make_results`
if [ ! $NEEDED_PROG ]; then
make
sudo make install

else
while [ FOUND_PROG != "" ]; do
# Gawk for name of dependency
FOUND_PROG=`apt-cache search $NEEDED_PROG | grep -dev`
sudo aptitude install $FOUND_PROG
./configure > make_results
NEEDED_PROG=`grep "not found" make_results`
done
make
sudo make install
fi
```

Please note this was rushed through and I haven't tested any parts of it yet. This is just a basic outline/idea of what needs to be done.

---

### Post by aidenscool09 on 2010-08-12
Alright, i'm a bit busy at the mo. Gonna have to give it a go. But thanks for the help you're giving me.

---

### Post by aidenscool09 on 2010-08-12
I get an error with it :( I'm attatching a picture because i can't copy output from MRXVT...[IMG]http://i36.tinypic.com/13za42t.png[/IMG]

---

### Post by aidenscool09 on 2010-08-12
Oops, sorry about the large pic...

---

### Post by Ozymandias_117 on 2010-08-12
Sorry, that should have been if [ ! $NEEDED_PROG ]; then


But like I said, that code needs work before it's actually usable, I haven't looked at the output of a configure script to see what it needs to look for. Also, it will still need to gawk the name.

Hmm... you don't have gawk installed... Which is stopping the program from working too... I thought gawk was default in all installations o.O

Try changing "gawk" to "awk" see if you have that...

---

### Post by aidenscool09 on 2010-08-15
Ok, will do, I'm a bit busy at the moment though, but I'll get round to it eventually.

---

### Post by aidenscool09 on 2010-08-17
Ok, I got it working as far as I can see. Also, I made it delete the source folder after it finishes, because if the "extract_program" folder is still there, it gives an error. Thanks for your help.

---

