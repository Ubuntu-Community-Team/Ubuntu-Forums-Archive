---
title: "Medibuntu public key issue?"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Norm24 on 2010-05-02
I get this error message after re-adding the Medibuntu repository after upgrading too Lucid:

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

Not a big deal for now.Just curious as to when this issue could be resolved.

---

### Post by coffeecat on 2010-05-02
> **Norm24 said:**
> I get this error message after re-adding the Medibuntu repository after upgrading too Lucid:

```
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```Not a big deal for now.Just curious as to when this issue could be resolved.

I was getting this yesterday. If you go to [http://packages.medibuntu.org/](http://packages.medibuntu.org/) in firefox you get a 503 Service Temporarily Unavailable.

> Service Temporarily Unavailable

The server is temporarily unable to service your request due to maintenance downtime or capacity problems. Please try again later.

*Apache/2.2.12 (Ubuntu) Server at packages.medibuntu.org Port 80*Hopefully it'll be back soon.

---

### Post by Norm24 on 2010-05-04
Still the same error message.

You'd think the Medibuntu team would be on top of this...guess not.

---

### Post by barney385 on 2010-05-04
I just *sudo apt-get update* and mine worked fine.

---

### Post by howefield on 2010-05-04
> **Norm24 said:**
> Still the same error message.

You can always use a mirror.

---

### Post by coffeecat on 2010-05-04
> **Norm24 said:**
> You'd think the Medibuntu team would be on top of this...guess not.

They are. The server has been up for some time now. You need to manually install the medibuntu keyring. This would have failed when the server was down. Open Synaptic and mark medibuntu-keyring for installation, or:

```
sudo apt-get install medibuntu-keyring
```

If you want to avoid the error:

```
sudo apt-get --allow-unauthenticated install medibuntu-keyring
```

---

### Post by Norm24 on 2010-05-05
[QUOTE=coffeecat;9237173]They are. The server has been up for some time now. You need to manually install the medibuntu keyring. This would have failed when the server was down. Open Synaptic and mark medibuntu-keyring for installation

This worked.Thankyou.

---

