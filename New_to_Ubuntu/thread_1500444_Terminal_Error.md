---
title: "Terminal Error"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by wishingstar on 2010-06-03
Hi,

Yesterday I made a clean Lucid install, I added the normal repos as I always do, and the terminal keeps giving me the following error:

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 75CFD31C9E5DB0C8
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

What does all this mean? and how do I fix it?

---

### Post by derekeverett on 2010-06-03
> **wishingstar said:**
> Hi,

Yesterday I made a clean Lucid install, I added the normal repos as I always do, and the terminal keeps giving me the following error:

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 75CFD31C9E5DB0C8
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

What does all this mean? and how do I fix it?

Were you having an internet connectivity issue?

I got error messages similar one time when I was running Ubuntu in a virtual machine. For some reason my internet wasn't getting through to it. I rebooted the VM and all was well.

---

### Post by wishingstar on 2010-06-03
It's not VM, clean Lucid install, and the internet was working fine (i was browsing the web while it was updating)

---

### Post by wojox on 2010-06-03
See here [NO_PUBKEY / GPG error]("http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error")

---

### Post by tom.swartz07 on 2010-06-03
I wrote a script specifically for this problem!

You could download it from here: [http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/GPG-key%20updater](http://bazaar.launchpad.net/~tom-swartz07/codemonkey/trunk/annotate/head:/GPG-key%20updater)

Just make sure you save it as 'gpg-key-updater.sh' and make it executable from the right click properties menu.

Run it from the terminal, and youre all set!

---

### Post by wishingstar on 2010-06-03
Alright, used both methods, the script tom.swartz07 linked to didn't  work, i ran it using

```
sudo ./GPG-key_updater.sh
```after making it executable of course, it gave me everything ok, but when  i ran update i got the same results as in the first post.

The MIT links helped with some of the keys, thanks wojox, however, the  latest i'm getting when i run update looks like this:

```
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release:  The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2   Hash Sum mismatch

W: Failed to fetch  http://us.archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2   Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old  ones used instead.
```please advise on what i can do to get rid of this error!

---

### Post by wishingstar on 2010-06-03
I also tried to go to the website:

[http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/)

where it says there is a problem, i opened the gpg file, copied the contents into an empty file on my desktop and named it: Release.gpg, then i tried to import it in software sources and it didn't work.

---

### Post by tlee on 2010-06-12
I'm having the same problem.  Google'd and tried everything I could find, but no luck.  [This post]("http://ubuntuforums.org/showthread.php?t=1480604") seemed to help a lot of people, but didn't produce results for me.

---

