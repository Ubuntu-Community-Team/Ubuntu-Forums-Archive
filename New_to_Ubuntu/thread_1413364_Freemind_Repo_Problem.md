---
title: "Freemind Repo Problem"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by P235 on 2010-02-22
Hi, I added the Freemind repository to Synaptic Package Manager, but I receive the following message:

W: GPG error: [http://eric.lavar.de](http://eric.lavar.de) unstable/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 27CD3F36869D2871
W: GPG error: [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 27CD3F36869D2871

I am not sure what the command is to get the key.

---

### Post by mikeyphi on 2010-02-22
You don't need to go to all that trouble! Freemind is available via Synaptic.

If that's not what you want please ask again!

---

### Post by P235 on 2010-02-22
Thanks for the help.  But, I currently have the 0.9.0 Release Candidate version and was wondering if I could get my hands on the 0.8 stable version.  I thought if I tried adding the repository manually I could find this stable version.

---

### Post by mikechant on 2010-02-22
I can't find the encrpytion keys for this repository.
However, if you install from the terminal with
```
sudo apt-get install freemind 
```
then it should prompt you about the missing keys and allow you to install regardless.

I'm not sure but you might need to specify freemind(+version) to install the specific version you want.


Alternatively you could download a .deb package of the version you want and install this by double-clicking it.

---

### Post by forbajato on 2010-03-14
P235,

I am with you, I love freemind and like to follow the latest versions.  I did a google search for "pubkey eric lavar" and found the following page:

[http://www.lavar.de/comp/linux/debian/](http://www.lavar.de/comp/linux/debian/)

On it there is a command for doing a wget to get the key and import it to your key ring.  I had problems with that, got a keyring not found error so I did the following (as root):

```
wget -O - http://eric.lavar.de/comp/linux/debian/deb_zorglub_s_bawue_de.pubkey >> deb_zorglub_s_bawue_de.pubkey
```

Then I went to the Software sources program (under System>Administration>Software Sources) and the Authentication tab, there is an "Add Key" button at the bottom, indicate the file you saved above (the deb_zorglub... file) and it will import the key, after that you have a working new repo to draw packages from.

Hope that helps!

---

