---
title: "Arista Transcoder - Patent Free Presets = Not Working"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by pspsampsp on 2010-01-30
Hey , using Arista Transcoder i am unable to convert any videos using the patent free presets for Computer , Launching it from a terminal produces this error/debug information: 
```

Traceback (most recent call last):
  File "/usr/share/arista/arista/transcoder.py", line 143, in _got_info
    self._setup_pass()
  File "/usr/share/arista/arista/transcoder.py", line 437, in _setup_pass
    self._build_pipeline(cmd)
  File "/usr/share/arista/arista/transcoder.py", line 456, in _build_pipeline
    str(e))
arista.transcoder.PipelineException: Unable to construct pipeline! could not link audioresample0 to vorbisenc1
^CTraceback (most recent call last):
  File "/usr/bin/arista-gtk", line 1397, in <module>
    gtk.main()


```

Is this a bug or is it just due to needing something extra that isn't pulled in with Arista can encode in that video format (Theora/Vorbis)?

---

### Post by Psumi on 2010-01-30
Tried handbrake instead? or winff (if the input video is ffmpeg supported)?

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by Daniel G. Taylor on 2010-06-13
These issues should all be fixed with the latest release. I also suggest you install all the gstreamer plugin packages (including good/bad/ugly/ffmpeg and the Multiverse ones) to get full functionality!

In the future please report bugs like this here:

[http://github.com/danielgtaylor/arista/issues](http://github.com/danielgtaylor/arista/issues)

Thanks!

---

