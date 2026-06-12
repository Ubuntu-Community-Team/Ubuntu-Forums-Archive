---
title: "Rhythmbox not opening"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Ddraig on 2011-01-12
Hi.  When I try to open Rhythmbox the program opens momentarily and disapears.  Opening it from the terminal gives this

```
hugh@lily-netbook:~$ rhythmbox
** (rhythmbox:2567): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DHmFC5wnG5dDN9mjMn0V%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1294831706%26oauth_token%3DnzQq78jFDClcvbLL3cFk%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&ncClvNHQ1kS528dW7ntxKVVmsSMHdtvwN6g5ZSXDKPs1xLnv4wLlPKMhRrcM8ccK56Gs9bX08pmzggC3'

** (rhythmbox:2567): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=HmFC5wnG5dDN9mjMn0V&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1294831706&oauth_token=nzQq78jFDClcvbLL3cFk&oauth_verifier=None&oauth_version=1.0&oauth_signature=YYlpfZFfE5XN76Wk7%2B6APEQIqTY%3D
Segmentation fault

```

This is on a clean lucid install.  The only reason I can think of is that I copied the fluendo codecs over from an 8.04 install as suggested in this thread [http://en.community.dell.com/support-forums/software-os/f/3525/p/19349601/19762023.aspx#19762023](http://en.community.dell.com/support-forums/software-os/f/3525/p/19349601/19762023.aspx#19762023)

---

### Post by khelben1979 on 2011-01-12
```
rhythmbox --version
``` and report how it looks like. It's possible that another version of the application works better on your system.

Also, what version of Ubuntu are you using?

---

### Post by Ddraig on 2011-01-12
uninstalling and re-installing worked

---

