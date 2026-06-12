---
title: "tarball installation/download"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by CaimSasori on 2009-01-02
okay
so I'm new to ubuntu
I don't know much about it

and I'm looking to download Stepmania

and it's in a tarball 

I'm unaware of the procedure of installing/downloading a tarball. :confused:
I've googled for about an hour

found a few links that didn't really help me very much.
I figured I could check the forums

anyone want to help me any?

~Caim

---

### Post by handydan918 on 2009-01-02
Please post the exact filename that you have downloaded.

Also, before installing any program you should try to find it in synaptic.

---

### Post by CaimSasori on 2009-01-02
the exact filename is StepMania-3.9a-linux.tar.gz

I apologize for that

---

### Post by oldos2er on 2009-01-02
I found some instructions here: [http://www.ubuntu-unlimited.com/?id=1228505195#howto1228505195](http://www.ubuntu-unlimited.com/?id=1228505195#howto1228505195)

---

### Post by bigO on 2009-01-02
First things first you may not need to install from source. If you are looking for games check out [http://www.playdeb.net/](http://www.playdeb.net/) and follow the instructions there. There have a bunch of games and stepmania is one of them. 

As for installing from source I will see if I can't find you a good tut that explains it rather than just telling you what to do. though I can do that for you if playdeb doesn't work and you don't understand the tut.  

I will repost with a link for you.

---

### Post by handydan918 on 2009-01-02
> **CaimSasori said:**
> the exact filename is StepMania-3.9a-linux.tar.gz

I apologize for that

try ```
tar -zxvf StepMania-3.9a-linux.tar.gz
```
and look for a README file. 

There is no one way to install from a tarball, because it can contain anything!

---

### Post by CaimSasori on 2009-01-02
thanks everyone
I'll try your many different methods

---

### Post by Pierrot Lafouine on 2009-01-03
> **bigO said:**
> First things first you may not need to install from source. If you are looking for games check out [http://www.playdeb.net/](http://www.playdeb.net/) and follow the instructions there. There have a bunch of games and stepmania is one of them. 

As for installing from source I will see if I can't find you a good tut that explains it rather than just telling you what to do. though I can do that for you if playdeb doesn't work and you don't understand the tut.  

I will repost with a link for you.

Hi BigO
Did you find a link ?
I'm trying to install a tar ball (pgSlideShow.tar.gz) and tar doesn't work (seams to be in an other format then gunzip), I would be interested to read more on this

---

### Post by taurus on 2009-01-03
> **Pierrot Lafouine said:**
> Hi BigO
Did you find a link ?
I'm trying to install a tar ball (**[COLOR="Blue"]pgSlideShow.tar.gz[/COLOR]**) and tar doesn't work (seams to be in an other format then gunzip), I would be interested to read more on this

If that is the exact name of the file that you've downloaded, what happens when you try to unpack it, assuming you have saved it to your desktop?

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf pgSlideShow.tar.gz
```

---

### Post by Pierrot Lafouine on 2009-01-03
under Ubuntu, tar zxvf works fine
under my Arm embedded computer using Debian based TS-Linux, this is the error message : 
gzip:stdin:not in gzip format
tar:Child returned status 1
tar:Error exit delayed from previous errors

I tried this:
tar xf pgSlideShow.tar.gz

This is the error message I got :
tar:This is not like a tar archive
tar:Skipping to next header
tar:Error exit delayed from previous errors

Any idea how I can point the problem?
Is the file format, or tar command on TS-Linux cause this problem ?

Thanks

---

