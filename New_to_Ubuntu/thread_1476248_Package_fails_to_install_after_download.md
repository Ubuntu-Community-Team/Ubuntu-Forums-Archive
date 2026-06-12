---
title: "Package fails to install after download"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by er6ben on 2010-05-07
Hello all,

I keep trying to download linux-image generic 2.6.32.22 (new install) from the update manager.

The package seems to download fine but upon installation I receive an error that some packages could not be retrieved and that there is a hashsum mismatch ?

Any ideas on how I fix this ?

---

### Post by Vined Adobo on 2010-05-07
> **er6ben said:**
> Hello all,

I keep trying to download linux-image generic 2.6.32.22 (new install) from the update manager.

The package seems to download fine but upon installation I receive an error that some packages could not be retrieved and that there is a hashsum mismatch ?

Any ideas on how I fix this ?


Packages use a way to determine if a file downloaded properly.  It sounds like you got a data bit twisted somewhere in your download.  Try deleting file and download it again.

You say you keep trying to download it.  I wouldn't think, even with a noisy line, you'd have to download it more than twice.  Maybe Synaptic needs to be downloaded and reinstalled again.

regards,
Dave

---

### Post by er6ben on 2010-05-07
Thanks Dave,

I will give that a look. I seem to never have a problem with any packages other than this one.

Cheers,

Ben

---

