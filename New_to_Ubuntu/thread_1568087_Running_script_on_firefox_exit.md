---
title: "Running script on firefox exit"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-09-04
Hi. I am trying to figure out if anyone knows a way, either through firefox, or GNU/Linux, to make a script run whenever firefox is closed.

---

### Post by apmcd47 on 2010-09-04
You probably want a wrapper:
```

firefox
wait $(pgrep firefox)
exec firefox_finished

```
where *firefox_finished* is the name of the script you want to run. Call the script something like *myfirefox*. Make sure both are executable and both in your *$PATH* (preferably in *$HOME/bin*).

Caveats: firefox forks. How this affects your program I don't know. *pgrep* will return the pid for every instance of a program with firefox as part of its name. You will have an instance of this wrapper for every invocation of your wrapper. This could result in multiple copies of *firefox_finished* being run. Consider this a starting point.

Andrew

---

### Post by Ozymandias_117 on 2010-09-04
> **apmcd47 said:**
> You probably want a wrapper:
```

firefox
wait $(pgrep firefox)
exec firefox_finished

```
where *firefox_finished* is the name of the script you want to run. Call the script something like *myfirefox*. Make sure both are executable and both in your *$PATH* (preferably in *$HOME/bin*).

Caveats: firefox forks. How this affects your program I don't know. *pgrep* will return the pid for every instance of a program with firefox as part of its name. You will have an instance of this wrapper for every invocation of your wrapper. This could result in multiple copies of *firefox_finished* being run. Consider this a starting point.

Andrew

```

#!/bin/bash

exec ./opening_script &

firefox &

while [ `pidof firefox` ]
do
wait `pidof firefox`
done

exec ./closing_script
```

Edit: This works if I run it from the command line, but if I try to run it from a custom launcher, (either running as an "application" or an "application in terminal") it doesn't work. Any ideas?

---

### Post by Ozymandias_117 on 2010-09-04
Alright, I figured it out. I needed to use full pathnames. Because of how the menu runs it, it was running in ~ instead of ~/customfox

---

