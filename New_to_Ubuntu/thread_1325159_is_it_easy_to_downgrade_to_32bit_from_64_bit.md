---
title: "is it easy to downgrade to 32bit from 64 bit?"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Irishpolyglot on 2009-11-13
I've tried 64 bit in hardy and now in karmic and it's just too much hassle considering the low resources I actually need on my comp. Flash and my video drivers are giving me a constant nightmare.
I have the 32 bit CD, is it just a case of installing it anew and selecting the same profile and everything will work the same, or is a change in the system layout and loss of data required?
Thanks!

---

### Post by philinux on 2009-11-13
If you have home on it's own partition then program settings, your desktop settings etc will be preserved on reinstalling. Choosing manual partitioning and NOT selecting home to be formatted.

However. It may be easier to sort out your 64 bit install. 

Flash for example. I'm using the 64 bit plugin are you?

---

### Post by ukripper on 2009-11-13
No, there is no such way to downgrade to different architecture.

Create a backup of your important data. Then do 32bit install as you would do for any other fresh installation.

If you have a separate home partition then it is pretty simple in that case. Then you just need to do a fresh install and leave your home partition intact. 

Whatever you do make sure you have backup!

---

### Post by philinux on 2009-11-13
Think this link might help too.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by Irishpolyglot on 2009-11-13
I was afraid it was more complicated than just reinstalling it... sadly, home is on the one and only partition, and I'd rather not get all messy with it unless I have to.

The only problem is that I spent weeks trying to fix flash and reached the "ok" stage of it working, but slowing down my computer and freezing grey for a few seconds regularly. Now in Karmic it's working, but buttons can't be pressed and the workarounds I found in these forums aren't doing anything for me.

And I've just recovered from a horrible 2 days with no computer because of a video driver issue. I've simply disabled the nvidia drivers for the moment. It's just frustrating to have to work everything around 64 bit- I just installed that version because my computer was made for 64 bit capabilities and could "theoretically" handle it and because 64 is a bigger number than 32 :P I wish I went the more humble route now...

---

### Post by Irishpolyglot on 2009-11-13
> **philinux said:**
> Think this link might help too.

[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Thanks for that. So you think I should hang in there and keep searching until I find a solution? Any ideas when flash 64 will come out of alpha? Thanks again for your help!

---

### Post by philinux on 2009-11-13
> **Irishpolyglot said:**
> Thanks for that. So you think I should hang in there and keep searching until I find a solution? Any ideas when flash 64 will come out of alpha? Thanks again for your help!

Not far off I dont think. It's rock solid for me. What problems are you getting?

---

### Post by ukripper on 2009-11-13
64bit is working great on mine too. No problem so far even with flash

---

### Post by Irishpolyglot on 2009-11-21
My problems are that firefox will often grey-out for several seconds whenever there is a page with flash. This is very annoying.
Also, I can't click within flash. [Others have this issue ]("http://ubuntuforums.org/showthread.php?p=8362911"), and the work-around is to right-click and then left click, which is quite awkward.
I have tried to run the alpha version of flash 64 bit instead of this annoying 32-bit piggy packed version, but Firefox crashes completely with that.

These issues were **not occurring** with the Nvidia drivers disabled, but they are slightly less annoying than the grainy screen I get on videos without any drivers applied.

It's frustrating because things were actually better before I upgraded to Karmic. If it's working fine for you it may be because my system (i.e. graphics card and drivers) doesn't work well with 64 bit in its current stage. At the moment all I can think of is just to hope that the stable version of 64 bit flash comes out soon.

---

### Post by ukripper on 2009-11-21
you can try using chromium instead of firefox and see if issue still persists.
[http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)

---

### Post by 3rdalbum on 2009-11-21
Your issues are not typical for 64 bit (except the mouse clicks in Flash Player - whenever this happens I left click on the page and the next click in Flash will work).

These days the Ubuntu installer will preserve the contents of /home even without it being on a different partition. But backup first and don't select the partition for reformatting!

---

