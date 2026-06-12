---
title: "Youtube issues"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by prad_G on 2010-01-17
Hi,

I am using ubuntu 9.04. I have seen two problems with youtube that I want some clarity on. 

1. Youtube mute: Even if the Mute button is pressed in the youtube video window i still get the sound. How is this possible. I have tried different browsers, Mozilla, opera. I am a bit baffled with this. Can anyone shed some light on this?

2. Youtube Buffering: Sometimes I get really bad internet speeds due to which I let the video on youtube buffer completely before watching it. now the problem is that if the video has buffered 50% and I slide the seek bar to the start so that I can watch the video(buffered part) all I see is that it starts to buffer again instead of showing me the already buffered part. Again a very strange situation.

PS: Never faced such issues in Windows. Am I doing something wrong here cos these things are not related to a OS in anyway. these are the website functionalities.

---

### Post by prad_G on 2010-01-18
Guys,

anyone have any clue to this?

---

### Post by MarkC502 on 2010-01-18
Go to adobe flash test site and see what it says about your installed version and post that here. You may not have the newest one available

Heres the site , go there and click "test"

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

Do that and post the version.



MINE SHOWS

You have version 
10,0,42,34 installed

---

### Post by Captain_tux on 2010-01-18
I think the first issue may be a hardware issue with your equipment(?). What happens when press mute on your machine?

The second issue sounds like a browser issue. Does the same thing happen with other browsers?

---

### Post by jward3010 on 2010-01-18
> **prad_G said:**
> 
1. Youtube mute: Even if the Mute button is pressed in the youtube video window i still get the sound. How is this possible. I have tried different browsers, Mozilla, opera. I am a bit baffled with this. Can anyone shed some light on this?

This happens to me sometimes, to be specific when it happens none of the buttons work. It's been quite recent so it could be a recent Flash update that causes it or something YouTube have done with their player. As far as I know it's also happenend to me in Windows too, so it's not just a Linux flash issue.

If it's only the mute button, in regards your problem well maybe something else is going on.

---

### Post by J V on 2010-01-18
second issue is bad programming on the part of youtube, its "worked" like that forever... you can open your /tmp folder and watch from there though, much better/quicker etc...

Edit: If jward is the issue, you need to install 64bit flash for linux, google it, then install, it will fix the button issue and possibly the sound issue...

---

### Post by MarkC502 on 2010-01-18
I am using Ubuntu 9.10 x64 with flash and my mute works fine and I have no stream latency issues at all. Highdef video works as well as full screen and video downloader can assimilate all so there are solutions to your problem.

I would still suggest you investigate your flash version.

---

### Post by jward3010 on 2010-01-18
> **J V said:**
> second issue is bad programming on the part of youtube, its "worked" like that forever... you can open your /tmp folder and watch from there though, much better/quicker etc..
That sounds interesting, give us some details on doing that. Do you use Movie Player or VLC?
> Edit: If jward is the issue, you need to install 64bit flash for linux, google it, then install, it will fix the button issue and possibly the sound issue...
I've always the standard Ubuntu repositories install and maybe he'll have to use the official Adobe version, the gzipped one. It's always been a tad more stable, usually anyway.

---

### Post by Dreadsen on 2010-01-19
> **jward3010 said:**
> That sounds interesting, give us some details on doing that. Do you use Movie Player or VLC?

I've always the standard Ubuntu repositories install and maybe he'll have to use the official Adobe version, the gzipped one. It's always been a tad more stable, usually anyway.


Yes i would also like to know how to do this too

---

### Post by prad_G on 2010-01-19
I investigated my flash version and it showed version 9.x.x.x. went through a lot of forums on how to install the 64bit version of ver 10. after trying all i am now in a situation where videos dont play in youtube(Mozilla) but somehow all the problems are gone if i use opera. 

I find Opera to be slow sometimes and I want to continue using Mozilla. Can someone explain how to install the latest version of flash.

PS: if i try to download from the Adobe website, I get an error message saying Jaunty package missing or something on those lines. and I have tried the extracting the latest version and putting it in the /.mozilla/plugins folder but to no avail.

---

### Post by pricetech on 2010-01-19
Your mileage may vary, but this is the best way I've found to do 64 bit flash.  My "notes to self":

```
Download the 64 bit Flash Player from Adobe Labs.  I suggest you go here:
http://labs.adobe.com/
and look for the latest flash listed under Recent Releases since it seems to be a moving target.

Extract the archive and copy libflashplayer.so to the following locations:  NOTE: They may not all exist on your particular installation.
/usr/lib/firefox/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/mozilla/plugins
/usr/lib/opera/plugins
/usr/lib/seamonkey/plugins
/usr/lib/xulrunner-addons/plugins
/home/username/.mozilla/plugins
```

Yes, there may be some redundancy there, but I recently went through some new headaches with flash and this is how I fixed it.

Just make extra sure you are getting the 64 bit flash and not something else.

---

### Post by tom.swartz07 on 2010-01-19
> **prad_G said:**
> I investigated my flash version and it showed version 9.x.x.x. went through a lot of forums on how to install the 64bit version of ver 10. after trying all i am now in a situation where videos dont play in youtube(Mozilla) but somehow all the problems are gone if i use opera. 

I find Opera to be slow sometimes and I want to continue using Mozilla. Can someone explain how to install the latest version of flash.

PS: if i try to download from the Adobe website, I get an error message saying Jaunty package missing or something on those lines. and I have tried the extracting the latest version and putting it in the /.mozilla/plugins folder but to no avail.

Hi guys,

Follow the link in my signature for x64 flash. Ive tried about 5 different ways to get it to work and this one is the best method.


Make sure you remove all flash-related packages from synaptic before you start!!
Hope this helps!

---

