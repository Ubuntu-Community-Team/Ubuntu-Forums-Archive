---
title: "Problem with Sound Juicer (Audio CD Extractor)"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-06-06
Hi Community:

Something has happened to [COLOR="Red"]Sound Juicer[/COLOR] on my system: when I load a pre-recorded music CD in my CD reader and Sound Juicer comes up, Sound Juicer no longer finds:

[LIST]
[*]The name of the album,
[*]The artist,
[*]any of the names of the cuts on the music CD.
[/LIST]

Sound Juicer used to do this!

How do I recover Sound Juicer's former capability to do this??

Thanks!
Phil Smith

---

### Post by Swagman on 2011-06-06
I wish that would happen on my system. I have to "pull the Plug" (Ethernet lead) to stop it fetching that information.

Why do I need it to stop  fetching that info ?

I have (numerous) Multi CD compilations etc. When you put the first CD in SJ goes and gets the info for the entire compilation, not just the first CD ( & repeat).

So you have to Delect ALL anyway, Then select the ones you want and remember that last track number so you can... Deselect ALL on the next cd and select from the last number etc.

And when you have finally ripped them all you find, for some strange reason, that the first two songs of the subsequent cd's are all the same song.

What an utter waste of effort

Pull the lead and do it manually !!

---

### Post by Old Jimma on 2011-06-22
Hi Ubuntu Community:

I found a solution to this problem posted on a blog at 

[COLOR="Red"]**[http://www.jpstacey.info/blog/2011/06/13/sound-juicer-no-longer-retrieves-track-names-when-you-extract-audio-cds]("http://www.jpstacey.info/blog/2011/06/13/sound-juicer-no-longer-retrieves-track-names-when-you-extract-audio-cds")**[/COLOR]

The problem was that Sound Juicer relies on Musicbrainz to retrieve metadata (CD title, artist name, track names, etc) to populate the fields in Sound Juicer. The blogger suggested that Musicbraninz discontinued/modified service, leaving old versions of Sound Juicer with no way to access the metadata.

For Lucid Lynx and more recent releases the solution is to remove the old version of Sound Juicer and install a new one that utilizes Musicbrains new way of providing users the metadata.

Here are the steps:

[COLOR="Red"][B]sudo add-apt-repository ppa:phw/musicbrainz
sudo apt-get update && sudo apt-get upgrade[/B][/COLOR]

THen reboot and try it. If this doesn't work try:

[COLOR="Red"][B]sudo apt-get remove sound-juicer
sudo add-apt-repository ppa:phw/musicbrainz
sudo apt-get install sound-juicer[/B][/COLOR]

reboot and try. 

[COLOR="Blue"]**In both of those code segments, replace that smiley face with a colon... ":" followed by a lower case p. The forum software automatically replaces a colon followed by a lower case p wit a smiley face.**[/COLOR]

[COLOR="Blue"]**My experience is that both of these suggestions worked on June 21, 2011 for Lucid Lynx.**[/COLOR]

Sound Juicer will populate fields for many CDs when Musicbrainz has the meta data. However, for obscure CD's Musicbrainz may not have the data. In this case, you will either need to 
[LIST]
[*]populate the fields manually, or
[*]enter the metadata into Musicbrainz so that the rest of the community has access to it, also.
[/LIST]

I hope this helps someone else.

Phil Smith de Duluthistan, GA

---

### Post by Swagman on 2011-06-22
It wouldn't do that if you encased your links in code tags

```
sudo add-apt-repository ppa:phw/musicbrainz
(press enter)
sudo apt-get update && sudo apt-get upgrade
(press enter)
```

And

```

sudo apt-get remove sound-juicer
(press enter)
sudo add-apt-repository ppa:phw/musicbrainz
(press enter)
sudo apt-get install sound-juicer
(press enter)
```

---

### Post by ubuntujonez on 2011-07-27
Thanks for posting this. I'm back to ripping without typing!

---

### Post by Old Jimma on 2011-07-31
:p

---

### Post by John_T on 2012-02-04
I ad the same issue. The fix above doesn't seem to work for me though. I'm using 10.04 Lucid

For what it's worth, the "Retrieving tack listing...please wait" message in the status bar never goes away, even though it has retrieved all the track names and artists.

Any ideas? Or is there an alternative ripper I can use for multi-disc compilations?

---

### Post by remerson on 2012-04-01
This is still broken for me also and the above fix does not seem to work. I am running 10.04 LTS 64-bit.

According to this:

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/797473](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/797473)

