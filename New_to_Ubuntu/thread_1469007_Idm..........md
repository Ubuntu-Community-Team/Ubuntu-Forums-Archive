---
title: "Idm........."
date: 2010-05-01
forum: New to Ubuntu
---

### Post by stampper on 2010-05-01
are there any programmers working on IDM for linux versions...........:KS

---

### Post by 3rdalbum on 2010-05-01
Not all of us use Windows, it would have been more helpful for you to describe what IDM does. I'm assuming you're talking about Internet Download Manager. On Linux, we use Wget or any one of several GUIs for Wget (like gwget).

---

### Post by stampper on 2010-05-01
i am newbie,   with idm in windows you can download videos directly in .flv format ..........do we have that option in wget

---

### Post by 3rdalbum on 2010-05-02
> **stampper said:**
> i am newbie,   with idm in windows you can download videos directly in .flv format ..........do we have that option in wget

Oh, so THAT'S what you want to do! I wish you'd said that in the first place :-)

You don't need an extra program to do that on Linux. Just start the video and pause it. Wait for the whole video to load, and then you'll find it sitting inside the /tmp directory. The filename begins with the word "Flash". Just rename it and give it a .flv extension and copy it to where you want it.

If you don't want to actually load the page, you can install "youtube-dl". Just put "youtube-dl" and then the URL of the web page that contains the video, into the terminal.

---

### Post by madjr on 2010-05-02
yep tmp directory

i always add it as a bookmark in nautilus (the file manager)

---

### Post by stampper on 2010-05-02
thanks a lot for ur help ..............:KS but what if the buffering of the video took very long time, u see if i use idm i will get downlink speed 200Kbp/s and can download 50minute video in just  10minutes so are there any other alternatives for downloading a file at faster rate...

and one more thing  linux is present for some time why hasnt any one created IDM for linux?

---

### Post by Paqman on 2010-05-02
> **stampper said:**
> thanks a lot for ur help ..............:KS but what if the buffering of the video took very long time, u see if i use idm i will get downlink speed 200Kbp/s and can download 50minute video in just  10minutes so are there any other alternatives for downloading a file at faster rate...


You're never going to be able to download it faster than the source will stream it to you. So Ubuntu will take exactly the same amount of time as Windows would.

> 
and one more thing  linux is present for some time why hasnt any one created IDM for linux?

There are plenty of plugins for browsers that will do this. They work fine on Ubuntu, even though you don't actually need them, as we can just look in the /tmp folder as explained above.

---

### Post by rajesh120 on 2010-05-02
hello i hav installed ubuntu right now and i was searching for idm for ubuntu but after waching you say just type /tmp and video is with u, i like it but tell me where shall i type it....in terminal window or where??

---

### Post by stampper on 2010-05-02
> **Paqman said:**
> You're never going to be able to download it faster than the source will stream it to you. So Ubuntu will take exactly the same amount of time as Windows would.



There are plenty of plugins for browsers that will do this. They work fine on Ubuntu, even though you don't actually need them, as we can just look in the /tmp folder as explained above.



if u download flv video  with IDM the download rate i can achieve is 220Kbp/s..........
where as if i let it buffer the download rate will not be constant it will vary from 100Kbp/s to 150Kbp/s so  a lot of time is spent on downloading 50minutes video file

---

### Post by stampper on 2010-05-02
> **rajesh120 said:**
> hello i hav installed ubuntu right now and i was searching for idm for ubuntu but after waching you say just type /tmp and video is with u, i like it but tell me where shall i type it....in terminal window or where??


/tmp is not a command its a directory........ go to ur file system there u will temp directory from there u can copy the .flv video........:KS

---

### Post by SwatKat on 2010-05-02
> **stampper said:**
> i am newbie,   with idm in windows you can download videos directly in .flv format

There are many firefox add ons to download videos like 'video download helper' and 'Download them all'
 [https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by rajesh120 on 2010-05-02
> **stampper said:**
> /tmp is not a command its a directory........ go to ur file system there u will temp directory from there u can copy the .flv video........:KS
friend i also hav finded a new way ie
i type /tmp as in window it is in home directory and viola it opened

---

### Post by stampper on 2010-05-02
happy downloading.........

---

### Post by sadaruwan12 on 2010-05-02
If you want some thing similar to IDM use DownThemAll fire fox add-on which is DM built in to fire fox I use it day in and day out it's gr8.

---

