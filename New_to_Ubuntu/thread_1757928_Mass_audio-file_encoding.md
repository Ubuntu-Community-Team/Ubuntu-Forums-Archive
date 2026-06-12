---
title: "Mass audio-file encoding"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by Rokkross on 2011-05-14
Recently, I decided to rip all of my CDs into my library (I had most of them on my drive before when I was using windows, but I didn't back anything up). Stupidly, I decided to encode all of the files that I have ripped in FLAC (though I do love the format, I haven't exactly got the space for it, so MP3 at 320 kbps will suffice). Anyways, I was wondering if there was a program or command(s) that will allow me to do this: 
1. Search for files within a directory based on file extension (.flac) 
2. Encode all of the files with that certain extension to MP3 all at once
3. delete the original files when encoding is done (though I can easily do this last part just by manually deleting them, I was just wondering if there would be a way to speed that process up). 
Any feedback is appreciated!

---

### Post by hashimoto on 2011-05-14
Try soundconverter. Available in universe

---

### Post by deconstrained on 2011-05-14
You sure? Storage space keeps getting cheaper and cheaper. You'll regret throwing away your lossless audio later, unless it's crappy music that you really don't like.

I've used whatmp3 (a python script) to transcode my entire library. It can do multithreading, so if you have 4 cores at your disposal it might go a little faster. But I only made an MP3 copy of my library so that I can fit more stuff on my Droid...

---

### Post by powerpleb on 2011-05-14
There is a perl script here that handles this:
[http://freshmeat.net/projects/flac2mp3/](http://freshmeat.net/projects/flac2mp3/)

To use it:
[LIST]
[*]Download and unzip it into a folder (eg /home/user/bin/) making sure "lib" directory goes in too.
[*]Ensure script is executable by running "chmod +x /home/user/bin/flac2mp3.pl"
[*]Install lame and flac with "sudo apt-get install lame flac"
[*]Navigate to the directory where all your music sub-directories are (eg "cd /home/user/Music/")
[*]Run the script like so: ```
/home/user/bin/flac2mp3.pl --lameargs='-b 320 -h' . .
```
[/LIST]
You can even make it go faster if you have a multicore cpu by telling it to use more than one core at once like so (eg if you had 4 cores):
```
/home/user/bin/flac2mp3.pl --processes='4' --lameargs='-b 320 -h' . .
```

I suppose to delete the flac files you could just use:
```
rm ./*/*.flac && rm ./*/*/*.flac && rm ./*/*/*/*.flac
```

Assuming you didn't have files more than 3 subdirectories in. 

There may be a better way of doing all this using find though.

---

