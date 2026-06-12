---
title: "converting mp3's etc. to ogg"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-05-15
is there an easy way to convert all my mp3's and such to .ogg?

---

### Post by nhasian on 2009-05-15
i searched the repositories for lines that contained both mp3 and ogg with this command:

```
apt-cache search ogg | grep mp3
```

and i found:

mp32ogg - Converts MP3 file to Ogg Vorbis

you can install it with:

```
sudo apt-get install mp32ogg
```

or by clicking this link: [mp32ogg]("apt://mp32ogg")

---

### Post by LunaticHiatus on 2009-05-15
many thanks

---

### Post by ad_267 on 2009-05-15
Applications - Add/Remove - [Sound Converter]("apt://soundconverter")

---

### Post by andrew.46 on 2009-05-18
Hi LunaticHiatus,

A fully equipped SoX can do this:

```
sox infile.ogg outfile.mp3
```

and is very easy to script. Plenty of options available as well if you want to dig into the unusually comprehensive man pages.

Andrew

---

### Post by Ms_Angel_D on 2009-05-18
> **ad_267 said:**
> Applications - Add/Remove - [Sound Converter]("apt://soundconverter")

+1 Sound Converter is great!

---

### Post by gali98 on 2009-05-18
You could also check out ffmpeg...
Kory

---

### Post by juancarlospaco on 2009-05-18
Nice idea!, unlock your music...

---

### Post by Volt9000 on 2009-05-18
> **andrew.46 said:**
> Hi LunaticHiatus,

A fully equipped SoX can do this:

```
sox infile.ogg outfile.mp3
```

and is very easy to script. Plenty of options available as well if you want to dig into the unusually comprehensive man pages.

Andrew

+1 for SoX
Excellent little program I discovered recently, works very well.

The only complaint I have is that by default it's not compiled with mp3 write support.

---

### Post by ad_267 on 2009-05-18
> **Volt9000 said:**
> +1 for SoX
Excellent little program I discovered recently, works very well.

The only complaint I have is that by default it's not compiled with mp3 write support.
Easy to fix:

sudo apt-get install libsox-fmt-all

---

