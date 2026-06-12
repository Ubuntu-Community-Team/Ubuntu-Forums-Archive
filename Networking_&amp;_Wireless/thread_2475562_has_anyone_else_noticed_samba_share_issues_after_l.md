---
title: "has anyone else noticed samba share issues after latest update to 18.04lts?"
date: 2022-06-01
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2022-06-01
Ever since the last update done under 18.04lts, anything on a samba share on a networked drive is taking several seconds to a minute to ls - both on the command line and in nemo; videos played over that connection pause and buffer; any action taken on a file takes several seconds to a minute to even begin...

I have rebooted every computer involved; rebooted the router; stopped any programs even thinking about looking at the shared drives... I don't know anything else to try. I didn't have this issue until after the last update, so... Has anyone else noticed this?

---

### Post by TheFu on 2022-06-01
I patch on Saturday. Haven't noticed any samba issues with 18.04. Did the update happen since then?  I have 2:4.7.6+dfsg.  According to my apt-cache, it hasn't been updated since Feb 1.

Could it be an issue with Windows? Did anything change there?  I stopped patching Windows when MSFT changed the EULA to give themselves the right to take, patch, spy on everyone.

Slowness in network access could be something else, perhaps a DNS or mDNS or Avahi issue?

Video playback over samba has always been known to be less good when compared to NFS. That's been reported in OSMC and Kodi forums.  Of course, if the playback client is Windows, then I'd either try lower bitrate/resolution videos or switch to a streaming protocol. I use DLNA, which has flaws of other sorts, but not in stream playback.
But for Unix-to-Unix file sharing, NFS is the best answer.

---

### Post by rebeltaz on 2022-06-01
It's weird. This morning, everything is working fine again. I don't know. That's the kind of thing I get around here...

As for samba versus nfs... when I first set this system up, it was years ago. I didn't know about nfs back then and I had a couple of systems still running windows, so I set i up the only way I knew at the time for everything to be able to talk to each other. Over the years, I've since gotten rid of all the windows systems but one still in the shop. I still need that one to be able to access the shared drives, so... Generally, I don't have issues with the samba shares, though. I'll take a look at nfs and maybe even dlna. 

I appreciate the reply.

---

