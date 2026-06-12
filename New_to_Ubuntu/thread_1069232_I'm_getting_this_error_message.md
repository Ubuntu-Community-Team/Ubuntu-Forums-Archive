---
title: "I'm getting this error message"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by cheese123 on 2009-02-13
I was trying to uninstall some games, but I get this message. 

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

I tried entering 'sudo dpkg --configure -a' into the terminal but I get this

```

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 newline in field name `ists.ubuntu.com>'

```

help?

---

### Post by drs305 on 2009-02-13
See if you can correct the file with a text editor:
```

gksudo gedit /var/lib/dpkg/updates/0000

```

My guess is the word is supposed to be **d**ists

I'd try that but since it's on line 1 there may be other errors further down. If it doesn't work rename the file to something else and run your command again.

---

### Post by cheese123 on 2009-02-13
> **drs305 said:**
> See if you can correct the file with a text editor:
```

gksudo /var/lib/dpkg/updates/0000

```

My guess is the word is supposed to be **d**ists

I'd try that but since it's on line 1 there may be other errors further down. If it doesn't work rename the file to something else and run your command again.

Could you give me steps on how to do this? Sorry I'm still pretty new.

---

### Post by RomeReactor on 2009-02-13
Hi. Try running:
```
sudo aptitude install -f
```
And post back if you get any errors.

EDIT: Too slow; try drs305's suggestion first. From a terminal (Applications->Accessories->Terminal):
```
gksudo gedit /var/lib/dpkg/updates/0000
```

---

### Post by cheese123 on 2009-02-13
Ok well I changed it to dist, but I still get this message after trying to run dpkg again. 

```

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 newline in field name `dists.ubuntu.com>'

```

---

### Post by ALIENDUDE5300 on 2009-02-13
Im getting almost the EXACT same message that you are... I posted a thread at [http://ubuntuforums.org/showthread.php?t=1069198](http://ubuntuforums.org/showthread.php?t=1069198) with additional details. If you find a solution, could someone let me know how to fix this? I've been trying to figure this out for almost an 2 hours...

---

### Post by RomeReactor on 2009-02-13
A similar problem is discussed [here]("https://answers.launchpad.net/ubuntu/+source/update-manager/+question/56796").

You can try removing the offending file:
```
sudo rm /var/lib/dpkg/updates/0000
```
Then update the repository information:
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by drs305 on 2009-02-13
> **cheese123 said:**
> Ok well I changed it to dist, but I still get this message after trying to run dpkg again. 

```

dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 newline in field name `dists.ubuntu.com>'

```

You could post the line, I'd guess it should look something like <something-here...dists.ubuntu.com> but personally I'd just rename it and try running update again.

---

### Post by cheese123 on 2009-02-13
Now it's giving me this

```

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 1:
 field name `.4),' must be followed by colon

```

:confused:

---

### Post by drs305 on 2009-02-13
So how many files do you have in /var/lib/dpkg/updates/ and were they all created at generally the same time? If you have a lot all created at the approximately the same time I'd just use "gksudo nautilus /var/lib/dpkg/", navigate to the updates folder and (at least temporarily) rename it. Note: I do not even have an *updates* folder. You can see if that is your only problem and then restore the name if you believe you need the contents of that particular folder.

---

### Post by ALIENDUDE5300 on 2009-02-13
Removing the file mentioned and then re-running sudo dpkg --configure -a worked for me. To do this, type 
```
sudo rm /var/lib/dpkg/updates/0000;sudo rm /var/lib/dpkg/updates/0001;dpkg --configure -a 
```
into the terminal.

---

### Post by jeremyll33 on 2009-02-17
Hi there, I am returning to Linux after a few yaesra away, thanks to wonderful Ubuntu.

If it helps, I was experiencing this problem but naving to the "Updates" folder mentioned above then cutting and pasting the files there into another folder empties that folder. You can then run Synaptic again.

---

### Post by p8baller07 on 2009-04-10
just incase doing sudo rm /var/lib/dpkg/updates/0000

doesnt work for everyone try this instead. 

```
sudo rm /var/lib/dpkg/updates/* && sudo apt-get update && sudo apt-get upgrade
```

if you want to just fix the issue and not update. do this
```
sudo rm /var/lib/dpkg/updates/* 
```

---

### Post by drowner on 2009-04-10
And, to the original poster, it is best if you specify the error message in your post title, or at least something more descriptive.

I know how to fix some error messages, but not this one, so I've opened this thread, posted this, and wasted everybody's time and bandwidth.

Not being picky, but asking good questions is very important.

---

