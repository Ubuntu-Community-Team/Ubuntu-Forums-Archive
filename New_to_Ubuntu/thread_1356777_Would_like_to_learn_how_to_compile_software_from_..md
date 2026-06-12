---
title: "Would like to learn how to compile software from .tar.gz (not through repositories)"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by asif_1088119 on 2009-12-16
i want to install the latest version of vlc.u cannot find this version  in repository.the only way to have this is to make it.but how can i do  it?i tried to follow some instructions from readme after extracting it.but it left me nowhere..i m stucked.what to do ?please give me enough idea & dont tell me to use aptget or synaptic.i want to solve this problem anyhow.WHERE ARE ALL DA LINUX GURU's???

---

### Post by fancypiper on 2009-12-16
Perhaps these will help:

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

---

### Post by asif_1088119 on 2009-12-16
thnx fancypiper...i checked first site before...i wasnt working..let me check the others

---

### Post by aysiu on 2009-12-16
Why don't you explain why we shouldn't recommend *apt-get* or Synaptic? Those are the two easiest ways to install VLC.

---

### Post by asif_1088119 on 2009-12-16
may be i hav been a bit arrogant in this matter..i hav been trying for about 12-15 hours at a stretch...but couldn't quite make it...i can easily use apt-get or synaptic...but i want to learn why cant i do this with source code??furhtermore...i wont get the latest version of vlc there in synaptic....if there is anyone who has installed vlc-1.0.4 HELP ME...i m new in this world but i want to be familiar with this

---

### Post by aysiu on 2009-12-16
If you want to learn how to compile software from source, that's one thing.

