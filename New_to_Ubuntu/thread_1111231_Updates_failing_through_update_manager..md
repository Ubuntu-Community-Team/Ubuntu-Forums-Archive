---
title: "Updates failing through update manager."
date: 2009-03-30
forum: New to Ubuntu
---

### Post by samyardley on 2009-03-30
When I run sudo apt-get update I get the following error: 

[B]sam@sam-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[/B]

---

### Post by Therion on 2009-03-30
Open the Update Manager, click on the "Settings" button, choose another server from the dropdown menu and try again.

---

### Post by kanikilu on 2009-03-30
I wonder why it's trying to connect to localhost? Are you running a proxy?

---

### Post by Lunx on 2009-03-30
Seems there's been a few update problems for people today. I installed Jaunty earlier this evening and went to change my server preference in Synaptic, but it wouldn't connect at all to my first choice, and when I connected to another I got the same error message. I since tried again to point it at my usual download location and it's all working fine again now.

---

### Post by raymondh on 2009-03-30
I concur ..... same thing ..... funny but am back on again.  Oh well, on with life :)

---

### Post by Therion on 2009-03-30
> **Lunx said:**
> Seems there's been a few update problems for people today. I installed Jaunty earlier this evening and went to change my server preference in Synaptic, but it wouldn't connect at all to my first choice, and when I connected to another I got the same error message. I since tried again to point it at my usual download location and it's all working fine again now.
I've been doing a similar "dance" for days now:  There's 30 updates available for download, for instance.  27 would install and three would "hang".  

Switch servers, Reload... Download the last three without issue.

<shrug>  I dunno...  I'm cutting the 'lope some slack since it's still a baby-beta.

---

### Post by robfindlay on 2009-04-10
> **samyardley said:**
> When I run sudo apt-get update I get the following error: 

[B]sam@sam-desktop:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-proposed/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[/B]


Sam here is a friend of mine and he's still getting the exact same error message after changing servers and some editing of his sources.list 

We've reset the router wit the same result, I'm running basically the same install in the same house, without this issue...

Any ideas?

---

### Post by ibuclaw on 2009-04-10
Is the environment variable **http_proxy** set?

```
echo $http_proxy
```
I suspect it is set to **[http://localhost:4001](http://localhost:4001)**, and that is preventing you from using apt.

This is sounds like typical behaviour if you've installed an anonymous proxy package on your computer (ie: anon-proxy).

To temporarily resolve your issue:
```
unset http_proxy
```
Then I suggest that you remove whatever proxy you have currently installed.

[EDIT]
or you could run:
```
sudo dpkg-reconfigure anon-proxy
```
and uncheck the option to enable the use of the http_proxy variable.


Regards
Iain

---

### Post by robfindlay on 2009-04-10
> **tinivole said:**
> Is the environment variable **http_proxy** set?

```
echo $http_proxy
```
I suspect it is set to **[http://localhost:4001](http://localhost:4001)**, and that is preventing you from using apt.

This is sounds like typical behaviour if you've installed an anonymous proxy package on your computer (ie: anon-proxy).

To temporarily resolve your issue:
```
unset http_proxy
```
Then I suggest that you remove whatever proxy you have currently installed.

[EDIT]
or you could run:
```
sudo dpkg-reconfigure anon-proxy
```
and uncheck the option to enable the use of the http_proxy variable.


Regards
Iain

Yeap, that was it, anon-proxy.  

thanks guys.

-Rob

---

### Post by LyonTamer on 2009-05-10
I have 8.01. I do not have a settings button or a preferences button on update manager. The only buttons it has is Check, Install and Close. Where do I go to change settings per the above posts?

---

