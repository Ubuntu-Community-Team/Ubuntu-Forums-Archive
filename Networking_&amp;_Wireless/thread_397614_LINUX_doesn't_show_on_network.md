---
title: "LINUX doesn't show on network"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by cgbier on 2007-03-30
I have set up a small wireless network at home, using a Win XP desktop as file and print server (yes, I know, I'm a pervert :) ). In any case, I can see and access all computers on the network from my LINUX lapdog, but the Windows machines don't even show the lapdog.

I know that NTFS cannot read LINUX partitions, but shouldn't at least the machine show up?

---

### Post by dbott67 on 2007-03-30
You need to install Samba on your linux computer.  Details are here:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

-Dave

---

### Post by cgbier on 2007-03-30
Thanks a lot!

---

### Post by cowlip on 2007-03-30
Just a sidenote, NTFS can read ext2 (and ext3, by ignoring the journal though it's less robust) with ext2ifs, just google it ;)

---

### Post by cgbier on 2007-04-06
Dave, thank you for posting the how to on mounting NTFS. 
However, a question: What do you do if you don't use a password on your XP machine?

Before you slaughter me now: This machine is only used for video and photo editing, and has no connection to the www, so I dind't bother to set up a user.

---

### Post by dbott67 on 2007-04-06
There may be other ways (and perhaps easier) of doing this, but off the top of my head, you could create a password and use a program like [TweakUI]("http://download.microsoft.com/download/f/c/a/fca6767b-9ed9-45a6-b352-839afb2a2679/TweakUiPowertoySetup.exe"). TweakUI can be set to auto-login to Windows for convenience.

Then, create the appropriate SMB user ([COLOR=Blue]sudo smbpasswd -a username[/COLOR]) as per the link in post #3.

More info about TweakUI here:
[http://www.microsoft.com/windowsxp/downloads/powertoys/xppowertoys.mspx](http://www.microsoft.com/windowsxp/downloads/powertoys/xppowertoys.mspx)

-Dave

---

### Post by cgbier on 2007-04-07
Thanks again!

---

