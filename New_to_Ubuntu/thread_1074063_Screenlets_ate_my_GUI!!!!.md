---
title: "Screenlets ate my GUI!!!!"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by AndyP79 on 2009-02-18
Okay, first I work on a boat, so I am gone from the internet alot. Second, I am still new to not only linux, but computers, but if in plain english and clear, I can usally follow alright.
So, I am on the boat, and decide to try the creenlets on my 8.10. At first it was pretty routine, trying them. So I got it all set up, and all of a sudden, BAM! They scattered all over the desktop, and now it is frozen. I have NO access to anything on my desktop. Nothing opens, nothing runs, I can not access anything on my panel! HELP!!!
 I was able to log into the terminal from the login in page. I just kinda guessed at sudo open firefox, and that is how I am using this now, though that is about my knowledge of the terminal. But, it works, so i can with some guidance, correct things that way.
Anyone?
Thanks
-a

---

### Post by konqueror7 on 2009-02-18
you could try entering the screenlets manager
```
screenlets-manager
```
this will open the manager, and you should be able to disable them all...
also, the reason behind why there are so many screenlets is maybe because when you where trying them out, you clicked on autostart on login...;)

---

### Post by AndyP79 on 2009-02-18
okay, so that got me so far as getting the screenlets off the screen. but still not response to either my panel or AWN??? 

I can open nautilus, and access my files through the terminal, is there a command to sve them to say my external harddrive, and then I can just reload the OS?

---

### Post by konqueror7 on 2009-02-18
mmm...you could try recreating your xorg conf file...
make a backup first...
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

now again in the terminal...
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
this should recreate it...

anyway, this is what i would do in my case, lets wait if others have other solutions...;)

---

