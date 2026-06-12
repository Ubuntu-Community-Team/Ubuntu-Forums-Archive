---
title: "linux mint-jdownloader"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by irish66 on 2009-01-31
Hi, i am trying to open some rsdf files, i have downloaded  jdownloader specifically jD.sh, but clicking provkes no reaction.
Can anyone help?
M

---

### Post by mikewhatever on 2009-01-31
Here is JDownloader's web site. [http://jdownloader.org/](http://jdownloader.org/)
Full instructions on what to do after downloading jd.sh are here -> [http://jdownloader.org/download/index](http://jdownloader.org/download/index)
> Try out our new Install/Start-Script for Linux!
1.) Download jd.sh
2.) chmod +x jd.sh
3.) start jd.sh
Note: Open jd.sh to read Manual or change Settings! 

Obviously, you need java installed.

---

### Post by irish66 on 2009-02-01
Well I'm guessing I have Java installed, as I can play videos on youtube. 
I have been to that site already. But the instructions are rather vague. 
I mean what does "chmod +x jd.sh" mean. 
Is it something you type in terminal.
Well i did anyhow, and here is the response
cannot access `jd.sh': No such file or directory
martin@martin-desktop ~ $

---

### Post by mikewhatever on 2009-02-01
> **irish66 said:**
> Well I'm guessing I have Java installed, as I can play videos on youtube. 
I have been to that site already. But the instructions are rather vague. 
I mean what does "chmod +x jd.sh" mean. 
Is it something you type in terminal.
Well i did anyhow, and here is the response
cannot access `jd.sh': No such file or directory
martin@martin-desktop ~ $

First, java has nothing to do with youtube. You have flashplayer installed, and so can play the videos. Just make it very clear, I don't have java installed, but can also play flash videos, get java installed otherwise jdownloader will not work.

chmod +x makes the file executable, yes you type it in terminal, the error you get means it's looking in the wrong place. When you open the Terminal, you are in your home folder by default. If the file in question is on your desktop, you need to move there with <cd Desktop>.

---

### Post by irish66 on 2009-02-03
Thanks for replies. I got that part sorted out.

---

### Post by pimchu on 2009-09-13
thanks mike, i too had a problem running it. works now.

---

