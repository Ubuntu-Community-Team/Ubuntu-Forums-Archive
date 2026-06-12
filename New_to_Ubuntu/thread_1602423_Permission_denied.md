---
title: "Permission denied"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Physicsnerdely on 2010-10-21
Dearest Ubuntu forum:
 Cheesy headings aside, story is  I just bought a DVD of a wonderful movie (How to Train Your Dragon) and was overjoyed to bring it home and indulge my inner and partly outer child with wonderful Dreamworks magic. Imigine then, my dismay when it will not read! I dual boot vista and ubuntu, with ubuntu being the primary. Upon trying to play the dvd with Vlc while in Vista, it worked swimmingly. Such little nagging errors and configurations are things I feel should be promptly fixed should the community at large be swayed to shift to the far more sensible OS. But until the day that everything comes in neat little packages and I can forget about the terminal I will continue to manually edit libraries and settings via command line while astonished onlookers assume I am hacking their Iphone.

Anyway, Excerpts of messages box is attached. Pretty sure it's the meat and potatoes of the problem. Problem is Vlc will not play a (legit) retail DVD while in Ubuntu, and Vista plays it fine.

dvdnav warning: cannot get next block (Error reading NAV packet.)
main error: ES_OUT_RESET_PCR called
main error: ES_OUT_RESET_PCR called
dvdnav warning: cannot get next block (Error reading from DVD.)
main warning: no access_demux module matching "file" could be loaded

There was also something in messages before saying something along the lines of "permission denied" once upon a time but it's not there anymore.

Maybe this belongs on Vlc's forum, but it works fine in Vista 32 bit, so I figured i'd bring the issue here.

More information is available should it be requested, but I am not sure what would be helpful yet.

---

### Post by uRock on 2010-10-21
Have you install the medibuntu package (libdvdcss) for reading encrypted DVDs? 

32bit; ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```
64bit;```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

---

### Post by Physicsnerdely on 2010-10-21
> **uRock said:**
> Have you install the medibuntu package (libdvdcss) for reading encrypted DVDs? 

32bit; ```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
```64bit;```
wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
```

I have not done this so far as I remember. I would try it now and post results, but I am in the university library for the foreseeable future. By tonight I should have it tried. From my ability to google words, I am seeing that this has some legal fuzziness surrounding it, and as such isn't included in Ubuntu by default. My questioning is if that is the reason it won't play, why is either that library included in the Windows version, or what does it have the Ubuntu version does not. 

If this turns out to be the problem, I would like to make a recommendation to the vlc devs or the open source community at large. These fixes are pretty simple, but seem to me so unintuitive that some sort of faq or initial statement could be really useful. Something to say "Oh, and by the way, because of legal issues if you want to listen to mp3s, or watch retail dvds, or *insert format here* you will need this thing *here*"

The solutions seem simple, but as of right now the way to go about finding them for newbies like me are to jump on a forum and post cryptic error messages from the innards of the program, then someone who knows the names of things pops up and says "You like the millions before you probably just need *this*". Some kind of legally releasing introduction to media players might help out a good many people, and hopefully turn more people over to the linux side.

---

### Post by trikster_x on 2010-10-21
If it is vlc you are using, you shouldn't need the restricted extras to make it work, since vlc comes with the codecs you need.  Although it wouldn't hurt to have them installed.

[This is always a good read for ubuntu noobs]("https://help.ubuntu.com/community/Medibuntu").  It is a page I have bookmarked for any time I install from scratch.  Basically you will want to run these commands:
```
sudo apt-get remove vlc
```
This is because there may be a problem with one of the files for vlc.  We'll reinstall in another step.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Adds Medibuntu to your sources list.
```
sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu
```
Ensures packages get added to synaptic and I believe software center, though I could be wrong on the last part.
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 vlc
```
Installs the restricted extras package and libdvdcss2, which is necessary for correct playback of newer DVDs.  Also reinstalls vlc.

---

### Post by QIII on 2010-10-21
> **Physicsnerdely said:**
> My questioning is if that is the reason it won't play, why is either that library included in the Windows version, or what does it have the Ubuntu version does not. 

Microsoft, a big proponent of DRM, pays licensing fees to include the libraries in its products.  Thus, it has a legal right to include the libraries required.

---

### Post by trikster_x on 2010-10-21
> **QIII said:**
> Microsoft, a big proponent of DRM, pays licensing fees to include the libraries in its products.  Thus, it has a legal right to include the libraries required.

This.

Unfortunately, copyright law basically says that although you legally bought and payed for the movie, you do not necessarily have the right to playback any of the information contained on the disc.  Only a ***machine*** or ***software*** that has been created using a legally licensed decryption code is allowed to access and display the information.  When you buy a DVD the only portion of the DVD you have a right to use is the raw materials used to make the physical disc.  And I'm sure there is a company somewhere trying to change that.  

Yes, folks, machines and software have more rights than people when it comes to playback of media.

---

### Post by zkriesse on 2010-10-21
Take a look at this thread, [Playing DVD's On Ubuntu 9.10]("http://ubuntuforums.org/showthread.php?t=1323790") while I wrote it based in the 9.10 version it should be the same packages thereby it should work for you. If this isn't what you need or it doesn't work lemme know and we'll go from there.

---

### Post by Physicsnerdely on 2010-10-21
My leige trikster_x, I grovel at your feet. It worked perfectly. Maybe vlc was broken, maybe it was restricted soemthings not being somewhere. Also the explination of libraries makes good deal of sense. 
As to placing packages in Software center, i do not see them if they're there.
Thanks much. I do wish that the solution wasn't quite so intimidating and honestly a bit difficult to find. Not in that it was really difficult, but in the "user friendly" point and click problem solving sense this was a fair bit of complicated.

---

### Post by trikster_x on 2010-10-21
No worries.  When I first installed Ubuntu, I had a hard time figuring out what questions to even ask.  Fortunately the forums here are extremely helpful, provided your problem is fixable (I've had one or two that weren't, stupid pulseaudio...).  I came from windows where a google search would come up with either the microsoft knowledge base/troubleshooter or one of those pay per answer sites.  But in Ubuntu you can usually throw some search terms out there and get a decent how to guide, many times from this very forum, or an explanation of why you can't do what you want to.

So have fun and keep asking questions.  It's the only way to learn to use Ubuntu to it's fullest.

---

### Post by AbdRahim on 2010-11-09
Did not work for me. will try another DVD

---