A package fix was release for the latest version 22 March 2012 but it looks like this has yet to make it to Lucid so users on this version are stuck with SJ broken until it's backported (?).

---

### Post by gumpish on 2012-06-10
> **remerson said:**
> A package fix was release for the latest version 22 March 2012 but it looks like this has yet to make it to Lucid so users on this version are stuck with SJ broken until it's backported (?).

Unfortunately in spite of Launchpad's assurances to the contrary, this bug is still present even in 12.04 LTS.

It's unusual since the version of sound-juicer (3.4.x) is high enough that it's built against libmusicbrainz4 (indeed, libmusicbrainz4-3 appears as a dependancy), and libmusicbrainz4 is supposed to work with the new data format for transmitting track info... but it still just doesn't work.

I'm not inclined to install mystery-meat on my system (untrusted PPA software) just to get my track names... guess I'll have to build this from source...

---

### Post by Old Jimma on 2012-06-10
Hi Gumpish:

So, for those of us that want to upgrade to Precise, what is your recommendaton?

Thanks,
Phil de Duluthistan

---

### Post by gumpish on 2012-06-10
Phil:

It seems the simplest answer is to just find an alternative. Thankfully there's a pretty versatile command-line ripping tool which is in the repositories, abcde (A Better CD Encoder).

It has many, many options - I found the config file on the following page to provide almost everything I needed: [http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

The biggest "gotcha" for me was that where it says ${OUTPUT} that's actually the format you're encoding to, so my files were in ~/music/ogg/Artist Name/etc...

Also I overlooked the fact that the config file is set up to output to ~/music (lowercase "m") instead of the usual ~/Music (uppercase "M").

You'll want to look at the config file before using it. For anything that doesn't make sense, the config file options are documented in the abcde man page.

I also noticed that the ripping speed (from the optical drive) was really slow... faster than 1x but not much. Maybe 4x? The man page claims that the default is to use the maximum speed supported by the underlying ripping program (cdparanoia by default) and the optical drive, but I don't think it worked out that way.

If I was going to rip a large number of discs I'd do more research into getting the speed up.

Another option would be to just a standalone ripper - something that just rips the audio tracks to WAV files or something, then use a standalone tagger. This is pretty much what abcde is, a script that glues those together, and it works well. (Apart from the speed issue.)

---

### Post by andrew.46 on 2012-06-11
> **gumpish said:**
> It has many, many options - I found the config file on the following page to provide almost everything I needed: [http://www.andrews-corner.org/abcde.html]("http://www.andrews-corner.org/abcde.html")

Good to hear my page has been useful to you :).Development has kickstarted for abcde again and 2.5.2 has been released:

```

andrew@skamandros~$ abcde -v | head -n 1
This is abcde v2.5.2.

```

with a few hints that [NeroAacEnc may be added in soon]("http://code.google.com/p/abcde/issues/detail?id=8") for aac encoding. Good to see some movement again!

---

### Post by andrew.46 on 2012-06-23
And now:

```

andrew@skamandros~$ abcde -v | head -n 1
This is abcde v2.5.3.

```

---

### Post by djfake on 2012-07-06
I'm trying Asunder, it's okay, won't strip spaces in titles however. 

Just a shame about Sound Juicer. Why it doesn't use CDDB is beyond me. And why Ubuntu lets a crap package like that be the default ripper is even more crazy.

---

