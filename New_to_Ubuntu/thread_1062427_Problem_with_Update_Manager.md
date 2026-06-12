---
title: "Problem with Update Manager"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by DarthOpto on 2009-02-06
I am getting the following error when trying to run updates

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

I just updated to KDE 4.2 if that helps

---

### Post by drs305 on 2009-02-06
Launchpad has started using keys for security purposes. Running these commands should import the key for you. If you get warnings about 'unsafe ownership' if means the gpg.conf file is owned by someone else, probably root. In that case, run the commands preceded by "sudo".

```

gpg --keyserver keyserver.ubuntu.com --recv 60D11217247D1CFF
gpg --export --armor 60D11217247D1CFF | sudo apt-key add -
sudo apt-get update

```

---

### Post by DarthOpto on 2009-02-06
Thank you very much. That appears to have fixed the problem.

---

### Post by forger on 2009-02-07
You also need to fix the ppa link of the repository: [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

