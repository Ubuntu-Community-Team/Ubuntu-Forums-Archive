---
title: "I don't understand what an online tutorial is telling me to do"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by w.g.hanna on 2009-07-14
Running Jaunty.  not a total noob - but I sure haven't gotten far past the gui stage of things.  so i often rely on others to help me get through a challenge that involves the command line and just do alot of copying and pasting.  sometimes the instructions are so straight forward that its hard to get confused (e.g. psychocats).  on the other hand, sometimes you get shorthand that might make sense to somebody who gets the context intuitively - but not to me.  

Right now, one of the two tasks I'm focused on is getting streamripper to rip last.fm streams (the other is running wordperfect).  i'm going to take it one step at a time, and hopefully somebody can help me make sense of it all.

first, i go to a website with instructions that seems to work for other people:

[http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html](http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html)

the first step says: installing lastfm proxy.  then it has a grey box with what looks like terminal commands - together with instructions for the user.  what am i supposed to do here?

it says save the file.  what file?  and where do i save it to?  

i've installed streamripper through synaptic, so that takes care of the next step.

then it says run the lastfm proxy.  again it looks like terminal commands - but then after the grey box is a note that says i have to direct my browser to a url specifying a station.  what browser?  firefox?  do the instructions assume i'm already logged in and using last.fm on firefox?  do i leave firefox up and running to use streamripper?  

next step says run streamripper - but the screen looks like what i'd see (in the terminal?) if i managed to get it to work right.  so do i have to type something in the terminal to get it to this point?  

at any rate - the only reason i need this is because exaile stopped working for the same function.  it seems to connect to last.fm, but i never hear the music and it never rips.  it used to work halfway good.

---

### Post by GMachine_24 on 2009-07-14
You might have more luck posting your question at the bottom the this Web page, like everyone else...


[http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html](http://www.linuxmonitor.net/blog/2007/03/ripping-mp3s-from-lastfm-with-linux.html)

---

### Post by oldos2er on 2009-07-14
"wget [http://vidar.gimp.org/wp-content/uploads/2006/07/lastfmproxy-1.1.tar.gztar](http://vidar.gimp.org/wp-content/uploads/2006/07/lastfmproxy-1.1.tar.gztar) -xzf lastfmproxy-1.1.tar.gz"

 The line above downloads and untars a file named lastfmproxy-1.1.tar.gz. This creates a directory named lastfmproxy-1.1, which you then "cd" into with the next command 

cd lastfmproxy-1.1

 Then you're asked to edit the file config.py and change the username and password to whatever your LastFM user and password is. I would recommend an editor other than vi, so try

gedit config.py

 After you've made those changes, save and exit the file. In the same directory, run
./main.py &

 Here's a link to the README: [http://vidar.gimp.org/wp-content/uploads/2006/07/README.txt](http://vidar.gimp.org/wp-content/uploads/2006/07/README.txt)

---

### Post by nhasian on 2009-07-14
the instructions dont look very difficult, but the filenames and versions numbers are newer now than when they were when the howto was written.

you need to grab:

[LastFMProxy]("http://vidar.gimp.org/wp-content/uploads/2007/12/lastfmproxy-1.3b.tar.gz")

extract the files, and in the folder lastfmproxy, double click on the config.py and insert your lastFM username and password between the quotes at the bottom.  

then you need top open a terminal (applications->accessories->terminal) and type:

```
sudo apt-get install streamripper
```

does that help at all?

---

