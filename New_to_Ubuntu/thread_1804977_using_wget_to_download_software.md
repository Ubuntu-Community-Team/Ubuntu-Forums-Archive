---
title: "using wget to download software"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by margaux on 2011-07-15
[FONT=Tahoma][SIZE=2]Hi,

I'm trying to download a software package called MACH 1.0 with the command [/SIZE][/FONT]

wget [[COLOR=windowtext]http://www.sph.umich.edu/csg/abecasis/Merlin/download/mach2qtl.tar.gz[/COLOR]]("http://www.sph.umich.edu/csg/abecasis/Merlin/download/mach2qtl.tar.gz") 

[FONT=Tahoma][SIZE=2]But I'm getting this error message:[/SIZE][/FONT]

--2011-07-15 12:30:42--  [http://www.sph.umich.edu/csg/abecasis/Merlin/download/mach2qtl.tar.gz](http://www.sph.umich.edu/csg/abecasis/Merlin/download/mach2qtl.tar.gz)
Resolving [www.sph.umich.edu](www.sph.umich.edu)... 141.211.51.150
Connecting to [www.sph.umich.edu|141.211.51.150|:80](www.sph.umich.edu|141.211.51.150|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-07-15 12:30:42 ERROR 404: Not Found.
[FONT=Tahoma][SIZE=2]
What gives?

If it helps, this is the website where the download is coming from:
[http://www.sph.umich.edu/csg/abecasis/MACH/download/](http://www.sph.umich.edu/csg/abecasis/MACH/download/)

Thanks in advance for your replies![/SIZE][/FONT]

---

### Post by margaux on 2011-07-15
Whoops I just realized I had the Merlin line inserted in the wget address....but I changed it to MACH, and I'm getting the same error message.

---

### Post by Elfy on 2011-07-15
I right clicked the link - copy link location.

wget <paste> and it worked

different filename apparently to the one you've got, if you typed it out try copying the link location.

Works fine here.
```

hobgoblin@hobgoblin:~$ cd Desktop/
hobgoblin@hobgoblin:~/Desktop$ wget http://www.sph.umich.edu/csg/abecasis/MACH/download/mach2qtl.source.V110.tgz
--2011-07-15 17:36:14--  http://www.sph.umich.edu/csg/abecasis/MACH/download/mach2qtl.source.V110.tgz
Resolving www.sph.umich.edu... 141.211.51.150
Connecting to www.sph.umich.edu|141.211.51.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2639545 (2.5M) [application/x-tar]
Saving to: `mach2qtl.source.V110.tgz'

100%[======================================>] 2,639,545    470K/s   in 5.9s    

2011-07-15 17:36:21 (439 KB/s) - `mach2qtl.source.V110.tgz' saved [2639545/2639545]

hobgoblin@hobgoblin:~/Desktop$ 

```

---

### Post by margaux on 2011-07-15
Thanks! I just figured that out.

Another question for you -- once I

 tar xvzf mach.1.0.17.Linux.tgz
  

and all the files are listed, what do I do next in order to install and run the software?

---

### Post by Elfy on 2011-07-15
Reading the README is always a good start. 

There's a makefile in the extracted folder.

Running make from a terminal gives this

```
hobgoblin@hobgoblin:~/Desktop/mach2qtl.source.V110$ make
Generic Source Distribution
 
This Makefile will compile and install mach2qtl on your system
 
Type...           To...
make help         Display this help screen
make all          Compile everything 
make install      Install binaries in /usr/local/bin
make install INSTALLDIR=directory_for_binaries
                  Install binaries in directory_for_binaries
make clean        Delete temporary files

```

I'm not going any further with it - I don't want to install it :)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

