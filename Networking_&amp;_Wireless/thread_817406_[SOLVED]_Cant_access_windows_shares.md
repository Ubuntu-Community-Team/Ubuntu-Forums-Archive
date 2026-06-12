---
title: "[SOLVED] Cant access windows shares"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Trunk_z on 2008-06-03
Heyhey.

Been having a few problems with Nautilus since I upgraded to Hardy. 
I have several computers, all windows based which I would like to access files on. They are all accessible with a username and password.

The problem started off like this: [https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/207072) I think.. the problem has been going on since Hardy came out, I lost interest a little while ago, but have returned to the problem.

After following the advice in the bug report,  I can see all of the shares, but when double clicked I receive the following error message: 

"DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered"

It also adds it to the left hand side as if it has been mounted (I think this is normal?). When I click here, I receive this error message:

"Error: DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered
Please select another viewer and try again."

Same happens if I use the "Connect to Server" option, and using the IP rather than the hostname doesn't seem to make a difference easier.

I've tried reinstalling it (I'm a windows user, reinstalls always work).

I have been messing around with Firestarter a little bit, trying to get ICS working (a seperate problem however), but as far as I can tell, its not a firewall problem.

Has anyone got any advice on this problem please?

Regards,
Chris

---

### Post by dmizer on 2008-06-03
i have a two part answer.  part 1 involves getting more information, part 2 involves an alternate fix.

part 1:
i cannot find any like errors in google.  this most likely means that the patch you applied was either applied incorrectly, or the patch has an error in it.  your best solution for resolution on this is to post your findings in the bug report and wait for a reply.

part 2:
you can ditch the unreliable, buggy, and slow (since breezy) nautilus/gvfs, and use cifs to mount your windows shares instead.  if you are interested in this solution, please see the second link in my sig.

---

### Post by Trunk_z on 2008-06-05
Hi again,

Thanks for the reply.

I'm just waiting for an email back from Launchpad so that I can register and post my problem there.

I had a look at the cifs mounting option. It works fine, well, as long as I use the IP address of the machine it does. Although I don't have a problem using the terminal options, I still like to use a GUI sometimes. I had a look into xsmbrowser, which seems to do everything I need, the only problem with it is it can't mount shares. When I run it from the terminal, it give me the following error:

"mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)"

This happens when run as root or normal. I thought that if I created a folder, (/media/Shares/) and changed the permissions, it would help. But this didn't work either.
Is there a way to get this working? Or should I just stick with the command line and cifs?

Regards,
Chris

---

### Post by linux6994 on 2008-06-05
Try thus configuration it works fine for windows shares. The default workgroup is workgroup not to hard to remember anyway. This will give you a sharing tab under file properties. I am networked with XP and Vista (2) using the Ubuntu (2) as file and printer servers. Good Luck.

---

### Post by Trunk_z on 2008-06-06
Hey guys,

Thanks for all your replies.

In the end, I decided to use xsmbrowser, however, this wasnt working correctly. I fixed by doing the following.

I realised that the program wasn't entering the username and password into the mount command, so I edited the file (details below). I hope this doesn't break any rules or anything, apologies if I did.

What I did (after installing through Synaptic) was:

Open terminal

typed in: sudo gedit /usr/bin/xsmbrowser

found the line: spawn mount -t smbfs -o ip=$computer_ip_num,workgroup=$workgroup,guest,rw //$computer/$share_m $mount_path

and changed it to: spawn mount -t smbfs -o ip=$computer_ip_num,workgroup=$workgroup,username=$user_name,password=$password,rw //$computer/$share_m $mount_path

So basically removed 'guest' and added in the username and password bits.



Still has to be run as root to mount shares, not that hard. As long as you use the 'Version >= 2.0.7' it works fine for me. Nautilus still doesn't like them, but i find xsmbrowser quicker and more responsive.

If you have questions on it I'll do my best to answer them. Please bear in mind that I am fairly new to the Linux world, so might give the right answers, but I'll try.

Regards,
Chris

---

### Post by dmizer on 2008-06-06
glad you got it working.

xsmbrowser is written for X11, which likely means it's pretty ancient, so i did some digging and there are a few things you should be aware of:

xsmbrowser is not currently being maintained.
the last update to xsmbrowser was in may 2007.  before that it was august 2006.
the developer's website is no longer available.
source: [http://www.freshports.org/net/xsmbrowser/](http://www.freshports.org/net/xsmbrowser/)

if you have problems with it now, they are likely to get worse with time as the development of samba progresses.

---

