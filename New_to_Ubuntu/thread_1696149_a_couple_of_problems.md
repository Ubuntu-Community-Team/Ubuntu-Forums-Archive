---
title: "a couple of problems"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by ben889 on 2011-02-27
update manager is showing a orange and yellow triangle last couple of days and it  is saying failed to download repository information. 
details it shows

W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

also my video play back freezes for a couple of seconds then goes and then repeats freeze and play any one know how i should go about starting to trouble shoot this?


thanks Ben


sorry im using 10.10

---

### Post by thefasterblueone on 2011-02-27
What version Ubuntu are you using?

---

### Post by ben889 on 2011-02-27
i am using 10.10

---

### Post by emoguitarist06 on 2011-02-27
> **ben889 said:**
> update manager is showing a orange and yellow triangle last couple of days and it  is saying failed to download repository information. 
details it shows

W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

also my video play back freezes for a couple of seconds then goes and then repeats freeze and play any one know how i should go about starting to trouble shoot this?


thanks Ben


sorry im using 10.10

**First Problem**
For some reason that repository source isn't working. You can remove it.
In 10.10 the "Software Sources" menu is hidden so go to System > Preferences > Main Menu on the left side scroll down and select System find Software Sources and make sure it's checked and Close

Now System > Administration > Software Sources (type password when prompt)
"Other Software" tab

Highlight [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main/source/) 
Click remove
Highlight [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/maverick/main)
Click Remove

**Second Problem**
What are your computer specs and what video card?
What program are you using when it freezes?
Did you check System > Administration > Additional Drivers and install any drivers (like Nvidia) and restart your computer?

---

### Post by ben889 on 2011-02-27
I have a acer aspire dual core amd 1.8 with 2 gigs of ram a nvidia 7000m video. I know it isnt my hardware as the same movies will work in windows. I think i have the novoue drivers with the accelerated drivers the only other option for me in the 173 drivers but i chose the recommended ones. as for the media players it does it in movie player and vlc



thanks Ben

---

### Post by vivek.pandey on 2011-02-27
is your ubuntu updated? if not do that also check whether your media player is updated or not.. try updating from terminal if update manager is not working see if you get same problem then let us know :-)

---

### Post by ben889 on 2011-02-27
OK I am not getting that error with update manager any more.  As far as the media players both are the most recent. what would be the worst thing that would happen if i tried the 173. Nvidia drivers?

Thanks Ben


when watching videos the video will freeze for a couple of seconds but i will have the audio

---

### Post by ben889 on 2011-02-27
switched to 173 driver same problem. also 10.10 likes to crash on me not sure if it is all related.
how would i go about checking to see why my computer crashes? would like to get rid of windows all together but with these couple of problems ill have to keep a dual boot.


Thanks Ben

---

### Post by ben889 on 2011-04-10
sorry for not marking this solved all issues are solved. just wish adobe would support linux more.

---

