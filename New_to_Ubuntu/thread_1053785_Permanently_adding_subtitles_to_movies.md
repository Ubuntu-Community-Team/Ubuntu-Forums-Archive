---
title: "Permanently adding subtitles to movies"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by adobrakic on 2009-01-29
Are there any programs that can do this?

---

### Post by alenis on 2009-01-29
You can convert the movie to a DVD adding subtiles. I never tried that in Ubuntu but it seems that manDVD (not in the repository) should allow you to do that.

---

### Post by binbash on 2009-01-29
Avidemux does this, correct me if i am wrong.

---

### Post by Circus-Killer on 2009-01-29
i'm sure k9copy will let you do this. but if you cant do it in k9copy and cant find another program that can, i recommend using handbrake to create xvid copies of the movie, cos then you can select the subtitle you want in the xvid.

---

### Post by adobrakic on 2009-01-30
> 
You can convert the movie to a DVD adding subtiles. I never tried that in Ubuntu but it seems that manDVD (not in the repository) should allow you to do that.


Will the extension be .avi or .wmv? My xbox can only detect those filetypes, unfortunately.

> 
Avidemux does this, correct me if i am wrong.


I, honestly, have absolutely no idea how to use Avidemux. I have it on my system, but I can't even begin to comprehend it.

> 
i'm sure k9copy will let you do this. but if you cant do it in k9copy and cant find another program that can, i recommend using handbrake to create xvid copies of the movie, cos then you can select the subtitle you want in the xvid.


i'll try handbrake then, thanks

---

### Post by Sup3r3g0 on 2009-01-30
Sorry to highjack your thread, but does anyone know how to actually create your own subtitles for a movie?

---

### Post by slinkey1981 on 2009-01-30
OP, DeVeDe will allow you to do this, but it will convert it to .iso for burning.


> **Sup3r3g0 said:**
> Sorry to highjack your thread, but does anyone know how to actually create your own subtitles for a movie?

Yes, you can do it with the following;

1. create a document.

2. Edit it (basically) as follows.

```
1
00:45:12,750 --> 00:45:32,750
I will kicka you ina da face!
```

This will tell the file that the first subtitle,
```
1
```

will display between
```
00:45:12,750 --> 00:45:32,750
```
in HH:MM:SS,SSS format.


and will read
```
I will kicka you ina da face!
```

Each line you want to add is in sequence 1,2,3,4,5....

When you are finished, change the file extension to .srt.

---

### Post by Sup3r3g0 on 2009-01-30
thanks

---

