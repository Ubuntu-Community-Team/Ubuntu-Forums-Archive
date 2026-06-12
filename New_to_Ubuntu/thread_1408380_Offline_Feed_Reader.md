---
title: "Offline Feed Reader?"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bornagainpenguin on 2010-02-16
I've been holding on to Ubuntu Hardy Heron 8.04.4 for awhile now both due to needed hardware support and for application compatibility with my preferred feed reader. Straw.  Unfortunately, while the hardware support seems to be slowly improving, I have been unable to find a replacement offline feed reader for Straw and since it has become increasingly clearer Straw is abandonware and will not be updated to work on the newer python, or to use the new python gecko modules I need to find a replacement for when Canonical drops support for Hardy Heron.  I have tried out quite a few different feed readers in the past but have been unable to find one with Straw's killer feature...

Straw has the ability to download and cache locally any images associated with a post for offline viewing.  I *need* that feature!  Many of my feeds include images as an important part of the article, and I am unable to always be connected to a WiFi hotspot in the rural area where I live.  Without the ability to cache both images and text a feed reader is not truly offline or useful to me.

Can someone please recommend me a feed reader that offers ***true*** offline?

Thanks in advance!

--bornagainpenguin

---

### Post by cameronedwards on 2010-02-16
GPODDER!
Took a long time to find the right one sorry (all caps and such)
I'm not sure but i think anything classed as a podcast client should be able to download from a feed (thereby making it offline viewable)

hope this helps!

---

### Post by cameronedwards on 2010-02-16
> **cameronedwards said:**
> GPODDER!
Took a long time to find the right one sorry (all caps and such)
I'm not sure but i think anything classed as a podcast client should be able to download from a feed (thereby making it offline viewable)

hope this helps!

Scratch that it only works in karmic, sorry.
but i think that the podcast client rule still stands so maybe search synaptic / apt-cache search for 'podcast'?

---

### Post by bornagainpenguin on 2010-02-16
> **cameronedwards said:**
> Scratch that it only works in karmic, sorry.
but i think that the podcast client rule still stands so maybe search synaptic / apt-cache search for 'podcast'?

You think I would be able to use a podcast client to read feeds like the engadget one here?

```
http://www.engadget.com/rss.xml
```

**EDIT--**  Okay I tried it out on my Karmic install on my spare desktop, and it doesn't want to display the images offline.  Gpodder grabs the first article of each feed and the text, then opens everything in firefox when I open the article.  If there is an active internet connection it will download any images in place, otherwise nothing gets displayed.  Any other suggestions?

---

### Post by bornagainpenguin on 2010-02-18
/two days later bump

---

### Post by bornagainpenguin on 2010-02-20
I just posted on the [Lucidor]("http://lucidor.org/lucidor/") support forums about their newsroom feature.  Lucidor is an ePub reader that runs on Linux, Windows, and MacOS X so if the developer can make it do what I need I may have at long last found the successor I need to Straw, one that also allows me to read ebooks!  I will keep this thread updated if there is any news.

Funny, I wasn't even looking for anything feed related and I stumbled across this application that could be the answer to my prayers...

--bornagainpenguin

---

### Post by jpl888 on 2010-02-20
I don't know if it is true offline but liferea has an offline option. Perhaps you could try that?

---

### Post by bornagainpenguin on 2010-02-21
> **jpl888 said:**
> I don't know if it is true offline but liferea has an offline option. Perhaps you could try that?

