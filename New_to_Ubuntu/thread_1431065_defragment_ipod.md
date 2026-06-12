---
title: "defragment ipod"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by corky748 on 2010-03-16
i know their is no need to defrag a linux hard drive but i want to clean up my ipod gen 5 without removing all my music from it, gtkpod rythtymbox, etc will not do it any ideas?/

---

### Post by Grenage on 2010-03-16
You want to clean it up, but not remove anything?  What exactly are you trying to achieve?

---

### Post by bug67 on 2010-03-16
The file systems on any *nix system does not need defragmentation. 

[http://blog.mypapit.net/2006/09/why-you-dont-have-to-defrag-linux-like-windows.html](http://blog.mypapit.net/2006/09/why-you-dont-have-to-defrag-linux-like-windows.html) 

Now, I'm *assuming* that since Mac OS X is based on Unix and since the iPod is an Apple product, see where I'm going?  Of course I could be way off base.  I, however, have never seen a need to defrag my iPod.

However, if you feel it an absolute necessity to defrag *your* iPod[COLOR="Red"]*[/COLOR]:

[http://www.google.com/#hl=en&source=hp&q=defrag+iPod&aq=f&aqi=g6g-m2&aql=&oq=&gs_rfai=&fp=22b4dcbb1403dc0f](http://www.google.com/#hl=en&source=hp&q=defrag+iPod&aq=f&aqi=g6g-m2&aql=&oq=&gs_rfai=&fp=22b4dcbb1403dc0f)

[COLOR="Red"]*proceed at your own risk[/COLOR]

---

### Post by corky748 on 2010-03-16
I started to remove the music from my ipod (so i can put it on to my new archos) using gtkpod and every so often it hits a damaged or corroupt file and crashes out.
was hoping to clean some of it up so i don't carry damaged files to A new mp3 player.... and stop it crashing out because it's going to take a life time to copy 60gb with it crashing every 5mins... 

any advice on how to clean it up or even another program i can use would be greatful..

---

### Post by Grenage on 2010-03-16
A defrag won't fix or remove corrupt files, what you need is some kind of file integrity checker.

---

### Post by NickJones on 2010-03-16
Defraging it will not stop it from crashing, it simply speeds up the process of finding and locating files on the hard drive, it doesn't make more space, it simply tidies everything into where it has to be.
Go to Applications, Accessories, and then Terminal and type this:
```
sudo palimpsest
```
Hit enter.

Try running that, unmounting your iPod and click the Check Filesystem, it's the one with the picture of the Hard drive and the stethoscope.

---

### Post by 3rdalbum on 2010-03-16
> **bug67 said:**
> The file systems on any *nix system does not need defragmentation. 

[http://blog.mypapit.net/2006/09/why-you-dont-have-to-defrag-linux-like-windows.html](http://blog.mypapit.net/2006/09/why-you-dont-have-to-defrag-linux-like-windows.html) 

Now, I'm *assuming* that since Mac OS X is based on Unix and since the iPod is an Apple product, see where I'm going?  Of course I could be way off base.

Sorry... you're way off base. HFS+ does require defragmentation. And if you formatted the iPod on a Windows machine, it will be using Fat32 which also requires defragmentation.

You really need to identify what songs are corrupted, delete them, and then back up your music library and reformat the iPod. Those players are especially prone to database corruption and require such a reset every so often. In future I'd recommend a non-Apple MP3 player, such as a Sony Walkman - completely cross-platform compatible and no database corruption issues.

---

### Post by bug67 on 2010-03-16
> **3rdalbum said:**
> Sorry... you're way off base. HFS+ does require defragmentation. And if you formatted the iPod on a Windows machine, it will be using Fat32 which also requires defragmentation.

Oh crud.  I didn't even think about a Windows formatted iPod.  Thanks for the clarity.

---

### Post by phillw on 2010-03-16
Now, hush and don't tell anyone ...  [http://ubuntuforums.org/showthread.php?t=1429653](http://ubuntuforums.org/showthread.php?t=1429653)

You may well be able to pull your files over with the Lynx, people are already doing so. Remember, 10.04 is NOT ready as a replacement for 9.10 yet - The developers may break it before the final release ;-)

But, if you've got about 5 GB for Lucid Lynx plus however much room more that your muzik etc takes up, to make a new partition it *may* be worth letting the canivorous Lynx have a 'chat' to your iPod, as it is in test, I don't guarantee it will not eat it. But others seem fairly happy with it.:p

Regards,

Phill.

---

