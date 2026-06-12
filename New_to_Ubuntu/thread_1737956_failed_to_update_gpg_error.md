---
title: "failed to update gpg error"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by ucuyeuhz on 2011-04-24
hi everyone..
please help for my problems on Ubuntu 10.10 maverick

when I type sudo apt-get update

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

and then I type 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192

it says like this
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


can anyone help for my probs? (sorry, I'm bad english)

---

### Post by Old_Grey_Wolf on 2011-04-24
To get the gpg key, enter these commands into the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
```

---

### Post by bdecie on 2011-04-27
Same problem here for several days now.  The gpg and apt-key commands above both produce the following error:
```
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

Is the keyserver functioning?

---

### Post by Old_Grey_Wolf on 2011-04-27
> **bdecie said:**
> Same problem here for several days now.  The gpg and apt-key commands above both produce the following error:
```
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
```

Is the keyserver functioning?

You may need to get a different key. Post the output from the update command.

---

