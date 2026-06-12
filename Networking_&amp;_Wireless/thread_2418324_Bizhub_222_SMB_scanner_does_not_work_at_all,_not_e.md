---
title: "Bizhub 222 SMB scanner does not work at all, not even ftp server"
date: 2019-05-05
forum: Networking &amp; Wireless
---

### Post by drazenprado on 2019-05-05
Greetings. It is a long time since I ask a question in forums, but now I am broke and I do not know what the hell do. You can skip the history, is irrelevant. 
Server: poweredge 2800
Raid 0 /
Raid 5 /home /srv
Network 100 mb (even with 1gb nics)
Network architecture all with static ip, no dhcp server
Modem=> switch tp-link tl-sf1024
Switch => -WiFi router
                   -other pcs, and the server too
                   -other switch tp-link tl-sf1005d
                            =>switch1005d 
                                 -the bizhub 222 printer

---the history behind---
I was using rdp server in windows, but as the server will soon be open to host a mail and web server and even a backup server, I am sure that windows is not sure at all for that. 

So I began with xrdp (broken in 18.04.2)(a dude has made a repo of a compiled xrdp and that works, see it in c nergy) (soon i will make LTSP, but no time right now). Later, I installed office 2007 with wine (they do not like open office) and even outlook is working (need to test a bit more). The printer that they use is a KONIKA MINOLTA BIZHUB 222 and it worked in windows, for work in Linux I got to install a custom pdd file in mint forums, worked but need to test the double side print. 
--- end of introduction ---

What matters here is that, I broke my mind trying to make scanner work. But I am unsucesfull until now. 
I tried a couple of tutorials for samba, one in ubuntu (worked a bit)and other in techrepublic(not worked at all). 
I can access write and read the shared samba folder from the same server, and from a windows pc which is behind another switch behind the 1005d. But when I config the printer to send with smb protocol to that folder, it does not work at all. How may I debug or see the log of this? 
I even tried to use ftp server but I have the same error, and did not work neither in the windows pc. 
Finally giving up, I shared a folder in the windows pc and worked so stupidly easy, I am thinking make that pc a smb server and my server dell access that shared folder; but it is not the right way, just a basic workarround. 
Btw, I tried to make a VM with virtualbox, and share that a folder. Did not work at all, neither from server, neither inside the VM(I mean, accessing to the folder with smb; with file explorer it works), neither windows pc. Maybe because it is a custom cutdown version, so I will update another try later with a full windows 7 iso. 
Btw, I googled a lot but I only saw the same problem with no solution but a guy that made chroot and not sure what else.

---

### Post by drazenprado on 2019-05-05
[https://ubuntuforums.org/showthread.php?t=866767This](https://ubuntuforums.org/showthread.php?t=866767This) is one of those thread

---

### Post by drazenprado on 2019-05-05
Update : I tried with virtualbox and a windows 7 ultimate stock iso. Share a folder and that... Worked... Finally it worked. May I use a xp vm for this pourpose. I will try later with a ubuntu vm. Maybe it works xD

---

