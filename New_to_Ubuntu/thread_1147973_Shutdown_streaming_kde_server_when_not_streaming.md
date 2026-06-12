---
title: "Shutdown streaming kde server when not streaming"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Forbuto on 2009-05-03
I have Kubuntu server edition installed on an  x335 which I use to stream video, music throughout the house.  This is the only purpose I have for it and I'd like to figure out a way to have it automatically shut itself down when a machine in my house is not accessing its shared folders for a period of time (say 30 minutes).

I have 2 xboxes running XBMC with static IPs that access the files through samba shares.   Is it feasible to program a script to initiate the moment one of IPs of my xboxes connect.  Once the server confirms an xbox is accessing the files, it would scans every 10 mins or so to confirm if the xbox is still connected.  If it is, continue to scan every 10 mins, if not, schedule a shutdown of the server 30 mins from the current time. 

I hope I've explained it somewhat clearly enough.  If anyone has any experience with this or can point me in the direction of some decent tutorials/resources, it'd be appreciated.

Thanks

---

### Post by chuckyp on 2009-05-03
I guess its possible you could write a script to do it. I'm not aware of any software that would accomplish what you are wanting to do. But with a bash script it would be possible.

---

