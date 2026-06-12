---
title: "movie player problems"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by sinhanikhil.5 on 2010-04-04
my movie player only gives audio output, if for eg i play a movie file, i can only hear  the sound but can see only black screen, no pictures.
Can any1 plz throw light on it, thanks.

---

### Post by itisbasi on 2010-04-04
have you installed all the restricted extras?

---

### Post by sinhanikhil.5 on 2010-04-04
> **itisbasi said:**
> have you installed all the restricted extras?
well honestly dont know, but it was working fine till my last shut down.

---

### Post by itisbasi on 2010-04-04
search for the ubuntu-restricted-extras package in synaptic, install them, restart your computer and try playing it or wait for someone else to help you out!

---

### Post by arnab_das on 2010-04-04
> **sinhanikhil.5 said:**
> my movie player only gives audio output, if for eg i play a movie file, i can only hear  the sound but can see only black screen, no pictures.
Can any1 plz throw light on it, thanks.

definitely install ubuntu-restricted extras. how to do that? Go to Application > Terminal and then type the following:

> sudo apt-get install ubuntu-restricted-extras

if that doesnt solve the problem, try VLC media player which is pretty much capable of handling anything under the sun.

how to install vlc?

go to ubuntu software center and then search for VLC. install it.

---

### Post by sinhanikhil.5 on 2010-04-04
WOW i did both, neither of it worked.
Now.
It seems like my files are effected.

---

### Post by 2hot6ft2 on 2010-04-04
Let's just cut to the end and install it all at once so you can play pretty much everything.

I could spend a half hour saying go here click this open that  yada yada yada instead do this.

Open a terminal
Applications > Accessories > Terminal
and run these commands one at a time and your password wont be shown when you type it in just type it in and hit enter.
This first one enables the medibuntu repository for restricted codecs and such
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
Remove any browser media player plugin you currently have installed (totem-mozilla is installed by default, but you may have installed mozilla-mplayer or mozilla-plugin-vlc) like this:
```
sudo apt-get remove totem-mozilla mozilla-mplayer mozilla-plugin-vlc
```
then for all the multimedia, mp3's java, divx web player, flash and dvd playback
```
sudo apt-get install ubuntu-restricted-extras libdvdcss2 gecko-mediaplayer vlc
```
Use your arrow keys and Tab key to select and Enter to accept the Java terms of use.
And to get rid of one package in the restricted extras that causes problems:
```
sudo apt-get purge ttf-mscorefonts-installer
```
ttf-mscorefonts-installer bug report
[https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/debian/+source/msttcorefonts/+bug/431217)

And you're done.
VLC Player will be in Applications > Sound and Video > VLC

---

### Post by sinhanikhil.5 on 2010-04-04
Sorry to be such a pain, but i tried to install all application whatever thats advised above and my computer did it successfully.
But still I am not able to see videos there is only audio output.
The only change in command i made is from the command:- 
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 

I removed all the --quite as my comp did not allow with it.

Now I am seriously thinking that my files are corrupted.

---

### Post by 2hot6ft2 on 2010-04-04
What file type are they? Or it?
VLC Player will usually try and fix a video file when starting it like rebuilding the header if it's corrupted to some extent.

Try another movie file.

---

### Post by sinhanikhil.5 on 2010-04-04
> **2hot6ft2 said:**
> What file type are they? Or it?
VLC Player will usually try and fix a video file when starting it like rebuilding the header if it's corrupted to some extent.

Try another movie file.
The file types are:- .mpg, .flv, .avi & .mp4. Yes vlc asked me to repiar and i did repaired but still iam getting only audio output for a video files.
I am not able to play with recently installed gnome mplayer, mplayer media player, vlc and movie player

I doubt there is nothing wrong with my players, its my video files corrupted.

---

### Post by arnab_das on 2010-04-04
> **sinhanikhil.5 said:**
> The file types are:- .mpg, .flv, .avi & .mp4. Yes vlc asked me to repiar and i did repaired but still iam getting only audio output for a video files.
I am not able to play with recently installed gnome mplayer, mplayer media player, vlc and movie player

I doubt there is nothing wrong with my players, its my video files corrupted.

download a sample podcast video from somewhere, tekzilla or something. and see if it works.

---

### Post by 2hot6ft2 on 2010-04-04
> **sinhanikhil.5 said:**
> The file types are:- .mpg, .flv, .avi & .mp4. Yes vlc asked me to repiar and i did repaired but still iam getting only audio output for a video files.
I am not able to play with recently installed gnome mplayer, mplayer media player, vlc and movie player
All those file types wont play. Wow.
You should be able to play pretty much everything after doing what I said.

Do you have desktop effects enabled?
Have you tried disabling them if they are on?
System > Preferences > Appearance
Visual Effects tab
Set it to None.
Try another movie.

If that doesn't help see this guide.
[Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

There is also a setting in Compiz for being able to play videos while compiz is on that should be enabled. See pic.

---

### Post by sinhanikhil.5 on 2010-04-04
[SIZE=3]**SOLVED,**[/SIZE]WELL thanks for ur help guys , its done thanks.



[COLOR=White].[/COLOR]

---

### Post by 2hot6ft2 on 2010-04-04
> **sinhanikhil.5 said:**
> [SIZE=3]**SOLVED,**[/SIZE]WELL thanks for ur help guys , its done thanks.



[COLOR=White].[/COLOR]
So what did the trick? The Visual Effects?
Welcome, and don't forget to mark the thread as solved using the Thread Tools at the top of the thread.

---

### Post by sinhanikhil.5 on 2010-04-04
> **2hot6ft2 said:**
> So what did the trick? The Visual Effects?
Welcome, and don't forget to mark the thread as solved using the Thread Tools at the top of the thread.
Well i was hoping nobody ask me this.

Anyways, I had set up contrast to minimum(0), edit>prefrence>display> contrast to minimum, giving me only dark video output.
sorry to bother u guys, but ya came to know many thing abouts player.
But honestly i never turned it to minimum:(
thanks.



[COLOR=White].[/COLOR]

---

### Post by 2hot6ft2 on 2010-04-04
> **sinhanikhil.5 said:**
> Well i was hoping nobody ask me this.

Anyways, I had set up contrast to minimum(0), edit>prefrence>display> contrast to minimum, giving me only dark video output.
sorry to bother u guys, but ya came to know many thing abouts player.
But honestly i never turned it to minimum:(
thanks.



[COLOR=White].[/COLOR]
LOL. At least we know now. Guess that's the first thing you'll check next time.
Enjoy

---

