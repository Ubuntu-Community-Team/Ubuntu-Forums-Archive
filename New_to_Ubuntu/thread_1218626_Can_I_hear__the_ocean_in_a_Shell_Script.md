---
title: "Can I hear  the ocean in a Shell Script?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by lile001 on 2009-07-20
Hurrah! I just wrote my first shell script that did something other than say "hello world".  I used to be pretty handy with .bat files in the DOS world back when that was a marketable skill, and now I'm back to being a lowly n00b. :shock:

What my little script accomplishes is to change permissions on a directory that both me and me sweetie share, that allows both of us (everyone in the group "users" to be exact) to access our common stuff.   Generally, when one of us puts something there, it isn't available for use by the other of us because the first one is the "owner" and everyone else is locked out by default. The script fixes this. 

I'm sure there are 100 better ways to accomplish this but I chose to learn a little about scripts in the process.  

OK, when I run my script, I'd like it to pause in Terminal long enough for me to see that it did it's dirty work - say "ls -l" and display the relevant files so that I can tell it worked. 

is there a "pause" or something like that?

---

### Post by llamabr on 2009-07-20
I'm not sure I fully understand the question, but there's sleep, which will sort of pause for a moment.  You could also put it in the background.

If you like, post your script, and say what you want it to do, and we'll show you where to go next.

---

### Post by utnubuuser on 2009-07-20
notify on completion

---

### Post by slakkie on 2009-07-21
for pause, use sleep $seconds_to_sleep, or just do a read.

eg

```

#!/usr/bin/env bash

ls -l
read

echo "continued"

```

You might want to look here: 
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
[http://www.opensolaris.org/os/community/on/shellstyle/](http://www.opensolaris.org/os/community/on/shellstyle/)
[http://www.bashscripts.org/](http://www.bashscripts.org/)

---

