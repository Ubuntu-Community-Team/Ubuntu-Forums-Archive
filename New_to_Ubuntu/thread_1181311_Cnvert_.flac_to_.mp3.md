---
title: "Cnvert .flac to .mp3"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-06-07
I have a bunch of .flac music files and I would like to convert them into .mp3.

I have used Sound Converter and set it to:

VBR
"Insanely High" (which shows the average conversion rate to be 320kbps)

After conversion when I check the bitrate it is between 100kpbs to 150kbps.

I downloaded the flac files from the net.

Should the final bit-rate be that low?

---

### Post by roquefilipe on 2009-06-07
it depends on the sounds embeded in the files. If they aren't very complex, then they don't need high bitrates, and the software chooses the best bitrate. 

just listen to the files. If they sound nearly as good as the original .flac files, then you are ok

---

### Post by abhiroopb on 2009-06-08
Unfortunately I don't have my "good" speakers with me, and currently only able to use my laptop headphones and without doing a thorough test of ALL the songs it would be difficult to see whether the quality is nearly as good or not.

But looking at the bitrate isn't it very low? I mean 100-150kbps seems VERY low.

Also, these flac files are part of a Jazz album, which should have been recorded at a high quality.

Could it be that the source I downloaded them from upconverted them to flac? Perhaps thats why when it is converting them back the quality is quite low.

---

### Post by Efros on 2009-06-08
Try using a CBR setting, I may get some flac(heheh) for this but I really dislike VBR and have had a lot of issues with it with non computer play.

---

### Post by MrWES on 2009-06-08
> **abhiroopb said:**
> I have a bunch of .flac music files and I would like to convert them into .mp3.

I have used Sound Converter and set it to:

VBR
"Insanely High" (which shows the average conversion rate to be 320kbps)

After conversion when I check the bitrate it is between 100kpbs to 150kbps.

I downloaded the flac files from the net.

Should the final bit-rate be that low?

Try this thread 
[http://ubuntuforums.org/showthread.php?t=84178]("http://ubuntuforums.org/showthread.php?t=84178")

And this simple code should work:
```
flac -d -c infile.flac | lame - outfile.mp3
```

Bill

---

### Post by abhiroopb on 2009-06-08
The script provided by GrammatonCleric in that thread works wonders :)! Thanks!

---

