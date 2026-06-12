---
title: "Which ATI driver to use: binary or open source? Are both in development?"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by SkyFire360 on 2009-02-17
So I'm confused about which driver for my x1400 (Dell's mobile x1300).  I'm using it solely for home theater purposes (no 3D) and possibly for encoding.  

I read a while ago that AMD open-sourced their driver API, so I was assuming that the open source (mesa?) driver was going to be the de-facto one to use.  However, AMD keeps updating their binary drivers too, so I'm confused as to which driver is better for what I'm looking for:

Requirements: 
Dual-head support

Wish list:
Hardware video decoding
Hardware video encoding
Flash hardware acceleration

I read over on Doom9, some poster mentioned AMD's "binary driver is bad, open source driver is now supported by AMD and is in rapid development, but not yet ready for 3D".  I don't need the 3D aspect, so which one should I be using?  Open source or binary (Mesa or Fglrx)?

---

### Post by ikisham on 2009-02-17
Hey mate, you may try to ask this at the 'main support categories', 'multimedia & video' forum. Think it'll be easier to get an answer.

---

### Post by kk0sse54 on 2009-02-17
> **SkyFire360 said:**
> So I'm confused about which driver for my x1400 (Dell's mobile x1300).  I'm using it solely for home theater purposes (no 3D) and possibly for encoding.  

I read a while ago that AMD open-sourced their driver API, so I was assuming that the open source (mesa?) driver was going to be the de-facto one to use.  However, AMD keeps updating their binary drivers too, so I'm confused as to which driver is better for what I'm looking for:

Requirements: 
Dual-head support

Wish list:
Hardware video decoding
Hardware video encoding
Flash hardware acceleration

I read over on Doom9, some poster mentioned AMD's "binary driver is bad, open source driver is now supported by AMD and is in rapid development, but not yet ready for 3D".  I don't need the 3D aspect, so which one should I be using?  Open source or binary (Mesa or Fglrx)?

Generally most people tend to go with the fglrx driver however it all comes down to do you feel comfortable using proprietary software on your computer. If you don't need 3D support (although open source ati supports it look at this link [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)) you would probably be fine with the open source ones. The open source driver tends to support older ati cards and can have better dual head support.

---

