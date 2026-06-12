---
title: "Desiring to convert swf movie to avi or other format"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by demarshall on 2011-02-17
Hello:

There are a couple of cool videos about previous decades on a web site but I'd like to be able to control the playing of it - pause it, rewind it, etc. I'm thinking that the best way to do that is to convert it to another video file format such as avi, wmv or mpeg.

The swf movies are: [http://www.objflicks.com/decadeofthe1940s.html](http://www.objflicks.com/decadeofthe1940s.html)

and [http://www.objflicks.com/theseventies.html](http://www.objflicks.com/theseventies.html)

Is there something that will convert these swf movies or is there a way to just capture the video?

I'd really appreciate some help with this.

I have already tried everything that I have found listed in the forum here, including ffmpeg and mmencoder. Neither of those work and I want to be able to do this on a Linux box not on a Windows box.

Thanks for any assistance. :)

---

### Post by jmszr on 2011-02-17
demarshall,

Both Handbrake and Avidemux can convert .swf to .avi. 

Here is the website for Handbrake: [http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php) and Avidemux should be in the repositories, but this is probably a newer version: [http://www.getdeb.net/updates/Ubuntu/10.04/?q=avidemux](http://www.getdeb.net/updates/Ubuntu/10.04/?q=avidemux) .

---

### Post by AvoidedRider on 2011-02-17
I took a look at this thinking that it would be easy to solve. Avidemux and handbrake don't even open the files in question. I tried to open them with ffmpeg and got an error > Compressed SWF format not supported I routinely pull stuff offline like this and nothing I have is touching those files. If anyone has used something that will I am curious what it is.

---

### Post by demarshall on 2011-02-17
Well, I'm glad that it's not just me...

Thanks guys. I hope that one of you or somebody else can come up with a solution.

I have heard that HTML 5 is not going to support Flash. I wonder if that means that it won't support swf as well.

---

### Post by lykeion on 2011-02-17
I don't think there is a method to convert compressed SWFs to another video format. You could use a screen recorder like recordMyDesktop to capture the video.

Otherwise play the SWF video with a standalone player like gnash
```
sudo apt-get install gnash
```
Then you can play the video with:
```
gnash video.swf
```
You'll get play/stop/pause control but unfortunately no seeking available

---

### Post by demarshall on 2011-02-17
> **lykeion said:**
> I don't think there is a method to convert compressed SWFs to another video format. You could use a screen recorder like recordMyDesktop to capture the video.

Otherwise play the SWF video with a standalone player like gnash
```
sudo apt-get install gnash
```
Then you can play the video with:
```
gnash video.swf
```
You'll get play/stop/pause control but unfortunately no seeking available

Thanks lykeion! :-)

Will gnash automatically install its addon for Firefox and mess that up or is there some way to prevent it from doing that? I have had to get rid of every trace of that app on my computer more than once so that Firefox could play Flash properly.

---

### Post by AvoidedRider on 2011-02-17
Seems to work as advertised. Did not change any of my flash plug-in settings in firefox. I am using the beta flash for 64 bit OS.

---

### Post by llamabr on 2011-02-17
I don't care for gnash, though I havn't looked at it for a few years.  Has it improved?

Usually, when you watch a flash movie, it will save a local copy in your /tmp folder.  You'll usually find it there as something like:

/tmp/Flashfhgus9 

or something like that.  You can then use mplayer to play them on your computer, using your controls to forward and pause, etc.

---

### Post by demarshall on 2011-02-18
No, the only files related to those swf movies are the swf movies themselves.

I installed gnash and it gives me at least some control over the playback of swf movies. It didn't infect Firefox so this is probably be best course of action right now.

Thanks lykeion

---

### Post by demarshall on 2011-02-22
> **dwightgenius2009 said:**
> Moyea SWF to Video Converter works well on my Windows, however, I don't know whether there is a Linux edition.
Here is the site: [http://www.swfkits.com/:KS]("http://www.swfkits.com/")
When I checked on that product in the past, it was only for Windoze. :-(

Thanks anyhow.

---

### Post by ron999 on 2011-02-22
This would make a good project for somebody.:P
Modify a flash player such as Gnash or Swfdec so that it would allow stdout to ffmpeg.
Something like this:-
```
flashplayer foo.swf - | ffmpeg -i - -vcodec mpeg4 -acodec libmp3lame foo.mp4
```

---

