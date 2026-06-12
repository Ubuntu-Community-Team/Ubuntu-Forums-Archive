---
title: "using grep to find large files"
date: 2010-10-22
forum: New to Ubuntu
---

### Post by mystmaiden on 2010-10-22
Ages back, I seem to remember someone advising a poster to use grep to check for large files that might be lurking on their computer (the hard drive was full when it shouldn't have been). I can not find the post anymore with the correct command. How would I use grep to search for files over 1 gig?

thanks
mystmaiden

---

### Post by ArgusVision on 2010-10-22
Actually, It's the **find** command. I'm looking through the **man** page to find a good string for that.

---

### Post by drs305 on 2010-10-22
My thread on finding lost disk space had a few:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

```
sudo find / -name '*' -size +1G

```

---

### Post by ArgusVision on 2010-10-22
I think it's something like  **sudo find / -size +2G** but my tests are a little abiguous...

---

### Post by ArgusVision on 2010-10-22
Fine drs305, make me look bad... :)
 ... what he said...

---

### Post by drs305 on 2010-10-22
> **ArgusVision said:**
> Fine drs305, make me look bad... :)
 ... what he said...

Ah heck, you could easily have come back with:
```
sudo find / -name '*' -size +1G | xargs ls -la | cut -d " " -f 5-10 | sort
```

---

### Post by ArgusVision on 2010-10-22
... or some other Chinese dialect... :)

Na. simple = good. (as long as it works...)

---

### Post by mystmaiden on 2010-10-23
It definitely works :) Thanks so much drs305 and you, too ArgusVision.

---

### Post by DaithiF on 2010-10-23
> **mystmaiden said:**
> Ages back, I seem to remember someone advising a poster to use grep to check for large files that might be lurking on their computer (the hard drive was full when it shouldn't have been). I can not find the post anymore with the correct command. How would I use grep to search for files over 1 gig?

thanks
mystmaiden

sounds like **find **probably is what you want, as the other posters have said.  but your question reminded me of this:
[http://ubuntuforums.org/showthread.php?t=1251827](http://ubuntuforums.org/showthread.php?t=1251827)
where grep is used to identify problem files in very specific case -- where the free space reported by the df command is less than should be the case based on the disk usage seen from the du command.  so just in case that was the post you were remembering.

---

