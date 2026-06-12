---
title: "Shell script - getting stuck!"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by MaxVK on 2010-09-23
Hi. I'm trying to get into shell scripting by creating a little startup script for an often repeated task:

I want to start xampp, start geany, then start firefox pointing at localhost.

However, this is not what happens! Instead I get to type my password for xampp (Which is started with sudo), then geany opens and the script stops until geany is closed, at which point firefox helpfully opens.

I'm sure this is really simple but while Google throws back lots of stuff, none of it seems to answer the question!

So! How can I get the script to run these three commands and then exit?

Ultimately Id like to be able to run this from a desktop launcher, so any information in that regard would be great too.

Cheers

Max

---

### Post by mcduck on 2010-09-23
Just add a "&" to the end of a command and the commamnd will be executed in background, allowing the script to progress to next command before the previous one has finished.
Like this:

```
#! /bin/sh

command1 &
command2 &
command3 &
```

---

### Post by MaxVK on 2010-09-23
Thanks, that sorted things out.

As far as running from a desktop launcher I'm guessing I create one, set it to run in terminal and then point it at the script?

Cheers

Max

---

### Post by da burger on 2010-09-23
Depends. If you set it to run in a terminal a terminal will open while the script is running. If you don't then it will run in the background.

---

### Post by mcduck on 2010-09-23
> **da burger said:**
> Depends. If you set it to run in a terminal a terminal will open while the script is running. If you don't then it will run in the background.

+1 to this.

Of course you'll need to use gksudo instead of sudo for launching XAMPP if you don't execute the script in a terminal, but other than that there really shouldn't be any difference.

---

### Post by MaxVK on 2010-09-24
Thats excellent guys, thanks for your help, its all working nicely now.

Cheers

Max

---

