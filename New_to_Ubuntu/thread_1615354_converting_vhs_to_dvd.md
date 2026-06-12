---
title: "converting vhs to dvd"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by lmm5247 on 2010-11-06
quick question.

i just converted my old home movies on vhs to dvd using a standalone converter. now i need to rip the dvds to my computer.
1)what program can i use to do that?
2)what format should i put the movies in?
3)what program can i used to do some basic editing?

thank you in advance =)

---

### Post by waynefoutz on 2010-11-06
> **lmm5247 said:**
> quick question.

i just converted my old home movies on vhs to dvd using a standalone converter. now i need to rip the dvds to my computer.
1)what program can i use to do that?
2)what format should i put the movies in?
3)what program can i used to do some basic editing?

thank you in advance =)

I can't help much with the editor, editing is not my thing. But for ripping, I use DVD::rip. It will rip the file, then you can go to the transcode tab on the program and convert it to an .avi file to the size of your choosing. The rip process takes about ten minutes for a full length movie, and the transcoding usually takes about an hour for a 2 hour movie.

---

### Post by syntr on 2010-11-06
1) Use dvdrip. It's in the repositories.
2) OGG! But it doesn't really matter, I suppose, as long as you have the package ubuntu-restricted-extras.
3) A great program called Pitivi Video Editor is included in Ubuntu 10.10 by default.

---

### Post by ieee488 on 2010-11-06
> **lmm5247 said:**
> quick question.

i just converted my old home movies on vhs to dvd using a standalone converter. now i need to rip the dvds to my computer.
1)what program can i use to do that?
2)what format should i put the movies in?
3)what program can i used to do some basic editing?

thank you in advance =)

What do you mean by standalone converter?
A DVD recorder made by JVC, Panasonic, Toshiba, etc or something else?

---

### Post by lmm5247 on 2010-11-07
> I can't help much with the editor, editing is not my thing. But for ripping, I use DVD::rip. It will rip the file, then you can go to the transcode tab on the program and convert it to an .avi file to the size of your choosing. The rip process takes about ten minutes for a full length movie, and the transcoding usually takes about an hour for a 2 hour movie. 
i will definitely look into dvd::rip, thanks for the suggestion.

> 1) Use dvdrip. It's in the repositories.
2) OGG! But it doesn't really matter, I suppose, as long as you have the package ubuntu-restricted-extras.
3) A great program called Pitivi Video Editor is included in Ubuntu 10.10 by default. 
i was considering ogg. thing is, my parents will be using a windows pc to watch this, so i need something that will just work. will ogg do that? 

> What do you mean by standalone converter?
A DVD recorder made by JVC, Panasonic, Toshiba, etc or something else? 
and yes, its a toshiba. you just pop in a tape and a dvd and basically hit go.

---

### Post by waynefoutz on 2010-11-07
Another option is to watch the DVD with VLC. If you click on "view" and then "advanced controls" it will put a record button on VLC. Then as you watch the movie it will write an .avi file into your home folder.

---

### Post by ieee488 on 2010-11-07
I have two DVD recorders - a JVC and a Magnavox.

Once video is recorded to a DVD, that DVD should have a DVD-Video file directory structure.

You need to read up and understand what you have. 
[http://club.myce.com/f62/tutorial-dvd-video-file-structure-77646/](http://club.myce.com/f62/tutorial-dvd-video-file-structure-77646/)

I work the video files from the DVD recorder in Windows XP. Once the files are ripped to my PC's hard drive, I use a Windows program called TMPGEnc DVD Author to edit out unwanted parts of the video. Once the edits are done, I reauthor the DVD again using the same program. The edits are not frame accurate but close enough for my needs. I can do this all without having to re-encode the entire DVD.

If you want to stay with UBuntu,
Avidemux can edit VOB files. Not sure whether it will force you to have to re-encode the entire DVD.

After you edit the VOB files, you will need to re-author your DVD.
[https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

---

### Post by lmm5247 on 2010-11-07
> Another option is to watch the DVD with VLC. If you click on "view" and then "advanced controls" it will put a record button on VLC. Then as you watch the movie it will write an .avi file into your home folder. 

that seems pretty straight forward. i'll probably try this and dvd::rip and see which i like better.

> I have two DVD recorders - a JVC and a Magnavox.

Once video is recorded to a DVD, that DVD should have a DVD-Video file directory structure.

You need to read up and understand what you have.
[http://club.myce.com/f62/tutorial-dv...ructure-77646/](http://club.myce.com/f62/tutorial-dv...ructure-77646/)

I work the video files from the DVD recorder in Windows XP. Once the files are ripped to my PC's hard drive, I use a Windows program called TMPGEnc DVD Author to edit out unwanted parts of the video. Once the edits are done, I reauthor the DVD again using the same program. The edits are not frame accurate but close enough for my needs. I can do this all without having to re-encode the entire DVD.

If you want to stay with UBuntu,
Avidemux can edit VOB files. Not sure whether it will force you to have to re-encode the entire DVD.

After you edit the VOB files, you will need to re-author your DVD.
[https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

thank you for the article, definitely cleared things up.

---

### Post by MrWES on 2010-11-07
> **lmm5247 said:**
> quick question.

i just converted my old home movies on vhs to dvd using a standalone converter. now i need to rip the dvds to my computer.
1)what program can i use to do that?
2)what format should i put the movies in?
3)what program can i used to do some basic editing?

thank you in advance =)

Without losing quality; put the DVD in the drive, open a terminal and type 
```
vobcopy -l
``` lower case -L

Bill

---

### Post by stmiller on 2010-11-07
[http://handbrake.fr/](http://handbrake.fr/)

:)

---

### Post by lmm5247 on 2010-11-07
> Without losing quality; put the DVD in the drive, open a terminal and type
Code:

```
vobcopy -l
```

lower case -L

Bill 
what will vob copy give me? one big avi file? or just a vob file? can i edit it after it is copied?

also, what format should i use? i feel like avi is old and nobody uses it. handbrake supports mp4, is that a good direction to go in?

---

### Post by waynefoutz on 2010-11-07
> **lmm5247 said:**
> that seems pretty straight forward. i'll probably try this and dvd::rip and see which i like better.





Personally, I prefer dvd::rip. You can control the size and quality of the avi file.

---

### Post by lmm5247 on 2010-11-13
here's my current status. i couldn't get dvd::rip to work, nor could i get acidrip or thoggen to work. so i used handbrake to make an m4v file.

so now i need to divide the movie into chapters. do i do that in video editing software, or in dvd authoring software?

thank you in advance =)

---

