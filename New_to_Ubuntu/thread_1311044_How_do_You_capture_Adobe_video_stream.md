---
title: "How do You capture Adobe video stream???"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by suomalainen on 2009-11-02
Hello All!

Is there a way to capture a Adobe Flash Player 10 video stream?

I thought I could go to Places-->Computer-->Filesystem-->tmp BUT I don't find anything here even when video is playing.

Any suugestions appreciated.

Thank You

---

### Post by scratman on 2009-11-02
Out of interest, which version of Ubuntu are you currently using, and also, which sites are you trying to perform this on?  This information will make it easier for us to ascertain the precise nature of the problem and recommend a solution to you.

---

### Post by suomalainen on 2009-11-02
I'm running 8.04 LTS.

---

### Post by Hazey on 2009-11-02
Hi,

when you're running firefox, there are a lot of extensions available in add-on Manager. Search for "video" in the Manager. Firefox will provide a lot of extensions to you.

Hazey

---

### Post by scratman on 2009-11-02
And which websites are you wanting to use?  The process I use works for Youtube, but not all websites.

Go to Youtube and start a video playing, then navigate to /tmp/ and look for a file called 'Flash(an Alpha-numeric code)', that ought to be your video file.  If that doesn't seem to work for some reason, could you start a video playing in Youtube, then open Terminal and post the output of this command for me please?

```
ls /tmp/
```

Regards.

---

### Post by suomalainen on 2009-11-02
ok I got it working thanks!

---

### Post by scratman on 2009-11-02
By which method, if you don't mind my asking.

---

### Post by suomalainen on 2009-11-02
there is an extension/add-on called video download helper and it does all the work for you....

---

