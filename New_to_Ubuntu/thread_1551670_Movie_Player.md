---
title: "Movie Player"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by XenoG on 2010-08-12
Hello,

Having problems with the Movie Player and Youtube,

I have installed the required plugins but when trying to watch I video I get -

**[SIZE=1]Could not open location; you might not have permission to open the file.[/SIZE]**


I have followed the guide [here]("http://linuxdesk.wordpress.com/2009/09/22/could-not-open-location-you-might-not-have-permission-to-open-the-file-totem-movie-player/") to try and fix this but I am using Ubuntu 10.4 and this doesnt appear to have the Youtube.py file in the Plugin directory.

Can anyone advise what to try next?

Thanks.

---

### Post by Bodsda on 2010-08-12
> **XenoG said:**
> Hello,

Having problems with the Movie Player and Youtube,

I have installed the required plugins but when trying to watch I video I get -

**[SIZE=1]Could not open location; you might not have permission to open the file.[/SIZE]**


I have followed the guide [here]("http://linuxdesk.wordpress.com/2009/09/22/could-not-open-location-you-might-not-have-permission-to-open-the-file-totem-movie-player/") to try and fix this but I am using Ubuntu 10.4 and this doesnt appear to have the Youtube.py file in the Plugin directory.

Can anyone advise what to try next?

Thanks.

Probably a stupid question, but have you tried running 'totem' as root to confirm that it is actually a permissions issue?

Bodsda

---

### Post by jtarin on 2010-08-12
> **XenoG said:**
>   doesnt appear to have the Youtube.py file in the Plugin directory.

Can anyone advise what to try next?

Thanks.sudo apt-get install totem-plugins

---

### Post by Bodsda on 2010-08-12
> **jtarin said:**
> sudo apt-get install totem-plugins
```

totem-plugins is already the newest version.

```

I have the same issue. 

Bug report: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/323649](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/323649)

Bodsda

---

### Post by jcolyn on 2010-08-12
> **jtarin said:**
> sudo apt-get install totem-plugins

Totem would not run quicktime movie files for me but gecko does..

---

### Post by mapes12 on 2010-08-13
Have you gone to Synaptic and installed ubuntu-restricted-extras

Then I always install the codecs recommended at [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

No problems after that.

---

### Post by karenyyng on 2010-08-21
Hi mapes12, 

I followed your instruction to install the ubuntu-restricted-extras and medibuntu codecs but still no luck. 

Can you show what codec you installed exactly? 
Thanks a lot for you help.

---

### Post by mapes12 on 2010-08-21
System>Admin>Synpatic "vlc" then try the vlc player.

---

### Post by Insperatus on 2010-09-06
> **XenoG said:**
> Hello,

Having problems with the Movie Player and Youtube,

I have installed the required plugins but when trying to watch I video I get -

**[SIZE=1]Could not open location; you might not have permission to open the file.[/SIZE]**

Can anyone advise what to try next?

Thanks.

I'm having the exact same problem.  Any new ideas?

---

### Post by InuY4sha on 2010-09-09
I also have the issue (with ubuntu 10.4) and definitely there's no youtube.py in there... by having a peek at the patch it clearly appears that the issue is not related to permissions I tried to watch the from totem console log  and it gave me this output when trying to start the youtube video:

```
** Message: Error: "http://www.youtube.com
/get_video?video_id=723b9yQR6Rk&t=vjVQa1PpcFPk91CVJX9uiWPSgQOVvs-4ppqeOwdq69U%3D&fmt=18": 
Not Found
gstsouphttpsrc.c(1096): gst_soup_http_src_parse_status (): 
/GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstSoupHTTPSrc:source:
404 Not Found

```

I believe that it's a problem in the format of the url address: I tried to open the log printed url from firefox and it gave me a blank page, so I assume that 404 error is the natural outcome.

All this led me to look for the place where the url address is built up but I had no clues and couldn't find it.. 

Looking for a more knowledgeable guy to take over the search from here!!!
R

---

### Post by winchendonsprings on 2010-09-24
same here

>               **Movie Player**
         Hello,

Having problems with the Movie Player and Youtube,

I have installed the required plugins but when trying to watch I video I get -

**[SIZE=1]Could not open location; you might not have permission to open the file.[/SIZE]**


I have followed the guide [here]("http://linuxdesk.wordpress.com/2009/09/22/could-not-open-location-you-might-not-have-permission-to-open-the-file-totem-movie-player/") to try and fix this but I am using Ubuntu 10.4 and this doesnt appear to have the Youtube.py file in the Plugin directory.

Can anyone advise what to try next?

Thanks.     

---

### Post by TCHebb on 2010-09-24
I just checked on my Totem, and I have the same problem. When was the YouTube plugin last updated? YouTube might have changed the video URL format since then.

---

