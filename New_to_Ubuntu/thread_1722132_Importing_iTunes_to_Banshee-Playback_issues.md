---
title: "Importing iTunes to Banshee-Playback issues"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by donaddup on 2011-04-05
I am new to Ubuntu (10.10). I love the Gnome desktop and tools built-in. I have a 64 bit laptop but installed 32 bit version of Ubuntu to keep things stable (bad idea?).
I installed 2 weeks ago and tweaked heavily. But I have never been able to get Banshee to play my iPod files properly. I found some older posts regarding playback problems with Pulseaudio interfering. I used the Synaptic Package manager and removed some Pulse packages which somehow crashed the OS. (Black screen after bios and Ubuntu boot splash, then nothing further). I reinstalled and lost 2 weeks of tweaks...no worries though. Starting over and still having this issue. I installed the good, bad & ugly gstreamer codec packages. After importing iTunes files from player through Banshee I noticed random duplicate track entries, MP4's don't play at all, and MP3's stutter, skip or play for 30 seconds and stop at which point it jumps to the next available track. I tried playing the tracks with VLC, and sure enough they skip and misbehave there as well. Should I be converting these files before importing? I can't seem to find any posts or threads that describe these same symptoms, it looks like most folks have little or no trouble importing their music files. Do I have too many codec packages installed? Should I stick with the good and ugly versions alone?
Any help or redirection to proper place to post is appreciated.

---

### Post by Daniel0108 on 2011-04-05
Try booting a LiveCD (10.04 LTS preferred) and tell me if it works,

Daniel

---

### Post by donaddup on 2011-04-05
Burned a CD of 10.04LTS and ran from CD. Installed Banshee and imported 10 iTunes files from the iPod.
Banshee asked to load suitable drivers (gstreamer0.10-ffmpeg, gstreamer0.10-fluendo-mp3 & gstreamer0.10-plugins-ugly). I allowed drivers to install.
Same results, some mp3's play, some mp4'splay, some files won't play and display an x next to them, some files play choppy and somewhat scrambled, others play for as long as a minute and 30 seconds fine, then suddenly stop and banshee jumps to the next track (which may or may not start playing). The files that play all the way through with no issues are mixed, some are mp4's and some are mp3's, so it doesn't seem to be a file type problem. When I look at the files to import they have 4 character filenames, and some import as such. For instance a file imported with the name WNZY but it doesn't play and says unknown name and artist.
  What should I do now?  Thanks.

---

### Post by thouartsimple on 2011-04-05
Most likely those files have DRM attached to them... you are going to have to convert them to either mp4 or mp4 to be able to play them in Banshee.  Did you purchase the music that isn't playing from Itunes?

---

### Post by donaddup on 2011-04-05
That doesn't seem to be the case either (purchased iTunes files that is). I know because some of the problem files show as mp4's that I personally ripped from the CD's that I still own. I'm really puzzled by the multiple imports. For instance one of the first folders in the list are from my 3 Doors Down CD. 2 files imported twice (none of which plays through) it's like they're in pieces. Now that I think about it....I've played back files that sound like they have pieces of other files mixed in them.(A file will be playing and stutter and you hear a split second of another file before it continues) could the problem be the way it "sees" the file structure? Some of these files under "properties" in Banshee show as MP4, some as M4A and some as MP3. I just tried playing a "problem" track with VLC player, and the slider moves and time tracks like it's playing, but I hear nothing from the speakers. Another track plays halfway through like there's nothing wrong and just goes silent (yet the slider and timer keep tracking) I think there's something going wrong on the import process. Although, originally I copied the files from an external HD to home/music and the same thing happened, i just don't know.

---

