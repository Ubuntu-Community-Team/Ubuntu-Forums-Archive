---
title: "Error Using Totem Movie Player"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by MoonWolf85 on 2009-05-18
I tried playing a DVD using Totem Movie Player and got this error message. 

An Error Occured 
Could not read from resource. 

Does anyone have any ideas on how to fix this? 

Thanks for the help.

---

### Post by emeraldgirl08 on 2009-05-18
Moonwolf TY for posting this! 

I was just about to ask the same question.

---

### Post by anewguy on 2009-05-18
Have you installed all of the extras needed for playing DVD's?  Start by adding (via the package manager) ubuntu-restricted-extras, and the gstreamer good/bad/ugly sets.  If those don't help please post back.

Dave :)

---

### Post by MoonWolf85 on 2009-05-18
Well I installed ubuntu-restricted-extras. I didn't see/couldn't find anything about gstreamer good/bad/ugly sets to install. I found gstreamer stuff. Almost all of which I already have. And there was some gstreamer good/bad/ugly stuff in the unbuntu-restricted-extras install stuff. 

But I still get the same error when I try to play a dvd.

---

### Post by NightwishFan on 2009-05-18
You may need libdvdcss2, which decrypts commercial DVDs. Also note it may be illegal in your country. Please enable the medibuntu repos to do so, help is here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you have libdvdcss2, then the problem is likely gstreamer/xine. VLC player is excellent for DVD playback.

```
sudo apt-get install vlc vlc-plugin-pulse
```

I like setting up VLC to use Pulseaudio, though some might not. VLC is a Qt4 program, though it looks native when used in GNOME.

---

### Post by MoonWolf85 on 2009-05-18
So I couldn't find libdvdcss2, but I found libdvdcss and installed that. The dvd won't play in VLC either. I have I believe every gstreamer/xine thing that could be found. I plugged that code in. I already have it, nothing new was done. So far nothing. 

When I try to play a dvd in VLC, it just doesn't play. No error code, nothing. In Totem, that one error code, nothing new.

---

### Post by GregA on 2009-05-18
If you couldn't find libdvdcss2, then it's likely that you don't have the extra repository set-up properly (per Nightwishe's note).  Kindly read that link again, about how to add 3rd party repositories like Medibuntu, and after adding that, you have to refresh the synaptic db.  If I recall right, the 3 basic packages I've always installed to get full DVD playability are:
- w32codecs (or sometimes called win32codecs or win32all),
- libdvdread3
- libdvdcss2
Do the above in that order (codecs are installed first).  You might need to do the above, then uninstall VLC, and then reinstall VLC in the new environment.   Check back with us if you don't understand the concepts of repositories in linux, how to install them (they can be installed via the synaptic gui, as well as directly by modifiying and saving your "sources" text file (which is just a master listing of all your repositories).

---

### Post by mkvnmtr on 2009-05-18
I don't think I can help you but I believe I can confirm there is a problem. On my powerpc machine I am having trouble playing videos that always before I could play. I use Mplayer from the medibuntu repository. Have used it for four upgrades. Up to 8.10 it played everything. I install all gstreamer that will install and every thing that medibuntu has. Never been a problem and on my !386 9.04 I have encountered no problem yet. Some videos just close after I try to play them but many still play. Of those that don't play en mplayer some will play in vlc but some will not. I have combed the repositories for programs and lib files that might help but so far no luck. I haven't yet tried plain totem or any other player. I have always liked mplayer from medibuntu but it looks like ppc is  supported by that repository less and less os time goes by.

---

### Post by repettus on 2010-01-18
So, anyone else able to fix this problem yet? I am still getting the same problem.  I was getting the message "could not read from resource," in Ubuntu 9.10, and now movie player is just crashing when I try to play a known good dvd from Blockbuster. I have installed restricted extras, and gstreamer "good, bad, ugly" packages. Still Can't play DVDs in 9.10. I am about to just go back to 8.10.

---

### Post by PenguinInside on 2010-01-19
> **repettus said:**
> So, anyone else able to fix this problem yet? I am still getting the same problem.  I was getting the message "could not read from resource," in Ubuntu 9.10, and now movie player is just crashing when I try to play a known good dvd from Blockbuster. I have installed restricted extras, and gstreamer "good, bad, ugly" packages. Still Can't play DVDs in 9.10. I am about to just go back to 8.10.

I can't say for sure, but is it possible it's not a codec problem, but rather a problem of finding the physical media?

Does Totem work for you to play other kinds of CDs? MP3, VCD, AVI, etc?

I've found that the default "What would you like to do with this CD" message that comes up when you insert a CD doesn't really play the disk. Rather, I have to manually specify the disk location in VLC.

---

### Post by repettus on 2010-03-13
Yeah, Totem does work to play anything else except that particular DVD. Seems like the Blockbuster DVD was encoded in such a way that Totem could not play it.

---

### Post by NightwishFan on 2010-03-13
I doubt that is the case. DVDs simply require libdvdcss, and then they should work. Once that is installed VLC will definitely play them if not Totem. Totem used to have problems with the DVD menus, but lately it works fine.

---

