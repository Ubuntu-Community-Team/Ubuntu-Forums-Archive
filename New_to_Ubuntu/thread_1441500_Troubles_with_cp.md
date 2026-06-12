---
title: "Troubles with cp"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2010-03-28
Hi all,
I'm having a bit of an issue with the cp command. 

I have the following bash script:

#!/bin/bash

sourceDir="/home/cmhughes/pcc/"
destinationDir="/media/KINGSTON/community colleges/PCC/"

cp -ur "${sourceDir}math 111c/"* "${destinationDir}math 111c"
cp -ur "${sourceDir}math 253/"* "${destinationDir}math 253"

I had hoped that it would only copy the updated versions of the files from the source directory to the destination directory, but so far it copies every file, every time. 

If anyone has any ideas, I would be most grateful.

---

### Post by Brandon Williams on 2010-03-29
That's exactly what the -u flag is for, and on my system, it works as expected. What makes you say that it copies every file? Are you running cp -vur to get a verbose listing of the activities? And are you certain that the mod times on the files being copied really are older than the mod times of the files being overwritten?

---

### Post by C. M .Hughes on 2010-03-29
Thanks for your response. Yes, I had previously used the command with -uvr but stopped because there was so much output- some of the directories have a lot of files, and a lot of sub directories. 

I'm certain that the mod times are exactly the same. I am copying from my Ubuntu file system onto a USB- is it a file system issue?

---

### Post by C. M .Hughes on 2010-05-26
If anyone has any ideas, I'd love to hear them, this problem is driving me nuts. 

I've tried all the commands I can think of to compare the directories, but would love to hear suggestions.

Many thanks.

---

### Post by CharlesA on 2010-05-26
If you want to copy just files that are updated, I would suggest using rsync instead of cp.

What file system is the USB drive using?

Also, it looks like your script is weird, is there a reason for the variable being surrounded by "{}"?

```
#!/bin/bash

SOURCE="/home/cmhughes/pcc/"
DESTINATION="/media/KINGSTON/community colleges/PCC/"

rsync --recursive $SOURCE"math 111c/"* $DESTINATION"math 111c/"
rsync --recursive $SOURCE"math 253/"* $DESTINATION"math 253/"
```

You can also add the --itemize-changes switch to see what files it is working with.

---

### Post by C. M .Hughes on 2010-05-27
Thanks for your response CharlesA. 

The USB is FAT32. 

I have tried the code below, and added the v flag so that I could see what was happening. It still copies almost every file every time I run it. 

Just to clarify: I was hoping it would only copy updated or new files. I'm guessing it's a file system issue, but have no idea what to check.


#!/bin/bash

sourceDir="/home/cmhughes/pcc/"
destinationDir="/media/KINGSTON/community colleges/PCC/"


rsync -rv "$sourceDir""math 111c/"* "$destinationDir""math 111c/"

---

### Post by C. M .Hughes on 2010-09-19
Not sure if anyone is still reading this thread, but I have a bit of an update.

I think it was a timestamp issue on the USB (FAT 32) disk that I was copying to. 

After some reading, I modified my script- here is a sample line:

```

rsync -uvrt --modify-window=1 "${sourceDir}math 251/"* "${destinationDir}math 251/"
```

I'll be testing it a lot over the next few days- if it works consistently then I'll mark the thread as solved.

---

### Post by CharlesA on 2010-09-19
I ran into a similar problem when I was using robocopy to backup files from a window machine to a linux one.

By using --modify-window, you should get past the problem with the time stamps.

---

