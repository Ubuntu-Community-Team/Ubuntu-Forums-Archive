---
title: "Songbird and iTunes"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by OllieGab on 2008-12-31
For a while now I've tried several ways of getting my ipod to work with an application that runs on Linux (Ubuntu). I tried Banshee and Rythmbox, and though they both recognised my ipod device, after synching my ipod would still claim there was nothing on it.
So I tried Songbird, which seemed to work. My ipod received all my music and that side works (fine?).
I downloaded a few podcasts and though they downloaded the contents they all said 'Fail' and 'Try again'. Don't know the reason for that!?

I think the installation of Songbird worked as it should but it never gave me an icon to click on (to open it) but I have to go into the file generated after extracting it and click on one of the icons there and select 'Run'. Seems a bit of a long-winded way of doing it!?

Any comments of what may have gone wrong?

Cheers Ollie!

---

### Post by jimmy the saint on 2008-12-31
Is it  a brand new ipod?  If so, the itunesdb has been encrypted by apple.  There is a project to get them working again though, so just be patient.  

JTS

---

### Post by OllieGab on 2008-12-31
It's iPod Classic, 160G, probably about  a year ago I bought it!

---

### Post by wmoore on 2008-12-31
> **jimmy the saint said:**
> Is it  a brand new ipod?  If so, the itunesdb has been encrypted by apple.  There is a project to get them working again though, so just be patient.  

JTSDo you mean this one? [http://sourceforge.net/project/showfiles.php?group_id=67873](http://sourceforge.net/project/showfiles.php?group_id=67873)

Nothing has happened with it for ages and I think it is dead, sadly. I watched this for a while after upgrading my iPhone to 2.0 but gave up when there was no movement. I now have pwnplayer installed on the iPhone and manually throw music on using scp :)

---

### Post by waspbr on 2008-12-31
it seems to me that you are just using the binary of songbird, extracted from a tar ball right? 

What I normally do with songbird, is to install a .deb packaged from getdeb ([http://www.getdeb.net/]("http://www.getdeb.net/")), download the appropriate deb package for your system (either 64 or 32 bit).

Deb packages work much like windows .exe installer files, it should generate an icon for you.

gl

---

### Post by jimmy the saint on 2008-12-31
no, gtkpod and libgpod are applications for interfacing with your ipod.  libgpod is what most of the music applications you mentioned use to accomplish the task.  The problem is that apple has implemented a procedure in which modifications of the itunesdb file have to be hashed in the latest generation of ipods.  There is a project underway to figure out the hashing mechanism.  Once they figure it out, it will likely be incorporated into libgpod, gtkpod and other appliations.  I hope that clarifies things a bit!

---

### Post by clive littlewood on 2008-12-31
Hi

As suggested download the .deb file to install songbird.

It has an addon for ipod sync as standard which when installed will detect your classic.

I have a Nano connected and can use this to transfer stuff with no prob.   :D

No Linux player will work with current Gen. ipods.   :(

Hope this helps

Clive

---

### Post by OllieGab on 2008-12-31
Yes, you're right. I did download a .tar.gz file. I did also download a .deb file of Songbird from the site you recommended but I still get a 'failure' notice after downloading a podcast! It doesn't actually tell me WHAT failed!

Ollie

---

### Post by sadaruwan12 on 2008-12-31
> I still get a 'failure' notice after downloading a podcast! It doesn't actually tell me WHAT failed!


Well did you tried these softwares

Listen
~~~~~~
**Description** :
Listen is an audio player which helps you to organize your music collections.

It supports many features such as Podcasts management, browse Shoutcast directory, and provides direct access to lyrics, lastfm and wikipedia information.

It intuitively creates playlists for you by retrieving information from lastfm and what you most frequently listen to.

go to : [http://linuxappfinder.com/package/listen]("http://linuxappfinder.com/package/listen")

gPodder
~~~~~~~
**Description** :
gPodder is a podcast receiver/catcher. You can subscribe to RSS feeds (Podcasts) and download audio/video content from different channels. You can then playback content on your desktop or synchronize to your iPod or portable MP3 player. Simultaneous downloads and automatic downloads of new episodes are also supported.

Go to : [http://linuxappfinder.com/package/gpodder]("http://linuxappfinder.com/package/gpodder")

gtkpod
~~~~~~
**Description** :
gtkpod is a platform independent GUI for Apple's iPod using GTK2. It allows you to upload songs and playlists to your iPod. It supports ID3 tag editing, multiple charsets for ID3 tags, detects duplicate songs, allows offline modification of the database with later synchronisation, and more.

Go to : [http://linuxappfinder.com/package/gtkpod]("http://linuxappfinder.com/package/gtkpod")

if you were unable to find the correct one this site might be able to help you [http://linuxappfinder.com]("http://linuxappfinder.com")

---

### Post by Maupertus on 2008-12-31
Isn't gPodder developement as dead as the musical stylings of Cliff Richards?

It still works, but far from making me a happy camper. I've actualy found the Amarok podcast handling the best, syncing to iPod and all.

---

### Post by sadaruwan12 on 2008-12-31
Yes I do agree with Maupertus try amarok also.

---

### Post by wmoore on 2008-12-31
> **sadaruwan12 said:**
> Yes I do agree with Maupertus try amarok also.Thirded. Amarok rocks \\:D/

---

### Post by cozmicharlie on 2008-12-31
I doubt simply trying different players is going to work for you.  As others have noted, the file system in the newer Apples has changed.  You may have an older ipod but with the newer firmware.  However, you should still be able to get it to work.  I just bought a new nano for my wife and it worked fine.  Please answer the questions below:

[LIST=1]
[*]Did you initialize the ipod on a pc or mac?
[*]When you plug it in under ubuntu it must be mounting.  When it mounts, right click on the ipod icon and go to properties and tell me if it is mounted "read only".  Also, check the volume tab and post output from "file system" (under label) and "mount options".
[/LIST]

---

### Post by LowSky on 2008-12-31
> **OllieGab said:**
> It's iPod Classic, 160G, probably about  a year ago I bought it!

This is considard one of the newer iPod's

iPod Classic, Touch, Nano, and iPhoney. All have issues with linux. Blame Apple in their inablity to share technology and let the user decide.

---

### Post by OllieGab on 2009-01-01
I have "gone round" the problem by installing Amorak - which seems to work fine.
I had to install KDE though to get Amorak...is this a must? I do prefer Gnome and would like to use Amorak with that.It seems I can use Amorak with Gnome if choosing Gnome at start up but I would like to remove KDE all together...I think!

Regards Ollie

---

### Post by wmoore on 2009-01-01
> **OllieGab said:**
> I have "gone round" the problem by installing Amorak - which seems to work fine.
I had to install KDE though to get Amorak...is this a must? I do prefer Gnome and would like to use Amorak with that.It seems I can use Amorak with Gnome if choosing Gnome at start up but I would like to remove KDE all together...I think!

Regards OllieYou can use Amarok with Gnome.

---

