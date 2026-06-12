---
title: "Trying to upgrade from 9.04"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by hollowtd on 2009-10-30
Hi

I'm trying to upgrade from Juanty to Koala and it almost works. I'm running a dual boot macbook with Tiger and Jaunty and trying to upgrade. Jaunty gets to the 3rd part of downloading the files and then says that it won't work. I got a message yesterday that the "juanty-minimal" was missing but that doesn't seem to be the case today. Hope I can upgrade soon.

Thanks

Terry

---

### Post by phillw on 2009-10-30
> **hollowtd said:**
> Hi

I'm trying to upgrade from Juanty to Koala and it almost works. I'm running a dual boot macbook with Tiger and Jaunty and trying to upgrade. Jaunty gets to the 3rd part of downloading the files and then says that it won't work. I got a message yesterday that the "juanty-minimal" was missing but that doesn't seem to be the case today. Hope I can upgrade soon.

Thanks

Terry


run an md5checksum on your cd ....

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, one cause of funnies is the burning of iso's at more than 4X ... weird, but true.

Phill.

---

### Post by hollowtd on 2009-10-30
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

I GET THIS MESSAGE IN TERMINAL WHEN I TRY TO UPDATE. MAYBE THIS IS THE ROOT OF THE EVIL. IM UPGRADING FROM THE INTERNET BUT SHOULD I MAKE AND USE A CD?

---

### Post by hollowtd on 2009-10-30
Anyone know why I get this when I try to check for updates. It seems to work and then I get this:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

When I try to upgrade, it starts getting the packages and then stops later on because some fail. I'm not sure what's happening.

---

### Post by kansasnoob on 2009-10-30
Post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by hollowtd on 2009-10-31
I may have solved this but I don't know how to make the thread done and solved? Any help would be good. Please write me on here and tell me how to do this so I can do it right for the whole community. What I did to fix the problem:

I removed everything skype through Terminal. This got me one step further. I then downloaded the ISO Ubuntu 9.10 Alternate CD and made an image burn. I logged into Jaunty and inserted the CD. When it asked to "also use the internet to upgrade" I ticked "no" (I just wanted to use the CD). This worked and the upgrade worked and then I had to download the language repositories, which took an hour. Then, I went back into software sources and ticked universal and the top one for ubuntu and let it do its thing. I seems that all is updated and works just fine now. Make sure to uncheck the CD box at the bottom of the software sources so that you don't have to insert the alt cd everytime you want to download updates. 

Cheers

Terry

---

