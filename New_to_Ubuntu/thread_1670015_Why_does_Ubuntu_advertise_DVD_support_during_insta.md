---
title: "Why does Ubuntu advertise DVD support during install?"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-01-18
Sorry if this question may seem dumb. I was bored the other day so I backed-up my stuff and re-installed Ubuntu. While it was installing, the installer advertised that it could play DVDs. Gave me the impression right out of the box.

So I tried a recorded DVD with family video last night, and it didn't work. From what I understand you need to install a package for DVD playback. So why did they advertise it if it's not available from start?

I'd just like an answer that's all, just something I noticed during install. I don't plan on installing it due to legal problems I keep reading about.

---

### Post by mikewhatever on 2011-01-18
Don't see why not. Playing DVDs is not illegal, and Ubuntu really can play them.

---

### Post by LinuxFox on 2011-01-18
> **mikewhatever said:**
> Don't see why not. Playing DVDs is not illegal, and Ubuntu really can play them.I know that, but they make it seem like Ubuntu had the feature out of the box.

As for the legal thing, I found it in the [documentation]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

> Legal Warning: Check with your local laws to make sure usage of libdvdcss2 would be legal in your area. 

Just posted it as a reference to what I read.

---

### Post by maryalesia on 2011-01-18
> **LinuxFox said:**
> 
I'd just like an answer that's all, just something I noticed during install. I don't plan on installing it due to legal problems I keep reading about.

I don't think the legal problems have to do with PLAYING DVDs, but rather the fact that it makes it easy to rip them onto your computer. Unless you are seriously opposed to breaking copyright laws, I don't think it's that big a deal. 

Then again, I was raised on limewire and BitTorrent and have a very fuzzy interpretation of copyright laws, so I understand if you are still worried about it.

---

### Post by maryalesia on 2011-01-18
> **LinuxFox said:**
> 
I'd just like an answer that's all, just something I noticed during install. I don't plan on installing it due to legal problems I keep reading about.

I don't think the legal problems have to do with PLAYING DVDs, but rather the fact that it makes it easy to rip them onto your computer. Unless you are seriously opposed to breaking copyright laws, I don't think it's that big a deal. 

Then again, I was raised on limewire and BitTorrent and have a very fuzzy interpretation of copyright laws, so I understand if you are still worried about it.

---

### Post by mikewhatever on 2011-01-18
Perhaps you could quote the exact statement or post a screenshot of it, and we can then discuss what the meaning is. I can't possibly account for your personal impression of an undefined statement.

There is a lot of confusion about the DVD format, most of it by the original design, to prevent people from using the media they legally own. Anyway, libdvdcss2 is a library for playing encrypted DVDs. It's not in the Ubuntu repositories, but can be obtained from Medibuntu by individual users. What's important is, libdvdcss2 is not required for playing unencrypted DVDs. I happen to have a couple of those and they play just fine in Totem.

---

### Post by mikewhatever on 2011-01-18
Perhaps you could quote the exact statement or post a screenshot of it, and we can then discuss what the meaning is. I can't possibly account for your personal impression of an undefined statement.

There is a lot of confusion about the DVD format, most of it by the original design, to prevent people from using the media they legally own. Anyway, libdvdcss2 is a library for playing encrypted DVDs. It's not in the Ubuntu repositories, but can be obtained from Medibuntu by individual users. What's important is, libdvdcss2 is not required for playing unencrypted DVDs. I happen to have a couple of those and they play just fine in Totem.

---

### Post by LinuxFox on 2011-01-18
> **mikewhatever said:**
> Perhaps you could quote the exact statement or post a screenshot of it, and we can then discuss what the meaning is. I can't possibly account for your personal impression of an undefined statement.

There is a lot of confusion about the DVD format, most of it by the original design, to prevent people from using the media they legally own. Anyway, libdvdcss2 is a library for playing encrypted DVDs. It's not in the Ubuntu repositories, but can be obtained from Medibuntu by individual users. What's important is, libdvdcss2 is not required for playing unencrypted DVDs. I happen to have a couple of those and they play just fine in Totem.I can't post a screenshot as it was during the install process and as far as I understand, I can't take a screenshot of the installation progress.  I was installing Ubuntu 10.04 for the record.  I'll try searching online for a screenshot of it.

---

### Post by uRock on 2011-01-18
Just install Fluendo DVD Player and enjoy.

