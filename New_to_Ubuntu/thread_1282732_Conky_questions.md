---
title: "Conky questions"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by xMastemah on 2009-10-04
I'm having some big trouble with the small parts of Conky. Probably because there's like 3 or 4 different file locations that I keep hearing about or "where to put this script" and such.

I'm wondering...

What is the difference between conky.conf and .conkyrc? Really, because no matter what I put into .conkyrc, when I start conky, it always looks the same. I end up renaming my .conkyrc to conky.conf and moving it into my /etc/conky folder...

If I start conky through a terminal, how do I close it for GOOD? I can close the terminal and it just stays open, usually stuck bugged on my desktop because whatever script I used had some error.

I have another question but it might make more sense if I know those answers.
Thanks.

---

### Post by Waappu on 2009-10-04
Hi,

You should but .conkyrc to your home folder.
That file contain configure that you like see in your desktop.

Close Conky for good type terminal```
killall conky
```

---

### Post by meowzers on 2009-10-16
I have some questions regarding my conky as well.  i have used a stock .conkyrc for the last year.  I start it up from command because when I added it to the startup programs it would not startup as transparent.  Anyways, whenever i start it up, it reads:
Conky: statfs '/home/tmo': No such file or directory
Conky: statfs '/home/tmo': No such file or directory
I typically just shut the terminal and move on however I am interested to know why this is happening?  Could be as a result of never configuring the wifi portion of the config i use?  everything reads on conky except the wifi.  Also, the .conkyrc files are only on the desktop because I was starting to mess around with it and see what I could do.

---

