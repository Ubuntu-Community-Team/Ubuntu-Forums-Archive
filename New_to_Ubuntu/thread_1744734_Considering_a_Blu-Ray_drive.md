---
title: "Considering a Blu-Ray drive"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-04-30
Okay so Blu-Rays are becoming cheaper (slowly) and a lot more popular so all the new films I buy are on Blu-Ray rather than DVD, so I'm considering upgrading to one, does anyone have much experince with Blu-Ray drives on ubuntu, 

Are they good?
Pros/Cons?
Are they easily detected and usable with ubuntu?


Thanks 
Mark

---

### Post by Fat-n00b on 2011-06-10
Bump this thread because I am also interrested!

---

### Post by Jerry N on 2011-06-10
> **CaptainMark said:**
> Okay so Blu-Rays are becoming cheaper (slowly) and a lot more popular so all the new films I buy are on Blu-Ray rather than DVD, so I'm considering upgrading to one, does anyone have much experince with Blu-Ray drives on ubuntu, 

Are they good?
Pros/Cons?
Are they easily detected and usable with ubuntu?


Thanks 
Mark

You might look at the user reviews/comments for Blue Ray drives at Newegg.com.  Most of the reviews I've seen aren't very complimentary.

Jerry

---

### Post by Fat-n00b on 2011-06-13
It is just crazy to think that Blu-Ray has been out for years now and yet to this date as far as I know you can not play Blu-Ray's (at full potiential) without paying for additional software at least on a PC.
 
It seems if I had the hardware I can create/author Blu-Rays without Purchased Software, but have no way to play them back (natively) on a PC without paying someone for that privilage? What? and If I rent/buy a Blu-ray disc am I not allowed to watch it on whatever Blu-ray deviece I have... Back a few years ago DVDs came (or still to come) with a DVD (Software) player on the disc, just incase you did not have the software installed to watch them on your PC.
 
Sony and Blu-Ray may have won the format war against Microsoft and the HD-DVD backers but we the consumer are the ones still fighting the war!

---

### Post by LowSky on 2011-06-13
I own a Blu-Ray drive, and its not so useful in Ubuntu. I only purchased it because the price was pretty low looks amazing in my silver case.

Anyway Blu-Ray playback stinks because of the DRM. Linux has no official support much like DVD's. Its funny that people are slowly forgetting tht DVD playback in Linux is still not perfect or legal.

---

### Post by Lateralis on 2011-06-13
> **LowSky said:**
> I own a Blu-Ray drive, and its not so useful in Ubuntu. I only purchased it because the price was pretty low looks amazing in my silver case.

Anyway Blu-Ray playback stinks because of the DRM. Linux has no official support much like DVD's. Its funny that people are slowly forgetting tht DVD playback in Linux is still not perfect or legal.

Yes.  There is a community help page on this very problem: [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

I haven't tried anything on this page to get Blu Rays to work in Ubuntu, as I keep a working copy of Windows 7 for playing games.  Also, my drive was a retail box not an OEM, so actually came with a version of, I think PowerDVD, which plays Blu Ray.  

I suspect that some of the information in that link is a little out of date and may not work.  However, as I said, I've not tried to play Blu Rays on my computer (I may try that now) and I've not seen anything approaching an alternative method just yet; does some one else have any ideas, tips, tricks or links they can share?

---

### Post by Lateralis on 2011-06-13
As a follow up, I decided that I would have a crack at this myself!  And I have got it to work.  The credit for what follows should be directed towards [this]("http://themediaviking.com/2010/bluray-linux/") page.



To get Blu-Rays to work, you will need [MakeMKV]("http://www.makemkv.com/").  There are Windows and Mac binaries available on their download page: Linux source can be downloaded from [this MakeMKV forum post]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224").  Instructions on how to install makeMKV are contained in the post but summaraised as follows:


1) Firstly you will need to ensure you have a few things installed:

```

sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev

```

2) Once those are installed, download the MakeMKV binary and source tarballs from [this MakeMKV forum post]("http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224").  Once both are uncompressed, navigate through the commandline first to the source ("oss") directory and type

