---
title: "[SOLVED] SMB 7.10 failure"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by ofb on 2007-11-12
Two machines, Ubuntu & Edubuntu 7.10 with identical SMB & firewall & permission setups. First machine can read the other's share fine, but the other can only see the first's share and not open it.

Clicking the share in konq: "The file or folder smb://192.168.0.1/downloads does not exist."

/var/log/samba/log.bluefish,

```
[2007/11/11 22:03:14, 0] smbd/service.c:make_connection_snum(1003)
  '/home/o/files/downloads' does not exist or permission denied when connecting to [downloads] Error was Permission denied
```

I'm jammed. I've double-checked that everything is configured identically on the two machines, and confirmed the smb.conf's also match, and of course I've rebooted a few times just for kicks. I can't think of what to look at next.

FWIW, the LAN consists of secondary NICs with static IPs connected by a null modem cable. PING is fine, and obviously the connection works well enough to see the reluctant share & create a log in the remote machine.

A minor difference is the Edu machine has network-manager removed as that was the only way to get networking to work on a two NIC machine in 7.10. (Had the same trouble with other installs than Edubuntu.) The U machine is also fresh install but with an old /home partition that carried over the old Session config of network-manager disabled in Addition Startup Programs -- hence did not need network-manager removed via Synaptic.

That shouldn't matter, but since it's the only difference I can think of other than brands of NIC, I include it for your enjoyment.

As far as permissions go, the machines are set up for the same user/password, and the shares are both folders within ~/. It really doesn't get simpler than this. I'm baffled.

---

### Post by ofb on 2007-11-13
bump

I don't like to bump, but haven't gotten any farther with this, so here's a bump to put the post on the front page while a diffferent timezone is active.

---

### Post by ofb on 2007-11-13
Well that was confusing. It was indeed a permission issue, but at a file level, not SMB.

/home/o/files/downloads

I first noticed /downloads had no permissions allowed for Others & Groups, so enabled that for the directory & contents and got nowhere.

Then noticed /o had no permissions allowed for Others & Groups, so enabled that, and also got nowhere.

Finally noticed that /files between also had no permission for Others & Groups, so enabled that and finally got somewhere. Which seems to be the trick - the whole path must be open or the pathway cannot be navigated.

Which is great, but brings up another question - what should the permissions be within /home/[user]?

The old /home partition I brought forward from previous installs is a dog's breakfast of permissions at this point. What's default?

The /home directory of the fresh install has consistent permissions across regular files & directories, but quite a variety for the hidden configuration files & directories. Hence I'm reluctant to just reset all permissions for /home subfolders & contents on the muddled machine.

In the fresh install, regular files all seem to be rw for the Owner, and r for Others & Groups. What I'm thinking should be done to reset the muddle is use that for all regular directories & contents, while leaving hidden config directories & files alone.

Does that sound right? Sounds right to me, but since I've just made a daft mistake, I'd like someone to check my thinking.

(And yes, add x for directories so they'll function of course.)

---

