---
title: "How to fix sound that did work in 9.04"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by thebigbluecan on 2009-12-09
I have a spdif Output on my computer... it worked in Ubuntu 9.04 and it doesn't work in 9.10... i poked around the new sound settings and none of them work. The picture below was the settings i used in 9.04 And yes i had to manually do that setup in 9.04 to get the spdif to work. 

[IMG]http://img22.imageshack.us/img22/9026/opticalaudioubuntu.png[/IMG]

Please help me out :)
PS: is there a way to revert to the sound setup from 9.04 on 9.10?

---

### Post by thebigbluecan on 2009-12-10
Anyone have any ideas?

---

### Post by Geoff918 on 2009-12-11
The config files were more than likely overwritten. Did you have a guide that you followed?

There's an extensive sound problem troubleshooting guide available here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

see also:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by thebigbluecan on 2009-12-11
I did a fresh instalation... so I doubt files got overwritten... and I did install twice. Both times it didn't work. Ill check out the links you provided. Thanks.

---

### Post by thebigbluecan on 2009-12-11
I got it to semi work... I went to Sound preferences and selected my spdif output... 
[IMG]http://img16.imageshack.us/img16/9343/screenshot1fv.png[/IMG]
Then went into terminal and typed "alsamixer" and turned up the volume for the spdif...
[IMG]http://img16.imageshack.us/img16/241/screenshotxl.png[/IMG]

........ On the older releases I had the option to play through my analog computer speakers and my spdif at the same time... This way I have to switch manually and go into terminal to turn it up every time I want to switch to spdif. 

But it kinda works... Thanks... I got some of the info from your second link. :popcorn:

---