If you just want the latest version of VLC, you can get that from GetDeb:
[http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc](http://www.getdeb.net/updates/Ubuntu/9.10/?q=vlc)

---

### Post by asif_1088119 on 2009-12-16
thanx a lot for the site...i wanted both...learn & get latest vlc...u helped me for half of the part...learning is still not complete yet :D....anywayz ...thanx again

---

### Post by aysiu on 2009-12-16
> **asif_1088119 said:**
> thanx a lot for the site...i wanted both...learn & get latest vlc...u helped me for half of the part...learning is still not complete yet :D....anywayz ...thanx again Okay. Glad to have helped with at least half of it.

I've retitled your thread. If you just say you want to install VLC, you're far more likely to get a flood of people asking you to use *apt-get* or Synaptic.

---

### Post by NoaHall on 2009-12-16
```
cd /home/user/locationofextractedfolder/
./configure
make 
make install

```
There you go.

---

### Post by SuperSonic4 on 2009-12-16
The above is usually, but not always, the case. Either way you should check the README or INSTALL text files that contain the instructions

Since you're compiling from source you may want to look at some of the optimisations you can give your install ;) ```
./configure --help > options.txt
```

That will give the options (for example *--prefix=/usr/local* will install VLC to /usr/local so it can coexist with the repo version) you can use in configuration and pipe it to a text file which called options which can be opened in a text editor



edit: yeah the above is fine, just watch out for dependency issues, especially regarding x264 in my experience

---

### Post by NoaHall on 2009-12-16
> **SuperSonic4 said:**
> The above is usually, but not always, the case. Either way you should check the README or INSTALL text files that contain the instructions

Since you're compiling from source you may want to look at some of the optimisations you can give your install ;) ```
./configure --help > options.txt
```

That will give the options (for example *--prefix=/usr/local* will install VLC to /usr/local so it can coexist with the repo version) you can use in configuration and pipe it to a text file which called options which can be opened in a text editor



edit: yeah the above is fine, just watch out for dependency issues, especially regarding x264 in my experience

+1 to that, too. If you run to a problem with installing from source, it will probably say something is missing. You need to install the dev package of the software it names. If you get stuck, we're always here to help, or google is never that far away :)

---

### Post by alien8predator on 2009-12-16
isn't it easier using the terminal?

sudo apt-get install vlc

---

### Post by NoaHall on 2009-12-16
> **alien8predator said:**
> isn't it easier using the terminal?

sudo apt-get install vlc

... Please read the other posts in this thread.

---

### Post by asif_1088119 on 2009-12-17
thanx @noahall & supersonic4....i hav tried ordinary ways to install...like noahall mentioned at first...but there were lots of errors & warnings in terminal...let me check about
_./configure --help > options.txt   _                  if this give me some idea...otherwise  i will let u know what trouble i face...but the interesting thing is do u know why i m so desperate to install the latest version of vlc???hav a guess...

@aysiu from getdeb i downloaded 1.0.2 ...it wasnt 1.0.4 actually...but it was better than 0.9 though

---

### Post by mc4man on 2009-12-17
here are some general tips to building vlc ( was in ref. to karmic and 1.0.3, -  1.0.4 represents no changes build wise, jaunty should be able to meet most, if not all, the deps as far as version

[http://ubuntuforums.org/showthread.php?p=8484189#post8484189](http://ubuntuforums.org/showthread.php?p=8484189#post8484189)

The real gist was to use static x264 and ffmpeg builds from current sources to build vlc off of. ( if vlc happens to error on one or the other then you need to use slightly earlier revisions of both x264 and ffmpeg

build static x264 -> build static ffmpeg -> build vlc

And also to read ./configure --help and read back thru your configure output before make.

---

### Post by oldos2er on 2009-12-17
And if you want a version of ffmpeg that isn't broken, you will first need to compile it: [http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by thelaw on 2009-12-17
Fancypiper.

Just a quick thanks for all three of those links.

signed...yan (yet another noob :) )

---

### Post by Jive Turkey on 2009-12-17
If I were you I would check out the guide on these forums for compiling the latest mplayer/ffmpeg/mencoder first.

Post the specific errors you get when compiling the package.  

Most likely they have to do with missing dependencies.  When I get those I look for the missing package in synaptic.  For compiling applications you would be looking for the <nameofpackage>-dev version of the package.

---

### Post by SuperSonic4 on 2009-12-17
> **asif_1088119 said:**
> thanx @noahall & supersonic4....i hav tried ordinary ways to install...like noahall mentioned at first...but there were lots of errors & warnings in terminal...let me check about
_./configure --help > options.txt   _                  if this give me some idea...otherwise  i will let u know what trouble i face...but the interesting thing is do u know why i m so desperate to install the latest version of vlc???hav a guess...

@aysiu from getdeb i downloaded 1.0.2 ...it wasnt 1.0.4 actually...but it was better than 0.9 though

Not sure to be honest, I would have thought if you wanted to compile you'd test the git version (which is 1.1-Git)


Post the error here, I've compiled vlc before and the git version required the repo x264 (20090416) or video would not play. Plus make install didn't work but it could still be launched from it's directory

Also it's unlikely configure help will give troubleshooting info

---

### Post by fancypiper on 2009-12-17
> **thelaw said:**
> Fancypiper.

Just a quick thanks for all three of those links.

signed...yan (yet another noob :) )Glad to help.

Try this:
sudo apt-get install rute
for a local copy of the [LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz).

---

### Post by mc4man on 2009-12-17
> Also it's unlikely configure help will give troubleshooting info

While it's not a 'troubleshooting' guide, if you read thru and also read thru the configure output then you won't need any 'troubleshooting' help and you'll have a well done vlc that can be installed.

The fact that vlc passes a configure is potentially meaningless

The 1.1 git is interesting to take a look at every once and awhile (or use if you need vaapi in vlc
For an everyday player I'd use the current 1.0.4 or 1.0.4+

---

### Post by Zoot7 on 2009-12-17
A very useful command when attempting to compile stuff from source is 
```
sudo apt-get build-dep <name>
```
That'll pull in all the dependencies needed to build the version in the repos.

---

### Post by andrew.46 on 2009-12-17
Hi asif,

> **asif_1088119 said:**
> i want to install the latest version of vlc.u cannot find this version  in repository.the only way to have this is to make it.but how can i do  it?i tried to follow some instructions from readme after extracting it.but it left me nowhere..i m stucked.

vlc is not the easiest to compile and as you have probably found the few guides that deal with the nuts and bolts of doing this either on these Forums or on the Internet in general are usually a little out of date. A good starting point is here:

UnixCompile
[http://wiki.videolan.org/UnixCompile](http://wiki.videolan.org/UnixCompile)

And as others have suggested perhaps have a look at a few of the compilation guides that are kept up to date on these forums for a few pointers towards the 'Ubuntu way'?

I should also mention that you may be a little disappointed if you are simply looking at differences between point revisions of the 1.0 versions of vlc. Each incremental upgrade is nice but you should weigh up the considerable effort involved to compile your own copy of current vlc with the rewards of going from say 1.0.2 to 1.0.4 :). Having said that I have compiled the current version myself, not on Ubuntu I'm afraid so I can be of little assistance to you, and I had a *huge* amount of fun doing it, so keep working at it!

All the best,

Andrew

---

### Post by asif_1088119 on 2009-12-19
thnx andrew.46 for ur link & thnx zoot7...

---

### Post by 3rdalbum on 2009-12-19
Make sure your terminal is in the correct directory (the one that contains the "configure" script for VLC) before you start running ./configure, make or sudo make install.

If you don't know how to navigate a terminal, you can learn ([www.linuxcommand.org](www.linuxcommand.org)) or install the "nautilus-open-terminal" package, which gives you an "Open Terminal Here" item in your right-click menu.

Also make sure you have the "build-essential" package. And to make your job easier you can tell Ubuntu to get all the build dependencies for its version of VLC:

```
sudo apt-get build-dep vlc
```

The build dependencies for the old VLC are probably the same as for the new version.

I hope this gets you on your feet and helps you to start compiling software!

---

