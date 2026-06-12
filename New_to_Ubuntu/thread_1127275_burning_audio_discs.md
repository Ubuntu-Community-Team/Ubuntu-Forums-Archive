---
title: "burning audio discs"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by numbness05 on 2009-04-16
Hi there.

I have a a whole load of albums I want to burn to disc, I have have two questions...

Is it AAC I need to convert them too? and if so what software can I grab to do this...I was told soundkonverter by some one but unfortunately this doesn't seem to offer the option of AAC..

Any body have any ideas please???

Many thanks

---

### Post by numbness05 on 2009-04-16
Hi there.

I have a a whole load of albums I want to burn to disc, I have have two questions...

Is it AAC I need to convert them too? and if so what software can I grab to do this...I was told soundkonverter by some one but unfortunately this doesn't seem to offer the option of AAC..

Any body have any ideas please???

Many thanks

---

### Post by kpkeerthi on 2009-04-16
What format do you have them as currently? mp3? Brasero can burn mp3s to Audio CDs.

---

### Post by gali98 on 2009-04-16
As long as you have the codec installed, you should be able to use something like brasero to burn the audio disks..
What format are they in now?
Kory

---

### Post by numbness05 on 2009-04-16
most are in MP3
I also tried K3b but that tells me even the mp3 is a n unsupported format? how would I go about installing the correct codecs?

Many thanks

---

### Post by Sef on 2009-04-16
Merged in Absolute Beginners.  Do not double post, please.   Double posting can result in a warning or infraction being given.   Thank you for your support in posting in the forums.

---

### Post by kpkeerthi on 2009-04-16
> **numbness05 said:**
> most are in MP3
I also tried K3b but that tells me even the mp3 is a n unsupported format? how would I go about installing the correct codecs?

Many thanks

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by halitech on 2009-04-16
MP3 should be burnable to an audio cd in k3b as I just did it last week. Do you have all the multimedia codecs installed? (ie. can you play and listen to MP3s okay?)

---

### Post by SuperSonic4 on 2009-04-16
I found that k3b only seems to work properly with lame 3.96 which you can compile easily enough [LAME on sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309")

---

### Post by halitech on 2009-04-16
> **SuperSonic4 said:**
> I found that k3b only seems to work properly with lame 3.96 which you can compile easily enough [LAME on sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=290&package_id=309")

I have lame 3.98 and it works fine

```
daryl@debian-desktop:~$ lame
LAME 32bits version 3.98.2 (http://www.mp3dev.org/)
```

---

### Post by gali98 on 2009-04-16
Try running this command:
```
sudo apt-get install ubuntu-restricted-extras
```
This will install a lot of codecs (including mp3) and might get you rolling.
Kory

---

