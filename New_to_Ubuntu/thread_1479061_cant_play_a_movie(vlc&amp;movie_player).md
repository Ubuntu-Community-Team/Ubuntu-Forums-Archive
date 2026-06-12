---
title: "cant play a movie(vlc&amp;movie player)"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-05-10
i installed vlc to play an ".avi" video after installation i drag the movie to vlc after buffering vlc dissappeared same thing happens when i used movie player. Anyone have an idea of whats wrong?

---

### Post by ubunterooster on 2010-05-10
My first guess would be that you don't have the codecs. Assuming you are in Xubuntu currently, go to synaptic and get "xubuntu restricted extras" 

Also search "gstreamer plugin ugly;" not exact name but can't remember what exact name is.

---

### Post by crjackson on 2010-05-10
> **cbbnewbie said:**
> i installed vlc to play an ".avi" video after installation i drag the movie to vlc after buffering vlc dissappeared same thing happens when i used movie player. Anyone have an idea of whats wrong?

Open up your software sources (System>Administration>Software Sources) and make sure you enable all repositories except pre-released updates and let it reload.

Open up a terminal and paste in the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update && sudo apt-get install w32codecs totem-mozilla libdvdcss2 libxine1 libxinerama1 libxine1-all-plugins libxine1 libxine1-ffmpeg libdvdnav4 libdmx1 libdvdread4 gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly && sudo /usr/share/doc/libdvdread4/install-css.sh
```

Once it's done, you should be good to go with pretty much all video.

---

### Post by ubunterooster on 2010-05-10
is medibuntu 64-bit now?

Last I saw it was not; but that has been a while

---

### Post by cbbnewbie on 2010-05-10
you did it again ubunturooster, installed the plugins via synaptic. I thought it was installed the first time i openned video player because it asked me to download the plugins then it installed it but when i looked at synaptic none of the plugins are installed (gstreamer plugin-ugly and bad) thanks, seems you have all the answers for my problem thanks again.

---

### Post by cbbnewbie on 2010-05-10
crjackson thanks too done what you said ty.

---

### Post by cbbnewbie on 2010-05-10
oh LOL just when i thought its now ok the problem again happened. I played the video after installing the plugins it played, i paused it to post the results but when i went to resume playback it dissappeared again.

---

### Post by goldshirt9 on 2010-05-10
does vlc play another avi file or does it "disappear" on all / any files.

possible the avi file is corrupt

---

### Post by cbbnewbie on 2010-05-10
no it happens to every movie a play wether with vlc or with movie player

---

### Post by crjackson on 2010-05-11
> **ubunterooster said:**
> is medibuntu 64-bit now?

Last I saw it was not; but that has been a while
yes, but i didn't notice he was 64bit.  In that case where it says w32codecs it should be changed to w64codecs.

---

### Post by cbbnewbie on 2010-05-23
For now I think vlc and compiz on my machine conflicts with each other, because once i close or replace compiz with the default window manager i can now use vlc to play movies. Is there any other way to fix this so I can watch movies even when compiz is on?

---

### Post by themusicalduck on 2010-05-23
I had this problem when I had my old video card. The problem was that I was trying to play HD videos while Compiz was on and I was running out of video memory.

If you run vlc in a terminal and open a movie, it might tell you what is happening, or if it is running out of video memory too.

Also, you could try using smplayer instead to see if it works any better. I prefer it to vlc for videos anyway.

---

### Post by crjackson on 2010-05-23
> **cbbnewbie said:**
> For now I think vlc and compiz on my machine conflicts with each other, because once i close or replace compiz with the default window manager i can now use vlc to play movies. Is there any other way to fix this so I can watch movies even when compiz is on?

What video card do you have?

Are you using vesa drivers or proprietary drivers?

I used to have similar problems on older systems with ATI onboard video and shared memory (512MB) upgrading the memory or the video card would fix the problem for me.  Tell us more about your system specs.

---

### Post by cbbnewbie on 2010-05-23
its old nvidia geforce2go, so does it mean it cant handle it so it crashes? it has only 16mb

---

### Post by crjackson on 2010-05-23
Wow! Geforce2 I haven't messed with one of those in many years.  I'm really not sure but it is suspect for me.  I've had to replace much more modern video cards than that so I could get compiz working properly.

How much memory does this laptop have and is the 16MB video memory shared ram or actual video ram?

---

### Post by cbbnewbie on 2010-05-23
only 256mb, the 16mb is its actual memory.

---

### Post by themusicalduck on 2010-05-23
I really suspect that this is the problem. You might just have to either have Compiz enabled or be able to watch videos, but not use them together.

If you really want Compiz it might help to set it to use the least effects in Appearance. Or if you have a dock or something that needs compositing, then using Metacity compositing might be ok.

---

### Post by WinterRain on 2010-05-23
> **cbbnewbie said:**
> only 256mb, the 16mb is its actual memory.

That is a *very* underpowered computer to begin with. Modern OS's like ubuntu need at least 512ram and a better video card to play videos correctly. Even a distro like Lubuntu might not be lean enough to work correctly. I would try something else like puppy linux or antix mepis. They are made to run better on older hardware. Even then, video performance may not improve much because of 16mb of video ram.

---

### Post by WinterRain on 2010-05-23
> **themusicalduck said:**
> You might just have to either have Compiz enabled or be able to watch videos, but not use them together.



This computer is way too underpowered to be concerned with compiz in the first place. I would turn off all effects and see what happens. But I stick by what I said about using a lighter distro.

---

### Post by cbbnewbie on 2010-05-23
My main purpose is to see how far this machine can go, and with linux in it I can see its going far more than when it has windows in it. Currently I'm experimenting on different desktop environments. For now I'm using lxde I only used ubuntu to install it. And at the moment I'm trying fvwm-crystal. Thanks for all the replies now I have learned a lot.

---

