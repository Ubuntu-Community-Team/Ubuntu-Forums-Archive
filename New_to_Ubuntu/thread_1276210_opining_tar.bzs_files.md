---
title: "opining tar.bzs files"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by bobevt on 2009-09-26
How do I open tar.bzs files using Ubunbtu 9.4 on a Toshiba L350,

Thank you Bobevt

---

### Post by hailtothethief on 2009-09-26
I think you might mean tar.bz2 files. All you should have to do is right click the file and then Click "Extract Here".

It should create a folder in the directory you're currently in.

---

### Post by bobevt on 2009-09-26
I have the  folder what do I do with it? Sorry but I'm very new at all this I love Ubuntu I never want to go back to windows!  Thank you for your help.

Bobevt

---

### Post by jms1989 on 2009-09-26
depends on what was in the .tar.bz2 archive. is it a program, data files, source files? If its a program than there should be an executable in the folder it created just double click that to run or run in a terminal. Source files need to be compiled to run so look for a readme or install text file for instruction on what to do with it.

---

### Post by bobevt on 2009-09-26
Quicktime for Linux requires a copy of of libmpeg3 in a directory next to itself. This provides the mp3 interface.
  Your directory structure should thus be:
 

/my_directory
/my_directory/libmpeg3-*.*.*
/my_directory/quicktime4linux-*.*.*
 type "make" in the libmpeg3 directory.
Type "configure" in the quicktime directory.
type "make" in the quicktime directory.
type "make util" to get quicktime to build some utilities.

I can not find the libmpeg3 file needless to say I'm lost :< And this is just the start!
Thanks 

Bobevt

---

### Post by MelDJ on 2009-09-26
isn't it in the 2nd line: /my_directory/libmpeg3-*.*.*?

---

### Post by bobevt on 2009-09-26
says it's not found ?

Thanks 
Bobevt

---

### Post by MelDJ on 2009-09-26
did you download the quicktime.tar.bz2 package? i hope link helps you install it: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by bobevt on 2009-09-26
yes I did, I'll check out the link Thanks a lot! :>

---

### Post by bobevt on 2009-09-27
Here is were I'm at now

bash: type: the: not found
bash: type: libmpeg3: not found
bash: type: directory.: not found
roland@roland-laptop:~$ Type "configure" in the quicktime directory.
bash: Type: command not found
roland@roland-laptop:~$ type "make" in the quicktime directory.
make is hashed (/usr/bin/make)
in is a shell keyword
bash: type: the: not found
bash: type: quicktime: not found
bash: type: directory.: not found
roland@roland-laptop:~$ type "make util" to get quicktime to build some utilities.clear
bash: type: make util: not found
bash: type: to: not found
bash: type: get: not found
bash: type: quicktime: not found
bash: type: to: not found
bash: type: build: not found
bash: type: some: not found
bash: type: utilities.clear: not found
roland@roland-laptop:~$ clear

roland@roland-laptop:~$ & cd ..
bash: syntax error near unexpected token `&'
roland@roland-laptop:~$ 
roland@roland-laptop:~$ cd libogg* && ./configure && cd ..
bash: cd: libogg*: No such file or directory
roland@roland-laptop:~$ 
roland@roland-laptop:~$ LIBOGG_PATH=`expr libogg*` && \
> cd libvorbis* && \
> CFLAGS="-I../../$LIBOGG_PATH/include -L../../$LIBOGG_PATH/src/" ./configure --enable-shared=no&& \
> cd ..
bash: cd: libvorbis*: No such file or directory
roland@roland-laptop:~$ 
roland@roland-laptop:~$ 
roland@roland-laptop:~$ 
roland@roland-laptop:~$ if [ `arch` == i686 ];
> then
> 
> cd jpeg-mmx* && ./configure && cd ..
> 
> fi
bash: arch: command not found
bash: [: ==: unary operator expected
roland@roland-laptop:~$ 
roland@roland-laptop:~$ 
roland@roland-laptop:~$ # success
roland@roland-laptop:~$ if [ $ERROR == 0 ];
> then echo "Configured successfully.  Type 'make' to build it.";
> fi
bash: [: ==: unary operator expected
roland@roland-laptop:~$ 
roland@roland-laptop:~$ 
roland@roland-laptop:~$ cd /quictime4linux-2.2
bash: cd: /quictime4linux-2.2: No such file or directory
roland@roland-laptop:~$ quicltime4limux-2.2
bash: quicltime4limux-2.2: command not found
roland@roland-laptop:~$ cd quictime4linux-2.2
bash: cd: quictime4linux-2.2: No such file or directory
roland@roland-laptop:~$ clear

roland@roland-laptop:~$ Your directory structure should thus be:
bash: Your: command not found
roland@roland-laptop:~$ /my_directory
bash: /my_directory: No such file or directory
roland@roland-laptop:~$ /my_directory/libmpeg3-*.*.*
bash: /my_directory/libmpeg3-*.*.*: No such file or directory
roland@roland-laptop:~$ /my_directory/quicktime4linux-*.*.*
bash: /my_directory/quicktime4linux-*.*.*: No such file or directory
roland@roland-laptop:~$ 
roland@roland-laptop:~$ 
roland@roland-laptop:~$ type "make" in the libmpeg3 directory.
make is hashed (/usr/bin/make)
in is a shell keyword
bash: type: the: not found
bash: type: libmpeg3: not found
bash: type: directory.: not found
roland@roland-laptop:~$ type "make" in the quicktime directory.
make is hashed (/usr/bin/make)
in is a shell keyword
bash: type: the: not found
bash: type: quicktime: not found
bash: type: directory.: not found
roland@roland-laptop:~$ type "make util" to get quicktime to build some utilities.
bash: type: make util: not found
bash: type: to: not found
bash: type: get: not found
bash: type: quicktime: not found
bash: type: to: not found
bash: type: build: not found
bash: type: some: not found
bash: type: utilities.: not found
roland@roland-laptop:~$ 


:confused:   Thanks for taking the time to read this

Bobevt

---

### Post by kevdog on 2009-09-27
Since it looks like you are trying to compile did you install the build-essential package?

sudo aptitude install build-essential

---

### Post by MelDJ on 2009-09-27
i think some of the codes you typed in terminal are incorrect. make sure you type in the proper code and in the correct case too

---

### Post by bobevt on 2009-09-27
Thank you I'll give it another go.

---

### Post by bobevt on 2009-10-07
Thanks everyone I got it. 
Bobevt

---

