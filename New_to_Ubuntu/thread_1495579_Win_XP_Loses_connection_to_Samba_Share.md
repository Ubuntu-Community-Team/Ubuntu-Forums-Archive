---
title: "Win XP Loses connection to Samba Share"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by elcidsps on 2010-05-28
Greetings all.  I have Googled this to no end and I still cannot find resolve to this issue.  

I have a samba share set up on a Ubuntu Linux box and I am able to access the share from my WinXP box after bringing up the Linux box.

If I attempt to access the share the next morning  (both boxes have been on all night) the connection to the Linux box fails (connection timed out).  

I have to reboot the Linux box to get the share back. 

Is there  a setting I need to configure that doesn't timeout the connection?

There are no firewall issues here. 

Thanks!

---

### Post by -humanaut- on 2010-05-28
I think after X amount of time the windows end gives up looking for your connection I have had a similar problem where win xp would stop looking for me after just a few hours. Then again I never properly set up samba though I just worked around it.

---

### Post by elcidsps on 2010-05-28
So Linux cannot be used as an effective file server in a hybrid network?

---

### Post by -humanaut- on 2010-05-28
It can be if it's setup proper and the windows end is setup proper as well. I never bothered setting up XP because I only needed it for short periods of time.

---

### Post by dixonstalbert on 2010-05-28
hi elcidsps

It sounds like a conflict in the master browser election on your LAN.

This link explains about samba master browser election:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html)

The link describes setting up things so your linux box will be the master browser; ie the computer on the LAN that is on the most and will host the browser list. 

It sounds like right now your shares work when XP is the master browser, but when your linux box eventually wins the election, things stop.

The quick and dirty fix is to set your OS level on in smb.conf in linux box to '1' so linux always loses and XP will remain master browser. (then reboot) However if your intent is to end up with linux being the master browser, you want to follow the instructions on the link then reset ip stack on XP and reboot it. ( google netsh ip reset XP and browstat.exe for info on this.)

As I am sure you have read, samba can fail for many many reasons and the chances of a single 'stab in the dark'  guess of a problem is going to work are not great. Every guide recommends backing up smb.conf re-installing samba and carefully going through step by step guide from scratch like ubuntuforums "setting up samba shares" to give you a clean start. 

So, hope this helps

Dixon

---

