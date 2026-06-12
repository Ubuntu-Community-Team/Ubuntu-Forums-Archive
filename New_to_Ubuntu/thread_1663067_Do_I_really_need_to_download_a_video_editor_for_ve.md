---
title: "Do I really need to download a video editor for very basic editing?"
date: 2011-01-09
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-01-09
I have a video that I just want to delete parts of to shorten it. Do I need to download an editor to do this? If so, which one?

---

### Post by TeoBigusGeekus on 2011-01-09
No, you don't. You can use the most powerful editor out there that is already installed on your system: ffmpeg.
Let's say that you have a 2h movie and you want to dismiss the part from 1:00 to 1:30.
```
ffmpeg -i inputfile.extension -sameq -ss "00:00:00" -t "01:00:00" part1.extension
```
This command will take the first hour of the inputfile and produce a part1 file with the same quality as the inputfile.
```
ffmpeg -i inputfile.extension -sameq -ss "01:30:00" -t "02:00:00" part2.extension
```
This command will create the second part of your final movie (one and a half hour to two hours from your original one).

So, after all the above, you're left with two parts: part1.ext and part2.ext.
You can use mencoder to unite them
```
mencoder -oac copy -ovc copy -o FinalFile.ext part1.ext part2.ext
```
and you're done.

For more info, man ffmpeg and man mencoder.

---

