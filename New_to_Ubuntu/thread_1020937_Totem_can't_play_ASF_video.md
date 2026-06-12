---
title: "Totem can't play ASF video"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by Chris Hansen on 2008-12-24
Hello,

I reinstalled Ubuntu and now I can't use Totem to play ASF videos. It seems to play in VLC but, before the reinstall, it worked fine in Totem too. I'm trying to play a video with a title that ends in .dvr-ms and I get the message:

The playback of this movie requires a video/x-asf-unknown decoder plugin which is not installed.

I just went through the multi-media how-to and everything except this type of video seems to work. Is there something I missed?

Thanks.

---

### Post by mc4man on 2008-12-24
I don't use totem but ck. and see if you have w32codecs installed and possibly gstreamer0.10-ffmpeg

If you don't have medibuntu as a repo source just go here, pick what release your using and do a download and install of w32codecs from list.

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by nynoah on 2008-12-24
Totem is garbage in my opinion.  VLC and Kaffiene work far better.  Just run all those files in VLC.  If you want to make VLC the default player, just right click on the file you want to play.  Go to properties and set the default player to VLC.  Then you won't have to chose the player all the time.

---

### Post by Chris Hansen on 2008-12-26
I thought about just using VLC but Totem used to play everything just fine so I know it's just not set up right and it bothers me that it doesn't work.

---

### Post by Chris Hansen on 2008-12-26
> **mc4man said:**
> I don't use totem but ck. and see if you have w32codecs installed and possibly gstreamer0.10-ffmpeg

If you don't have medibuntu as a repo source just go here, pick what release your using and do a download and install of w32codecs from list.

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

I looked at the link and saw where the w32 codecs are but I'm kind of a newbie so I'm not sure how to install them from there.

I apologize but I might need a little hand holding until I become more familiar with the Ubuntu way.

---

### Post by Dedoimedo on 2008-12-26
Did you install restricted media codecs? gstreamer ...

See this:
[http://www.dedoimedo.com/computers/mp3_linux.html](http://www.dedoimedo.com/computers/mp3_linux.html)

Wait! It shows mp3 thingie, but the codecs are for all sorts of restricted media formats! Check out image 3 in above article ... under install multimedia codecs.

Dedoimedo

---

### Post by Chris Hansen on 2008-12-26
> **mc4man said:**
> I don't use totem but ck. and see if you have w32codecs installed and possibly gstreamer0.10-ffmpeg

If you don't have medibuntu as a repo source just go here, pick what release your using and do a download and install of w32codecs from list.

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

I did go to the link and install the w32 codecs and it didn't help. I just got a message that they were already installed.

---

### Post by Chris Hansen on 2008-12-26
> **Dedoimedo said:**
> Did you install restricted media codecs? gstreamer ...

See this:
[http://www.dedoimedo.com/computers/mp3_linux.html](http://www.dedoimedo.com/computers/mp3_linux.html)

Wait! It shows mp3 thingie, but the codecs are for all sorts of restricted media formats! Check out image 3 in above article ... under install multimedia codecs.

Dedoimedo

I looked at the link and I think that's how it got set up last time. It didn't work this time of course because I already have mp3 support installed and the other stuff is already installed too.

Would it make a difference to un-install all that stuff and re-do it?

---

### Post by Dedoimedo on 2008-12-27
If you have the codecs, no need.
BTW, is this a specific .asf file or any .asf file that give you the gip?
Dedoimedo

---

### Post by Chris Hansen on 2008-12-27
> **Dedoimedo said:**
> If you have the codecs, no need.
BTW, is this a specific .asf file or any .asf file that give you the gip?
Dedoimedo

They're videos that my friend recorded off television and put on the pc with dvd decryptor. They have a .dvr-ms extension. Everything else seems to work.

What puzzles me is that they used to work in Totem before I reinstalled so I know that it's capable of working. They also work fine in VLC so I might just use that. It just bothers me that I can't get them to work now.

I did alt-f2 and typed in "gstreamer-codec-install" and got a window to "Search for suitable codec". When I clicked search it told me "There is no matching application available". 

Is it possible that some codec used to be available but was recently removed, perhaps for legal reasons?

---

### Post by Dedoimedo on 2008-12-27
Might be ... Did you open Synaptic and check through there?
You should look for restricted, ugly codecs, those are usually the names for 3rd-party properietary ones.

BTW, not everything must work. Sometimes, you'll get tiny things that will drive you mad ... but that's life :) We'd like to have everything purring like Swiss clockwork, but sometimes, being knowledgeable is knowing when to divert your efforts to something else. After all, it works for you in 99.95% of cases, which means there's probably something (wrong) with those specific files.

Dedoimedo

---

### Post by Chris Hansen on 2008-12-27
> **Dedoimedo said:**
> Might be ... Did you open Synaptic and check through there?
You should look for restricted, ugly codecs, those are usually the names for 3rd-party properietary ones.

BTW, not everything must work. Sometimes, you'll get tiny things that will drive you mad ... but that's life :) We'd like to have everything purring like Swiss clockwork, but sometimes, being knowledgeable is knowing when to divert your efforts to something else. After all, it works for you in 99.95% of cases, which means there's probably something (wrong) with those specific files.

Dedoimedo

I did see ugly codecs but wasn't sure what to think. Should I just install everything that say ugly?

---

