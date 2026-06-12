---
title: "Help with Newsreaders, Nzsbins and Pan"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by RemyCarson on 2008-12-04
Hey Guys,

Have recently joined the wonderful world of Linux :) and much preferring it Windows although it is more time consuming at the mo! :)

I have never used Newsreaders, Newsbins etc before but a friend was telling me of their uses and I thought I would give it a try. They told me that Pan is a good program to start with, is this true or are their better ones?  However having installed Pan I realized that I might actually have to find out how to work it... It seems a little complex to a newb like me :(  Is their an easy tutorial somewhere?

Many thanks in advance,

Remy.

---

### Post by nhasian on 2008-12-04
wikipedia says > The name Pan originally stood for Pimp-*** newsreader

I highly recommend LottaNZB.  its a front end for HellaNZB and very easy to use.  Once its installed you just click on a .nzb file and it automatically retrieves the files, error checks them, downloads parity files if necessary, uncompresses it and moves it to your done folder.  You can also just drag and drop .nzb files to the queue directory.  to install LottaNZB:

```
sudo apt-get install lottanzb
```

this will also install hellanzb and its dependencies.

---

### Post by Lantash on 2008-12-11
Unfortunately, LottaNZB isn't part of Ubuntu's repositories yet, so "sudo apt-get install lottanzb" won't work.

I recommend you to go to the _[LottaNZB download page]("http://lottanzb.org/downloads")_ and grab the Ubuntu package from there.

PS: Welcome to the world of Linux and have fun with LottaNZB!

---

### Post by oldos2er on 2008-12-11
Your choice of newsreader is dependent on whether you intend to read Usenet, or download from Usenet. If you're just going to be reading newsgroups, Pan is fine, and probably the simplest newsreader for a newbie to set up. For downloading, LottaNZB was recommended and is a good choice. Of course there's no reason you can't run both programs.

 Do you know the name of your newsserver, and whether it requires a username and password? Pan needs to know these things when you first run it.

---

