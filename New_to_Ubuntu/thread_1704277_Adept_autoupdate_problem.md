---
title: "Adept autoupdate problem"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by jimwill on 2011-03-10
Autoupdate has been showing 3 updates for the last few weeks. When I do updates it will not do these three. Even trying from the command line as sudo it will not complete them. I've been hoping a new update would fix it, but no luck. Trying to change the 'no change' to 'install' shows <break> and will not allow update. I can get the linux-generic to change from 'no change' to 'remove' by trying to intall the restricted modules, but I'm not sure if I should do that!
Any suggestions? Do you need more info? 

Since I can't copy from Adept I've included a screen shot -
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=185658&stc=1&d=1299775948[/IMG]

---

### Post by Zorael on 2011-03-10
Ah, been a while since I saw that panel and that UI look. :3

Try using the terminal **aptitude**; it should offer you some suggestions or at least tell you why it can't upgrade those. It's much better at resolving problems than apt-get is.

```
$ sudo **aptitude** update
$ sudo **aptitude** full-upgrade
```

---

### Post by jimwill on 2011-03-11
> **Zorael said:**
> Ah, been a while since I saw that panel and that UI look. :3

Try using the terminal **aptitude**; it should offer you some suggestions or at least tell you why it can't upgrade those. It's much better at resolving problems than apt-get is.

```
$ sudo **aptitude** update
$ sudo **aptitude** full-upgrade
```

If being old fashioned is a crime then I guess I'm guilty! :D
I prefer KDE 3.5 over KDE 4.0 - 4.0 reminds me of windows too much!! I recently found the trinity distro for Kubuntu 10.10 and have it on a laptop, but haven't changed my desktop yet.

ok - sudo **aptitude** update - gives me:
> W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

sudo **aptitude** full-upgrade;
not sure if I really want to do this one - does it upgrade Hardy to later releases or does it keep it in Hardy?

anyway - thanks for the suggestions!

---