---

### Post by LinuxFox on 2011-01-18
> **uRock said:**
> Just install Fluendo DVD Player and enjoy.Thanks for the suggestion uRock, it's nice to see Fluendo giving Linux users legal options to enjoy media.  But I'm a bit concerned about digital downloaded software is if it could be backed up to CD or not.  I prefer a physical copy in the event I need to re-install.  At least my Windows DVD player is on a CD.

Anyway, the message I was talking about is found in [this article]("http://www.omgubuntu.co.uk/2010/03/preview-the-new-installation-slides-for-ubuntu-10-04/").  In the screenshot is the message I was talking about.  They make it seem DVD works out of the box.  Which is why I ask this question.

---

### Post by uRock on 2011-01-18
You can buy fluendo via the Ubuntu Store as well. I just install libdvdcss2.

---

### Post by LinuxFox on 2011-01-18
> **uRock said:**
> You can buy fluendo via the Ubuntu Store as well. I just install libdvdcss2.Maybe I'll consider it since I live in the US and can't use libdvdcss2 due to laws here.

What about recorded DVDs, they shouldn't need libdvdcss2.  When I was trying the family video DVD out (due to the slide show during install), nothing played back.  So why even advertise it if packages need to be installed?

---

### Post by mikewhatever on 2011-01-18
> **LinuxFox said:**
> I can't post a screenshot as it was during the install process and as far as I understand, I can't take a screenshot of the installation progress.  I was installing Ubuntu 10.04 for the record.  I'll try searching online for a screenshot of it.

Got the screenshot. It says:

> Ubuntu is ready to play videos and music from the web, from CDs and DVDs
[http://www.dedoimedo.com/images/computers_years/2010_1/lucid-slide-2.jpg](http://www.dedoimedo.com/images/computers_years/2010_1/lucid-slide-2.jpg)

Oh well, I'll have to say, it can likely be interpreted as if it's ready out of the box. On the other hand, with a little stretch of imagination, one could say it means the tools for playing music and videos are readily available, some out of the box, and others a few clicks away.
I guess, there only so much you can put into a slideshow.

---

### Post by kansasnoob on 2011-01-18
> At least my Windows DVD player is on a CD.

If you prefer installing every bit of software via CD maybe Linux just ain't your thing :)

I'm not being snotty saying that, but I've helped bring dozens of seniors out of the stone age that was Win 98/ME to either Ubuntu or Mint (or a derivative) and quite often their kids gripe to me about Linux' software management.

I always tell them, "if you prefer the Windows way just stick with Windows." I then usually suggest they buy their folks a new computer and return the parts and pieces I usually provide for free :wink:

---

### Post by mc4man on 2011-01-18
> What about recorded DVDs, they shouldn't need libdvdcss2
"out of the box" it probably won't support any vidoe but ogv.
For dvd's - non encrypted you still need to install some gstreamer plugins (ugly, and then usually bad and ffmpeg ones.

The gnome-codec-install package which is part of the default install should pop up, find and install the gstreamer plugins
It is somewhat broken in lucid as it won't install the ugly plugin for "DVD Source", though it will install the ugly and ffmpeg if needed.
> 
can't use libdvdcss2 due to laws here
Highly debatable - only decss was found to be illegal, libdvdcss2 is different in a critical way and has never been, nor likely to ever be challenged

---

### Post by LinuxFox on 2011-01-18
> **mikewhatever said:**
> Got the screenshot. It says:



Oh well, I'll have to say, it can likely be interpreted as if it's ready out of the box. On the other hand, with a little stretch of imagination, one could say it means the tools for playing music and videos are readily available, some out of the box, and others a few clicks away.
I guess, there only so much you can put into a slideshow.Yup this was what I was talking about.  The screen made me curious to try a DVD out to see if it would work.  I used a family video on a recorded DVD since I know store bought DVDs do not work.  Makes no sense really since it gives the "out of the box impression".  By the way, thanks for taking a screenshot.

kansasnoob: Actually I like Linux and don't mind the way of installing software.  It's just if I spend money on software, like that Fluendo DVD player, I prefer to have a disc or be able to back it up in event something goes wrong and I need to re-install.  I don't think you were being "snotty", it's just if I buy software, I'd like to have a disc with a backup, that's all.  I'm sorry if I didn't clarify that. ;)

---

