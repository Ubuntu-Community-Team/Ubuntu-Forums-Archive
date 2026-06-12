---
title: "Message in Update Manager"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by Castor68 on 2009-04-04
Hi guys.

Every time I check the Update Manager, I got this message:

[COLOR="Blue"]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783[/COLOR]

What does mean this?

Thanks for all your help.

---

### Post by davec64 on 2009-04-04
Sounds like it's having trouble pulling the key down. Have you done anything recently to lose the key?

Try:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

EDIT Changed the code!

---

### Post by hessczoo on 2009-04-04
Try:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by k3lt01 on 2009-04-04
> **Castor68 said:**
> Hi guys.

Every time I check the Update Manager, I got this message:

[COLOR="Blue"]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783[/COLOR]

What does mean this?

Thanks for all your help.Go to Synaptic, then click on Origin, then on Medibuntu Free, then select Medibuntu Keyring and install it. Check the screenshot to see what I mean. That will fix your problem.

---

### Post by Castor68 on 2009-04-04
**k3lt01**: I did as you said. It works fine now.

Thank you.

---

### Post by k3lt01 on 2009-04-05
Pleasure to be of assistance.

---

