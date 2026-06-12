---
title: "audacious help install"
date: 2010-05-01
forum: New to Ubuntu
---

### Post by D3jan on 2010-05-01
in my software center i found audacious 2.1.1 and on player site is the 2.3.1 but it's not official and i would like to know how can i use this arhive files. the question is stupid but i'm only the beginer  in this :)    [http://audacious-media-player.org/](http://audacious-media-player.org/)

---

### Post by D3jan on 2010-05-01
I just install v2.3 but no skin

---

### Post by agnes on 2010-05-01
Generally for source archives:
1. extract .tgz file (in a Terminal you can do this with 'tar xvzf file.tgz').
2. see the file called 'INSTALL' in the extracted directory :)
or
2. go the the extracted directory in a Terminal. Type './configure'. This will check if you have the right dependencies - if not it will say what libs/programs you are missing, you need to get those. Then, if all the dependencies are ok, type 'make' and 'make install'. The program will be installed in /usr/local/bin by default.

---

### Post by mister_playboy on 2010-05-05
I get an error when trying to compile the plugins... any idea?

```
Entering directory pulse_audio.
Successfully generated dependencies.
pulse_audio.c: In function &#8216;pulse_open&#8217;:
pulse_audio.c:554: error: &#8216;PA_SAMPLE_S24_32LE&#8217; undeclared (first use in this function)
pulse_audio.c:554: error: (Each undeclared identifier is reported only once
pulse_audio.c:554: error: for each function it appears in.)
pulse_audio.c:557: error: &#8216;PA_SAMPLE_S24_32BE&#8217; undeclared (first use in this function)
pulse_audio.c:560: error: &#8216;PA_SAMPLE_S24_32NE&#8217; undeclared (first use in this function)
Failed to compile pulse_audio.c!
make[5]: *** [pulse_audio.o] Error 1
make[4]: *** [all] Error 1
make[3]: *** [subdirs] Error 1
make[2]: *** [all] Error 1
make[1]: *** [subdirs] Error 1
make: *** [all] Error 1
```

---

