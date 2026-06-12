---
title: "script help"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by ozzyprv on 2010-06-07
I would like to copy some specific files from folder1 to folder2. I have the key piece of the name of the files I want to move in a "text" file.

Let say the files in folder1 are:
IMG_2234.JPG
IMG_2345.JPG
IMG_2367.JPG
IMG_2387.JPG
IMG_2456.JPG
IMG_2488.JPG
IMG_2591.JPG
(in reality there are thousands of files)

And inside names.txt I have this:
```
2234
2367
2591

```(note that there is only a piece of the filename within this list)

How do I automate the copying process?

Thank you.

PS: please let me know if there is a better place to ask this question.

---

### Post by kaibob on 2010-06-07
This will do what you want:

```
while read name ; do mv /folder1/IMG_${name}.JPG /folder2/ ; done < names.txt
```

If the names of the files in folder1 vary from the pattern shown in your post, you can use pattern matching:

[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)

---

### Post by ozzyprv on 2010-06-08
Worked really well.

Thanks.

---

