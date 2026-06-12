---
title: "When is tar not a tar"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by patC42 on 2009-09-12
Hi Guys, Its my first time so be gentle with me. Im trying to give Gnugo a graphical frontend (I think) with cgoban-1.9.14.tar.gz by using tar xvf- cgoban-1.9.14.tar.gz and it is coming up with This does not look like a tar archive. Is this a Ubuntu thing as I have had it working on Mandriva. (although I can't exactly remember how I did it). I also tried the jago. jar option when cgoban failed and seemed to be trying to connect to a server but didnt realy understand what I was doing

---

### Post by Bachstelze on 2009-09-12
You must use [font=monospace]tar xzvf[/font] to extract gzipped tarballs.

---

### Post by wojox on 2009-09-12
Try:

```
tar xzvf cgoban-1.9.14.tar.gz
```

---

### Post by patC42 on 2009-09-12
Im still getting the same error with tar xzvf

---

### Post by wojox on 2009-09-12
What happens if you right click and extract here?

---

### Post by patC42 on 2009-09-12
It does the same thing. This does not look like a tar archive.

---

### Post by Bachstelze on 2009-09-12
> **patC42 said:**
> Im still getting the same error with tar xzvf

Paste the exact command you type, and the exact output you get.

---

### Post by patC42 on 2009-09-12
pat@pat-desktop:~/Desktop$ tar xzvf cgoban-1.9.14.tar.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Error exit delayed from previous errors

---

### Post by wojox on 2009-09-12
I just went and downloaded it and it worked fine. Try re-downloading it.

---

### Post by KIAaze on 2009-09-12
Maybe your download is corrupted.
It worked perfectly for me.
```
[80][~/Desktop]$  md5sum cgoban-1.9.12.tar.gz cgoban-1.9.14.tar.gz
11894899d6fe83b47effac9b935a99db  cgoban-1.9.12.tar.gz
b360bc0374a1ee8b1fa296ad1c903bde  cgoban-1.9.14.tar.gz
[81][~/Desktop]$  file cgoban-1.9.12.tar.gz cgoban-1.9.14.tar.gz
cgoban-1.9.12.tar.gz: gzip compressed data, from Unix, last modified: Thu Feb 28 04:34:59 2002, max compression
cgoban-1.9.14.tar.gz: gzip compressed data, from Unix, last modified: Mon Jan  6 20:35:29 2003, max compression

```
I downloaded them from here:
[http://www.igoweb.org/~wms/comp/cgoban/](http://www.igoweb.org/~wms/comp/cgoban/)
And here:
[http://sourceforge.net/projects/cgoban1/files/](http://sourceforge.net/projects/cgoban1/files/)

You should also be able to get the latest code over CVS:
```
cvs -d:pserver:anonymous@cgoban1.cvs.sourceforge.net:/cvsroot/cgoban1 login
cvs -z3 -d:pserver:anonymous@cgoban1.cvs.sourceforge.net:/cvsroot/cgoban1 co -P cgoban1

```

Also, from the cgoban website:
> Important Note:
CGoban 1 is no longer under active development. Instead, I am working on CGoban 3 which is a port of the SGF editor of CGoban 1 to Java combined with a client for the KGS Go Server. It is missing the Go Modem Protocol adapter from CGoban 1 and the IGS/NNGS client from cgoban 1, but the SGF editor is a bit better (and of course the KGS client in it is much better than the IGS/NNGS client in CGoban 1). You can download it from the KGS web site. 
;)

edit:
Actually, it seems only cgoban 1 is Free Software. :(
> CGoban 2 is distinct from an earlier program by the same author called CGoban. Unlike CGoban, both CGoban 2 and CGoban 3 are not [ext] free software. William Shubert claims that by making both the protocol and the source code closed, he can innovate the features of KGS without having to support other clients. 
[http://senseis.xmp.net/?CGoban2](http://senseis.xmp.net/?CGoban2)

---

### Post by hal10000 on 2009-09-12
[COLOR="Red"]sudo apt-get install gnugo[/COLOR]
will avoid all the mess you have with a tar package if you have the universe repos activated

---

### Post by KIAaze on 2009-09-12
> **patC42 said:**
> Im trying to give Gnugo a graphical frontend

He wants to work on gnugo/cgoban1, so he needs the source. :)
Of course, he could also run:
```
apt-get source gnugo
```
to get the source and then
```
sudo apt-get build-dep gnugo
```
to get the build dependencies.

But this might not give him the latest source code. (+ it might have Debian/Ubuntu-specific modifications)

---

### Post by patC42 on 2009-09-12
Thanks for that the first 2 site options did the same but I seem to have got it with the cvs options. As you can see I am now having trouble with ./configure.

pat@pat-desktop:~/Desktop/cgoban1$ ls
acconfig.h       ChangeLog     grab_cgoban.in  missing            src
AUTHORS          configure.in  INSTALL         mkinstalldirs      TODO
bootstrap        COPYING       install-sh      NEWS               wmslib
cgoban1.spec.in  CVS           Makefile.am     README
cgoban_icon.png  depcomp       man6            seigen-minoru.sgf
pat@pat-desktop:~/Desktop/cgoban1$ ./configure
bash: ./configure: No such file or directory
pat@pat-desktop:~/Desktop/cgoban1$ sh ./configure
sh: Can't open ./configure
pat@pat-desktop:~/Desktop/cgoban1$ 

Sorry to be such a pain, but I am very new.

---

### Post by KIAaze on 2009-09-12
Well, I tried gnugo and cgoban1 and it seems that cgoban1 does have a GUI! :D
So you don't have to write a GUI unless you really want too.

Actually gnugo and cgoban are 2 separate programs. Both are in the repositories:
```
sudo apt-get install gnugo
sudo apt-get install cgoban

```
(Of course, you can use add/remove programs or synaptic... I don't know how experienced you are. ;) )

gnugo only has an ASCII interface, but if you read its man page, it says you can use cgoban as a GUI for it:
>        Playing a game with CGoban

       CGoban is a general purpose client program by Bill Shubert for playing Go. It runs under X Window System with a beautiful resizeable graphic display. To use GNU Go under X Window System,
       obtain the most recent version of CGoban from Bill Shubert&#8217;s web site

       [http://www.igoweb.org/~wms/comp/cgoban/index.html](http://www.igoweb.org/~wms/comp/cgoban/index.html)

       Start CGoban. When the CGoban Control panel comes up, select &#8216;Go Modem.&#8217;  You will get the Go Modem Protocol Setup. Choose one (or both) of the players to be &#8216;&#8216;Program,&#8217;&#8217; and fill out the
       box to the path to gnugo. After clicking OK, you get the Game Setup window. Choose &#8216;&#8216;Rules Set&#8217;&#8217; to be Japanese (otherwise handicaps won&#8217;t work). Set the board size and handicap if you want.
       Click OK and you are ready to go.

       In the Go Modem Protocol Setup window, when you specify the path to GNU Go, you can give it command line options, such as --quiet to suppress most messages. Since the Go Modem Protocol pre&#8208;
       empts standard I/O, other messages are sent to stderr, even if they are not error messages. These will appear in the terminal from which you started CGoban.


Anyway, I spent some time trying to compile the CVS version of cgoban and succeeded, so here's how:
Download the attached patch_and_script.tar.gz
Then:
```

sudo apt-get build-dep cgoban       #install the build dependencies for cgoban
tar -xzvf ./patch_and_script.tar.gz #extract it
cd patch_and_script                 #change into the created directory
./get_and_build_cgoban.sh           #get, patch and build cgoban

```

Here's what the ./get_and_build_cgoban.sh script does:
```
#!/bin/bash
# make the script exit on error
set -e
# make the script output each command
set -x
#login to the CVS server. Just press enter at the password prompt
cvs -d:pserver:anonymous@cgoban1.cvs.sourceforge.net:/cvsroot/cgoban1 login
#checkout the CVS repository
cvs -z3 -d:pserver:anonymous@cgoban1.cvs.sourceforge.net:/cvsroot/cgoban1 co -P cgoban1
#change into the created directory
cd cgoban1
#apply patch
patch -p1 -i ../cgoban1_autotools.patch
#make autogen.sh executable
chmod 755 ./autogen.sh
#run autogen.sh to create the configure script and all the other necessary stuff
./autogen.sh
#run the configure script
./configure
#build the program
make
#cd into the directory containing the binary
cd src
#run the binary
./cgoban
#just a message, so you know everything worked well. :)
echo SUCCESS

```

I already submitted the patch I made to the cgoban devs:
[https://sourceforge.net/tracker/?func=detail&aid=2857805&group_id=52805&atid=468097](https://sourceforge.net/tracker/?func=detail&aid=2857805&group_id=52805&atid=468097)

I also attached the original cgoban tarballs in case you still want to try them.

The reason ./configure didn't work for you is because the configure script isn't available on the CVS.
It has to be generated by running commands like aclocal, autoconf, autoheader and automake.
The autogen.sh script that comes with my patch takes care of this.
It's more complex than necessary, but should take care of everything.
I got it from [https://sourceforge.net/projects/buildconf/](https://sourceforge.net/projects/buildconf/)

The release tarballs already contain the configure script, so all you have to do there is:
```
./configure
make

```

If you still have any questions, just ask. :)

---

