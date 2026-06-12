---
title: "Video converter"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by RemmyNumber7 on 2010-06-02
I have Ubuntu 8.04  and have some video's in avi format I want to put them to another video format and put them on disk. Here's my problem, I have been to Google and the web to find a video converter to install but but they don't add to my programs and interact through my GUI . So then I go to try to run them in Terminal and it tells me that it doesn't work..  please help

---

### Post by hansdown on 2010-06-02
Hi RemmyNumber7.

```
sudo apt-get install devede
```


Or look in synaptic package manager.

---

### Post by yamfox on 2010-06-02
Go to the software center, and go to Edit>Software Sources in the menu bar. Go to "Other Software". Press add, and paste in this:
```
ppa:stebbins/handbrake-snapshots
```
Then reload, and search for handbrake. Install it, and run it from sound and video. Click on source, find the file you want to convert, then click on one of the presets on the side, and click start.

---

### Post by JohnAStebbins on 2010-06-02
> **RemmyNumber7]I have Ubuntu 8.04 and ...[/quote]
[QUOTE=yamfox said:**
> Go to the software center, and go to Edit>Software Sources in the menu bar. Go to "Other Software". Press add, and paste in this:
```
ppa:stebbins/handbrake-snapshots
```
Then reload, and search for handbrake. Install it, and run it from sound and video. Click on source, find the file you want to convert, then click on one of the presets on the side, and click start.

Unfortunately, the latest version of handbrake which is supplied by that PPA is not compatible with Ubuntu 8.0.4.  What you want is to find a version of HandBrake 0.9.4.  That may be difficult since that version was pulled from HandBrake's download page because it will not work with Ubuntu 10.04 and was causing a user support nightmare.

HandBrake 0.9.3 is available for 8.04 here
[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

### Post by anewguy on 2010-06-02
My suggestion - OpenShot video converter - similar to a Microsoft product.

Dave ;)

---

### Post by fooman on 2010-06-02
another vote for devede here.  :)

convert to an .iso file and burn with k3b works great for me.

if in the U.S.,  be sure to change the "default format" to NTSC.

---

### Post by manny43 on 2010-06-02
mobilemediaconverter

---

### Post by zipperback on 2010-06-02
I would highly recommend ffmpeg for what you want to do.  

It's not hard to use if you take a little time and read over the documentation for it, and it's very powerful.

Look in synaptic and you should be able to find it. It works with numerous audio and video file formats.


- zipperback
:popcorn:

---

### Post by jerenept on 2010-06-02
> **zipperback said:**
> I would highly recommend ffmpeg for what you want to do.  

It's not hard to use if you take a little time and read over the documentation for it, and it's very powerful.

Look in synaptic and you should be able to find it. It works with numerous audio and video file formats.


- zipperback
:popcorn:

Or you could try WinFF...

---

### Post by RemmyNumber7 on 2010-06-02
i have these video's in a folder on my desktop and none of these programs won't let me switch video format. It is in AVI i would like to switch it to mpeg or maybe wmf or another format that i could put it into a dvd player on top of the TV

---

### Post by jerenept on 2010-06-03
I think that Brasero should do that nicely.
Applications>Sound and Video>Brasero Disc Burner.

Select "Video Project"
Click the green "+" sign and browse to the files you would like to burn.

DeeVeeDee also comes highly recommended. (in the Software Center)

---

### Post by zipperback on 2010-06-03
> **RemmyNumber7 said:**
> i have these video's in a folder on my desktop and none of these programs won't let me switch video format. It is in AVI i would like to switch it to mpeg or maybe wmf or another format that i could put it into a dvd player on top of the TV


ffmpeg works just fine with avi files. 

```

ffmpeg -i example.avi -target ntsc-dvd example.mpg

```


You might want to look at the man pages for ffmpeg as well.

```

man ffmpeg

```

- zipperback
:popcorn:

---

### Post by RemmyNumber7 on 2010-06-06
I tried this one did not work

---

### Post by fooman on 2010-06-06
> **RemmyNumber7 said:**
> i have these video's in a folder on my desktop and none of these programs won't let me switch video format. It is in AVI i would like to switch it to mpeg or maybe wmf or another format that i could put it into a dvd player on top of the TV

as stated before....devede will do what you want.  when it starts,  look under "advanced options" and you can convert the file(s) to MPEG [I]if you wish.
[/I] 
however,  if what you want to do is create a dvd which you can play on your standalone dvd player...then just convert the file to an .iso (which is default) and then use a burning app. (k3b, brasero, etc) to burn the .iso to a dvd which will be playable on set top, standalone,  dvd players.  if you are in the U.S.,  then be sure to convert the file as NTSC.

hope that helps.

---

