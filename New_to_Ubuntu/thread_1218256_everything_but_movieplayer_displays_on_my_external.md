---
title: "everything but movieplayer displays on my external monitor"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by PembyR6er on 2009-07-20
I'm running Ubunbtu on my notebook with an external monitor.  Everything displays on the external monitor EXCEPT movieplayer which will only play on the notebook screen.  I've tried everything and searched to see if others have had this problem but to no avail.  It would be one thing if it was everything, I'd know I had a setting wrong but when it's only this app? Flash movies embedded in websites play just fine on the external monitor.

Help, it's driving me crazy trying to figure out this issue.:(

Thanks,

Matt

---

### Post by NESFreak on 2009-07-20
had a similar issue some time ago. It had something to do with the video being outputted directly to the first screen.

press alt-F2 and run gstreamer-properties go to video and press test. Does this output works on your secondary screen? if not try selecting no Xv from the plugin dropdown.

---

### Post by PembyR6er on 2009-07-20
tried that, got a test pattern (with a box containing old time tv snow in the bottom right corner) in the test window when I changed to xv but still no video on the external monitor

---

### Post by NESFreak on 2009-07-20
wouldn't know what else could be causing this, but maybe you could consider using another mediaplayer, like mplayer or vlc. (both are in the repositories)

--edit
im sorry i just saw the kubuntu tag, i wouldn't know how to change the settings of kubuntus default mediaplayer, id still recommend vlc anyways.

---

