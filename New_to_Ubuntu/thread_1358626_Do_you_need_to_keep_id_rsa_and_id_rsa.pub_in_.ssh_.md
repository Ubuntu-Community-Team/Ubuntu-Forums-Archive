---
title: "Do you need to keep id_rsa and id_rsa.pub in .ssh directory?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by CharlesA on 2009-12-18
Hi all,

Simple question. Do you need to keep id_rsa and id_rsa.pub in the ~/.ssh directory after you generated the keys?

Thanks.

---

### Post by bodhi.zazen on 2009-12-18
No you do not.

.pub goes to the server (in authorized_keys) so once you transfer it you do not need it (assuming you can retrieve it later).

id_rsa can go on a flash drive if you wish.

---

### Post by CharlesA on 2009-12-18
> **bodhi.zazen said:**
> No you do not.

.pub goes to the server (in authorized_keys) so once you transfer it you do not need it (assuming you can retrieve it later).

id_rsa can go on a flash drive if you wish.

Thanks! I've got a copy of both sitting on a flash drive. :-)

---

