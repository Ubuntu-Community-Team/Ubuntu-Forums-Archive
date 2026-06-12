---
title: "videos not playing on newly downloaded ubuntu 10.10"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by zirgut on 2011-03-11
I cannot get videos to play on newly downloaded ubuntu 10.10

---

### Post by mastablasta on 2011-03-11
wow, that's really a lot of information you provided there.
 
anyway have you installed the restricted extras package found in software center?
If the video is a DVD then you will have to use commands found here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by ~Plue on 2011-03-11
have you installed the necessary codecs first?
the easiest way to do so would be to install the package 'ubuntu-restricted-extras' from the software-center, synaptic or apt-get
and run from a terminal *sudo /usr/share/doc/libdvdread4/install-css.sh *(that is if you want dvd support)[I]

more info here >> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[/I]edit; beaten to it[I] =/
[/I]

---

### Post by zirgut on 2011-03-11
Thanks for reply. Yes Sorry was not very clear on problem. Downloaded 10.10 yesterday and have very limited experience with ubuntu. Tried to play a video on yahoo news and it would not come up. I am not sure how to proceed to download/ install the restricted extras and the run for a from a terminal bit sudo stuff makes me want to run the other way. Yes a novice. Perhaps a step by step thing is what I need.
Regards

---

### Post by Thijk on 2011-03-11
An easier way:

Go to help (press F1)

There on the left side you see "*new to ubuntu?*" under topics. Click it and on the right side, select "*Playing music and videos*"

then there's a frame with 

"*To add support for all frequently used music and video files, install the ubuntu-restricted-extras package. This will also add support for websites which use Flash video."*

And then you click on *"install the ubuntu-restricted-extras package."*

that should do it

---

### Post by Thijk on 2011-03-11
Or if you want to do it with the terminal.

To open a terminal , go to applications -> accessories -> terminal.  That opens a terminal window.

And then you just type in those two lines in the link ~Plue gave:

```
 sudo apt-get install libdvdread4
```and then 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

or you can copy and paste them in the terminal.

Then a reboot and it should work.

---

### Post by zirgut on 2011-03-11
> **Thijk said:**
> An easier way:

Go to help (press F1)

There on the left side you see "*new to ubuntu?*" under topics. Click it and on the right side, select "*Playing music and videos*"

then there's a frame with 

"*To add support for all frequently used music and video files, install the ubuntu-restricted-extras package. This will also add support for websites which use Flash video."*

And then you click on *"install the ubuntu-restricted-extras package."*

that should do it
Hi,
Thought that would solve my problems but for some reason the package does not install. I copied the details of why it did not . Here they areinstallArchives() failed:  Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
Preconfiguring packages ... 
 Extract templates from packages: 37% Extract templates from packages: 75% Extract templates from packages: 100% 
Preconfiguring packages ... 
Setting up tzdata (2011c-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011c-0ubuntu0.10.10) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 .
 Well I wish I could make head or tail of it. Maybe in my next incarnation. 
Also I tried going into terminal and doing the sudo thing but it asked for my password and wouldn't register it when tried to type it in.
Any more suggestions. Thanks

---

### Post by The End of The World on 2011-03-11
> **zirgut said:**
> Hi,
Thought that would solve my problems but for some reason the package does not install


Here, try this in the terminal, this should sort out your package install problem:

```

sudo dpkg --configure -a && sudo apt-get install -f 

```Hope this works! Good luck!

---

### Post by Thijk on 2011-03-11
> **zirgut said:**
> Hi,

Also I tried going into terminal and doing the sudo thing but it asked for my password and wouldn't register it when tried to type it in.


you don't get stars or anything like that in the terminal, you can just type your password and hit the rerturn key

---

### Post by zirgut on 2011-03-16
> **Thijk said:**
> you don't get stars or anything like that in the terminal, you can just type your password and hit the rerturn key
Hi,
I have been out of circulation for a while. But thanks your last suggestion worked and I am now running videos. Thanks for your patient responses.
Kind regards
Adrian

---

### Post by PM47 on 2011-03-17
> **The End of The World said:**
> Here, try this in the terminal, this should sort out your package install problem:

```

sudo dpkg --configure -a && sudo apt-get install -f 

```Hope this works! Good luck!

Hi, 

I had the same problem and your solution worked for me too. I'm on day 2 of trying to get to grips with Linux (for the umpteenth time in the past 15 years), is there any chance of a quick explanation of what your command line actually did please ?

Paul

---

