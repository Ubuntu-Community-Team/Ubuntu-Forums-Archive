---
title: "No Video is playing in Ubuntu 9.04 !"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-11-02
Hi,

I am able to play mp3 and other audio files in my ubuntu 9.04 using vlc. But I am not able to play any video files in it. I am having vlc already. 

what will be the problem ?

---

### Post by mikewhatever on 2009-11-02
What do you mean you are not able, what exactly is the problem? Please be detailed.

---

### Post by luckydeveloper on 2009-11-02
> **mikewhatever said:**
> What do you mean you are not able, what exactly is the problem? Please be detailed.
[LIST=1]
[*]When i play any video file with Movie Player, the player closes immediately
[*]When i play the same with vlc, the same thing happens except that another Video Output window opens and closes along with Vlc
[/LIST]

Please help.

---

### Post by danastasio on 2009-11-02
> **luckydeveloper said:**
> [LIST=1]
[*]When i play any video file with Movie Player, the player closes immediately
[*]When i play the same with vlc, the same thing happens except that another Video Output window opens and closes along with Vlc
[/LIST]

Please help.

Can you play the video in any other player? i.e. totem?

---

### Post by luckydeveloper on 2009-11-02
> **danastasio said:**
> Can you play the video in any other player? i.e. totem?

No, I am not able to play it with totem as well. The totem player just opens and closes immediately .

Even .Ogv files are not getting opened.

what may be the problem ?

---

### Post by pootan on 2009-11-02
Check out this page to see if it helps you.

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-playback.html)

---

### Post by prshah on 2009-11-02
Open a terminal (Applications-Accessories-Terminal) and give the command```
totem
``` to open the video player; now load a video file into the player and try to play it; when it closes, post back the output in the terminal for a clue as to why it closes.

---

### Post by luckydeveloper on 2009-11-02
> **prshah said:**
> Open a terminal (Applications-Accessories-Terminal) and give the command```
totem
``` to open the video player; now load a video file into the player and try to play it; when it closes, post back the output in the terminal for a clue as to why it closes.

This is what i got !

```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 91 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by superharas on 2009-11-02
I am also new to ubuntu, just know it for 2 weeks.
I think you need to install these packages, from this site [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) .
It didn't work for me, and I tried this and it did, I hope it works for you.

---

### Post by 11010110 on 2009-11-02
Hey there,

I was having similar problems in Karmic. A workaround I found was if you go into vlc, then preferences and under video chose Output: OpenGL video output. This worked for me. Try all of the output types if OpenGL doesnt work. Hope this helps!

Good luck!

---

