---
title: "Samba or Not?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by brentdavis29 on 2009-03-04
THE SCENARIO:

I'd like to consolidate the media on my computer (XP), and my wife's computer (XP) onto one home server. So I installed Ubuntu on an extra machine to be a media server. I opted for the desktop version of Ubuntu because I'd also like to start getting familiar with that, in case I want to make the full switch on my PC.

I read that Samba is the way to setup a media server. However, after trying to install Samba (unsuccessfully I think), I just went to the sharing option on the file folders on the Ubuntu machine, and then was able to see them on my XP box. 

QUESTION #1:

Why would I want to use Samba over just sharing folders? I don't get what the difference is.

QUESTION #2: 

Ultimately, I want to sync iTunes on either PC to a "music" folder & "podcasts" folder on the Ubuntu machine, and sync Picassa on either PC to a "photos" folder on the Ubuntu machine.

---

### Post by Iowan on 2009-03-04
If you're sharing files between Ubuntu and Windows, you're probably using Samba. IMHO, it was easier on the older versions (that'd be your 7.04)

---

### Post by AndyCooll on 2009-03-04
To answer your question 1, you'll want to install Samba on the Ubuntu pc (your media server) because "Samba is Linux's implementation of Windows' SMB (Server Message Block) protocol", i.e. the protocol used by Windows for sharing files.

See [here]("https://wiki.ubuntu.com/ComprehensiveSambaGuide") for more information on how to get Samba up and running.

:cool:

---

