---
title: "Can't rip in Mp3 in K3b"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by sdim on 2009-04-22
Hi,everyone.
I just can't seem to be able to rip in mp3 format in k3b,evethough I've installed this:```
sudo apt-get -y install k3b libk3b2-extracodecs
```
Any help would be appreciated.
I attach a screenshot of the error.
Thank you.

---

### Post by gn2 on 2009-04-22
Have you installed ubuntu-restricted-extras and Lame yet?

Maybe try Grip, it works a charm.

---

### Post by sdim on 2009-04-22
The answer is here:[http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128]("http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128")
Settings->Configure k3b->Plugins->k3b external audio encoder->Configure->mp3 lame->edit->check both boxes under Options.
Thanks for the help.

---

### Post by logos34 on 2009-04-23
> **sdim said:**
> The answer is here:[http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128]("http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128")
Settings->Configure k3b->Plugins->k3b external audio encoder->Configure->mp3 lame->edit->check both boxes under Options.
Thanks for the help.

I've seen this fix before.  I wonder why mine works with both options UNCHECKED?  I only get hiss if I enable them. hmm

---

### Post by stchman on 2009-04-23
> **sdim said:**
> Hi,everyone.
I just can't seem to be able to rip in mp3 format in k3b,evethough I've installed this:```
sudo apt-get -y install k3b libk3b2-extracodecs
```
Any help would be appreciated.
I attach a screenshot of the error.
Thank you.

I have never tried to rip CDs to mp3s using K3b.  The lik3b2-extracodecs allows you to burn mp3s to an audio CD.

If you wish to do CD ripping duty follow my tutorial.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

---

### Post by logos34 on 2009-04-23
the only thing I could find to explain why some (a lot?) are having this problem is the following:
> 
* [New settings]("http://www.videohelp.com/tools/K3b/version-history") "Swap byte order" and "Write Wave header" in the audio encoding plugin using external apps. This makes way for the usage of such programs as mppenc to encode Musepack files. In fact, mppenc is set up as a default along with flac if installed.
> 
[Ensure you select ]("http://wiki.hydrogenaudio.org/index.php?title=K3b_and_Nero_AAC_Guide")'Swap Byte Order' and 'Write Wave Header' so that the neroaac script gets the right format. (Note: I think k3b has this setting around the wrong way. If k3b was actually outputting little endian, neroaac-enc would work OK. Swapping the byte order seems to fix it.)
(but this is in reference to .m4a, not lame mp3)

and the bubble in k3b edit prefs:
> 
Please insert the command used to encode the audio data. The command has to read raw little endian (see Swap Byte Order) 16bit stereo audio frames from stdin. 

Can anyone elucidate for me what all this means?

---

### Post by raymondh on 2009-04-23
Also ... have a read at this and the "sound" sticky.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=205449&page=144](http://ubuntuforums.org/showthread.php?t=205449&page=144)

Best of luck.

Raymond

---

### Post by SuperSonic4 on 2009-04-23
I installed an old version of lame which seemed to work although it was more likely a coincidence

---

### Post by logos34 on 2009-04-23
> **SuperSonic4 said:**
> I installed an old version of lame which seemed to work although it was more likely a coincidence

i'm using 3.97, just one version behind latest

---

### Post by windwalker78 on 2010-11-01
> **sdim said:**
> The answer is here:[http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128]("http://kubuntuforums.net/forums/index.php?topic=3101681.msg172128#msg172128")
Settings->Configure k3b->Plugins->k3b external audio encoder->Configure->mp3 lame->edit->check both boxes under Options.
Thanks for the help.

Good info!!!
Thanks

---

