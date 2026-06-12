---
title: "multi-threaded download and cat"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by hammad1337 on 2009-09-11
I am trying to download an flv file from a video site using a script i made, which uses curl.
Problem is, when I cat those files, the complete file does not play. can anyone tell me what am I doing wrong?

Fyi, this is my script:

```

#!/bin/sh
echo "URL?"
read url
echo "File size? (Bytes)"
read size
export inc=`echo $size / 9 | bc`
export pos=1
for count in 1 2 3 4 5 6 7 8
do
export pos2=`echo $pos + $inc | bc`
curl -U user:pass -x 192.168.32.73:2222 --range $pos-$pos2 -o file.$count $url &
export pos=`echo $pos2 + 1 | bc`
done
curl -U user:pass -x 192.168.32.73:2222 --range $pos- -o file.9 $url &

```

and, this is how I cat the completed files:
```

hammad@1337-mash33n ~/scripts $ cat file.2 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.3 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.4 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.5 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.6 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.7 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.8 >> file.1
hammad@1337-mash33n ~/scripts $ cat file.9 >> file.1

```

---

### Post by scragar on 2009-09-11
Just a small comment, but why are you asking the user for the file size? Just use the -D flag do dump headers and get the file size from there...

And to cat all the files together:
```
cat file.{1..9} >> finishedResult.extention
```Much easier to write if you ask me.

There is also no need to call bc, bash has integer maths built in:
```
export inc=$(($size / 9));
...
export pos2=$(($pos + $inc));
```

---

