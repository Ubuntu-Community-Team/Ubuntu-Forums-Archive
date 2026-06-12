---
title: "GRLDR error"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Leilendial on 2010-10-26
Hello everyone.

I hope you can help me, as I seem to have a small problem I am unable to solve. I know nothing about Linux and slim to none about Ubuntu.

My brother-in-law set up Ubuntu on my 64 bit Windows pc, so that I could connect to my desktop at work, thus allowing me to work from home. My company uses a CISCO VPN connection.

Due to train issues today, I found myself stuck at home. When I started UBUNTU, I received an error message stating "Cannot find grldr on all devices press ctrl+alt+delete to restart"

Following this path C: -> ubuntu -> winboot

The following files are present:
wubildr
wubildr.cfg
wubildr.mbr

I looked on the forums prior to posting this, and found that one of the possible causes was a fragmented drive. So I defragmented my C: and ran the ftests with the following results:

fstest info C:\ 
Cant open drive

fstest inode C:\wubildr
Cant open drive

fstest comp C:\wubildr
Cant open drive

Obviously there is something going on, and I am so nervous about messing with anything as I do not know how to set up the vpn and remote desktop connections and my BIL is busy and unreachable atm. In the meantime, my boss is getting pretty cranky that I am not working. 

So if anyone could give me a hand, I would greatly appreciate it!

---

