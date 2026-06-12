---
title: "Can't uninstall FFMPEG, help!"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by transmition on 2009-01-01
After trying to get a version of ffmpeg that wasn't castrated, I tried multiple methods of compiling and installing it. Needless to say, I can't seem to remove the package.

When I type:

```

sudo apt-get remove ffmpeg

```

I get 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ffmpeg is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

However, typing ```
ffmpeg -formats
``` still gets me a list of all its capabilities.

---

### Post by oldos2er on 2009-01-01
If you compiled and installed it with "sudo make install," you need to go back to its folder and enter "sudo make uninstall."

---

### Post by transmition on 2009-01-01
Thanks.

---

### Post by snova on 2009-01-01
> **transmition said:**
> and if this folder is gone? ....

How did you install it? Just plain old "make install"?

---

### Post by transmition on 2009-01-01
[UPDATE]

I did as oldos2er said, but now after running
```
sudo apt-get install ffmpeg
```
and then
```
ffmpeg -formats
```
I get an error stating
```
bash: /usr/local/bin/ffmpeg: No such file or directory
```

---

### Post by adult swim on 2009-01-01
if you havent already deleted the folder in which you ran sudo make uninstall, sometimes you have to run that command several times to clean everything out.

---

### Post by nemilar on 2009-01-01
can you post the output of:

```
which ffmpeg
```

as well as:

```
file /usr/bin/ffmpeg
```

```
file /usr/local/bin/ffmpeg
```


using configure/make/make install tends to install things to /usr/local/ whereas apt will put things in /usr/.  So I think at this point your system is a bit confused...

---

### Post by transmition on 2009-01-01
Sorry, I think I got things working out alright. Now I have to solve my main problem, being that I can't seem to rip a DVD with VLC using mp3 for sound.

Thanks for all the help though.

---

### Post by FakeOutdoorsman on 2009-01-01
If you want a more capable ffmpeg, then I suggest installing the unstripped ffmpeg libraries as well (assuming you're using 8.10):
```
sudo apt-get install libavcodec-unstripped-51
```
I prefer compiling my own ffmpeg.  This guide explains how to properly install ffmpeg with checkinstall so your package manager recognizes the installation:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by kristopher.ives on 2009-01-01
To avoid this and still be able to user temporary compiled tests of a package you can use checkinstall to generate a package. It won't be a pretty package usually, but at least it lets you remove the files if you delete the source or the source changes.

---

