---
title: "getting audio from a video (i.e. youtube)"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by jiminos on 2010-01-22
i am still really new at this ubuntu thing. what i want to do is extract the audio from some youtube videos. can this be done? if so, how?

thank you in advance.

be well,

jim

---

### Post by Ant59 on 2010-01-22
If you have the ffmpeg package installed, use:

```
ffmpeg -i get_stream.flv -f mp3 -vn -acodec copy audio.mp3
```

where *get_stream.flv* is the downloaded youtube vid, and *audio.mp3* is the audio destination file.

---

### Post by sylvainrb on 2010-01-22
Or if you prefer a more graphical interface, you can use winff:

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

Not updated for Ubuntu 9.10 but pretty much the same thing. Might have to double check which codecs you're missing.

---

### Post by Sef on 2010-01-22
[Youtube Terms of service]("http://code.google.com/apis/youtube/terms.html") (in part):

> **II. Prohibitions**


11. access any portion of any YouTube audiovisual content by any means other than use of a YouTube player or other video player expressly authorized by YouTube;

12. store copies of YouTube audiovisual content; 

Hence thread has been locked since it violates Youtube's terms of service, and therefore, [Ubuntu Forums's Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") #1-6

---

