---
title: "good FLV downloader for Ubuntu?"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-12
I love keeping my favorite video's from the internet (as I know lots of people do)

Whats the best downloader for Ubuntu that you have found to use?

---

### Post by Michael.Godawski on 2009-01-12
hi,

have a look at these:


[LIST]
[*][https://addons.mozilla.org/en-US/firefox/search?q=flv&cat=all](https://addons.mozilla.org/en-US/firefox/search?q=flv&cat=all)
[/LIST]

or have a look into your web cache in /tmp

---

### Post by ChildOfMana on 2009-01-12
I use Video Downloadhelper.

It's an extension to Firefox. Go [here]("https://addons.mozilla.org/en-US/firefox/") and search for it.

Full instructions on the site.

Enjoy :)

---

### Post by cptrohn on 2009-01-12
Thanks all.... I used to use Reals FLV downloader, but it doesn't work in FF only IE... and since I completly ditched the butterfly I guess I have to change that too eh?

---

### Post by cerealtx on 2009-01-12
```
wget "http://moviefile.flv"
``` works awesomely too but im a command line kinda person, to get the link just view the html source and look for the link

---

### Post by crjackson on 2009-01-12
> **ChildOfMana said:**
> I use Video Downloadhelper.

It's an extension to Firefox. Go [here]("https://addons.mozilla.org/en-US/firefox/") and search for it.

Full instructions on the site.

Enjoy :)
+1 Works great for me.

---

### Post by karlr42 on 2009-01-12
youtube-dl

---

### Post by andrew.46 on 2009-01-19
Hi,

[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

  Andrew

---

### Post by mcduck on 2009-01-19
Actually you don't need any program, or any Firefox extension, to save those .flv videos.

After the video is completely loaded you can just copy it from /tmp to your desktop or where ever you want. Firefox automatically saves the video in /tmp while loading it.

---

### Post by s3kt0r on 2009-01-19
Getting the files in /tmp is by far, the quickest..Just need a browser installed, nothing more.

---

### Post by lukjad on 2009-01-20
> **karlr42 said:**
> youtube-dl
+1 to youtube-dl

You need to open an instance of the Terminal (*Application->Accessories->Terminal*) and type: ```
youtube-dl http://www.youtube.com/watch?v=SomeRandomText
```

From there, it should download itself to your /home/username/ folder. Then you can rename it from *SomeRandomText* to *ThisReallyCoolVideoAboutAHamster*. :D

---

