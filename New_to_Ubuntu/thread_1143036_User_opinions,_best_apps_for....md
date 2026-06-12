---
title: "User opinions, best apps for...?"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-04-29
After reading many of the threads that have been asked in a very generic way and checking out some of the suggestions made in those threads and some in the Add/Remove as well, I would like users oppinions on the best replacements for some of the applications I used in Windows.

Okay some ground rules. Please refraim from using links as your reply, I am looking for opinions that are current. Please give your opinion why you liked an app over others. If you can please link to a trusted source if its not in any of the defualt repositories or medibuntu, preferably a site related to that app for further reading.

Alright starting off:

Winamp for playing multi-media audio files as well as easily searching shoutcast streams. So far I have found Xaile and seems to work a charm for finding Shoutcast streams and the only one I tried that does this, which is surprising.

Windows Media Player for playing multi-media video files.

Power DVD for watching DVDs.

Extentions for Firefox as I would prefer to stick with Firfox you may have found useful, particularly looking for a replacement for FireShots that is not supported under Linux and I have found fairly useful.

ActiveSync for my HP iPAQ hx2490b (Boy is it getting on in age.), none the less would be interesting if it eventually got a Ubuntu transfusion as well, don't think that will work yet. Likely would be my graduating projet Linux geekdon.

Microsoft Outlook, as its the only e-mail calander, contacts etc I have found that will sync with my ActiveSync and will need this till my main tower goes Linux. And so will need to work the whatever I use to sync my iPAQ.

Microsoft Office as well. Open Office seems to have everything I will need though.

Finally any other addons for Ubuntu you may have found invaluable when you were new and getting settled in not related to the above. Again not generic list as those are just hard to determine if its really something I would be interested in adding, please give a reason why if you can.

Thanks all in advance.

I may add more when I get around to dualbooting my main tower.

---

### Post by didiercool on 2009-04-29
As far as multi-media and DVD playing is concerned, I always just go straight for Xine.  It's sleek and works like a charm.

Also, if you're a note taker in any degree, Tomboy is a fabulous little app which I've been enjoying; there is no XP equivelent.

---

### Post by Mortus Pryde on 2009-04-29
Thanks will check the Repos for that.

Also forgot to ask about what the best GUI Network/Wireless manager may be for a laptop to that may use either the onboard (Intel 2100 Wireless B) or D-Link Wireless N PCMCIA card, as I find in situations where speed is not an issue I can get better signal strength to the Wireless B at time, but also may want to use my wireless N card when speed is an issue. I noticed that with the native manager it attempts to run both at the same time and the Hot Key on my ThinkPad disables ALL wireless not just the onboard. The PCMCIA is easy to disable. ;)

---

### Post by vexorian on 2009-04-29
For mp3, ogg, and videos, I like totem, just install the restricted codecs.

DVD playback : VLC media player, I even use it on dows (Used to use...)

Too bad there are windows-only firefox addons, that's retarded, I guess it is because of the authors doing pretty unsafe things like running their executables instead of using the addon api. I am fond of "NoScript" and "Download helper" note that in Linux it is harder to make  download helper auto convert video files, but it is also not necessary, get codecs and bot tote, VLC and Xine will play the flv files from youtube just well.

Cool apps? Well, as a developer my favorite IDE is "geany", I  like gnote  for desktop notes. And hmnn, well try themes at : gnome-look.org . What else? If you miss some windows XP stuff, you should try virtualbox a very good virtual machine (free as well) . Something that imho should come by default is inkskape, much better than openoffice-draw and it is easier to do simple graphics in it than in Gimp.

Regarding zincing to esoteric devices, I used virtual box and windows XP to be able to zync to my palm zire 22, it was really the only way.

---

### Post by billgoldberg on 2009-04-29
**Winamp for playing multi-media audio files as well as easily searching shoutcast streams. So far I have found Xaile and seems to work a charm for finding Shoutcast streams and the only one I tried that does this, which is surprising.**

A great media player if you are into shoutcast streams is BMPx.

I don't know if it is in the repositories, but you can get it here:
[http://www.getdeb.net/app/Beep+Media+Player](http://www.getdeb.net/app/Beep+Media+Player)

**Windows Media Player for playing multi-media video files.**

Totem plays everything.

**Power DVD for watching DVDs.**

Totem or VLC.
[B]
ActiveSync for my HP iPAQ hx2490b (Boy is it getting on in age.), none the less would be interesting if it eventually got a Ubuntu transfusion as well, don't think that will work yet. Likely would be my graduating projet Linux geekdon.[/B]


Try running it in Wine.

Finally any other addons for Ubuntu you may have found invaluable when you were new and getting settled in not related to the above. Again not generic list as those are just hard to determine if its really something I would be interested in adding, please give a reason why if you can.

See my codecs link in my signature for getting all your codecs.

p7zip-full

---

### Post by NightwishFan on 2009-04-29
Winamp, not sure but you can try Banshee/Rhythmbox on GNOME, and perhaps Amarok on KDE. I only use jamendo, so I do not know about Shoutcast. Search for shoutcast in synaptic perhaps.

Windows Media Player: Totem-Xine, Mplayer, VLC

Power DVD: Install libdvdcss2 from medibuntu, and use any of the above, I recommend Totem-Xine or VLC if you do not mind Qt4 (KDE) apps, there should be no problem.

Firefox addons work in Linux too.

Outlook: Evolution mail or Thunderbird?

Microsoft Office: Gedit compares to MSOffice as far as I am concerned. Try Koffice, Goffice, and of course, OpenOffice.org.

Games: Frozen-Bubble, Battle For Wesnoth

---

### Post by Mortus Pryde on 2009-04-29
Tried Banshee and Rhythembox (Which is the default in Ubuntu BTW.), niether supporting Shoutcast searching. On that note I wonder why more audio media players don't. I mean scripted "Radio" objects have existed in the virtual world of SecondLife for over a year now that do this. And meanwhile they all support Podcasts?

Will be checking out video suggestions when I get home.

Did some installing of themes, have one that can't seem to find its engine but seems to work alright so not so worried about that. Still have not found a background I like though. Can I used any fonts I like to customize my themes even if they are for Windows?

While I am on fonts is there an easier way to manage and install new fonts in Ubuntu?

---

### Post by NightwishFan on 2009-04-29
> **Mortus Pryde said:**
> While I am on fonts is there an easier way to manage and install new fonts in Ubuntu?

In your home directory, create a folder named

.fonts

Copy any .ttf files into there, they should appear in your fonts list.

---

### Post by cariboo on 2009-04-29
Before you try any of the media players, make sure you install the ubuntu-restricted-extras meta package. It will install flash, java and most of the codecs needed to play most types of audio/video media.

To play DVD's you will need libdvdcss2, make sure it is legal in your jurisdiction. To install libdvdcss2 you will need to enable the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu") repositories. Once the repositories have updated, you can do the install.

---

### Post by Sir Jasper on 2009-04-29
Hi,

I especially like "Clipboard Manager".

My regards

---

### Post by NightwishFan on 2009-04-30
Try stellarium. That program is just plain awesome. It is a virtual planetarium, of excellent quality.

---

### Post by Mortus Pryde on 2009-04-30
Thanks for all the great suggestions.

I did look at and try BMPx, have to say it looked a little more finnished than Exaile but was very put off when it would not retain my bookmarks, and Shoutcast Search seemed dodgy and did not always work. Exaile on the other hand once I figured out I had to rightclick Shoutcast and search worked like a charm, found what I wanted and bookmarked it easy enough, not to mention displaying my bookmarks right on the interface and not in a menu hidden from plain sight.

---

