---
title: "cifs errors cause temp freeze"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by eaz2 on 2007-10-18
My 7.04 system runs fine, but freezes now and then: the errors in kernel log:

Oct 16 20:41:33 mediac kernel: [ 691.269713] CIFS VFS: server not responding
Oct 16 20:41:33 mediac kernel: [ 691.269723] CIFS VFS: No response to cmd 46 mid 16588
Oct 16 20:41:33 mediac kernel: [ 691.269732] CIFS VFS: Send error in read = -11
Oct 16 20:41:33 mediac kernel: [ 691.269743] CIFS VFS: No response for cmd 50 mid 16589
Oct 16 20:41:35 mediac kernel: [ 692.147422] CIFS VFS: Send error in read = -9
Oct 16 20:53:18 mediac kernel: [ 1028.963816] CIFS VFS: server not responding
Oct 16 20:53:18 mediac kernel: [ 1028.963825] CIFS VFS: No response to cmd 46 mid 26259
Oct 16 20:53:18 mediac kernel: [ 1028.963834] CIFS VFS: Send error in read = -11
Oct 16 20:53:18 mediac kernel: [ 1028.963846] CIFS VFS: No response for cmd 50 mid 26260
Oct 16 20:53:20 mediac kernel: [ 1029.741844] CIFS VFS: Send error in read = -9
Oct 16 21:03:48 mediac kernel: [ 1375.335086] CIFS VFS: server not responding
Oct 16 21:03:48 mediac kernel: [ 1375.335093] CIFS VFS: No response to cmd 46 mid 36463
Oct 16 21:03:48 mediac kernel: [ 1375.335099] CIFS VFS: Send error in read = -11
Oct 16 21:03:48 mediac kernel: [ 1375.335919] CIFS VFS: No response for cmd 50 mid 36464
Oct 16 21:03:55 mediac kernel: [ 1378.762151] CIFS VFS: Send error in read = -9
Oct 16 21:17:48 mediac kernel: [ 1780.474649] CIFS VFS: server not responding
Oct 16 21:17:48 mediac kernel: [ 1780.474658] CIFS VFS: No response to cmd 46 mid 49678
Oct 16 21:17:48 mediac kernel: [ 1780.474665] CIFS VFS: Send error in read = -11
Oct 16 21:17:48 mediac kernel: [ 1780.474675] CIFS VFS: No response for cmd 50 mid 49679
Oct 16 21:18:39 mediac kernel: [ 1805.343428] CIFS VFS: Send error in Close = -9
Oct 16 21:18:39 mediac kernel: [ 1805.347431] CIFS VFS: Send error in Close = -9
Oct 16 21:32:33 mediac kernel: [ 2231.490608] CIFS VFS: server not responding
Oct 16 21:32:33 mediac kernel: [ 2231.490617] CIFS VFS: No response for cmd 50 mid 56223
Oct 16 21:44:33 mediac kernel: [ 2592.176610] CIFS VFS: server not responding
Oct 16 21:44:33 mediac kernel: [ 2592.176620] CIFS VFS: No response to cmd 46 mid 62278
Oct 16 21:44:33 mediac kernel: [ 2592.176629] CIFS VFS: Send error in read = -11
Oct 16 21:54:03 mediac kernel: [ 2874.574293] CIFS VFS: server not responding
Oct 16 21:54:03 mediac kernel: [ 2874.574301] CIFS VFS: No response to cmd 46 mid


Anyone a suggestion?

---

### Post by dmizer on 2007-10-18
i have a fix posted at the bottom of the howto for cifs in my sig.

---

### Post by eaz2 on 2007-10-18
dmizer, 
thanks, there is a lot of usefull info there, but the fix (maybe i am mistaken, there is so much info there) is about this same errror while doing a shutdown.
In my case it happens every say 10 minutes. 
In case this has been fixed too, could you please be a little bit more specific about the place to find this fix?

thx

---

### Post by dmizer on 2007-10-18
nope ... you're right, i don't think that will fix your problem.

are you using winbind?

as a temporary fix, you could just kill the hal dameon.
```
sudo killall hald
```
that way at least your machine won't freeze anymore, and it will give you time to hunt for a more perminant fix.

the downside to this is that you will not have automount for your drives (cdrom)

---

### Post by eaz2 on 2007-10-18
no I dont use winbind, although is is installed.

I found another clue: I tried to change cifs back to smbfs (in fstab), and another error, with a much longer history on the forum is showing up: 
Oct 18 16:29:38 mediac kernel: [ 3779.501216] smb_add_request: request [ffff810067f70b40, mid=5738] timed out!
Oct 18 16:29:38 mediac kernel: [ 3779.583187] smb_add_request: request [ffff810067f700c0, mid=5739] timed out!
Oct 18 16:40:01 mediac kernel: [ 4121.142655] smb_add_request: request [ffff81003e75ee40, mid=22921] timed out!
Oct 18 16:40:02 mediac kernel: [ 4121.462240] smb_add_request: request [ffff810052613200, mid=22922] timed out!

These errors must be connected.

So far, no one could help me, so if you find something..

---

### Post by dmizer on 2007-10-18
1) is "wins" referenced in the hosts line of /etc/nsswitch.conf?
2) the samba server you're trying to connect to ... is it linux?

if so, please post your server's /etc/samba/smb.conf file.

---

### Post by dmizer on 2007-10-19
also an update, the smb_add_request: request [...] timed out error is a problem with smbfs because smbfs is no longer maintained (different than your hal problem in cifs).  this problem will NOT be fixed, use cifs instead.

---

### Post by eaz2 on 2007-10-20
i did an update to 7.10, to make sure a possible bug was fixed. But it didnt.
I found this as a bug in [www.samba.org:](www.samba.org:) and the bug has status new:

" 
I have reproduced the bug in the following case:
- setup a Samba server with a short deadtime;
- on a client side, mount a share, dont do anything with it but wait for the
disconnection;
- once disconnected, try to mount a share from the same server with the same
credentials, you should get the error 11.

Here is what happens in the cifs driver:
- when Samba closes the connection to the idle share, it closes the socket;
- the driver notices it, marks the current sessions as needing reconnection,
and reestablishes the TCP connection;
- on the next mount, the driver finds an existing cifs session for that
particular server and wants to use it to mount the share ; but the session
still needs to be reestablished.

The patch is a small copy/paste from the reconnection part of smb_init, which
seems to fix the problem. I am absolutely not sure if it is the right way to do
it.
" 
Any idea where i can increase dead time or idle tine in samba?

---

