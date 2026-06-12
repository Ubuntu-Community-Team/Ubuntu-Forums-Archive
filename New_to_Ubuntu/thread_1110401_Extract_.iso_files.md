---
title: "Extract .iso files"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by dvdhaar on 2009-03-29
I wondered if there's a way to extract ISO files from the terminal? Without mounting it first?
You can simply rightclick and 'extract here' in nautilus, but I'm looking for a way to do it in CLI. unrar doesn't support iso files unfortunately.

Is there a way?

---

### Post by mkvnmtr on 2009-03-29
I believe the app ISO master will do what you want.

---

### Post by dvdhaar on 2009-03-29
> **mkvnmtr said:**
> I believe the app ISO master will do what you want.

Thanks for your reply, but it seems like it's only graphical:

```

ISO Master(1)                                                                  ISO Master(1)

NAME
       isomaster - an ISO image editor

SYNTAX
       isomaster [image.iso]

DESCRIPTION
       ISO  Master  is  an open-source, easy to use, graphical CD image editor for Linux and
       BSD. Basically you can use this program to extract files from an ISO, add files to an
       ISO, and create bootable ISOs - all in a graphical user interface.

       ISO Master can open ISO, NRG, and some MDF files but can only save as ISO.

OPTIONS
       The only command-line parameter supported is the name of the image to open.

AUTHORS
       Andrew Smith, < http://littlesvr.ca/misc/contactandrew.php >

       All other contributors are listed in the CREDITS.TXT file.

Andrew Smith                                1.3.1                              ISO Master(1)

```

And:

```

daniel@server:~$ isomaster test.ISO 
(isomaster:8719): Gtk-WARNING **: cannot open display: 

```

---

### Post by llamakc on 2009-03-29
From the Terminal.

```

sudo mkdir /media/iso
sudo mount -o loop -t iso9660 /path/to/file.iso /media/iso

```

From a GUI program:

```

sudo aptitude install gmountiso

```


[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

---

### Post by dvdhaar on 2009-03-29
> **llamakc said:**
> From the Terminal.

```

sudo mkdir /media/iso
sudo mount -o loop -t iso9660 /path/to/file.iso /media/iso

```

From a GUI program:

```

sudo aptitude install gmountiso

```


[http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html](http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html)

I am familiair with these solutions, but I'm looking for a way to extract an iso directly, without mounting it first.

---

### Post by llamakc on 2009-03-29
My bad. You stated that in the OP and I glossed over it. Have you tried PowerISO yet?

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)


[LIST]
[*]     **PowerISO     for Linux** -- This is a free utility for linux which can extract, list,     and convert image files (including ISO, BIN, DAA, and other formats).      Type " poweriso -? " for detailed usage information.  File Size: 278KB    [**Download Now**]("http://www.poweriso.com/poweriso-1.3.tar.gz") 
[/LIST]

---

### Post by dvdhaar on 2009-05-03
> **llamakc said:**
> My bad. You stated that in the OP and I glossed over it. Have you tried PowerISO yet?

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)


[LIST]
[*]     **PowerISO     for Linux** -- This is a free utility for linux which can extract, list,     and convert image files (including ISO, BIN, DAA, and other formats).      Type " poweriso -? " for detailed usage information.  File Size: 278KB    [**Download Now**]("http://www.poweriso.com/poweriso-1.3.tar.gz") 
[/LIST]

I can't get any further then this:

```
daniel@server:~$ tar xvf poweriso-1.3.tar.gz 
poweriso
daniel@server:~$ file poweriso
poweriso: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), statically linked, for GNU/Linux 2.2.5, stripped
daniel@server:~$ poweriso --help
-bash: poweriso: command not found
daniel@server:~$ poweriso
-bash: poweriso: command not found
```

Am I doing something wrong? Perhaps it's a GUI-style program?

---

### Post by dvdhaar on 2009-05-15
Anyone? :)

---

### Post by kanikilu on 2009-05-15
I assume wherever you extracted it to is not in your PATH environment variable, so cd to where the executable is, and then do:

```
./poweriso
```

---

### Post by kanikilu on 2009-05-15
Also, the default archive manager in Ubuntu can extract an ISO without mounting it:

```
file-roller -h filename.iso
```

**man file-roller** for other options.

7z can do it to. Install the **p7zip-full** package and then you can use:

```
7z x filename.iso
```

---

### Post by dvdhaar on 2009-05-15
Thanks for your reply :)

When using the file-roller I get this message, so apparently it's GUI only:

```

** (file-roller:27499): CRITICAL **: Failed to parse arguments: Cannot open display: 

```

And with 7zip I get this:
```

7-Zip  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: test.iso

Error: Can not open file as archive
```

Going to try the poweriso thing aswell though

---

### Post by dvdhaar on 2009-05-15
Cool! It works:

```
daniel@server:~$ ./poweriso extract test.iso / -od /home/daniel/isotest

PowerISO   Copyright(C) 2004-2008 PowerISO Computing, Inc
            Type poweriso -? for help

Extracting to /home/daniel/isotest/VIDEO_TS/VTS_03_1.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_03_0.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_03_0.IFO ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_03_0.BUP ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_4.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_3.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_2.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_1.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_0.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_0.IFO ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_02_0.BUP ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_01_1.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_01_0.VOB ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_01_0.IFO ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VTS_01_0.BUP ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VIDEO_TS.IFO ...   100%
Extracting to /home/daniel/isotest/VIDEO_TS/VIDEO_TS.BUP ...   100%

daniel@server:~$ 

```

So all I have to do now is to move the poweriso file into /bin/ and then I'll be able to execute it wherever I am right?

---

### Post by kanikilu on 2009-05-15
> **dvdhaar said:**
> So all I have to do now is to move the poweriso file into /bin/ and then I'll be able to execute it wherever I am right? Right, anywhere in your path will work ```
echo $PATH
```

---

### Post by clancyhood on 2012-05-13
:guitar:
Beautifully concise and well transacted forum advice (I love Ubuntu people). 
** p7zip-full** is the package needed by those on openvz to extract iso
:)

---

### Post by Utkarsh Ray on 2012-05-13
latest versions of 7zip extract almost everything

---

### Post by lisati on 2012-05-13
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217837&stc=1&d=1336887956[/IMG]

---

