---
title: "CODEC of .MKV files"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by abirphs on 2010-06-30
My internet connection is very slow thats why i'm having problem in downloading codecs for playing .mkv files on my ubuntu. Can I download the codecs from any other source rather than directly downloading them to my pc. If it is possible then I can download the codecs from my friends pc, then install it in my pc by usb drive.

Is there any such way out?

---

### Post by okplayer02 on 2010-06-30
what codecs are you talking about? If you are downloading something from the internet you can use the wget command

```
wget -c the-url-ofthecodec
```

with this if you stop a download it will pick up from where you left off as long as you are in the same directory where the original file is at.

am curious which codecs are you looking to install?

---

### Post by nikhilbhardwaj on 2010-06-30
you should just enable the multimedia repos and you'll be playing mkv files in no time
just google around for the step by step instructions to enable multimedia repos for whichever version of ubuntu you are running.

---

### Post by ankspo71 on 2010-06-30
Hi,
With synaptic package manager, you can create a download script that you can bring to your friend's computer to download the files with.
[http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html](http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html)

Also have a look at the following sites. You can use one of these on your friend's computer to download and gather up all of the packages you need.
[http://keryxproject.org/](http://keryxproject.org/)  (multi-platform - windows and linux)
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) 

Hope this helps.

---

### Post by abirphs on 2010-06-30
Thanks all very much, this forur is really very helpfull.

thanks again

---

