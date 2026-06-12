---
title: "AWESOME script to convert flv fles to mp3"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-18
i found this script online and tried it.. works like a CHARM..

just make sure you chmod a+x your script so that it will work!

enjoy!
```

#!/bin/sh
# this script should convert files from FLV to WAV and then to MP3
echo " "
echo " Welcome to FLV to MP3 converter! version 0.1"
echo " "
echo " "
echo "Here is a list of the FLV files in the current directory:"
echo " "
ls *.flv
echo " "
echo -n "Which FLV file would you like me to convert?: "
read infile_name
# exit if the user did not enter anything:
if [ -z "$infile_name" ]; then
echo " "
echo "You did not tell me the file name, so I will exit now."
echo " "
exit
fi
echo " "
echo "OK. Starting the conversion!"
echo " "
ffmpeg -i "$infile_name" -acodec pcm_s16le -ac 2 -ab 128k -vn -y "${infile_name%.flv}.wav"
lame --preset cd "${infile_name%.flv}.wav" "${infile_name%.flv}.mp3"
rm "${infile_name%.flv}.wav"
echo " "
echo "OK. I'm done! Have fun!"
echo " "
exit
```

---

### Post by GCoffee on 2009-04-19
Just read through that, looks pretty cool :D

Alternatively you can use winFF, I cant remeber if it is in the repostories or not but there is a .deb download from the website at:

[http://winff.org/html/](http://winff.org/html/)

It converts all sorts of files, can convert to ipod and all sorts :)

GC.

---

### Post by SuperSonic4 on 2009-04-19
Looks good to me, I just use pacpl and the dolphin plugin though

---

### Post by perspectoff on 2009-05-02
Seems like an awful lot of work.

FFMPEG does the same thing with a simple one-line command:

```
ffmpeg -i nameofvideoclip.flv -ab 160k -ac 2 -ar 44100 -vn nameoffile.mp3
```

where -i indicates the input, -ab indicates the bit rate (in this example 160kb/sec), -vn means no video ouput, -ac 2 means 2 channels, -ar 44100 indicates the sampling frequency.

Of course, you have to install FFMPEG first (it may already be installed on your system, since it is used by a lot of other programs):

 sudo apt-get install ffmpeg

---

### Post by perspectoff on 2009-05-02
> **GCoffee said:**
> Just read through that, looks pretty cool :D

Alternatively you can use winFF, I cant remeber if it is in the repostories or not but there is a .deb download from the website at:

[http://winff.org/html/](http://winff.org/html/)

It converts all sorts of files, can convert to ipod and all sorts :)

GC.


It's in the Jaunty repositories. Not in earlier repositories,

---

