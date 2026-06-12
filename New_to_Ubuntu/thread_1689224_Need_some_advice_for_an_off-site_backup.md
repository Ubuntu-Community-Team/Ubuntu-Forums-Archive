---
title: "Need some advice for an off-site backup"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by ClaytonHowell on 2011-02-16
I am wanting to make an off-site backup for my home and work pc. I work for home but my office is going to allow me to put a backup pc there. I was looking into using a monitor-less Ubuntu box for this. I was looking around and thought LuckyBackup would do exactly what I wanted. The only problem is that it is no longer being updated. I am on an extremely slow (64kb/s down a ton less up) internet connection at home but it is all I can get out on "the farm".

All I really need is:
The ability to backup cross platform remotely

The ability to VNC

The ability to remotely check the computers ip/port settings in the event of something getting screwed up on the router. T was thinking of maybe sending it an email and it replies with said info.

The ability to add data on the backup server and then via usb drive add it to my work pc (at home) and synchronize it with out it trying download it from me again.



If it was rather simple it would be a plus, I am no guru by any stretch of the imagination but I know how to read and use google. I think the vast majority of forums are the devil when it comes to trying to find information but am capable of using them.

Any information of any sort would be appreciated. Looking for ideas/apps mainly.

---

### Post by cariboo on 2011-02-16
If your want to do remote backups, I would suggest using rsync+ssh. The first backup may take quite a while due to your slow network connection, but after that rsync only backups up changed files.

For an rsync howto, have a look [here]("https://help.ubuntu.com/community/rsync").

---

### Post by ClaytonHowell on 2011-02-16
I think that is what I am looking for. Any idea of how to set the machine to auto notify if its ip or network settings change? So I can vnc in with out driving 40 miles to see why I can no longer vnc.

Also Is there a way to add data to the backup server and my work PC via a usb hdd and not have it try to download everything from my home pc? 
So if say I transfered some home videos from my camcorder to a usb hdd then added it to my backup server the next time I was in town (every 2 weeks or so.) Then added those same files to my home pc. Make the server verify that the information had not changed and continue to check for new or modified files and not try to download a bunch of 500 meg files I already added locally.

---

