---
title: "maxemum tv guide problem... ..."
date: 2009-12-01
forum: New to Ubuntu
---

### Post by techno-mole on 2009-12-01
hello.

I have run into a small problem with maxemum tv guide, i normally install it using synaptic and then i follow this how to - ```
http://ubuntuforums.org/showthread.php?t=121437
``` and in the past it has always worked a treat, but today for some reason its not, everything goes fine until i hit this step ```
tv_grab_uk_rt --output ~/.xmltv/tvguide.xml

```
after i run this in terminal it will start downloading what it needs to, but after it gets to about 36% it stops and gives this message - ```
http://xmltv.radiotimes.com/xmltv/1542.dat: Cannot decode string with wide characters at /usr/lib/perl/5.10/Encode.pm line 182.

``` i have never run into this in the past, so i am a tad puzzled.

i have all the required dependencies, and made sure that the libraries in the first section of the post are installed.

cheers in advance for any help.

---

### Post by Singing Dwarf on 2009-12-01
This has been reported as a fault:
[https://bugs.launchpad.net/ubuntu/+source/xmltv/+bug/471372](https://bugs.launchpad.net/ubuntu/+source/xmltv/+bug/471372)

I am getting the same issue - and it corresponds to the Community Channel (Freeview).  You could temporarily remove the xmltvid for this channel from the .xmltv file for that source and see if that resolves the issue for you, until such a time as XMLTV is updated.

---

### Post by techno-mole on 2009-12-02
i have downloaded a slightly more up to date version of maxemum tv guide from sourceforge, mine was 7.3.2-0 im now using 7.3.2-1 (dont know how much of a difference that makes) i did try various different channel sets, eg - channels for virgin media etc, but in the end i just selected 0 and picked my own channels, it is now working.

cheers

PS - whilst I was looking around the " ubuntu geek " website I found this - [http://www.tvbrowser.org/index.php](http://www.tvbrowser.org/index.php) it works quite well, and is easy to set up.

---

