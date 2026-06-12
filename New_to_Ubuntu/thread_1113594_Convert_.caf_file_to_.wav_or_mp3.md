---
title: "Convert .caf file to .wav or mp3"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by tdrusk on 2009-04-01
I bought an iphone app that records audio and lets me sync to Ubuntu. The only problem is it ships it to me in .caf format, which is apples core audio format. I don't know how to convert it or play it(which would be an acceptable option).

Any ideas?

---

### Post by HermanAB on 2009-04-01
Sound exchange 'sox' can convert it for you.

---

### Post by tdrusk on 2009-04-01
> **HermanAB said:**
> Sound exchange 'sox' can convert it for you.
I tried that will the libsox-fmt-all package. I did
```
sox Recording.caf Recording.wav
```and it returned
```
sox soxio: Can't open input file `Recording.caf': Supported file format but unsupported encoding.

```

---

### Post by mikechant on 2009-04-02
You could try audacity (in the repositories, I believe). This is supposed to have good sound import facilities.

---

### Post by vadakr on 2010-07-20
Just wanted to confirm that Audacity gets this done!

---

### Post by neilobremski on 2011-03-06
Audacity refuses to load the CAF I have, giving the following error message:

> Audacity recognized the type of the file '/path/to/file.caf'.
Importers supposedly supporting such files are:
WAV, AIFF, and other uncompressed types,
but none of them understood this file format.


Any assistance would be great; perhaps extra importers for my Audacity need to be installed?

---

### Post by dionysius on 2011-03-07
> **neilobremski said:**
> Audacity refuses to load the CAF I have, giving the following error message:



Any assistance would be great; perhaps extra importers for my Audacity need to be installed?

```
sudo apt-get install pacpl
```


```
pacpl input.caf -to mp3
```

Tons of options, info in the man pages :)

---

### Post by neilobremski on 2011-03-17
I'll check the man files later, but a wee smoke test reveals ...

```
neilo@sleeepnow:~/Music$ pacpl file.caf -to mp3
Perl Audio Converter - 4.0.5

Converting:  [input.caf] -> [mp3] decode failed with exit status: 256


Total files converted: 0, failed: 1
```

It appears I do not have a CAF decoder which is probably why both this and Audacity are failing ...

```
neilo@sleeepnow:~/Music$ pacpl -f | grep caf
caf       Y   Y   sndfile-convert sndfile-convert    N          N
```

---

### Post by christg76 on 2011-04-26
Hi,
Were you able to do this in the end? I'm having precisely the same problems...

Chris

---

### Post by stmiller on 2011-04-26
.caf is a somewhat new apple lossless container.

[http://en.wikipedia.org/wiki/Core_Audio_Format](http://en.wikipedia.org/wiki/Core_Audio_Format)

You aren't going to be able to easily decode that in Linux (for now).

Ex:

[http://stackoverflow.com/questions/4541600/linux-conversion-of-caf-file-with-ilbc-codec-2-wav](http://stackoverflow.com/questions/4541600/linux-conversion-of-caf-file-with-ilbc-codec-2-wav)

If you have access to OS X, you can convert it:

[http://www.devdaily.com/mac-os-x/convert-caf-sound-file-aif-aiff-mp3-format](http://www.devdaily.com/mac-os-x/convert-caf-sound-file-aif-aiff-mp3-format)

---

### Post by andrew.46 on 2011-04-27
I could not find any samples of this type of file, anybody have a link to some?

---

### Post by neilobremski on 2011-05-07
I have an example:

[http://www.gw-basic.com/uploads/6/1/9/1/6191204/closing_losing_theme.caf]("http://www.gw-basic.com/uploads/6/1/9/1/6191204/closing_losing_theme.caf")

P.S. - It's too bad I couldn't just upload to the forum as an attachment.

---

### Post by andrew.46 on 2011-05-07
> **neilobremski said:**
> I have an example:

[http://www.gw-basic.com/uploads/6/1/9/1/6191204/closing_losing_theme.caf]("http://www.gw-basic.com/uploads/6/1/9/1/6191204/closing_losing_theme.caf")

Thanks for that :). This particular caf file converts easily enough with the current ffmpeg although of course caf is simply a container and can contain [several different audio codecs]("http://en.wikipedia.org/wiki/Core_Audio_Format"). This particular file contains *adpcm_ima_qt* and FFmpeg converts it and FFplay plays it. I attach wav and mp3 versions of this file.

If the repository FFmpeg will not work with this file, and I admit I have not tested with the repository FFmpeg, have a look at this guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by jtarin on 2011-05-07
First check if the CAF file is a valid file. Does it play? Is the header correct? What is the data format? Is it compressed? 

(The data format is separate from the file format, which is just a container for various bits of data as well as the sample data. The data format could be PCM, or it could be compressed in any format such as MP3, AAC, uLaw, etc.)

---

### Post by eakinc on 2011-05-12
@neilobremski
Try converting to wav instead of mp3.
#pacpl --to wav inputfile.caf
Works for me from files created on iPad with QuickVoice app.
Erik

---

### Post by tumutanzi.com on 2012-09-21
> **dionysius said:**
> ```
sudo apt-get install pacpl
```


```
pacpl input.caf -to mp3
```

Tons of options, info in the man pages :)

Thanks, your method works, great.

---

### Post by papibe on 2012-09-21
Please do not replay on old threads.

**Thread closed**.

---

