---
title: "Synaptic error"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by old_dope on 2009-05-05
When i open the Synaptic Package Manager i click on 'refresh' to make sure that everything is upto date and then i get an error message as follows:

**An error occurred **

W:GPG error:[http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid release: The following signatures couldn't be verified because the public key is not available:
NO_PUBKEY 2EBC26B60C5A2783

Could someone tell me what's going on here please. Thanks

---

### Post by kostkon on 2009-05-05
Open a terminal and give
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
and you should be fine.

---

### Post by old_dope on 2009-05-05
Hi Kostkon

Have done as you suggested but the same error message still appears when i refresh Synaptic?

---

### Post by Zoowey on 2009-05-05
Simply run this command in a terminal.

gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783 && gpg --armor --export 2EBC26B60C5A2783|sudo apt-key add -

---

### Post by Absolut Newbee on 2009-05-05
in terminal type 

wget -q [http://fr.packages.medibuntu.org/medibuntu-key.gpg](http://fr.packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

and if that didn't work try

gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783 && gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

hope it helps

---

### Post by old_dope on 2009-05-05
Job done! Thanks for the replies and help folks

---

