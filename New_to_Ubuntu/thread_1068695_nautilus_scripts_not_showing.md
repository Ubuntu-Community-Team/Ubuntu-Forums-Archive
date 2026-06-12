---
title: "nautilus scripts not showing"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-02-13
I have installed the audio converter script for nautilus from the repos and restarted my computer, but when i right click on a sound filethe option for scripts is not shown - what am I missing.

---

### Post by jou770d on 2009-02-13
This thread should help you:
[http://ohioloco.ubuntuforums.org/showthread.php?p=4054318#post4054318](http://ohioloco.ubuntuforums.org/showthread.php?p=4054318#post4054318)
This post in particluar is what you're looking for:
[http://ohioloco.ubuntuforums.org/showpost.php?p=4054318&postcount=3](http://ohioloco.ubuntuforums.org/showpost.php?p=4054318&postcount=3)
Don't forget that you'll also have to download the neccessary codecs for the convertion to work.

Edit:
Here's a simple trick to find out what codec you need:
Create an empty document, rename it and add the extension you want to convert to/from. Use the script and it will give you an error with the name of the missing codec.
Now just ```
sudo apt-get install 'missing codec'
``` in a terminal.

---

### Post by celticbhoy on 2009-02-13
The second post helped the script wasnt copied to home directory.

---

