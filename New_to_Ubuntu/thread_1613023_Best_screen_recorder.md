---
title: "Best screen recorder?"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-11-03
Hey everyone, I'm interested in making Ubuntu video clips. I'm looking for a good screen recorder, to record video of my computer screen in real time. 

Any suggestions?

---

### Post by s3MA00RRNY on 2010-11-04
There's one called gtkRecordMyDesktop. Have only used it once. It didn't handle sound, though it claimed to. Perhaps I did something wrong. Of course you could always splice it in later.

---

### Post by Ranger_Joe on 2010-11-05
Has anyone ever used Desktop Recorder? I'm trying to use it and I like the interface but the actual video capture is pathetic. I'm wondering if I'm using it wrong or what. I've tried tweaking the frame rate and it doesn't work.

It basically is great for screenshots but has a real problem capturing movement. Any pointers?

---

### Post by manchildjr on 2010-11-16
i heard it was the same thing as record my destop

---

### Post by Verbeck on 2010-11-16
have you tried vlc?

---

### Post by pqwoerituytrueiwoq on 2010-11-16
i have been using xvidcap cause gtk-recrormydesktop hates me
*goes to try vlc*

---

### Post by sandyd on 2010-11-16
```

ffmpeg -y -f alsa -ac 2 -i** pulse **-f x11grab -r 25 -s **1920x1080** -i :0.0 -vcodec libx264 -vpre lossless_ultrafast -crf 22 -acodec **libmp3lame** -ar 44100 -ab 126k -threads 3 ~/Desktop/screencast.mkv

```
Substitute for the bolded parts 
1. Screen Size
2. Audio Input
3. Audio codec

Don't change the audio bitrate or samplling, changing it usually results in crappy audio.

---

### Post by cblnchat on 2011-02-20
I am also interested in recording the screen on Ubuntu.  But im not sure how.  Is there any simple way to do it.  Like download something and just run it?  
Btw im still pretty new to ubuntu so be specific plz.  
Thanks

Edit:  I just tried the screen recorder called RecordItNow and it sucks.  Its too bright and it doesnt capture movement at all.  Id like one that can also record games. 
Thanks

---

### Post by Stray Wolf on 2011-03-29
Does any one know of a desktop recorder that plays nice with compiz and cairo-dock?

---

### Post by Locke_99GS on 2011-03-29
Kazam is a very simple screencap software. Captures the screen and audio without fuss - you may want to re-encode the output though.

gtkRecordMyDesktop is the one I use the most, though configuring it to record proper audio can be a chore. Fortunately, very seldom do I require audio capture.

Search in the Software Centre or Synaptic - there are several choices.

---

### Post by wsherliker on 2011-06-14
Try this - didn't have much success with any of the other options and this simple script does what I want. Captures an area of the screen but could be easily altered to work for whole screen etc and add gui/edit functions. Anyone want to do it!

```
#/bin/bash

echo "CAPTURE - Record a portion of the screen with sound"
echo "Script by Warren Sherliker - The SmartTHING Limited"
echo ""
echo "NOTE: Ensure you have to set ffmpeg to capture from the monitor of your computers audio otherwise you will get silence"
echo "(see http://openubuntu.com/index.php?topic=690.0 and ensure you have unmuted the monitor)"
echo ""
echo "PREREQUISITES: ffmpeg and xdotool (both available by sudo apt-get install ....)"

echo "Please position your mouse in the top left of the capture area"
for i in `seq 1 5`; do
    echo -n "Pausing for 5 seconds: $i second(s)"
    echo -n $'\r'
    sleep 1
done
echo ""

POS=`xdotool getmouselocation`
X=`echo $POS | cut -d\  -f1`
Y=`echo $POS | cut -d\  -f2`

echo "Found $X and $Y"

echo "Please position your mouse in the bottom right of the capture area"
for i in `seq 1 5`; do
   echo -n "Pausing for 5 seconds: $i second(s)"
   echo -n $'\r'
   sleep 1
done
echo ""

POS=`xdotool getmouselocation`
X2=`echo $POS | cut -d\  -f1`
Y2=`echo $POS | cut -d\  -f2`

echo "Found $X2 and $Y2"

echo "Please start your video"
for i in `seq 1 5`; do
   echo -n "Pausing for 5 seconds: $i second(s)"
   echo -n $'\r'
   sleep 1
done
echo ""

if [ -e "output.mkv" ]; then
   echo "Removing previous recording (output.mkv)"
   rm "output.mkv"
fi

# Not much error checking here but should work in most cases
X=${X:2}
Y=${Y:2}
X2=${X2:2}
Y2=${Y2:2}

width=$(($X2 - $X))
width=$(($width / 2 * 2)) # Round to nearest multiple of 2 for ffmpeg
width=${width#-} # Ensure it is not negative (should really swap X and X2, Y and Y2 if so)
height=$(($Y2 - $Y)) 
height=$(($height / 2 * 2)) # Round to nearest multiple of 2 for ffmpeg
height=${height#-} # Ensure it is not negative (should really swap X and X2, Y and Y2 if so)

echo "Capturing ${width} by ${height} at position ${X} ${Y} to output.mkv in the current directory"

CMD="ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s ${width}x${height} -i :0.0+${X},${Y} -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv"

echo "RUNNING $CMD"
$CMD

echo "Output saved to output.mkv"
echo ""
echo "NOTE: You can perform basic cuts to the video using: "
echo " ffmpeg -sameq -ss <start in seconds> -i output.mkv output-cut.mkv"
echo "        add the -t <duration in seconds> parameter if needed"

```

---

### Post by ranjit. on 2011-11-11
for the love of god if u are using the terminal when u are recording some thing, please dont use desktop video recorder:( it will make ur terminal look as if it has steps, the video becomes vey much choppy and at the end u will hate ur self, so is there any other option available when recording the desktop, i have seen a lot of videos in youtube which has people using terminal and they make such wonderful videos:guitar:

---

### Post by cprofitt on 2011-11-11
Here is a youtube video of how to use RecordMyDesktop:

[http://www.youtube.com/watch?v=A0Tn3Z8OklQ](http://www.youtube.com/watch?v=A0Tn3Z8OklQ)

---

### Post by beew on 2011-11-12
Kazam hands down. 

RecordMydesktop cannot handle Compiz, the image breaks up into little "steps" when Compiz is enabled, which makes it quite useless for the new Ubuntu because Unity is Compiz. Xvidcap is often recommended,--probably what they used to record the spinning cube on Youtube, it creates smooth images when Compiz is enabled but somehow cannot record sound,--apparently it is disabled in the Ubuntu build for some reasons,-- the "workaround" is to either record the sound separately and then add it to the video, or to install an old version for Jaunty with a .deb. "Jaunty"????? Are you kidding me?

Kazam renders a Compiz enabled desktop beautifully and records the sound as well. The only small problem I experienced is that if you have the Nvidia proprietary driver installed the recorded film somehow appears as a big smudge while playing back in mplayer with vdpau enabled, and it doesn't play in VLC at all if hardware acceleration is enabled. The easy work around would be to either 1) use totem or 2) switch to xv instead of vdpau in mplayer or 3) disable hardware acceleration in vlc  while playing the movie, then playback is fine. Also transcoding the file in handbrake, for example, would eliminate the problem once and for all.

---

### Post by headcheese3 on 2012-08-10
Unless you have a high end computer, don't use Kazam. Kazam records "on the fly" meaning that it writes everything down as it records, taking up a lot more CPU. Personally, I can't find a good one for my laptop. I'm currently looking into XVidcap.

---

