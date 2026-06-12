---
title: "join mp3's simply"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by stoppage on 2009-09-05
Hi I looking for a simple GUI app. to join mp3's, but without losing quality. Ubuntu 8.04 & I already have Audacity. Obliged for any help here

---

### Post by Liolikas on 2009-09-05
Audacity is the best.

---

### Post by stoppage on 2009-09-05
Thought as much

---

### Post by Sealbhach on 2009-09-05
You can do it at the command line as well:

```

cat first.mp3 second.mp3 > joined.mp3
```

You can join most files like that.

.

---

### Post by Shampyon on 2009-09-08
Adding to Sealbhach's reply:

If your MP3's are all numerically named and zero padded (eg: 01.mp3, 02.mp3 etc) you can navigate to the directory
```
cd /path/to/directory
```
and combine them all at once with this command:
```
cat *.mp3 > joined.mp3
```

Remember, that will combine every MP3 in that directory in order, so make sure your MP3s are properly separated/categorised, eg: don't have *01 - Music Track.mp3* in the same folder as *01 - Other Music Track.mp3* in the same folder, or it'll combine them both into the same file in alphanumeric order (first *01 - M...* then *01 - O...*).

---

