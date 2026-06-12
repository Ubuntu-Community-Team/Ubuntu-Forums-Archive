---
title: "Movie Questions"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by lotusalive on 2010-09-16
Hi everyone:  

1) Web is changing, causing me not to be able to stream movies from free sites, shutting me out because I'm not using W's, now, where it never used to be an issue.

2) Last night I tried to watch a Netflix rented Disc on my drive and the last 3 scenes were copyright encrypted so it would not play the last 3 scenes of the Merchant of Venice for me.  :popcorn:

3) I'm wondering if I should just upgrade to Karmic, and if that will help some of these issues, and also make the behavior of the whole PC & Internet less slippery & glassy with about a 2 second delay / LAG most of the time. :(  Slippery is GREAT when there's no delay / lag !  As I have not been enjoying the delayed behavior (most of the time), for about the last 3 mos.

All suggestions welcome & appreciated.  Thanks.):P

---

### Post by NightwishFan on 2010-09-16
Here is a link to help you, and the part in question to enable DVD playback.
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Open up a terminal and copy and paste the following command:
```
sudo apt-get install libdvdread4
```

Then after the command finishes, run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

Other sections in the link may be of use as well.

---

### Post by lotusalive on 2010-09-16
Wow, 'It's 'Christmas'':KS  Thank U NightwishFan, RA SO HUM :KS

---

