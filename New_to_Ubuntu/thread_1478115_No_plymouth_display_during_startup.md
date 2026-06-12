---
title: "No plymouth display during startup"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by sunk8 on 2010-05-09
Well, I installed Ubuntu 10.04 some time back...
And also installed the 'ubuntusatanic' plymouth...
For about 15 days, there was no issue, and then one day the startup splash simply disappeared!
I was getting a nice display during shutdown, but none during startup...
Changed to the default plymouth, but issue wasn't resolved...
Tried solutions at most threads here, still no go...

Finally, today I was able to get the splash during startup; and just wanted to share the solution with you...
I have an on-board Intel display card, and I suspected that the display driver might be the problem...
Added this to the software sources...
_deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) lucid main_

Installed the latest drivers for my Intel 945 chipset...
And viola, I got the splash screen back!
Right now I'm running the 'solar' plymouth without any problems...

Just thought I'll share this with you...

---

### Post by [::AP::] on 2010-08-30
Trying it now, I have same graphics "card".

Hope this works. I *just* made a thread regarding the problem. If it works, I will mark as solved and post a link to yours. 

Thanks!

Yes, I know, kinda dead thread...

---

### Post by [::AP::] on 2010-08-30
Ah... never mind. 

My previous post - I got ahead of myself. 

Doesn't work - yet. 

Thanks though, I had 93 updates from that repo!

---

### Post by garvinrick4 on 2010-08-30
[I]The reason you are not getting Plymouth at startup is your graphic drivers are not starting before mountall package.
If you are interested read up on ureadahead and mountall

To run default plymouth at startup
[/I]

*Start graphic drivers first in boot #540801 launchpad*
  
 ```
sudo -i
``` ```
echo FRAMEBUFFER=y > [/etc/initramfs-tools/conf.d/splash]("file:///etc/initramfs-tools/conf.d/splash")
``` ```
update-initramfs -u
``` *ctrl/d*
  
 *exit* 


To run optional plymouth screens.
Choose what ever plymouth desired in synaptics such as solar and then run.





```
sudo update-alternatives --config default.plymouth 
```                                  ```
sudo update-initramfs -u
```

---

