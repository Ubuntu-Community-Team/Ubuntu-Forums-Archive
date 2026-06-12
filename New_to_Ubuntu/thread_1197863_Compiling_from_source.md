---
title: "Compiling from source?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by musicguyguy on 2009-06-26
I downloaded the source for [VBALink]("http://vbalink.info"), and when i unzipped the file to /usr/local/src/V172lsrc (as recommended by the [compiling tutorial]("https://help.ubuntu.com/community/CompilingEasyHowTo")) and tried the "make" command.

I get this:
```
jonathan@ubuntu-presariom2000:~$ make
make: *** No targets specified and no makefile found.  Stop.
jonathan@ubuntu-presariom2000:~$ make /usr/local/src/V172lsrc/
make: Nothing to be done for `/usr/local/src/V172lsrc/'.

```

What exactly am I supposed to do?

---

### Post by WRDN on 2009-06-26
There is no configuration file/ make file/ other GNU Build files located in the file you attached, so you must compile it manually (you may want to write the makefile yourself).

You can use the following script I wrote recently to make life easier for yourself. It will run the GNU Build process for you, creating a configure script, make file, then running them.

```
#! /bin/sh

echo "Starting GNU Build Process!"

if [ $# != 4 ]
then
echo "Format: ./BUILD.sh [location] [ProgramName] [Version] [Bug Report Address]"
echo "Must provide location of Makefile.am, program name, program version and bug report address!"
exit
fi

cd $1

rm config.h

find . -name '*.cpp' -o -name '*.h' > /tmp/fndOP
while read line
do
VAR=$VAR" "$line
done < "/tmp/fndOP"
echo $VAR
rm /tmp/fndOP

rm Makefile.am
echo "bin_PROGRAMS = $2" > Makefile.am
echo ""$2"_SOURCES = $VAR" >> Makefile.am


PROGNAME=$2
VERS=$3
BUGREP=$4

# Check if Makefile.am exists. If it doesnt, make one and exit

if [ -e "Makefile.am" ]
then
echo "Makefile.am found"
else
echo "Makefile.am does not exist"
echo "A blank file has just been created. Please edit this to add the bin and sources"
touch Makefile.am
exit
fi

touch configure.ac
autoscan
cp configure.scan configure.ac

sed '6i\AM_INIT_AUTOMAKE' configure.ac > conf1596
cp conf1596 configure.ac
rm conf1596
sed "5s/AC_INIT(FULL-PACKAGE-NAME, VERSION, BUG-REPORT-ADDRESS)/AC_INIT($PROGNAME, $VERS, $BUGREP)/" configure.ac > conf1596
cp conf1596 configure.ac
rm conf1596

aclocal
autoheader
touch NEWS README ChangeLog
echo "Built by: $BUGREP" > AUTHORS
automake -a
autoconf
./configure
cd $1
make dist-gzip
make
```

It's not perfect, but it does the job.
You need to run it from the top level where the source is located (/usr/local/src/V172lsrc/).

---

### Post by bodhi.zazen on 2009-06-26
Usually you run ./configure

to see your options try

./configure --help

Typical useage

```
./configure --prefix=/usr/local
make
sudo make install
```

---

### Post by musicguyguy on 2009-06-30
> **WRDN said:**
> 

You can use the following script I wrote recently to make life easier for yourself. It will run the GNU Build process for you, creating a configure script, make file, then running them.



Wait, so what exactly do I do with the script? I've saved it to a file ("compile script") in the folder. Am I supposed to run it in Terminal?


EDIT:
Ah, never mind. I figured it out.
But then I get

```

jonathan@ubuntu-presariom2000:~$ /usr/local/src/V172lsrc/compile.sh
Starting GNU Build Process!
Format: ./BUILD.sh [location] [ProgramName] [Version] [Bug Report Address]
Must provide location of Makefile.am, program name, program version and bug report address!

```

So am I supposed to enter the location, program name, version, and bug report address?
...I'm a noob, so can you do a step by step walkthrough? :D

---

### Post by Paqman on 2009-06-30
Have you tried vbaexpress? It's a Gameboy emulator that's available in the repos. No compiling required.

---

### Post by musicguyguy on 2009-06-30
> **Paqman said:**
> Have you tried vbaexpress? It's a Gameboy emulator that's available in the repos. No compiling required.
Actually I'm just looking for something that can link.

---

### Post by shae on 2009-06-30
You should download this one: [https://sourceforge.net/project/downloading.php?group_id=63889&filename=VisualBoyAdvance-src-1.7.2.tar.gz&a=42787039](https://sourceforge.net/project/downloading.php?group_id=63889&filename=VisualBoyAdvance-src-1.7.2.tar.gz&a=42787039)

Then use ./configure, make, and make install.

But I would suggest a different one since that was last updated in 2004 from what I can tell.

---

### Post by Paqman on 2009-06-30
One good tip if you are compiling: use checkintstall.

Install it then replace the make install step with checkinstall. It should whip up a .deb package so that the package manager knows about it. Generally speaking circumventing the package manager by compiling is possible source of instability.

---

### Post by musicguyguy on 2009-06-30
> **shae said:**
> You should download this one: [https://sourceforge.net/project/downloading.php?group_id=63889&filename=VisualBoyAdvance-src-1.7.2.tar.gz&a=42787039](https://sourceforge.net/project/downloading.php?group_id=63889&filename=VisualBoyAdvance-src-1.7.2.tar.gz&a=42787039)

Then use ./configure, make, and make install.

But I would suggest a different one since that was last updated in 2004 from what I can tell.
Yes, that's the original VBA that I'm running on Ubuntu right now. VBALink (with linking capabilities) doesn't have a Linux port yet, but they offer the source code on their website.

---

