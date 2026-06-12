---
title: "bash script with a popup"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-04-04
Hi All,

I've been playing with Ubuntu for a little over six months and I like it a lot.

Every once in a while I move large files from my internal harddrive to an external drive.

I've been doing this with the mv command.

I was wondering is there a way to run that as a script but have the script popup asking me the name of the file I want to move?

So that I could just type that in and let it go?

Does that make sense?

---

### Post by nothingspecial on 2011-04-04
For a gui popup have a look at zenity, if you just want a question in the terminal use read.

---

### Post by kerry_s on 2011-04-04
Use zenity in your script.

example:
```
#!/bin/sh
from=`zenity --entry --text="from" `
to=`zenity --entry --text="to" `
mv $from $to
zenity --info --text="mv $from $to"

```
something like that, i'm on my android tablet so can't test.

---

### Post by GrouchyGaijin on 2011-04-04
Thanks guys,

I'll give Zenity a try tonight.

---

### Post by kerry_s on 2011-04-04
> **GrouchyGaijin said:**
> Thanks guys,

I'll give Zenity a try tonight.

tested that script it works, you need to use full path.
example:
/home/you/file-or-folder
not
~/file-or-folder

---

### Post by GrouchyGaijin on 2011-04-04
Pretty cool how you plucked that out of thin air.

Thanks!

---