I have it only displays text, not images offline.  Supposedly there was [a filter script that would allow it to do this, but I have never been able to make it work](http://ubuntuforums.org/showthread.php?t=1251672).  If you figure it out and can explain how to make it work for me, I'd be much obliged!

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-09
Got a hold of the guy writing Lucidor and he explained the application does cache images for offline reading in ePub files created using the feeds section of the program, unfortunately these images are only cached locally and will not transfer with the ePubs themselves,  He also said that the feeds section is still a work in progress so it will not be able to do what I need yet.

So, back to the main point of this thread--does anyone know of a way to cache feeds in full, in an application of their own that can download the various images and text associated with the feeds for later offline reading in such a way it will display everything?

--bornagainpenguin

---

### Post by Sir Jasper on 2010-03-09
My apology for double posting. Please see the next post.

---

### Post by Sir Jasper on 2010-03-09
> **Sir Jasper said:**
> Hi,

This is probably a throwaway thought, but could you identify what you need using your Feed Reader and then use Evernote [free version] to get the pages with full text and pictures.

I have used Evernote via Wine and Internet Explorer but I think there  is a ´buntu Firefox Evernote add-on.

I have no expertise in your requirement - just trying to help as you have waited a long time.

My regards

PS There is also a Scrapbook add-on for Firefox.

---

### Post by bornagainpenguin on 2010-03-09
> **Sir Jasper said:**
> Hi,

This is probably a throwaway thought, but could you identify what you need using your Feed Reader and then use Evernote [free version] to get the pages with full text and pictures.

I have used Evernote via Wine and Internet Explorer but I think there is a ´buntu Firefox Evernote add-on.

I did a google of the application and found the Firefox extension you speak of, the reviewers are saying it is incredibly [unstable](https://addons.mozilla.org/en-US/firefox/addon/8381) on the latest version of Firefox.

> **Sir Jasper said:**
> I have no expertise in your requirement - just trying to help as you have waited a long time.

My regards

I appreciate that.  Basically what I am looking for is an application that can upon being opened read through a list of feeds and download their content (text and any associated images) and cache these for later reading offline.  I have a netbook with WiFi but unfortunately not everywhere I go has an open access point, so having my feeds (from news sites and blogs) allows me to read stuff offline and stay current even while not connected.

Straw Feed Reader used to do this quite well, before it was essentially abandoned and allowed to bitrot away as newer versions of Python dropped backwards compatibility and html libraries changed names and versions.  Sure the application occasionally seemed to really slam the hard disk when writing the feeds to its database, but I could set it to run overnight while I was sleeping and have all sorts of articles to read later.  Unfortunately it seems that Straw is the only application of its kind that runs on Linux.  When ever you see a feed reader on Linux claiming to have offline support it always seems to be the text they refer to, not the associated images.

What good is it to have an xkcd feed without the images?

Or an engadget feed discussing a new device without the images of that device?

This is why I want a truly offline feed reader.

> **Sir Jasper said:**
> PS There is also a Scrapbook add-on for Firefox.

I've tried that one before, it seemed to be more of a webcopier like HTTRack than a feed reader.

Also, I'm trying to get something that is its own application if at all possible.

--bornagainpenguin

PS: Thanks again for the reply, I appreciate any help given!

---

### Post by bornagainpenguin on 2010-03-17
Regularly scheduled bump.  Feel free to ignore (most people chose this option).

--bornagainpenguin

PS: Is there a prize for thread with the most bumps and no solution that works?

---

### Post by Sir Jasper on 2010-03-17
Hi again,

Perhaps you could PM carlee, for example, with a link to this thread asking if she/he would would so kind as to read it.

Expecting a PM response might be a bit much, but asking someone to view your thread seems,  at least to me, to observe good etiquette.

My regards

---

### Post by vincentertainment on 2010-03-17
Sounds like a useful program. I live in a rural area too. No broadband here.
 
I'm not a programmer but I was wondering how hard would it be for someone who is a programmer to update Straw for newer releases or to import that offline photo archiving feature into another program?
Isn't that one of the advantages of open source and free licensces?

---

### Post by bornagainpenguin on 2010-03-18
> **Sir Jasper said:**
> Perhaps you could PM carlee, for example, with a link to this thread asking if she/he would would so kind as to read it.

Okay, I'll bite--who is carlee and why should I ask for her to read this thread?  Googling does nothing.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-18
> **vinsect said:**
> Sounds like a useful program. I live in a rural area too. No broadband here.

Then you know my pain.  Actually I get DSL at home, but I don't stay home all day, I have to move about and that is where I run into the dearth of internet issue.  Not that the DSL I get is all that much better than dial-up these days thanks to how much Verizon keeps choking me, but still...

> **vinsect said:**
> I'm not a programmer but I was wondering how hard would it be for someone who is a programmer to update Straw for newer releases or to import that offline photo archiving feature into another program?

As far as I can tell the biggest issue seems to be the changes between the 2.4 versions of Python and later, which have no backwards compatibility with each other and the changes in the HTML libraries the application uses to render with.  Assuming this can be fixed...

> **vinsect said:**
> Isn't that one of the advantages of open source and free licensces?

I keep hearing that one too.  Doesn't seem to hold up much unless you're either a programmer or a corporation; the rest of us have to make do the best we can no matter which platform we run...

--bornagainpenguin

---

### Post by ramnarayan on 2010-03-22
Solution from 2005

[http://mrpostman.sourceforge.net/index.html](http://mrpostman.sourceforge.net/index.html)

(03/06/2005) A new script for reading RSS feeds was released. In contrast to lots of RSS readers it will also download the full news message including pictures. Thus offline reading is made easy. Sample configurations for CNN, BBC, ... are provided.

**
Seems like this is an age old problem with no decent solution.

If anyone gets MRpostman running please let me know, its how to sucks and am not sure how this integrates into a mail client. ??

ram

---

### Post by bornagainpenguin on 2010-03-22
> **ramnarayan said:**
> Solution from 2005

[http://mrpostman.sourceforge.net/index.html](http://mrpostman.sourceforge.net/index.html)

(03/06/2005) A new script for reading RSS feeds was released. In contrast to lots of RSS readers it will also download the full news message including pictures. Thus offline reading is made easy. Sample configurations for CNN, BBC, ... are provided.

**
Seems like this is an age old problem with no decent solution.

If anyone gets MRpostman running please let me know, its how to sucks and am not sure how this integrates into a mail client. ??

ram

As I said in the other thread, I'll be giving this a try and posting back what my results (if anything) are.  Oh, and I also posted a link to Lucidor in that thread in case you're still looking for it.

--bornagainpenguin

---

### Post by sandyd on 2010-03-23
> **bornagainpenguin said:**
> I've been holding on to Ubuntu Hardy Heron 8.04.4 for awhile now both due to needed hardware support and for application compatibility with my preferred feed reader. Straw.  Unfortunately, while the hardware support seems to be slowly improving, I have been unable to find a replacement offline feed reader for Straw and since it has become increasingly clearer Straw is abandonware and will not be updated to work on the newer python, or to use the new python gecko modules I need to find a replacement for when Canonical drops support for Hardy Heron.  I have tried out quite a few different feed readers in the past but have been unable to find one with Straw's killer feature...

Straw has the ability to download and cache locally any images associated with a post for offline viewing.  I *need* that feature!  Many of my feeds include images as an important part of the article, and I am unable to always be connected to a WiFi hotspot in the rural area where I live.  Without the ability to cache both images and text a feed reader is not truly offline or useful to me.

Can someone please recommend me a feed reader that offers ***true*** offline?

Thanks in advance!

--bornagainpenguin
> **bornagainpenguin said:**
> Okay, I'll bite--who is carlee and why should I ask for her to read this thread?  Googling does nothing.

--bornagainpenguin
that would be me.
[s]
a) although ubuntu has dropped straw in karmic... installing it in karmic still works. If you want to stay with straw, you can still upgrade all the way to karmic and still use it.

I havent tested it on lucid cause one of the lucid bugs is inhibiting my ability to boot to the desktop, but ill get testing once I get the computer moving.[/s]

b) RSSowl seems to be able to cache images. [s]im downloading it to give it a run right now, but comcast is giving me 50kb/s, so this is gonna take some time....[/s]

Yup. As long as you open the post once, RSSowl will cache the image.
If you dont open it, only the text is cached.

Just press the update button, and ill download all the text. Ill see if it has a hidden option to download the images as well...

---

### Post by bornagainpenguin on 2010-03-30
> **carlee said:**
> that would be me.
[s]
a) although ubuntu has dropped straw in karmic... installing it in karmic still works. If you want to stay with straw, you can still upgrade all the way to karmic and still use it.

I havent tested it on lucid cause one of the lucid bugs is inhibiting my ability to boot to the desktop, but ill get testing once I get the computer moving.[/s]

Okay, thank you for your response.  Hmmm...in that case I'll give it a try again.  If I am able to get this working in my testing box I'll go ahead and install Karmic on my eeepc.

I was actually the one who more or less got Straw removed.  I was *hoping* to light a fire under someone to fix the problems that had plagued it since Jaunty...  My reasoning was that if the package was broken it should be removed until it is fixed.  Maybe it should be added back to the repositories if someone is willing to maintain it?

> **carlee said:**
> b) RSSowl seems to be able to cache images. [s]im downloading it to give it a run right now, but comcast is giving me 50kb/s, so this is gonna take some time....[/s]

