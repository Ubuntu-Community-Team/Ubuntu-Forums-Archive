---
title: "Help a newbie!! ;)"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by Kryptonas on 2010-09-05
guys i am new in linux and i need some help!
i am trying to download a video from youtube and i get this:

kryptonas@kryptonas-pc:~$ youtube-dl [http://www.youtube.com/watch?v=YzFlUiPvwQ8](http://www.youtube.com/watch?v=YzFlUiPvwQ8)
[youtube] Setting language
[youtube] YzFlUiPvwQ8: Downloading video info webpage
[youtube] YzFlUiPvwQ8: Extracting video information
ERROR: format not available for video

do you know what shall i do?

---

### Post by dream_coder on 2010-09-05
Just use Downloadhelper addon for firefox :)

---

### Post by 0004tom on 2010-09-05
try

```
youtube-dl -f 18 http://www.youtube.com/watch?v=YzFlUiPvwQ8
```

---

### Post by quinnten83 on 2010-09-05
You can do the following:
play the video on youtube and let it finish.
After it's done playing keep the browser page open,
go to the folder /tmp, that's places>computer>filesystem>tmp
there should be a file there with a weird name consisting of random letters and usually without an extension. that is the file you want.
Copy it to a safe place. It will play in VLC.
 But the flashdownloader thing sounds good too.

---

### Post by quinnten83 on 2010-09-05
> **0004tom said:**
> try

```
youtube-dl -f 18 http://www.youtube.com/watch?v=YzFlUiPvwQ8
```

Does this only work with youtube or can you use it to download other flash files?

---

### Post by Kryptonas on 2010-09-05
> **0004tom said:**
> try

```
youtube-dl -f 18 http://www.youtube.com/watch?v=YzFlUiPvwQ8
```
 
it doesn't work.. but it's ok! [dream_coder]("http://ubuntuforums.org/member.php?u=452018") gave me a solution! :P
 thank you guys!!

---

### Post by sxmaxchine on 2010-09-05
enter this in your url box 
[http://www.youtubekeep.com/watch?v=YzFlUiPvwQ8](http://www.youtubekeep.com/watch?v=YzFlUiPvwQ8)

---

### Post by 0004tom on 2010-09-05
> **Kryptonas said:**
> it doesn't work.. but it's ok! [dream_coder]("http://ubuntuforums.org/member.php?u=452018") gave me a solution! :P
 thank you guys!!

Works fine here :s

```
tom@tom-desktop:~/Downloads$ ./youtube-dl -f 18 http://www.youtube.com/watch?v=YzFlUiPvwQ8
[youtube] Setting language
[youtube] YzFlUiPvwQ8: Downloading video webpage
[youtube] YzFlUiPvwQ8: Downloading video info webpage
[youtube] YzFlUiPvwQ8: Extracting video information
[download] Destination: YzFlUiPvwQ8.mp4
[download] 100.0% of 12.83M at   99.72k/s ETA 00:00 
tom@tom-desktop:~/Downloads$ ./youtube-dl --version
2010.08.04
tom@tom-desktop:~/Downloads$
```

---

