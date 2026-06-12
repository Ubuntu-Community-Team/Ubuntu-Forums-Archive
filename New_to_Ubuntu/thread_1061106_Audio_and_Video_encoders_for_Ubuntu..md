---
title: "Audio and Video encoders for Ubuntu."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by melrokz on 2009-02-05
Please tell me which are the best video and audio encodes to convert between multiple (including proprietary) formats.

---

### Post by SuperSonic4 on 2009-02-05
soundconverter and avidemux for audio and video respectively

---

### Post by Hospadar on 2009-02-05
I really like avidemux.
If you have huge jobs to do, you might consider a command-line tool like ffmpeg, harder to use, but extremely powerful.  You can install a version that will handle any sort of proprietary format from the medibuntu repositories.  Google medibuntu to find out how to add their repo.

---

### Post by wolfen69 on 2009-02-05
> **Hospadar said:**
> 
If you have huge jobs to do, you might consider a command-line tool like ffmpeg, harder to use, but extremely powerful.

but there is a gui frontend for ffmpeg called winff, if you prefer a gui.

---

### Post by jerome1232 on 2009-02-05
> **wolfen69 said:**
> but there is a gui frontend for ffmpeg called winff, if you prefer a gui.

Very cool, even though I found ffmpeg very easy  to use considering I don't know much about trans-coding. I think I'll give winff a go.

---

### Post by nothingspecial on 2009-02-05
[[COLOR="Magenta"]ffmpeg cheat sheet[/COLOR]]("http://www.catswhocode.com/blog/19-ffmpeg-commands-for-all-needs")

---

### Post by FakeOutdoorsman on 2009-02-05
> **Hospadar said:**
> I really like avidemux.
If you have huge jobs to do, you might consider a command-line tool like ffmpeg, harder to use, but extremely powerful.  You can install a version that will handle any sort of proprietary format from the medibuntu repositories.  Google medibuntu to find out how to add their repo.
Medibuntu doesn't supply ffmpeg for Intrepid.  FFmpeg from the repository doesn't support restricted formats until you install the **libavcodec-unstripped-51** package.

You could also compile FFmpeg and x264 yourself to gain access to the latest revision and the libx264 presets which makes high-quality encoding with FFmpeg much easier:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