```

$ make -f make.linux
$ sudo make -f make.linux install

```

3) Do the same for the binary directory

4) Once that is done, start makeMKV from the commandline

```

$ makemkv

```

5) In the MKV box, go to File -> Open Disc -> [Select your Blu-Ray drive].  Once it has finished reading the disc, go to File -> "Stream".  Once it has completed setting up the streaming daemon, you will get a message something like "Operation sucessfully completed. Streaming server started, web server address is..."

6) You can now stream this Blu-Ray disc over your local network and play it on the local machine.  For example, in the VLC media player, go File -> Open Network Stream and type something like [http://localhost:51000/stream/title1.ts](http://localhost:51000/stream/title1.ts) - the number after *title* depends somewhat on the disc.  I tried *title0.ts* on one BD and that took me to the copyright notices displayed once the film has ended.  *title1.ts* instead took me straight into the movie.  You can probably gain some idea as to which one is the main titles by reading the MakeMKV log window.  

7) You're done!  I'm currently watching a Blu-Ray film in glorious HD!  


A note: This makeMKV apparently only has a 30 day trial before you "need" to by a license.  I'm not sure that you will ever need to do that though.  On the MakeMKV website it does say that updating to the latest beta "resets the clock".  Alternatively, you could try removing the installed files from /usr/bin and /usr/share, *make clean* the tarball directories and just reinstall.


Edit: I've just noticed a link to themediaviking's post linked above on the Community help page.  I didn't notice that - I found themediaviking's post entirely separately through Google.

---

### Post by Fat-n00b on 2011-06-13
> **Lateralis said:**
> 
I haven't tried anything on this page to get Blu Rays to work in Ubuntu, as I keep a working copy of Windows 7 for playing games.  Also, my drive was a retail box not an OEM, so actually came with a version of, I think PowerDVD, which plays Blu Ray.  

But you have to open use PowerDVD as the player (or atleast the "unlocker") and you dont have surround sound (as far as I remember you need PowerDVD pro for that).

---

### Post by Lateralis on 2011-06-14
I couldn't agree more with your sentiments.  Fortunately for me, I don't have surround sound on my PC, so that doesn't concern me.  :P

---

### Post by Fat-n00b on 2011-06-14
I dont guess we will ever get to a true (all) Media PC... Instead it will have to be an (all) Media PS3 with a DVR box I guess?  
 
I want to reduce the number of "appliances" in my house that not add them?

---

### Post by Fat-n00b on 2012-02-03
It maybe time to upgrade the PC and add a Blu-Ray to it.

Has anyone tried this yet:
[http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/](http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/)

It looks very promising!

Anyone with Ubuntu (or Xubuntu) and Blu-ray willing to test and report back before I spend the dough on a drive???

---

### Post by 3rdalbum on 2012-02-03
> **Fat-n00b said:**
> It maybe time to upgrade the PC and add a Blu-Ray to it.

Has anyone tried this yet:
[http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/](http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/)

It looks very promising!

Anyone with Ubuntu (or Xubuntu) and Blu-ray willing to test and report back before I spend the dough on a drive???

It's just MakeMKV glued to VLC. It does nothing that I haven't been doing for years with my Bluray drive.

It just tells MakeMKV to start decrypting, and then tells VLC to play the file even as it's decrypting.

MakeMKV works. Even its free cousin DumpHD works; I think you can use MakeMKV's AACS key in DumpHD because it wasn't protected too well :-)

---

### Post by andrew.46 on 2012-04-25
> **Fat-n00b said:**
> It maybe time to upgrade the PC and add a Blu-Ray to it.

Has anyone tried this yet:
[http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/](http://www.omgubuntu.co.uk/2010/10/easy-blu-ray-movie-playback-in-linux/)

It looks very promising!

Anyone with Ubuntu (or Xubuntu) and Blu-ray willing to test and report back before I spend the dough on a drive???

Script works nicely. I personally have substituted MPlayer for vlc in this script as MPlayer + vdpau seems to do a better job with the playback than hardware-accelerated vlc.

---

