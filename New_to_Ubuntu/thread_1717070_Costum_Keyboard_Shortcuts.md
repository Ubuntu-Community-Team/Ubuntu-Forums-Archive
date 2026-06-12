---
title: "Costum Keyboard Shortcuts"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by buren on 2011-03-29
Im trying to assign some keyboard shortcuts to some programs that i use frequently.. It was no problem setting up i.e Chrome launcher to a shortcut. On the other hand if Chrome is running already and i press my assigned shortcut it just opens another browser instead of (as in WIN7) it show the already opened browser... 

Is there a way to maybe assign the keyboard shortcut to a file with a small script in it where it checks whether i've an open browser or not. So if a browser is opened show the window otherwise open a new browser. Like a simple if / else... 

Thanks

---

### Post by kaibob on 2011-03-30
Have a look at the shell script in post 10 in the following thread:

[http://ubuntuforums.org/showthread.php?t=1244309](http://ubuntuforums.org/showthread.php?t=1244309)

This script uses the wmctrl utility to identify application windows, and it does this by way of the window title. I don't use the chrome browser, but if I understand correctly this browser has an option to hide the title bar. If you have enabled this option, the shell script probably won't work.

By way of example, the following is the shell script I use to start firefox:

```
#!/bin/sh

wmctrl -a "Mozilla Firefox" || firefox &
```

---

### Post by buren on 2011-03-30
Thanks got it to work peftectly with another shell script

```

#!/bin/bash

#check if Chromium is open, if so, give it focus, else open Chromium

chromwin=`wmctrl -l | grep -m 100 -o "Google\ Chrome"`
if [ $chromwin ="Google\ Chrome" ];
	then
		wmctrl -R Google\ Chrome
	else	
		/opt/google/chrome/google-chrome &
fi

```

---

### Post by kaibob on 2011-03-30
> **buren said:**
> Thanks got it to work peftectly with another shell script

```

#!/bin/bash

#check if Chromium is open, if so, give it focus, else open Chromium

chromwin=`wmctrl -l | grep -m 100 -o "Google\ Chrome"`
if [ $chromwin ="Google\ Chrome" ];
	then
		wmctrl -R Google\ Chrome
	else	
		/opt/google/chrome/google-chrome &
fi

```

I'm glad you got things working as you want, but I thought I would add a few comments about the shell script in your post. There is no reason I can see to pipe the output of wmctrl -l through grep--all it appears to do is slow and unnecessarily complicate the shell script. Unless I'm missing something, your shell script is functionally equivalent to:

```
wmctrl -R "Google Chrome" || /opt/google/chrome/google-chrome &
```

Or, if you prefer to use the if command:

```
#!/bin/bash

if ! wmctrl -R "Google Chrome" ; then
  /opt/google/chrome/google-chrome &
fi
```

For other forum members who may use one of these shell scripts, the difference between the -a and -R wmctrl options, as stated in this utility's man page, are:

-a <WIN> Switch to the desktop containing the window <WIN>, raise the window, and give it focus.

-R <WIN> Move the window <WIN> to the current desktop, raise the window, and give it focus.

Anyways, just as a matter of reference and for additional discussion on this topic, the shell script in the OP's post is from post 8 in the following thread:

[http://ubuntuforums.org/showthread.php?t=1680571](http://ubuntuforums.org/showthread.php?t=1680571)

---

### Post by buren on 2011-03-31
thanks, i've changed it know as goos as the other script...

---

