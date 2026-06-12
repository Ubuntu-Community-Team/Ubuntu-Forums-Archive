---
title: "Samba Problems"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by logical_thought on 2007-05-26
For the last two days, I've been unable to connect to my Windows shares or browse my network. I tried looking at the shares using *smbclient -L 192.168.1.46 -U%* and got the error:

> cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.1.46.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.46 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[HOME] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

I haven't changed any setting on my laptop, or on the XP machine. Also, I have a Ubuntu server that can connect fine with the command line.

I'm relatively new to Linux, and would appreciate any help on this problem as I need this ability to connect to shares.

---

### Post by logical_thought on 2007-05-26
Ok, after playing around with the smbclient command I found that it will show the shares if I force it to use the username guest with a blank password. I do not know how to force the GUI to use the guest account, and I would like to use the GUI.

---

### Post by dmizer on 2007-05-26
if you're insisting on using the gui to connect to your share, be aware that your performance will be fairly poor.

to connect using gui, click on places > connect to server > change the service type to "windows share" and fill in the information (including username) > click connect.

---

### Post by tailwindALWAYS on 2007-05-27
bmizer, what would be the command that it runs.  i'm having problems connecting to a server on a Windows AD domain unless I use the GUI 'Connect to Server'.  thanks!

---

### Post by dmizer on 2007-05-27
for active directory authentication ... you're looking at a real honest to god nightmare.

here's a howto i found which looks promising: [http://developer.novell.com/wiki/index.php/Feisty/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication](http://developer.novell.com/wiki/index.php/Feisty/HOWTO:_Configure_Ubuntu_for_Active_Directory_Authentication)
and another i found on the forums (but beware it's old, so you may have to dig through the thread for answers):
[http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510)

i cannot vouch for its success as i've not yet been brave enough to tackle that one.  i'll probably work on that some time in the near future though ... when i'm feeling particularly masochistic, as it's a hole in my knowledge i'd like to fill in.

---

### Post by t2000kw on 2007-05-27
I have a home network, got the Windows machine to print through the linux machine where it's connected to, but can't get file sharing working properly. 

I did set up a Windows user account with the same username and passowrd as used in Ubuntu.

---

### Post by logical_thought on 2007-05-27
Thank you dmizer. That worked, but only when I used the ip instead of the computer name.  Well, at least it works.  :)

I'm curious, is there a command to send or receive a single files to/from a Windows share. Kind of like scp. If there is something like that, I would be glad to drop the GUI.  The only reason I used the GUI in the first place was because it was easier when I only wanted a single file.

Edit: I found out that smbclient can be used as a ftp like program, so I don't need the last question answered.

---

