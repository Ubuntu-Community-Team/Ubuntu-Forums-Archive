---
title: "Trouble installing x264 for ffMpeg"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by ROVDude on 2011-06-10
Hey folks,

OK, so i found this really great tutorial and "HowTo" [here]("http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html").

I got through to the part where I have to get and install the x264 codecs with the following:

git clone git://git.videolan.org/x264.git

I put it in, and got:

Initialized empty Git repository in /home/bossman/x264/.git/
git.videolan.org[0: 88.191.250.118]: errno=No route to host
fatal: unable to connect a socket (No route to host)

So, yeah, even after looking around the forums for this error I'm kind of at a loss as to what that means, and what I can do about it.

Any thoughts, guidance, explanations, input would be appreciated.

Thanks.

---

### Post by ron999 on 2011-06-10
Delete the x264 folder and try again.
> ron@ubuntu:~$ git clone git://git.videolan.org/x264.git
Initialized empty Git repository in /home/ron/x264/.git/
remote: Counting objects: 13903, done.
remote: Compressing objects: 100% (4545/4545), done.
remote: Total 13903 (delta 11306), reused 11533 (delta 9317)
Receiving objects: 100% (13903/13903), 3.40 MiB | 765 KiB/s, done.
Resolving deltas: 100% (11306/11306), done.


---

### Post by andrew.46 on 2011-06-10
> **ROVDude said:**
> OK, so i found this really great tutorial and "HowTo" [here]("http://pasindudps.blogspot.com/2010/12/compiling-ffmpeg-in-ubuntu-1010.html").

This guide seems to have been drawn at least in part from this long standing guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

I guess there is an old saying: 'Imitation is the sincerest form of flattery.' :)

---

### Post by ROVDude on 2011-06-11
Yep.  That's true.
 
Anyway, I tried to uninstall x264, and ended up really messing my system up.  Don't know exactly what happened.  But since my Ubuntu experience is completely experimental at this stage, that's ok.  I reinstalled, reformatted, and tried to follow that howto again.  Same error.  Then I realized I hadn't installed any updates or anything.
 
SO....
 
I'll try again after I install the updates with the update manager, and see what I'll see.

---

### Post by FakeOutdoorsman on 2011-06-11
> **ROVDude said:**
> Initialized empty Git repository in /home/bossman/x264/.git/
git.videolan.org[0: 88.191.250.118]: errno=No route to host
fatal: unable to connect a socket (No route to host)

Any thoughts, guidance, explanations, input would be appreciated.

Thanks.

Do you have a firewall interfering with Git? If not then perhaps your IP address has been added to a blacklist on the Git server for some reason (I'm not sure if they actually do this or not). You could ask at IRC channels *#x264* or maybe *#videolan*.

If you still can't get Git to work, you can download a [snapshot of the x264 source](http://git.videolan.org/?p=x264.git;a=snapshot;h=refs/heads/master;sf=tgz) instead.

---

### Post by VOT Productions on 2011-06-11
Use the Ubuntu Forums howto, not the pasindudps one.

---

### Post by ROVDude on 2011-06-12
ok, so I followed the forums howto, and when I copy and pasted this:

cd
git clone git://git.videolan.org/x264
cd x264
./configure --enable-static
make
sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \
    awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \
    --fstrans=no --default
I got this:

bossman@bossman-1005HA:~$ cd
bossman@bossman-1005HA:~$ git clone git://git.videolan.org/x264
Initialized empty Git repository in /home/bossman/x264/.git/
git.videolan.org[0: 88.191.250.118]: errno=No route to host
fatal: unable to connect a socket (No route to host)
bossman@bossman-1005HA:~$ cd x264
bash: cd: x264: No such file or directory
bossman@bossman-1005HA:~$ ./configure --enable-static
bash: ./configure: No such file or directory
bossman@bossman-1005HA:~$ make
make: *** No targets specified and no makefile found.  Stop.
bossman@bossman-1005HA:~$ sudo checkinstall --pkgname=x264 --pkgversion="3:$(./version.sh | \
>     awk -F'[" ]' '/POINT/{print $4"+git"$5}')" --backup=no --deldoc=yes \
>     --fstrans=no --default
bash: ./version.sh: No such file or directory

checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 


So, I ran back to the forums, and Faker posted:
[I]
If you still can't get Git to work, you can download a [snapshot of the x264 source]("http://git.videolan.org/?p=x264.git;a=snapshot;h=refs/heads/master;sf=tgz") instead.

[/I]Sweet!  So I downloaded the "/x264-master-c1e60b9/" and ran it from the site.  Got it downloaded, annnnnd..........now what?

On the other hand, when I search in Synaptic for x264, it comes up, so I might try that too.  Yeah, that's the ticket....

Wish me luck!

---

### Post by andrew.46 on 2011-06-14
> **ROVDude said:**
>  Got it downloaded, annnnnd..........now what?

Perhaps this *single* command might be the easiest way for you to get started:

```

wget ftp://ftp.videolan.org/pub/videolan/x264/snapshots/x264-snapshot-20110613-2245.tar.bz2 && \
tar xjvf x264-snapshot-20110613-2245.tar.bz2 && cd x264-snapshot-20110613-2245 && \
./configure --enable-static && make && \
sudo checkinstall --pkgname=x264 --pkgversion="3:115~gitc1e60b9" --backup=no --deldoc=yes \
    --fstrans=no --default

```

The compilation instructions are modified from FO's guide...

---

