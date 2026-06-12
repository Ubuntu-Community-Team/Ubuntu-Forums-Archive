---
title: "Stopmotion Problems"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by Canobuntu on 2009-03-27
I have been struggling with Stopmotion and having got it working, I thought it would be good to list what worked for me, here.

a) The first problem was that when I imported .jpg files they showed as a blank image. After a lot of head scratching I worked out that Stopmotion does not like special characters in file names or paths. My Canon camera calls its files IMG_000234.JPG - The "_" was causing problems with the file import. Also, I had put the files in a directory called "Working Files" and the space in the directory name also caused it to fail.

Once the file name and path name issues had been addressed Stopmotion burst into life and started displaying images as advertised.

b) When I came to create a video it again failed. I played with the codecs, and installed mancodec which got me a long way towards the answer, but still no success. This problem turned out to be capitalisation of the .jpg in the file name. Stopmotion seems to save the images in a temporary directory, with a new file name 000001, 000002 etc, but keeps the original extension. So if the original file has the extension .JPG (as my Canon files did) then the resultant files in the directory were 000001.JPG etc. However, the mancodec driver was looking for *.jpg, and so found no files.

The fix is to change the original files to xxxx.jpg. and the mancodec video encoder bursts into life.

Thats it, so far. Hope this is helpful.

:)

---

### Post by unutbu on 2009-03-27
Thanks for sharing this information. Perhaps you'd find this useful:

There is a way to set up a special directory so that whenever you download pictures into the special directory, the files automatically get renamed (without underscores and with lowercase '.jpg').

For instructions on how to do it, see [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)

The script you would want to use is 
```

#!/bin/sh
cd /path/to/special/dir
rename 's/(.*)_(.*).JPG$/$1$2.jpg/' *

``` (Save it as ~/bin/rename_image.sh)
and the .dirmon config file would be
```

path: /path/to/special/dir
event: file_created
command: ~/bin/rename_image.sh
filter: .JPG$
```

---

