---
title: "Transcoding several .VOB files to a single .ogg"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by Aero_Zeppelin on 2011-01-07
I have a large number of Dvd movies stored on an external hard drive (not ripped,just copied) in the .vob format,and in most cases there are around 2 or 3 .vob files for a single movie.So my question is,How do i transcode several .vob movie files into a single .ogg or .avi file?Which transcoding application is the best for doing the same?Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-01-07
The best is ffmpeg:
```
ffmpeg -i file1.VOB -vtag xvid -vcodec mpeg4 -b 3000k -acodec libmp3lame -ab 192k file1.avi
```
You'll end up with some avi files, let's say 3 of them. Use mencoder to create one file of them:
```
mencoder -oac copy -ovc copy -o NameOfMovie.avi file1.avi file2.avi file3.avi
```

---

### Post by Aero_Zeppelin on 2011-01-07
Any GUI tool to do this?

---

### Post by Ghost_Mazal on 2011-01-07
Handbrake is a good gui for encoding video

---

### Post by JohnAStebbins on 2011-01-09
> **Ghost_Mazal said:**
> Handbrake is a good gui for encoding video

HandBrake doesn't create ogg or avi files which the OP asked for.  It can only create mp4 and mkv.  These are better containers, but older devices don't support them.

To combine several vob files when using handbrake, you would have to concatenate them first.
```

cat file1.vob file2.vob file3.vob > file.vob

```

---

### Post by TeoBigusGeekus on 2011-01-09
> **JohnAStebbins said:**
> To combine several vob files when using handbrake, you would have to concatenate them first.
```

cat file1.vob file2.vob file3.vob > file.vob

```

Using cat to concatenate video files could lead to problems with the resulting file (video-sound not syncing, lost frames, etc. better use mencoder for concatenation.

---

### Post by Aero_Zeppelin on 2011-01-10
> ffmpeg -i file1.VOB -vtag xvid -vcodec mpeg4 -b 3000k -acodec libmp3lame -ab 192k file1.avi
When i do this in the terminal,it starts processing the files but later shows an error that the libmp3lame is missing.

---

### Post by TeoBigusGeekus on 2011-01-10
See [this]("https://answers.launchpad.net/openshot/+faq/1040") and try again.

---

### Post by Synthetic Sam on 2011-01-10
> **JohnAStebbins said:**
> HandBrake doesn't create ogg or avi files which the OP asked for.  It can only create mp4 and mkv.  These are better containers, but older devices don't support them.

To combine several vob files when using handbrake, you would have to concatenate them first.
```

cat file1.vob file2.vob file3.vob > file.vob

```
In handbrake, if you load the first vob from a series (files are stored logically, for example on DVD) then it will automatically read the entire vobset in my experience.  You can select the titleset and chapter range that you want to transcode.

---

### Post by Aero_Zeppelin on 2011-01-10
> **TeoBigusGeekus said:**
> See [this]("https://answers.launchpad.net/openshot/+faq/1040") and try again.

Synaptic is showing two libavformats- libavformat-extra-52 and libavformat-unstripped-52.Which one should i install?

---

### Post by TeoBigusGeekus on 2011-01-10
Try all.

---

