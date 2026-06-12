---
title: "Adding source - Can't find public key?"
date: 2010-08-28
forum: New to Ubuntu
---

### Post by UnknownFear on 2010-08-28
I installed Ubuntu 10.04 LTS and upon starting for the first time, I added the Canada source "deb [http://ftp.ca.debian.org/debian](http://ftp.ca.debian.org/debian) sid main" and ran apt update. It gives me an error stating the public key can't be found. Any help with this?

```
W: GPG error: http://ftp.ca.debian.org sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
```

---

### Post by UnknownFear on 2010-08-28
Oh, it appears the source I wanted to add works in Debian only. I got rid of it and ran an apt-update it everything works now. Please excuse this thread.

---

