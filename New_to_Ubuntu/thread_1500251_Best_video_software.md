---
title: "Best video software??"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by TriBlox6432 on 2010-06-02
Hello,

On Window$ I used unregistered hyper cam so I could take video of my screen.  How do I do this in Ubuntu?  What's the best program for the job?

---

### Post by Ozymandias_117 on 2010-06-02
I've never personally used it, but I've heard great things about Record My Desktop

```
sudo aptitude install recordmydesktop
```

---

### Post by cariboo on 2010-06-02
There are many screen capture packages in the repositories, have a look [here]("http://linuxappfinder.com/graphics/screencapture") all the applications listed are available except for Kim and Wink.

I won't recommend any, because what may work well for me, may not be what you are looking for. I suggest you try them all and pick the one that works best for you.

---

### Post by SoFl W on 2010-06-02
VLC will allow screen capture, and it is a great media playback tool.

---

### Post by brennydoogles on 2010-06-02
> **Ozymandias_117 said:**
> I've never personally used it, but I've heard great things about Record My Desktop

```
sudo aptitude install recordmydesktop
```

I would go a step further and suggest gtkRecordMyDesktop. It is the GUI version of Record My Desktop, which I use regularly. The only issue I have found so far with recordmydesktop is that it records into .ogg format (an issue if you want to upload to youtube). I have written a script to take care of that for you:
```

#!/bin/bash
#convert Ogg video to AVI

### Storage directories
### If you would like to store your video in another place, you may set that here:
###
CASTDIR=/home/$USER/screencasts
AVIDIR=$CASTDIR/avi
OGGDIR=$CASTDIR/ogv
###
### Please edit the following line to reflect the location recordmydesktop saves your screencasts:
###
CAST=/home/$USER/out.ogv
if [ ! -d $AVIDIR ]; 
  then mkdir -p $AVIDIR; 
fi 
if [ ! -d $OGGDIR ]; 
  then mkdir -p $OGGDIR; 
fi
echo "What would you like to call your screencast?"
read OUTFILE
### Uncomment the below selection to allow for the passing of the file name as a command line argument
### mencoder -idx "$1" -ovc lavc -oac mp3lame -o "$OUTFILE".avi
###
### Comment the following line if you uncommented the previous line
mencoder -idx $CAST -ovc lavc -oac mp3lame -o "$OUTFILE".avi
echo "Moving your videos to $CASTDIR and renaming them."
mv "$OUTFILE".avi $AVIDIR/"$OUTFILE".avi
### Uncomment the below selection to allow for the passing of the file name as a command line argument
### mv $CAST $OGGDIR/"$OUTFILE".ogv
###
### Comment the following line if you uncommented the previous line
mv $CAST $OGGDIR/"$OUTFILE".ogv
exit 0

```

Hope that helps!

---

### Post by HermanAB on 2010-06-03
There is also 'Istanbul'.

---

### Post by philinux on 2010-06-03
> **SoFl W said:**
> VLC will allow screen capture, and it is a great media playback tool.

How do you do this?

---

