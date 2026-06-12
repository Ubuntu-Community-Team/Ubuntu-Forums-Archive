---
title: "basic question how to set-up bash script"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by willfriedwald on 2009-01-28
A helpful individual has given me info on a bash script - but I'm not savvy enough to know what to do with it.  Can someone show me how to set up and implement a bash script?  (These are terminal commands?)

thanks!

----


> **phenest said:**
> If it's of any help, I've spent a whole day trying work out how to rip CD's to high quality aac/m4a files. I have discovered that you do not use bitrates, as aac is really meant to be a vbr format, and using cbr reduces the quality. So you need to set the quantizer setting which is between 10 and 500(max). I also discovered that gstreamer and faac produce very horrible sounding files whereas ffmpeg gives excellent results even at high settings. So I've written a bash script:
```
#!/bin/bash

# CD rip to m4a

cdparanoia -B 1-

for i in *.wav; do ffmpeg -y -i $i -acodec libfaac -aq 200 `basename $i .cdda.wav`.m4a; rm $i; done

exit 0
```
Change the 200 to whatever you want (500 max) but I have no idea why you want such high bit rates. 500 should give approx 320kb/s.

---

### Post by ptn107 on 2009-01-28
1- Copy and paste the code you were given into a text editor like gedit (Applications -> Accessories -> Text Editor).
2- Save it in your home folder with the extension .sh like *myscript.sh* or whatever you want to call it.
3- Now navigate to your home folder (Places -> Home Folder).  You should see the file there.  Right-click on it, select properties, then click the permissions tab.  Check the box 'Allow executing file as program' and click close.

You should now be able to double-click your script file and select 'Run in terminal' when the run box comes up.  From the looks of the code my guess is that this file needs to be in a folder containing .wav files to be of any use.

---

### Post by willfriedwald on 2009-01-28
thanks for the helpful info!

I tried it - it worked as you said.

it converted a CD into a bunch of wav files, but am not sure where it put them!  at one point, they were in my home folder along with the script itself, but then when the script finished, they disappeared.

I had the impression that it was supposed to convert the WAV files into AACs and then delete the WAVs, but am not sure what it actually did - the only thing I could swear to is that it did create some WAVs and ultimately deleted them - more I can not tell you!

thanks - have been searching high & low for a means to get high quality AAC files from a CD, and hope to find it eventually... if only there were iTunes for Ubuntu!

w

---

### Post by ptn107 on 2009-01-28
I'm looking into it.  As for iTunes for Ubuntu, Rhythmbox seems to do the job.  There is also an application called Songbird that looks identical to iTunes ([_http://www.getsongbird.com/_]("http://www.getsongbird.com/")) though it's still under active development.

---

### Post by willfriedwald on 2009-01-28
a good idea - but unfortunately Songbird does NOT support CD ripping yet! (or so it tells me...) 

however, if it could support transferring / importing from a WAV file to an AAC, that might be just as good - not sure if it can do that though...

thanks again

willfriedwald

---

### Post by donkyhotay on 2009-01-28
I use vlc for for backing up media from discs. It's a little complicated until you get used to it but is very powerful and can convert just about anything.

---

### Post by willfriedwald on 2009-01-28
VLC is my favorite movie player for Mac - it plays AVI files effortlessly - but I didn't know it could RIP CD... how do I tell it to rip a CD?

w

---

