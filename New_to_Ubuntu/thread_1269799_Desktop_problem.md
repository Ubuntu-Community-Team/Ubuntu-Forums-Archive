---
title: "Desktop problem"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by Kinetic1001101 on 2009-09-18
I put this code in the command line to try and get the ability to have multiple desktop images and now every desktop is black and i can't even see or put icons on the desktop, even though they're still there but just unable to see them. Please tell me how to get my original settings back.    Thanks in advance!!

gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'
sudo gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'false'

---

### Post by mikewhatever on 2009-09-18
Running the same command with 'true' instead of false should do the job. I really don't think sudo was needed though.

---

### Post by Kinetic1001101 on 2009-09-22
> **mikewhatever said:**
> Running the same command with 'true' instead of false should do the job. I really don't think sudo was needed though.
Thanks I'll give that a try...

---

### Post by Kinetic1001101 on 2009-09-22
> **mikewhatever said:**
> Running the same command with 'true' instead of false should do the job. I really don't think sudo was needed though.
I tried that and this is what I got for an output...

me@my-laptop:~$ gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'true'
me@my-laptop:~$ sudo gconftool-2 --type string --set /apps/nautilus/preferences/show_desktop 'true'
[sudo] password for stall: 
me@my-laptop:~$ 

I tried it with just the first line as well / not including the sudo line and both just bring me back to my promt and the desktops are all still blacked out...  I hope we can figure this out, I would hate to have to reinstall.

Thanks again and in advance
-------

  	 	 	 	 	 	  A man is what he thinks about all day long. 
[COLOR=#0000ff]_[[COLOR=#00000a]Ralph Waldo Emerson[/COLOR]]("http://www.brainyquote.com/quotes/quotes/r/ralphwaldo108797.html")_[/COLOR]

---

