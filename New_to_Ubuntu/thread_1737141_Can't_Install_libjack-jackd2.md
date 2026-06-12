---
title: "Can't Install libjack-jackd2"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by klausner on 2011-04-23
Trying to get ffmpeg installed on lucid with upgraded kernel 2.6.38. Synaptec complains about dependencies, which chase down to libjack-jackd2. 

The error message is:> Package libjack-jackd2-0 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

How can I get ffmpeg installed? ](*,)

---

### Post by spikoley on 2011-04-23
I installed it for 10.10.  Do an update and try again.

```
sudo apt-get update
```

Then try installing libjack-jackd2-0 by itself.

```
sudo apt-get install libjack-jackd2-0
```

---

### Post by klausner on 2011-04-23
> **klausner said:**
> Trying to get ffmpeg installed on lucid with upgraded kernel 2.6.38.

As I said, lucid. It doesn't install!

---

### Post by klausner on 2011-04-26
Bump.

---

### Post by FakeOutdoorsman on 2011-04-27
Are you sure this package is even available for Lucid? I don't see it using *aptitude search*, in Synaptic, nor in [Ubuntu Packages Search](http://packages.ubuntu.com/search?suite=lucid&searchon=names&keywords=libjack-jackd2-0). My apt output is different:
```
$ sudo apt-get install libjack-jackd2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libjack-jackd2-0
```
Are you using the wrong sources for Lucid or any PPAs?

---

### Post by mysterious_beans on 2011-07-13
Not sure if you're still into this, OP, but it's a prominent search result for a similar problem I'm working on (installing Neil Modular Tracker on Lucid), so here's a guess as to what's wrong, and how to fix it.

It appears that jackd2 wasn't added to Ubuntu until Maverick (the next release), so the sources for apt-get have no idea about it. We have at least two possible (and possibly insane) paths to try:

1) find a repository for the jackd2 stuff and add it to 'sources.list', update, blah blah blah

2) find the source, and unpack it locally, then build-n-install, blah blah blah

Have you tried either of these? If not, for a good reason, please post your reason so I may be disabused of my ignorance.

I'm about to investigate the viability of these options. I will try to post back with results regardless of success or failure.

Even if you're not still tracking this (or you've solved it and forgotten to follow-up), here's hoping it'll help someone. :-D

Cheers!

P.S. I'm distracted by many, many things, and I may take a while to get back to this if there are complications along the way. ;-)

---

### Post by mysterious_beans on 2011-07-13
Okay, so I added this line to my 'sources.list'
```
deb http://ca.archive.ubuntu.com/ubuntu/ maverick main universe
```
and then I did
```
sudo apt-get update
```
followed by
```
sudo apt-get update
```
and then I got distracted by something and didn't notice that a massive number of other Maverick packages had been selected, so I said 'go', and it installed them all (took a few mins), but nothing really unusual happened.

So, I may have all but upgraded to Maverick, but I'm not fussed if that's the case (as long as it doesn't screw over any automatic upgrade in the future).

Either way, the library (jackd2) is installed. This was my only outstanding dependency while attempting to install Neil (so far, anyway).

I'm not going to bother with idea 2, even though it was probably the more effective/tactical/precision method (what I did probably amounts to cluster bombing, but I'm over the whole "immaculate file system" thing I used to be into). :-)

If you found another (most likely better) solution, I would definitely like to hear about it.

---

### Post by mysterious_beans on 2011-07-13
Update:

After a few more distractions, and a few more thoughts, I'm going to upgrade to Maverick with
```
sudo apt-get upgrade
```
because I have no compelling reason not to, and I want to make sure my kernel and libs match.

I will admit I'm not totally certain it would even be a problem, but better safe than sorry, I suppose. :-)

Good luck!

---

### Post by CatKiller on 2011-07-14
> **mysterious_beans said:**
> Update:

After a few more distractions, and a few more thoughts, I'm going to upgrade to Maverick with
```
sudo apt-get upgrade
```because I have no compelling reason not to, and I want to make sure my kernel and libs match.

If you're going the command-line upgrade route, you need to change all your repositories to maverick rather than just main, and you want to use ```
sudo apt-get dist-upgrade
```

From man apt-get:

```
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages. The /etc/apt/sources.list file
           contains a list of locations from which to retrieve desired package
           files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

```

---

### Post by mysterious_beans on 2011-07-17
Cheers. It looks like Natty was available, so I upgraded straight to that.

No major problems, though there appear to have been a few small hitches, like for instance, my 'EDITOR' environment variable is no longer defined (I think it used to be). It seems to be small stuff like that mostly, so I'll just fix as I go.

I was mostly worried about something silly like a library trying to call a kernel function that doesn't exist until a newer version, on boot, and leaving me with a more or less inoperative system). As long as I have a half-working shell or better, I'm okay. :-)

Oh yes, I found this helpful for inspecting the 'sources.list' contents for the various releases: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by mysterious_beans on 2011-07-17
So, the main annoyance from the upgrade relates to a shell I like to use called Tilda; it depends on 'TERM' being set, and it seems that was being done by a library before. That library has changed, so now something else needs to help Tilda figure out its terminal info.

My just-get-it-working solution was to add
```
export TERM=xterm
```
to my .bashrc file (near the top). And then I restarted Tilda, and confirmed the fix with
```
set | grep TERM
```

I found some bug reports that were somewhat related, but they are in mid-process; this quick fix will tide me over.

---

### Post by mysterious_beans on 2011-07-17
(Sorry, this is a duplicate post, and I couldn't find a way to delete it; mods, please?)

---

