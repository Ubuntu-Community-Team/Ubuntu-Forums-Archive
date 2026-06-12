---
title: "LDAP PXE bott net cafe linux windows clients. linux kubuntu server"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by Apollo101 on 2008-02-20
Hi, i have 3 internet cafes having a server and 30 clients in each cafe. (10 windows 20 linux.) i want to pxe boot them all (so every time its rebooted. people get same os and confgs, no messes. no virus. and the boot image (on server) should not be effected. (read only). want to make linux as my server. 
2. i want to make a user account (in all those 30 machines) to stop or screen lock after every 30 minuts (no matter what. idle or not. wana force it.(runing apps should not be closed, oppertunity should be there to resume by typing pwd and resuming to use those running apps again) the user just have to enter password again.
 3.for every such event of unlocking screen and giving pwd.(i 'guess' thats logging in?) i get stats on server.. possible? do i need any thing else. like ldap ? any suggestions? i 'think' i would have to use LDAP and put the home directories of linux clients + windows clients on the server.?

i thought of a script to lock screen every 30 minuts but as the script will be running all time, suppose a persone sits for 30 mins. then 15 min gap. and other person comes . after 15  mins. the script will close the screen since 15 mins of usage have passed (15min idle time + 15 of second person usage) = doesnt looks good.

so any brighter ideas..?

 i need to lock down after 30 mins of 'unlock event'. not just locking after every 30mins.   i hope you got the point.

or any other way? may be make accounts that auto close screen after 30 mins of login time. or may be log out user.? (but i want the apps to be runing in background so that user can resume.
please feel free to give ANY alternatives. thanks

---

