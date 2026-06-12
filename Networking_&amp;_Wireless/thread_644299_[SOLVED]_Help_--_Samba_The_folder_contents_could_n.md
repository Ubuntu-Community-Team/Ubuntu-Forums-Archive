---
title: "[SOLVED] Help -- Samba The folder contents could not be displayed -- on the same comp"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by gilf on 2007-12-18
The problem:

1.) I create a folder on my Ubuntu desktop called "Transfer"
2.) I right click on it and set it to shared via Samba
3.) I go to Places>Network>Windows Network>*thiscomputername*.
4.) I see the folder "Transfer"
5.) I click on it
6.) I get error message: [COLOR="Red"]The folder contents could not be displayed. "Transfer" couldn't be found. Perhaps it has recently been deleted.
[/COLOR]

In other woerds I can't even open a shared file on the same computer via the samba network. This should be a piece of cake -- no problem with an unrecognized user or system password. I am the user who has created the folder.

I get the same results when trying to access this folder from another machine.

My system: Ubuntu 7.10  I use DHCP. I can see other computers on the network -- some allow folder access and others report the same problem when opening folders.

On the desktop, folder properties are as shown in the attached screenshot. Thinking this may be the problem, when I try to change "File access" lines and close the window, reopening it shows it is back to the state shown in the attachment. I'm not sure what the double dash means -- no access? or undetermined or not applicable or what?

Thanks!

---

### Post by froy02 on 2007-12-19
on the file permission, try  to choose also read and write.

---

### Post by gilf on 2007-12-19
Thanks Froy2 for replying. I have tried that. That didn't work.

I was able to resolve my problem, but I didn't ever determine what caused it.

The solution was to completely rewrite my /etc/samba/smb.conf file and follow the user and folder setups as outlined in the following post:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

The only variation I used from that complete setup was to use a folder in my home directory as my "Transfer" folder, and also I use DHCP so could not and did not did not allow Wins functionality.

It would have been nice to troubleshoot my old system to find out exactly what was causing the problem, instead of using the brute force method of completely re-doing smb.conf. But I didn't have time.

I suspect now that the file permissions weren't the problem.

[It may have been that I didn't set up samba  users and smbpasswds, as outlined in the above thread. I wasn't aware that normal users and passwords needed to be suplemented with special samba users and passwords -- it seemed like I didn't need to do this in an earlier linux setup I had (Kanotix) but maybe that was all taken care of by a script behind the scenes in that distro.

anyway, things are working as they should now, and I would suggest to others with samba problems that they visit the above referenced thread.

**EDIT**  I've noticed a fair number of hits on this thread, so I would now like to add thatI now use a GUI program that greatly eased Samba user and share setups, and doesn't reqire typing users into the terminal.

It's called** system-config-samba** and you can download and install it with synaptic.

To use it, you'll find it in the **System** menu under** Administration>Samba.**

First try double clicking on one of your shares in the window to see how you can alter its configuration and access permissions. Then try clicking on the **Preferences** menu and selecting **Samba Users**. Notice that you can edit or add them.

Hope this helps those who stumble upon this thread.

---

### Post by deebocean on 2008-05-23
thanks gilf, you are helpful

---

