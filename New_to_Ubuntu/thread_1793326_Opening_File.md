---
title: "Opening File"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by inxnix on 2011-06-29
Hi!

I'm definitely an absolute beginner considering I'm having trouble just opening a file.  I'm using GNOME at work.

I went to the right directory (it's called "images") and tried to open up a file called JUN22.ps in Document Viewer.

I tried: open [-a Document Viewer] JUN22.ps 
and: open JUN22.ps 

plus some other variations, but I keep getting: "couldn't get a file descriptor referring to the console"

Thanks for any help!

Also, if anyone is wondering, the reason why I don't just click on folders is because I'd rather get a hang of the terminal to keep everything clean. :P

---

### Post by Ozymandias_117 on 2011-06-29
Try ```
evince file.ps
``` you want to call the program and pass it the file - I'm pretty sure Ubuntu/Gnome uses evince for it's document viewer.

---

### Post by gdonwallace on 2011-06-29
When trying to manipulate files from the command line, you have to start with the name of the program you want to run followed by the file to be opened by the program.

Optionally, you can use nautilus, navigate to the directory that has the file and double click on the file.  By doing this, whatever program is setup as the default for the file type will then be launched and open that file for you.

---

### Post by dcsoldschool53 on 2011-06-29
I have 2 commands that you can try in the terminal```
envince JUN22.ps
``` and```
gnome-open JUN22.ps
```Hope this will help you:)

---

### Post by inxnix on 2011-06-29
evince and gnome-open both worked... thanks guys!

---

