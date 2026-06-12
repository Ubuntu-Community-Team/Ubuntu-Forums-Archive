---
title: "SMPP deliver_sm - HOW?"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by ddragas on 2010-08-19
Hi all

I'm using perl Net::SMPP to build SMPP client.

While making code as receiver - stacked with these two responses / requests


```
0x00000005 => { cmd => 'deliver_sm', reply => undef, },    # we originate this
0x80000005 => { cmd => 'deliver_sm_resp', reply => undef, },  # *** need to handle this?
``` 


can somebody please suggest me how code should be ?

thank you in advance

---

