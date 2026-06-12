---
title: "How to play DVDs"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by crong on 2010-05-26
I knew I needed VLC on my new Ubuntu 10.04 system and got it quickly & easily using Synaptic, but I was very disappointed to discover that it wouldn't play most of my DVDs properly.

It turns out that almost all commercial DVDs are "protected" by CSS (Content Scrambling System) and decryption is required. For some (presumably legal) reason, this is not part of the Ubuntu VLC distribution but I stumbled upon the solution on another website and it is as simple as typing these two lines into a terminal:

sudo aptitude install ubuntu-restricted-extras
 sudo /usr/share/doc/libdvdread4/install-css.sh 

Hope this helps someone.

---

