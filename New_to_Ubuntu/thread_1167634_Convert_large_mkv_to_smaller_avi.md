---
title: "Convert large mkv to smaller avi"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-05-23
So, I have many large mkv files ranging from 4gb to about 12gb. I don't need such great quality, but I've noticed that converting them down to about 2gb avi is good enough for me. I used avidemux to do this. Unfortunately it took a LONG time. I was wondering if there was a quicker way to do this, and also what settings should I be using? For a 1 hr 48 min movie I told it to do: Two Pass, "Max Size = 1800mb". But I just chose that at random. Are there any set specifications? For that long a movie should I be aiming for a certain size? No experience with this so any help would be much appreciated.

Thanks!

---

### Post by MegaJim on 2009-05-23
If quality isn't a big problem you can try converting a short (1 minute) clip of your data into avi with a single pass and compare it to the two pass version, obviously a single pass will take a lot less time, but video encoding is a computationally demanding process.

---

### Post by abhiroopb on 2009-05-23
any advice? I'm just thinking of doing something along the lines of 15mb = 1min...?

---

### Post by MegaJim on 2009-05-23
Depends on the resolution of the file, but for something 600x350 (roughly tv quality) 7-8mb per minute is plenty.

---

### Post by abhiroopb on 2009-05-23
ok, well the options I use:

Video: MPEG-4 ASP (Xvid4)
Configure
Encoding Type:
Two Pass: Video Size
Then I set the size

The one pass has "Bitrate", and "Quantizer", can I use either? I'd rather do it quickly, but keep the file small as well.

---

### Post by lovinglinux on 2009-05-23
> **abhiroopb said:**
> ok, well the options I use:

Video: MPEG-4 ASP (Xvid4)
Configure
Encoding Type:
Two Pass: Video Size
Then I set the size

The one pass has "Bitrate", and "Quantizer", can I use either? I'd rather do it quickly, but keep the file small as well.

Since you are using Xvid4 you could try using the Turbo mode option to speed up the encoding. I prefer to encode using MPEG-4 ASP (lavc), which is faster in my opinion. I don't like to use the Quantizer. I prefer to set the bitrate manually. If I'm encoding a good quality video source like you probably have, then a lower bitrate like 1500 won't affect the output quality that much, but if the source is not that good, then I prefer to use higher values like 4000. The grater the bitrate, the bigger will be the encoded video size and the quality will be better. You need to make some tests and check what is acceptable quality for you. 

I do prefer to use single pass. Last time I converted a video of 1:30 hrs recorded from my TV card, it took 6 hours to convert it. I was experiencing issues tho, because converting on Hardy was much faster. I guess it should take about 2 to 3 hours max.

BTW, you could use the "Resize" filter and shrink the video to 624x352. This will help to keep the file size small.

---

### Post by abhiroopb on 2009-05-23
thanks a lot for the help. Keen to try it out, but right now I can't really leave my computer going for so long :P! But I shall keep it in mind!

---