Yup. As long as you open the post once, RSSowl will cache the image.
If you dont open it, only the text is cached.

Just press the update button, and ill download all the text. Ill see if it has a hidden option to download the images as well...

Funnily enough that's what I was searching for when I found this post again in Google.  Have you found any such settings?  If at all possible I'd prefer to move to an active feed reader rather than hold on with a death grip to one that is...well dead.  There haven't been any updates or any activity in Straw's git for 19 months now.

If for some reason the project would come back to life, then great; otherwise I'm looking to upgrade if at all possible.

Thanks for your time.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-04-01
Okay, I'm starting to remember why I didn't stick with Karmic on my eeepc--hardware issues.  I'm going to have another go at a reinstall to see if that makes any difference but right now its beginning to look more and more likely I'll be rolling back to Hardy again, especially now that the temperatures are hitting the 80's where I'm at.  I can't be having a netbook overheating on me when the ambient temperatures are also rising...  (Maybe the ambient temperatures are making me notice more the eeepc is fine?)

**EDIT --definitely a configuration error on my part somewhere along the line!  This install is moving along smoothly and without burning a hole in my pants from the heat!  Glad I gave it another try...**

Thanks for the reminder that the Jaunty package of Straw still works on Karmic.  Anyone know how to force it to install in Lucid?  Or failing that know of another application that can do the same functions Straw does?  (Offline reading complete with images)

