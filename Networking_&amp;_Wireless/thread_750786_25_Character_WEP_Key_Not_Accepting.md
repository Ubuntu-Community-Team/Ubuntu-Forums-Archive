---
title: "25 Character WEP Key Not Accepting"
date: 2008-04-09
forum: Networking &amp; Wireless
---

### Post by kolisikepu on 2008-04-09
Hi Community,

Disperately needing help with this WEP key.

I have posted something before about this issue, but not many replied.  I tried going somewhere else to find some help, but that was no good either.

The Issue.... and please don't give me lectures about WEP is not secure and what not...  I already know that, but this is something work has configured everywhere on our wireless.

...back to the issue...
Our work wireless is configured for 128bit WEP.  My windows can connect to it with no issues.  My Linux though (even Apple has the same problem) won't accept 25 characters for 128bit ascii WEP key.  It'll only go as far as 13 characters and that's it.

Any suggestions as to how I can over right this without changing settings on the wireless router?

---

### Post by kutjara on 2008-04-09
> **kolisikepu said:**
> Hi Community,

Disperately needing help with this WEP key.

I have posted something before about this issue, but not many replied.  I tried going somewhere else to find some help, but that was no good either.

The Issue.... and please don't give me lectures about WEP is not secure and what not...  I already know that, but this is something work has configured everywhere on our wireless.

...back to the issue...
Our work wireless is configured for 128bit WEP.  My windows can connect to it with no issues.  My Linux though (even Apple has the same problem) won't accept 25 characters for 128bit ascii WEP key.  It'll only go as far as 13 characters and that's it.

Any suggestions as to how I can over right this without changing settings on the wireless router?

It's been a while since I used WEP, but I thought 128bit WEP used either 13 character ASCII keys or 26 character hexadecimal keys. Your Linux box is behaving correctly by only allowing 13 ascii characters, because the rest of them simply wouldn't be used by WEP. I have no idea what Windows is doing (probably just dropping the last 12 characters and not telling you about it).

I know some people have been having to add special characters in front of their WEP keys to force their wireless drivers to read the characters as either ascii or hex, but that seems like a very different problem.

---

### Post by kolisikepu on 2008-04-10
Thanks for the reply kutjara...  it is an unusual one.

Honestly, it disappoints me that I think I have found something that windows can do that Linux can't :o(

It's also funny that the Apple powerbook we also have in the office cannot connect to it as well as it won't accept the 25/26 character wep key.  So, it's quite unusual that both unix boxes can't connect to it.

Someone did suggest though that Windows will accept the long wep key, but may only acccept 13 characters, meaning faking the whole long key and only taking the 13 characters somehow.  I thought that may be right, but we're the ones who configure the wireless around our sites in Australia and it's always been 25or26.

I'm very confused as to why it's doing this.  Is there a way where I can force it/over writing the restriction?

---

### Post by kutjara on 2008-04-10
> **kolisikepu said:**
> Thanks for the reply kutjara...  it is an unusual one.

Honestly, it disappoints me that I think I have found something that windows can do that Linux can't :o(

It's also funny that the Apple powerbook we also have in the office cannot connect to it as well as it won't accept the 25/26 character wep key.  So, it's quite unusual that both unix boxes can't connect to it.

Someone did suggest though that Windows will accept the long wep key, but may only acccept 13 characters, meaning faking the whole long key and only taking the 13 characters somehow.  I thought that may be right, but we're the ones who configure the wireless around our sites in Australia and it's always been 25or26.

I'm very confused as to why it's doing this.  Is there a way where I can force it/over writing the restriction?

It's a puzzle alright. I don't think Windows is doing anything that Linux or OS X can't, just that it's trying to be "user friendly" by allowing the input of arbitrary-length keys (and then presumably using only the 13 characters it needs), but this feature makes it very difficult for non-Windows users to connect (which may be the whole point :)).

I assume you've tried inputting only the first 13 characters of the WEP key?

---

