---
title: "You watch online video, then you wanna save it.So where is Temporary internet files"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Ubunser on 2009-05-09
I have a video in browser. In Windows I could find .flv files in temporary internet files

---

### Post by pastalavista on 2009-05-09
/tmp

---

### Post by Ubunser on 2009-05-09
Thanks:P

---

### Post by servicetech on 2009-05-09
Give the Firefox extension Download helper a try. Makes it easy to download flv files.

---

### Post by -kg- on 2009-05-09
> **servicetech said:**
> Give the Firefox extension Download helper a try. Makes it easy to download flv files.

Absolutely.  I've done it a bunch of times and it works great.  Video Download Helper is a Firefox add-on and can be found at:

[https://addons.mozilla.org/en-US/firefox/addon/3006]("https://addons.mozilla.org/en-US/firefox/addon/3006")

---

### Post by t0p on 2009-05-09
Check out the link in my sig.

---

### Post by l-x-l on 2009-05-09
> **pastalavista said:**
> /tmp

So if I want to clean my system of temporary files/history like "most recent files", what utilites for linux are available?

Thx for the help.

---

### Post by -kg- on 2009-05-09
> **l-x-l said:**
> So if I want to clean my system of temporary files/history like "most recent files", what utilites for linux are available?

Thx for the help.

As far as internet files, use FF's "Clear Private Data" under the "Tools" menu.  For most everything else, I got a bash script written that will clear temporarily downloaded packages, etc., from somewhere, but I can't remember where.  It is written primarily to clear out old downloaded packages under the apt-get package manager.

```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```

Paste the above in Gedit (or whatever text editor you want to use) and save it to your desktop (or where ever you want to store it) as "Disk-Cleanup-Script.sh", and when ever you want to do a clean-up of your old or unneeded packages, it will do that for you.

As for other unneeded files, Google "linux disk cleanup" and it will show you some of the stuff that has been written to do various things.  I really would rather do such things manually, myself.

---

### Post by pastalavista on 2009-05-09
> **l-x-l said:**
> So if I want to clean my system of temporary files/history like "most recent files", what utilites for linux are available?

Thx for the help.
Go to Places->Recent Documents->Clear Recent Documents. It will also clear recent videos in movie player and downloads in Down Them All and Download Manager Helper.

Sounds like someone is doing something they don't want to be caught doing...

---

### Post by ubuntu27 on 2009-05-09
> **pastalavista said:**
> 
Sounds like someone is doing something they don't want to be caught doing...

LOL. Not everyone who deletes their browsing history is doing something wrong.

Like in my case, I don't want people to know that I watch [Anime]("http://en.wikipedia.org/wiki/Anime").
I am trying to avoid this "Anime is for kids" tag.

---

### Post by -kg- on 2009-05-09
> **pastalavista said:**
> 
Sounds like someone is doing something they don't want to be caught doing...

Oh, not necessarily.  I also like to keep a clean hard drive on my computer, and get rid of files that I don't need to keep (like temporary internet files and the such).  Besides, the original question was where to find these files so he could save them.

Firefox (at least in Windows...I assume the same is true under Linux) slows down when loaded down with a bunch of temp files and the like, and always runs better once the temp files are cleared out.  While the "Clear Private Data" function does work, I've found that it doesn't always clear out *everything* that is in there (again, at least under Windows), and occasionally I like to go into the tmp folders (or directories, if you will) and clear some of them out manually.

I do appreciate the info you gave, though.  I've never found the "Clear Recent Documents" selection before.

OOPS!

> I am trying to avoid this "Anime is for kids" tag.

Now you've done it!

Don't you know that Anime is for kids, ubuntu27 ?! :lolflag:

---

### Post by penga on 2009-05-09
I find the best way to retrieve /flv files is to download /install 'Ant' toolbar for FF..in brief: start the flv movie, wait for the download button to come alive and hit it - save it to your fav destination when prompted...voila - watch,convert,edit,share or whack it the choice is yours...

---

### Post by Zorael on 2009-05-09
Regarding anime being for kids, pah! That's a very broad generalization. Taking an extreme example, the printed word must also be for kids, since (most) comicbooks are.

Find (download) the first two episodes of [Higurashi no Naku Koro ni](http://anidb.net/perl-bin/animedb.pl?show=anime&aid=3574) and watch both in succession, then tell me it's for kids. Watch those [yandere](http://en.wikipedia.org/wiki/Yandere) characters you grew to like suddenly flip out, and know suffering.

If the world has anything against [K-On!](http://anidb.net/perl-bin/animedb.pl?show=anime&aid=6257), it's their loss. Art; gorgeous. Voice acting; at a loss for words. Over-the-top cute moments; abound. The slice of life genre is surprisingly enjoyable.

Naruto/Bleach/similar have their moments, though I keep to the manga. I simply **cannot for the life of me** stand fillers; non-canonical content = lore rape, waste of my time.

I can't make sense of [Basquash!](http://anidb.net/perl-bin/animedb.pl?show=anime&aid=6255) yet, though [Higashi no Eden](http://anidb.net/perl-bin/animedb.pl?show=anime&aid=6238) (Eden of the East) is certainly worth the time watching.

</tangent>

---

### Post by -kg- on 2009-05-11
Zorael, don't get so defensive...I was making a joke! :lol:

Didn't you see the LOL Flag?

I like anime too!  I've been watching it for years upon years, like the old Speed Racer; The Eighth Man; and quite a few others from years ago.  And I watch some of the new stuff too.

---

### Post by freeman2000 on 2009-05-11
There's a real good program in the repos called "bleachbit".  Go to Synaptics to download it.  It will clean out the cache, cookies, history, etc in Firefox along with other web browsers.  In addition, it cleans out temp files from numerous other programs, such as Adobe, OpenOffice, and others.  Works great.  Good luck.

---

### Post by Zorael on 2009-05-11
> **-kg- said:**
> Zorael, don't get so defensive...I was making a joke! :lol:

Didn't you see the LOL Flag?

I like anime too!  I've been watching it for years upon years, like the old Speed Racer; The Eighth Man; and quite a few others from years ago.  And I watch some of the new stuff too.
Didn't mean to come through as defensive, just piping in. :3

</tangent^2>

---

### Post by l-x-l on 2009-05-12
> **pastalavista said:**
> Go to Places->Recent Documents->Clear Recent Documents. It will also clear recent videos in movie player and downloads in Down Them All and Download Manager Helper.

Sounds like someone is doing something they don't want to be caught doing...

I just don't like the whole concept of "recent documents". I know where I keep everything & how to access it quickly. It seems to me to serves no real purpose.

---

### Post by anjilslaire on 2009-05-12
> **l-x-l said:**
> I just don't like the whole concept of "recent documents". I know where I keep everything & how to access it quickly. It seems to me to serves no real purpose.

I understand & agree, but you'd be amazed how many non-technical people really *don't* know where their docs are...

---

### Post by l-x-l on 2009-05-12
> **freeman2000 said:**
> There's a real good program in the repos called "bleachbit".  Go to Synaptics to download it.  It will clean out the cache, cookies, history, etc in Firefox along with other web browsers.  In addition, it cleans out temp files from numerous other programs, such as Adobe, OpenOffice, and others.  Works great.  Good luck.

Thanks for the tip. I'm checking it out now.

---

