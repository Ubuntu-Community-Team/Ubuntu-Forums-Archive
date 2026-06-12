---
title: "copy script does not complete when run as scheduled task"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by corkscrew on 2009-01-25
I have written my 1st script in ubuntu to copy all my data files from one hd to my backup hd. here's the script
```
cp -dpRuvx /data/user /media/sata2-data/usercopy
```

The script runs perfectly if I run it by double clicking and selecting run.

However if I run it as a scheduled task it only copies 1 dir level down,
for example if I have DIR1 which has 3 directory's below DIRA DIRB DIRC. It will only copy DIR1 and DIRA and omit the other 2 

Can anyone help?

---

### Post by cmnorton on 2009-02-14
-r is copy directories and what is in them. 

I would run this script without scheduling it, and play around with what happens.

Also, you are using -d. I am assuming you do not want to traverse links. 

Another thing to consider is using find, and pipe that into cp right in the find -exec parameter.

---

### Post by KIAaze on 2009-02-15
You might also want to use "rsync" for backing up.
I'm not a pro with rsync, but this worked well for me:
```
rsync -avZ source/data dest/data
```

It's strange that your copy command doesn't work with crontab.
Have you made sure that the script is executable? (chmod +x ./script.sh)
Have you tried entering the command directly in crontab instead of using a script?

---

### Post by cmnorton on 2009-02-15
Also knowing how you created the shell script helps Having been used to Red Hat, I had to use the explicit #!/bin/bash at the beginning of all my scripts, because they run on Ubuntu and Red Hat.

I agree with the rsync suggestion. It's used quite handily for backups.

What ever you choose to do, I would pursue finding out why this isn't working for you, just so it's not one of those we sometimes fix with a "shotgun" approach, not knowing how it was really fixed.

---

