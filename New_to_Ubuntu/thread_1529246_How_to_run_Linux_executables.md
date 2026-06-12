---
title: "How to run Linux executables?"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by camn on 2010-07-12
I'm trying to run ePSXe, a PSX emulator, so I downloaded the linux executable but I don't know what to do with it >_< Hellpppp

---

### Post by themusicalduck on 2010-07-12
Right click on the file and go to Properties. On the Permissions tab, check that Allow executing file as program is checked. If it is, then you should just be able to double click on it to run it.

If not, then open a terminal (applications>accessories>terminal) and navigate to the folder it is in. (If it was on the desktop in a folder called ePSXe then use command ```
cd ~/Desktop/ePSXe
```

Then type ./ePSXe (or whatever the name of the binary is called with a ./ before it) to run it.

---

### Post by potat on 2010-07-12
Or to do it all from the command line:
```

cd ~/Desktop/epsxe160lin/
# or wherever you unpacked the zip

# the executable is the file "epsxe", so
chmod +x epsxe
# this changes the file permissions so that the executable can be run.
# Anything you download from the 'net will require you to do this for security reasons

./epsxe
# the dot (.) refers to the current directory. 
# For executables you must always give a file path because otherwise it will search through the system binary folders.

```

For the future, the executable is usually the file that doesn't have an extension. Some executables do, but those are usually scripts (e.g. shell script uses ".sh" and Python script uses ".py").

---

### Post by camn on 2010-07-12
> **themusicalduck said:**
> Right click on the file and go to Properties. On the Permissions tab, check that Allow executing file as program is checked. If it is, then you should just be able to double click on it to run it.

If not, then open a terminal (applications>accessories>terminal) and navigate to the folder it is in. (If it was on the desktop in a folder called ePSXe then use command ```
cd ~/Desktop/ePSXe
```Then type ./ePSXe (or whatever the name of the binary is called with a ./ before it) to run it.
It gave me an error, > cam@cam-laptop:~/ePSXe$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


---

### Post by camn on 2010-07-12
> **potat said:**
> Or to do it all from the command line:
```

cd ~/Desktop/epsxe160lin/
# or wherever you unpacked the zip

# the executable is the file "epsxe", so
chmod +x epsxe
# this changes the file permissions so that the executable can be run.
# Anything you download from the 'net will require you to do this for security reasons

./epsxe
# the dot (.) refers to the current directory. 
# For executables you must always give a file path because otherwise it will search through the system binary folders.

```For the future, the executable is usually the file that doesn't have an extension. Some executables do, but those are usually scripts (e.g. shell script uses ".sh" and Python script uses ".py").
And that's basically the same thing, no? Just marking it as an executable from the terminal?

---

### Post by 3rdalbum on 2010-07-12
isn't   there   already   a   Playstation   emulator   in   the   repositories?

Your   error   message   says   that   you   need   to   install   'libgtk-1.2'   from   the   package   mabager.

---

### Post by camn on 2010-07-12
> **3rdalbum said:**
> isn't   there   already   a   Playstation   emulator   in   the   repositories?

Your   error   message   says   that   you   need   to   install   'libgtk-1.2'   from   the   package   mabager.
Yeah, but I have saved games and stuff on a USB drive, and they'll only work with this emulator >_<
And I didn't see "libgtk-1.2" in synaptic.

---

### Post by potat on 2010-07-16
> **camn said:**
> And that's basically the same thing, no? Just marking it as an executable from the terminal?

Yep, it's the same (except more fun, of course!)

---

### Post by JustinR on 2010-07-16
> **camn said:**
> I'm trying to run ePSXe, a PSX emulator, so I downloaded the linux executable but I don't know what to do with it >_< Hellpppp

Hi,

Not really related to ePSXe but if you want to be able to execute linux scripts (I believe just my double clicking it instead of the command line) There is a program called App Runner. 

Its a very nice and easy to use program [http://hacktolive.org/wiki/App_Runner](http://hacktolive.org/wiki/App_Runner)

---

### Post by mrphud on 2010-07-17
Have you looked in the .tar.gz or the unpacked folder to see if there is a .txt file for install/run directions. 

Most all of the programs I have to download and install manually have one. 

Or there is some .deb file on sourceforge that allows you to get it. It might help to look for one of those.

---

