---
title: "Quicktime??"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by adsy mac on 2009-08-24
Ok, so i am fairly new to ubuntu, had it for a couple of weeks now. Ive  been looking around and have installed the best apps and what not. the weird thing is is that quicktime used to run fine but now it doesnt let me anymore. i get this message

[B]"The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported."[/B]

When i search for the plugin, it says there isnt one.
I dont understand why it suddenly stopped working. all i can think of is that after installing an app, its dissabled something.

ive also read many threads about people with quicktime problems in ubuntu but theirs just seems to be the simple matter of installing and app such as mplayer or something.

any ideas?

any help is much appreciated :)

---

### Post by oboedad55 on 2009-08-24
> **adsy mac said:**
> Ok, so i am fairly new to ubuntu, had it for a couple of weeks now. Ive  been looking around and have installed the best apps and what not. the weird thing is is that quicktime used to run fine but now it doesnt let me anymore. i get this message

[B]"The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported."[/B]

When i search for the plugin, it says there isnt one.
I dont understand why it suddenly stopped working. all i can think of is that after installing an app, its dissabled something.

ive also read many threads about people with quicktime problems in ubuntu but theirs just seems to be the simple matter of installing and app such as mplayer or something.

any ideas?

any help is much appreciated :)

Not to worry, I've got the same problem. All the restricted extras are installed, etc. Type in "about:plugins" without quotes into your Firefox address bar and see if quicktime is listed. That's your first step. Do a tag search for quicktime and you'll see my post.

Jon

---

### Post by SunnyRabbiera on 2009-08-24
If you are going to apples site no wonder, watching trailers is becoming a pain as quicktime is becoming more and more linux unfriendly...
as if it wasnt unfriendly enough

---

### Post by oboedad55 on 2009-08-24
> **SunnyRabbiera said:**
> If you are going to apples site no wonder, watching trailers is becoming a pain as quicktime is becoming more and more linux unfriendly...
as if it wasnt unfriendly enough

Yes, it is unfriendly. I don't normally bother with quicktime files, but since this came up I wanted to find a solution. Is there one? Everything is set up correctly in Firefox, all the plugins are there, file associations are correct, but no love. Any ideas?

---

### Post by Thelasko on 2009-08-24
Does Quicktime not work at all or just in Firefox?

In Firefox, go to edit>preferences and click on the applications tab.  Next to Quicktime Video, make sure it says "Use Movie Player."   If it doesn't you can change it by simply clicking on it.

---

### Post by adsy mac on 2009-08-24
> **Thelasko said:**
> Does Quicktime not work at all or just in Firefox?

In Firefox, go to edit>preferences and click on the applications tab.  Next to Quicktime Video, make sure it says "Use Movie Player."   If it doesn't you can change it by simply clicking on it.

no luck, just keeps saying i need to search for a suitable plugin, even though there isnt one when i click search, and it worked before so somethings gone missing or something :/

---

### Post by oboedad55 on 2009-08-24
> **adsy mac said:**
> no luck, just keeps saying i need to search for a suitable plugin, even though there isnt one when i click search, and it worked before so somethings gone missing or something :/

No luck here either. Same idiotic message.

---

### Post by meeples on 2009-08-24
apple have just made it so qucktime movies can only be played on quicktime and not gstreamer [what ubuntu uses] but there working on a patch upstream :D

---

### Post by adsy mac on 2009-08-24
> **meeples said:**
> apple have just made it so qucktime movies can only be played on quicktime and not gstreamer [what ubuntu uses] but there working on a patch upstream :D

SCANDALOUS!! haha. well i hope the get it working soon.

---

### Post by LowSky on 2009-08-24
they changed something again.... install w32/64codecs donesnt work?

32 bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

64bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

---

### Post by adsy mac on 2009-08-24
> **LowSky said:**
> they changed something again.... install w32/64codecs donesnt work?

32 bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```64bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

how do i find out what "bit" my ubuntu is??

---

### Post by meeples on 2009-08-24
> **LowSky said:**
> they changed something again.... install w32/64codecs donesnt work?

32 bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

64bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

doesnt make a difference, because its apple restricting it.

just have to wait it out :(

---

### Post by Thelasko on 2009-08-24
Do you have a link to the video in question?  Perhaps I missed it...

---

### Post by oboedad55 on 2009-08-24
> **LowSky said:**
> they changed something again.... install w32/64codecs donesnt work?

32 bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

64bit ubuntu

```
wget -c [http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20071007-0medibuntu1_amd64.deb)
sudo dpkg -i w64codecs_20071007-0medibuntu1_amd64.deb
```

Nope, doesn't work. I've got all that stuff installed. In firefox it's set to use the quicktime plugin. Setting it to use the movie player does nothing.

---

### Post by Thelasko on 2009-08-24
> **oboedad55 said:**
> I've got all that stuff installed. In firefox it's set to use the quicktime plugin. Setting it to use the movie player does nothing.

You want it set to use the movie player since there really is no Quicktime plugin for Ubuntu.

---

### Post by oboedad55 on 2009-08-24
> **Thelasko said:**
> You want it set to use the movie player since there really is no Quicktime plugin for Ubuntu.

I did set it to movie player. Still no love...

---

### Post by Thelasko on 2009-08-25
> **oboedad55 said:**
> I did set it to movie player. Still no love...
You may have to install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

---

### Post by oboedad55 on 2009-08-25
> **Thelasko said:**
> You may have to install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

Been there already.

---

### Post by LowSky on 2009-08-25
> **adsy mac said:**
> how do i find out what "bit" my ubuntu is??

a few ways but for people not used to Linux, open firefox, go to help, click on about, and it will say what version is install64 bit will say x86_64

---

### Post by Thelasko on 2009-08-25
So I'm playing around on movies.apple.com and am noticing that instead of giving your browser a video file to play, it gives it some sort of header file.  It's a .mov file type, but it's only about 84-85 bytes.  This tells me that the video is not actually in that file but somewhere else, because it's much too small.

The question is, what's in that file?

---

### Post by Technoviking on 2009-08-25
Here is the upstream bug report about it.
[http://bugzilla.gnome.org/show_bug.cgi?id=592665](http://bugzilla.gnome.org/show_bug.cgi?id=592665)

T-V

---

### Post by Thelasko on 2009-08-25
Good work Technoviking.  I changed Firefox's user agent string to
```
QuickTime/7.6.2 (qtver=7.6.2;cpu=IA32;os=Mac 10.5.7)
```
and was able to get the "The following **Preview** has been approved for **Appropriate Audiences** by the Motion Picture Association of America, Inc." part of the preview.  Unfortunately, the video still does not play.

---

### Post by Thelasko on 2009-08-25
A solution I found [here]("http://www.macosxhints.com/article.php?story=20050430173712176") says you also need the following cookie to view the video.
```
ac_survey=1; dssid2=b79000f5-aa77......%3B;
```
Unfortunately, I don't know much about cookies other than how to delete them.

---

### Post by Thelasko on 2009-08-25
[This post]("http://ubuntuforums.org/showthread.php?t=1245441&page=4") as a lot more information on the problem.  Hopefully it will be solved soon

---

### Post by wild_oscar on 2009-08-27
I'm also having trouble watching quicktime trailers. Has any upstream bug been opened for it?

---

