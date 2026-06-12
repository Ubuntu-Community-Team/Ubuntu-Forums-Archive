---
title: "i can't access /Music/Band Name/Ablum Title/song.mp3 using the shell."
date: 2011-01-05
forum: New to Ubuntu
---

### Post by beginningGimp on 2011-01-05
When using the shell, i can't access the directory /Matchbox Twenty/.  I think it has something to do with the space between Matchbox and Twenty.  It like the shell looks at Matchbox Twenty as two directories.  Is there a simple solution to this issue?  Is there something I need to do to the Environment Variables?  Does anyone have a simple script, i could run to eliminate the spaces in my music folder? I don't know what I should do at this point.

I have been using ubuntu for about a month.  The first thing i did was copy my music collection to /Places/Music.  Then I have been using Rythm Box to play my music. 

 I also am taking a shot at learning the shell to reduce the demand on my resources.  I am experimenting with mpg321 and sox.  And up and coming in the book will be alsamixer,  aumix, oggenc, commands.  But, im no guru though.

---

### Post by b0b138 on 2011-01-05
Yes, it is the space. It must be typed in like
```
 /home/user/Music/Album\ Title/song.mp3
```
or in quotations
```
 "/home/user/Music/Album Title/song.mp3"
```

You can also hit the "Tab" key while typing and it will start to auto complete for you

---

### Post by beginningGimp on 2011-01-05
Thanks a million.  I didn't expect a rapid and effective solution.  I was able to fly through the directories at command.

---

