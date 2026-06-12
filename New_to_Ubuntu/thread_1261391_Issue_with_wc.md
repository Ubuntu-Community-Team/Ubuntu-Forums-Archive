---
title: "Issue with wc"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by j.bell730 on 2009-09-08
I'm using this command in a bash script:
```
wc -l /home/jared/Scripts/Output/bands.txt
```
However, the output includes the path, like this:
```
171 /home/jared/Scripts/Output/bands.txt
```

Is it possible for me to only display the line count and not the path?

---

### Post by Volt9000 on 2009-09-08
Filter the output through cut, thusly:

```

wc -l /home/jared/Scripts/Output/bands.txt | cut -d ' ' -f 1

```

That's a number one after the f, not a lowercase L.

What cut does is delimit lines for you. The first parameter " -d ' ' " tells cut to use the space character as a delimiter. The second parameter " -f 1" tells cut you only want field #1.

---

### Post by j.bell730 on 2009-09-08
Thanks, it works!

---

