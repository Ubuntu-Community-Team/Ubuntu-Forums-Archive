---
title: "Hardy Heron, Samba shares, and a question about wireless adapters."
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by Tyshalob on 2008-04-28
I had set up Samba  so I could have access to files on my Windows desktop from my Ubuntu 7.10 laptop. Today I decided I would upgrade to 8.04. After upgrading to 8.04 my network shares are no longer being mounted. I've checked for errors with Samba, but all the logs are clean. When I try to mount -a it will sit forever without exiting (no error code or anything). But I can access the shares if I do Places - Connect to server. What is preventing the shares from being mounted properly like they were in 7.10?

I've also noticed odd behavior where after I reboot and log in I have to issue ifdown wlan0 and then ifup wlan0 or my wireless adapter doesn't work properly. Any idea what's up with that? I use ndiswrapper and the net5416 driver from Windows XP for my lovely Atheros wireless adapter.

---

### Post by PierGroup on 2008-05-05
Moral support! I have just upgraded to H/H and also have lost contact with my Windows file server. Internet access via the server is not affected, though. I am guessing that this is a permissions thing, rather than a network thing.

---

### Post by PierGroup on 2008-05-05
I've just noticed that there are multiple reports in the auth.log:
> PAM unable to dlopen(/lib/security/pam_smbpass.so)

A quick look in /lib/security shows several pam_ type files but no smb one. Could this be related?

---

### Post by dyefade on 2008-05-05
The package libpam-smbpass will install /lib/security/pam_smbpass.so - not sure if this will help with your problem.

It certainly hasn't helped mine ([http://ubuntuforums.org/showthread.php?t=777321](http://ubuntuforums.org/showthread.php?t=777321)).

---

### Post by phoenix49 on 2008-05-05
Try connecting to samba shares with specified folder. Places -> Connect to server, choose windows share, server, and select folder. It will do a workaround.

---

### Post by bartos on 2008-05-05
On the same subject so I don't hijack or start a new thread. Do I have to be logged on with same user on both machines or as long as user is added to both machines? Example , My wife is on her account on a vista machine and I am on my Ubuntu machine with my account name. Both machines have both accounts setup with same passwords.

---

