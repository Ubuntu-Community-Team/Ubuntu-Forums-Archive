---
title: "Adobe flash low fps issue amd64"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by aloprot on 2010-03-30
I observe that there are some big issues with flash under ubuntu 64 that when I was using Windows I didn't had. Everytime I experience low fps and basicly everything is messed up. What can I do to fix this? I found out that this is a common problem for everyone in the linux world but how can we fix this? I heard a lot of people saying"well...i use gnu/linux but have flash issues, asked why and they told me...well this is it if you don't like it ....use other things..."This issn't a reply that a linux user should give. I know open source is a "best effort service" but...this is not the way someone should answer. Anyway, right here and right now, what progress has been done exactly? Were can people help and with what? 
thanks!

---

### Post by Calmor on 2010-03-30
Flash is an Adobe product, not created by anyone in the open source world.  The best you can hope for is Adobe to fix it.  

nspluginwrapper originally used a Windows version of Flash to work on Linux, now we have a native version (even 64-bit, which took forever to come out).  But while 10.1 supports h.264 hardware acceleration on Windows, I don't see any of that in the 64-bit beta versions of 10.1.  They make reference to "hardware acceleration" but that's about it.

Until Adobe makes its code more Linux-friendly, there's not much we can really do.

Edit: I might add, I agree with you that flash is terrible right now.  With vdpau, I can watch a 1080i stream from my cable box in fullscreen mode and use up only 10-15% of -one core- of my processor, but a SD Flash stream via Hulu Desktop is choppy and jerky even windowed and taps one of my cores out to 98% (and can't multi-thread, so the other sits idle).  There's NO reason for this, especially when cell phones can now do Flash video.  My machine isn't the latest and greatest, but it's far from incapable.

---

### Post by aloprot on 2010-03-30
I understand, thank you for the answer. I heard also about gnash. I'm a beginner, not an advance user but I'm just courious, could I replace flash with gnash on my ubuntu amd64 machine to get better fps?

---

### Post by sandyd on 2010-03-30
> **aloprot said:**
> I understand, thank you for the answer. I heard also about gnash. I'm a beginner, not an advance user but I'm just courious, could I replace flash with gnash on my ubuntu amd64 machine to get better fps?

gnash / swfdec is largely imcomplete, and the last time I checked, it only works w/ youtube. p.s. have you tried the 64-bit version of flash? the version you download by default from the ubuntu repos is the 32 bit version, and the 64 bit version may perform better. if you wanna try, see my signature.

---

### Post by aloprot on 2010-03-30
Thanks carlee, tried the 64bit version but the same.

---

### Post by charliehorse55 on 2010-03-30
Compiz somehow interferes with flash performance. Try disabling it temporarily, and see how flash performs. 

```
metacity --replace
```

---

### Post by aloprot on 2010-03-30
Tried this aswell but still the same experience.

---

### Post by clhsharky on 2010-03-30
HI

Adobe

RECOMMENDED HARDWARE FOR STANDARD- AND HIGH-DEFINITION (HD) VIDEO PLAYBACK
[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

Do you have minimum hareware for intended use?

As far as cellphone, a 2" screen requires a lot less to render than say a laptop.

Adobe flash is proprietary soft ware, and you should be filing a complaint with them if you are having problems. Its Adobe that doesn't give Linux the same experience as Microsoft. 

Sharky

---

### Post by aloprot on 2010-03-30
4gb ram and a t4300 intel processor on a Dell. So system requirements are more than enought. I think that if I'm the only one complaining then adobe will probably or 100%ignore me but if more people I don't know, make a petiton or something they can raise aware of this issue. If not I hope that gnash or other problem will make flash player not needed anymore in order to whatch videos on youtube, etc.

---

### Post by quadproc on 2010-03-30
> **aloprot said:**
> I observe that there are some big issues with flash under ubuntu 64 that when I was using Windows I didn't had. Everytime I experience low fps and basicly everything is messed up. 
Perhaps you do not have the correct driver installed?  Just a thought.  The last that I checked, the open source drivers were much slower than the graphics card's vendor's drivers.

I found that I was getting roughly 60 FPS on a simple test with the "ati" open source driver, but using the fglrx driver (from ATI) yielded about 3500 FPS.

quadproc

---

### Post by dez_cole on 2010-04-05
> **clhsharky said:**
> HI


Adobe flash is proprietary soft ware, and you should be filing a complaint with them if you are having problems. Its Adobe that doesn't give Linux the same experience as Microsoft. 

Sharky

 I propose that we all (ubuntu's community and possibly other distro's forums as well if we can get the word out) send an email to adobe requesting better drivers in our own words. Do you think they will just ignore thousands of emails? Its a possibility but I hope not.

---

### Post by Naggobot on 2010-04-05
Adobe flash has a weird check for availability of HW acceleration so it may be that on your machine the HW acceleration is not enabled. I know that on my machine it is not enabled. 

More info can be found from

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html) 

and 

[http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html](http://blogs.adobe.com/penguin.swf/2008/08/secrets_of_the_mmscfg_file_1.html)

and the bug you are probably suffering from is reported to Adobe and you can find the link from my signature. Please vote for fix for this issue. It takes only a few minutes.

I tried forcing the HW acceleration on my other laptop which has ATI 3D card. I noticed clearly improved frame rate with full screen / HD video but there were also frame drops and stutter. With out HW acceleration it actually works more fluently but HD video can not be played. 

Note: Forcing HW acceleration only effects the full screen video display
Edit:
Note2: HW acceleration does not work with Compiz

---

### Post by no2498 on 2010-04-05
10 to 1 he does not have any gstreamer installed

type this in a terminal gstreamer-properties click enter

 what come up ?

---

### Post by aloprot on 2010-04-06
When i type that command in the terminal a window pops up ...multimedia systems selector...and i was able to test succesfully the input and output.

---

### Post by no2498 on 2010-04-06
guess i owe you 10 then lol
had to install it on my computer
click video
try setting the plugin to, x11
after a restart

set the plugin back if it did not help

you may look and see if the good,bad,and ugly, is installed

---

### Post by aloprot on 2010-04-07
[no2498]("http://ubuntuforums.org/member.php?u=906707"), tried, the same.

---

### Post by J V on 2010-04-07
99% of the time there are flash problems, its on 64bit... 99% of those problems are from using a 32bit flash...

Download the 64bit linux flash beta (Or was it alpha?) its so much more stable than the 32bit one...

---

### Post by aloprot on 2010-04-07
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

I run this version. So this thing is excluded.

---

### Post by sinbin on 2010-04-07
> **aloprot said:**
> I understand, thank you for the answer. I heard also about gnash. I'm a beginner, not an advance user but I'm just courious, could I replace flash with gnash on my ubuntu amd64 machine to get better fps?

Don't use gnash

I am using Adobe Flash Player 10 for 64 bit Linux and I have 2gb of ram. Flash runs really well for me. Here is a link to a really good tutorial with instructions for installing it :

[http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/en/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

I have not tried the release candidate for Adobe Flash Player 10.1 but will update when I have

I hope this helps

---

### Post by aloprot on 2010-04-08
I don't use gnash, I only heard about it that's all. Did exactly like in the link provided but still the same. I have the proprietary ati drivers installed. Although this happens, I noticed that when controling the volume on a media site that uses flash, the controls are responsive now like in windows. But still the picture freezes, and it's not because of my specs. I have 4 gb ram, 2x 2,1 ghz intel, ati hd4330, isn't that enough to run a simple flash video?

---

### Post by aloprot on 2010-04-10
I have done a fresh install and run flash from the link you gaved me [sinbin]("http://ubuntuforums.org/member.php?u=794865"), it worked ok  and I seem to have found the problem. When enabling my ati hd 4330 driver, my flash sometimes freezes, and such things. So I found the problem, the ati driver. But what do I do next? I can not stay with my proprietary driver because sometimes I play games, I want to enable my effects in ubuntu...what do I do next?

---

### Post by gordintoronto on 2010-04-10
I'm using 64-bit Linux Mint, which is based on Ubuntu. I have never had a problem with Flash. If you re-install, try it.

---

### Post by Naggobot on 2010-04-11
> So I found the problem, the ati driver. But what do I do next? I can not stay with my proprietary driver because sometimes I play games, I want to enable my effects in ubuntu...what do I do next?

If you have not already done so, then check if the open source ATI driver supports your hardware?

---

### Post by aloprot on 2010-04-11
How do I check that? If it helps i installed the drivers from hardware drivers. The one recommended there. Games work, effects work.
:KS
Ps:what open source drivers? I use proprietary drivers from hardware drivers.

---

### Post by bobbob94 on 2010-04-11
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

