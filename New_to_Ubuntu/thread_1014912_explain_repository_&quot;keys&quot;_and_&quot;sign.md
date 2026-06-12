---
title: "explain repository &quot;keys&quot; and &quot;signatures&quot; to me, please :)"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by earthpigg on 2008-12-18
> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


i have no idea wtf a 'signature' or 'key' is... if i added it to my sources.list, doesn't that **already** indicate that i trust this source?? :P


also, and this is less important to me than understanding the concept... how do i fix that?

---

### Post by Kobalt on 2008-12-18
See this for more info on Key and Signatures in APT : [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by plucky on 2008-12-18
> and this is less important to me than understanding the concept... how do i fix that? 



From [here](https://help.ubuntu.com/community/Medibuntu)

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


Good Luck

---

