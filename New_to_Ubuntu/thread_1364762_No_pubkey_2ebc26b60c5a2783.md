---
title: "No_pubkey 2ebc26b60c5a2783"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by dedikcr on 2009-12-26
I get the following error when I check for updates in the Update manager.

> 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Wha am I doing wrong?
I know that medibuntu is not active for default, but I don't want to eliminate it from the repository list because it has lots of interesting software.

Thank for any help. Marry Christmas and happy new year.

---

### Post by kansasnoob on 2009-12-26
Well, my thoughts, I'm not sure what method you followed to install Medibuntu, but this just works:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

Personally what I would recommend is going to System > Administration > Software Sources and under the Other Software tab you should be able to locate the Medibuntu repos. I'd remove them, then click on the Authentication tab and look for the Medibuntu Packaging Team gpg and remove it.

Then I'd close Software Sources and run this command:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

Hopefully that will get rid of the error.

---