--bornagainpenguin

---

### Post by sandyd on 2010-04-03
> **bornagainpenguin said:**
> Okay, I'm starting to remember why I didn't stick with Karmic on my eeepc--hardware issues.  I'm going to have another go at a reinstall to see if that makes any difference but right now its beginning to look more and more likely I'll be rolling back to Hardy again, especially now that the temperatures are hitting the 80's where I'm at.  I can't be having a netbook overheating on me when the ambient temperatures are also rising...  (Maybe the ambient temperatures are making me notice more the eeepc is fine?)

**EDIT --definitely a configuration error on my part somewhere along the line!  This install is moving along smoothly and without burning a hole in my pants from the heat!  Glad I gave it another try...**

Thanks for the reminder that the Jaunty package of Straw still works on Karmic.  Anyone know how to force it to install in Lucid?  Or failing that know of another application that can do the same functions Straw does?  (Offline reading complete with images)

--bornagainpenguin
no lucid without source editing :(

Ive taken a look at the changelogs for python and sent some emails to the python guys, and it seems the gtkhtml section of python is no longer included in the new release.

It has been replaced by the mozilla-gecko libraries, which will require a complete overhaul of straw in order for it to work.

---

### Post by bornagainpenguin on 2010-04-03
> **carlee said:**
> no lucid without source editing :(

Ive taken a look at the changelogs for python and sent some emails to the python guys, and it seems the gtkhtml section of python is no longer included in the new release.

It has been replaced by the mozilla-gecko libraries, which will require a complete overhaul of straw in order for it to work.

Oh well, I was a afraid of that.  I kind f expected Straw would be a dead end, considering as how it *has* been nineteen months since there were any commits in its git repository...

Do you know anything about [perl scripts]("http://ubuntuforums.org/showthread.php?t=1251672")?  I was looking to see if I could get Liferea to do what I need (considering it is still actively being worked on and all, always a good sign...) and this filter script came up in Google.  Unfortunately neither I or the other guy on the guy's blog have been able to make it work for us.  Could you look into it and see if you can figure out what we're doing wrong?

It's not like I'm holding on to Straw for dear life or anything, it just happens to be the one app that I ***know*** does what I want....  If I can find something else that does the same thing or can easily be made to do the same thing then I can let go of Straw and move on with everyone else, so I'm looking for something active...

Thanks for the replies!

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-04-11
Segmentation faults over and over for no apparent reason.  :/

I really need an upgrade path off of Straw and on to a feed reader that will work offline with full images and text...

Also word to the wise for anyone else possibly having issues with Straw on Karmic--do not install the python adns package, it stop the app dead in the water.  I wonder if this was the cause of the trouble I experienced in Jaunty?  I know the text in the terminal recommends\complains about adns not being found when starting the app, and possibly someone did the common sense thing and added it to the dependencies to be automatically installed...  DO NOT DO THIS.  Just a FYI.

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-03
Monthly /BUMP...you may wish to collect them all...

---

### Post by bornagainpenguin on 2010-05-12
> **carlee said:**
> no lucid without source editing :(

Somehow I managed to get it to work by installing some random older debs from Ubuntu's launchpad and package site, while compiling it from source.  It's messy, but it works.

Also HABITUAL BUMP.  I can quit any time I want to...no really...

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-07-26
A friend on the eeeuser.com forums who knew that I'd been looking for a solution to this for some time now introduced me to [Naufrago!]("http://www.gnomefiles.com/app.php/Naufrago!") on [Gnomefiles.com]("http://www.gnomefiles.com").  This nice little app is pretty much exactly what the doctor ordered.  While it is still only at version .0.1 it is functionally able to step right into the gaping void the loss of Straw made.  I strongly recommend anyone searching for an offline feed reader for Linux give this app a look despite its very alpha status.

--bornagainpenguin

PS: How would I go about recommending an app for inclusion to the repositories?

---

