---
title: "update manager"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by bob58523 on 2010-10-16
Hi All,

I have had ubuntu 10.10 installed for several days now and everything was working very well, that is until today. I had a warning pop up saying that my update was 7 days old. I tried to update and got this error:

*A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192*

It then either dumps the update program or tells me there are no new updates. Any ideas?

thanks,
Bob

---

### Post by Troll_the_Great on 2010-10-16
> **bob58523 said:**
> Hi All,

I have had ubuntu 10.10 installed for several days now and everything was working very well, that is until today. I had a warning pop up saying that my update was 7 days old. I tried to update and got this error:

*A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192*

It then either dumps the update program or tells me there are no new updates. Any ideas?

thanks,
Bob


Try this: open a terminal (Applications - Accessories - Terminal) and paste this command:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192
```
Then try again searching for updates:
```
sudo apt-get update
```
Post back the results.
Cheers!

---

### Post by bob58523 on 2010-10-16
that worked.... thanks so much.

What would cause this to happen?

---

