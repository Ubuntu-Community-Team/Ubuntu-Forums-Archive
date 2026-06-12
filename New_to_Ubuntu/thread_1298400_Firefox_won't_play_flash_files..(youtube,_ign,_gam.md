---
title: "Firefox won't play flash files..(youtube, ign, gamespot, etc)"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by bob.rea on 2009-10-22
I just installed Ubuntu yesterday and I'm a first time Linux user.  I appreciate any help anyone can give me but unfortunately, I basically need step-by-step instructions as I don't fully understand the fundamentals  of this OS yet.  I'm running version 9.04, and I have installed the flash player plugin via firefox's plugin installer tool.  I have also downloaded and installed a packet of non supported file type playersa from the Ubuntu website.  
Thank you again for any help.

Also, I don't know if this will help, but when I load a youtube video, the screen where the video appears shows up and is all black.  The play and pause button, progress bar, etc are not there.

---

### Post by wojox on 2009-10-22
See this great HowTo: [URL="http://ubuntuforums.org/showthread.php?t=1193567"]Firefox optimization and troubleshooting thread
[/URL]

Also did you download ubuntu-restricted-extras?

---

### Post by bob.rea on 2009-10-22
> **wojox said:**
> See this great HowTo: [URL="http://ubuntuforums.org/showthread.php?t=1193567"]Firefox optimization and troubleshooting thread
[/URL]

Also did you download ubuntu-restricted-extras?

Yes, I did dl the extras pack, I'll check out the how-to and get back to you.  Thanks!

---

### Post by bob.rea on 2009-10-22
Unfortunately that guide did not solve my proble.  Everything is as the same in the first post.

---

### Post by The Pokemon Master on 2009-10-22
Did you try the latest .deb file on the Adobe Website?

---

### Post by bkratz on 2009-10-22
> **bob.rea said:**
> I just installed Ubuntu yesterday and I'm a first time Linux user.  I appreciate any help anyone can give me but unfortunately, I basically need step-by-step instructions as I don't fully understand the fundamentals  of this OS yet.  I'm running version 9.04, and I have installed the flash player plugin via firefox's plugin installer tool.  I have also downloaded and installed a packet of non supported file type playersa from the Ubuntu website.  
Thank you again for any help.

Also, I don't know if this will help, but when I load a youtube video, the screen where the video appears shows up and is all black.  The play and pause button, progress bar, etc are not there.



This is the one that worked for me.

[http://ubuntuforums.org/showpost.php?p=8137539&postcount=2](http://ubuntuforums.org/showpost.php?p=8137539&postcount=2)

Good Luck

---

### Post by penguinv on 2009-10-26
Same problem.

Yes I've installed this and that.
gnash, medibuntu, java, flash, non-supported.

Happily I can play .avi files!

So does youtube work for anyone?
Could I need to remove something?

Still black.

--- why am I using Ubuntu then?
Windows doesnt like my nvidia card. Yes, I reinstalled the driver from the website. It puts Windows in an infinite loop, so the blue screen tells me. I have to use it in safe-mode.

---

### Post by Hosmion on 2009-10-26
Try this:

```
sudo apt-get install flashplugin-nonfree
```

I never used this, and I heard someone else use it, but idk..

```
sudo apt-get install flashplugin-installer

```

---

### Post by sandyd on 2009-10-26
are you running 64 bit or 32 bit? run ```
uname -r 
```

---

### Post by Hilko on 2009-12-27
If you're using 64 bit, you want to go here [http://ubuntuforums.org/showthread.php?t=1358591](http://ubuntuforums.org/showthread.php?t=1358591)

get the script from the first post. Then your flash works.

---

