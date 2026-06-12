---
title: "Downloading adult material from Youtube"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Jonathan E-D on 2009-03-30
There is a dance sequence that I have tried to download from Youtube via the terminal in the usual manner (youtube - dl + videoclip address).  Due to the fact that the dancer is nude in the sequence I want to download, Youtube considers it to be adult material and I am unable to complete download.  Please tell me what I should place after - dl in order to do so.  I am an absolute beginner.  Thank you.

---

### Post by MarcusA on 2009-03-30
You can always use the firefox addon "downloadhelper" to download youtube videos.

Or a site like [http://www.downloadyoutubevideos.com/](http://www.downloadyoutubevideos.com/) I guess

---

### Post by mister_pink on 2009-03-30
If I want to save a youtube video I've just watched I tend to just copy and paste it from /tmp before I browse away from the video. Not much use if you want to download lots of them or something though.

---

### Post by Simian Man on 2009-03-30
I believe that clive works for those so long as you are logged onto youtube at the time.

---

### Post by Therion on 2009-03-30
> **MarcusA said:**
> You can always use the firefox addon "downloadhelper" to download youtube videos.
Yup.  [https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

Problem solved.

---

### Post by LowSky on 2009-03-30
[QUOTE=Jonathan E-D;6982857]... Youtube ...nude.... QUOTE]

Since when does youtube have nudity? Ive seen the adult warning, but I thought nudity was againt the posting policy. I assume each country has a different posting policy that go with that nations internet policies.

---

### Post by aktiwers on 2009-03-30
or put pwn infront of the youtube url...

like this

[www.pwnyoutube.com/allthotherstuff](www.pwnyoutube.com/allthotherstuff)...

---

### Post by Malalo on 2009-03-30
> 
Since when does youtube have nudity? Ive seen the adult warning, but I thought nudity was againt the posting policy. I assume each country has a different posting policy that go with that nations internet policies.

I'm also interested in knowing which video you're talking about :P

---

### Post by Jonathan E-D on 2009-03-31
What is clive?  thanks for answering

---

### Post by andrew.46 on 2009-04-09
Hi Jonathan,

> **Jonathan E-D said:**
> There is a dance sequence that I have tried to download from Youtube via the terminal in the usual manner (youtube - dl + videoclip address).  Due to the fact that the dancer is nude in the sequence I want to download, Youtube considers it to be adult material and I am unable to complete download.  Please tell me what I should place after - dl in order to do so.  I am an absolute beginner.  Thank you.

You will see the full range of options for youtube-dl as follows:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl --help[/COLOR]**
Usage: youtube-dl [options] url...

Options:
  -h, --help            print this help text and exit
  -v, --version         print program version and exit
  **[COLOR="Red"]-u UN, --username=UN  account username[/COLOR]**
  **[COLOR="Red"]-p PW, --password=PW  account password[/COLOR]**
  -o TPL, --output=TPL  output filename template
  -q, --quiet           activates quiet mode
  -s, --simulate        do not download video
  -t, --title           use title in file name
  -l, --literal         use literal title in file name
  -n, --netrc           use .netrc authentication data
  -g, --get-url         simulate, quiet but print URL
  -e, --get-title       simulate, quiet but print title
  -f FMT, --format=FMT  video format code
  -m, --mobile-version  alias for -f 17
  -d, --high-def        alias for -f 22
  -i, --ignore-errors   continue on download errors
  -r L, --rate-limit=L  download rate limit (e.g. 50k or 44.6m)
  -a F, --batch-file=F  file containing URLs to download
  -w, --no-overwrites   do not overwrite files

```

So the syntax should be:

```
youtube-dl -u '**[COLOR="Red"]my username[/COLOR]**' -p '**[COLOR="Red"]my password[/COLOR]**' videoclip
```

If you are interested in exploring youtube-dl a little more I have written a guide that demonstrates how to update your copy of youtube-dl, manipulate the title of the downloaded file as well as capture the newer high quality videos available from youtube:

Mini guide: Download high quality youtube vids suitable for your phone ...
[http://ubuntuforums.org/showthread.php?t=1037760](http://ubuntuforums.org/showthread.php?t=1037760)

All the best,

Andrew

---

