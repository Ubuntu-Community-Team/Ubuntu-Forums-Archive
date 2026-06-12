---
title: "Problem with Samba and Windows network"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-10-05
Man, this is driving me crazy!  When I set up Samba, I was able to see and write to my windows machines on my local network, no problem.  But I couldn't see the linux server in Windows.

After much trial and tribulation, I finally got Windows to recognize the Linux server.  (I don't even remember what I did, unfortunately)

Everything worked fine for a couple of weeks.  Then, after updating my Linux server (using Ubuntu's autoupdate) suddenly, I can't see my Windows machines from Linux anymore.  However, I can still see the Linux server from Windows and write successfully.

What the heck is my problem???  Any help would be greatly appreciated.

---

### Post by guysmiley25 on 2006-10-06
This sometimes happens to me when I can't see my windows shares in linux.

I dont know why it happens and if you find out please share. I just just around it in the mean time just my mounting them blind.

$ mkdir winshare
$ sudo mount -t smbfs //windowsbox/sharedFolder winshare

Sorry I can't help much more than that.

---

### Post by Iowan on 2006-10-06
A few thoughts (none guaranteed any good):
How are you looking for the Windows machines? Connect to Server seems to work better than the alternative.
Though it shouldn't have, I wonder if the workgroup got changed on the Ubuntu box.  The Samba server is probably still set to serve the windows workgroup, but the actual host may not be a part.

---

### Post by zoon_unit on 2006-10-07
What's so bizarre about this problem is that Samba can read some Windows folders sometime, but fails most of the time.  So, it doesn't seem to be a configuration problem.

Any other ideas?

---

### Post by Charlotte on 2006-10-07
Hi,

what are the logs saying?
(var/log/samba/... log.smbd, log.nmbd, log.name_of_your_winbox, etc)

You might want to set the log level in the [global] section of your /etc/samba/smb.conf somewhat higher to have an output more significant than usual.

Hope that will help you.

In my samba installation I experienced while heavily testing curious things. All went well untouched but out of nowhere I couldn't log in into my samba machine and had to add the samba users with smbpasswd -a repeatedly.

Maybe it's nothing to be concerned over earnestly.

Good luck,
Charlotte

---

### Post by zoon_unit on 2006-10-07
Thanks for the suggestion.  I checked the logs and they're filled with copious amounts of errors similar to this:

```
[2006/10/07 17:24:41, 0] lib/util_sock.c:send_smb(765)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2006/10/07 17:56:41, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 192.168.xxx.xxx. Error Connection reset by peer
```

The log also contains some successful connections from my windows computer to the ubuntu server, so the problem is one way only.

---

### Post by Charlotte on 2006-10-08
Hallo again,

I am sorry for cannot offering an expert's advice so I suggest that you will check some Samba documentation on troubleshooting, i. e.
[http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html).

For me the error messages are pointing to authentication problems, but I am not an expert (s. a.).

Good luck and keep us updated
Charlotte

---

### Post by Charlotte on 2006-10-08
Hallo Iowan,

> **Iowan said:**
> 
The Samba server is probably still set to serve the windows workgroup, but the actual host may not be a part.

could you please explain this in more detail?
Up to now I thought a Samba server could serve just one windows workgroup and it has to be a member of just this workgroup. Maybe I'm wrong.

Thanks in advance.

Charlotte

---

### Post by Iowan on 2006-10-09
> **Charlotte said:**
> Maybe I'm wrong.
I'm probably the one who is wrong.  I'll need to try resetting one of my Samba servers with a different workgroup than the smb.config is set to serve - just to see what happens.  I may be confused in thinking there is a separate, local workgroup for the hostname.
[http://www.ubuntuforums.org/showthread.php?t=272499&highlight=workgroup]("http://www.ubuntuforums.org/showthread.php?t=272499&highlight=workgroup")

---

### Post by Charlotte on 2006-10-09
Hallo Iowan,

thanks for explaining. I am interested in the outcome of your proposed experiment to get a better understanding of what SAMBA does.

If it is of interest for you: I am running two samba servers on my network - they both serve windows machines of which some are domain members (W2K3) and others aren't. The domain name equals to the name of the workgroup and samba servers are doing well. The only problems I am experiencing are that windows browsing is only functioning if my domain controller is up, but that seems to be a notorious windows problem I couldn't solve up to now.   

Have fun,
Charlotte

---

