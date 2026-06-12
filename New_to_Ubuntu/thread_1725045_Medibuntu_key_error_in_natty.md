---
title: "Medibuntu key error in natty"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-04-09
After installation of natty beta (11.04), I tried to add medibuntu using the command at [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php). 
```

sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

However, I keep getting the following error,
```
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Searching showed several solutions, but none worked for me. Perhaps I am not looking at the right place.

Please tell me how can I solve this problem. Thanks in advance.

---

### Post by mmasroorali on 2011-04-09
Separately executing the above-mentioned commands reveals the following error.

This goes fine

```
masroor@Dell-Home:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list

```

Getting the files for update goes fine,
```
sudo apt-get --quiet update
```


except this error at the end.
```
W: GPG error: http://packages.medibuntu.org natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

This returns error

```
masroor@Dell-Home:~$ sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring 
Reading package lists...
Building dependency tree...
Reading state information...
E: Unable to locate package medibuntu-keyring
```

apt-cache search also returns blank
```
masroor@Dell-Home:~$ apt-cache search medibuntu
masroor@Dell-Home:~$ 
```

What is missing here?

---

### Post by Old_Grey_Wolf on 2011-04-09
Enter these commands to get the key:
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by mmasroorali on 2011-04-09
> **Old_Gray_Wolf said:**
> Enter these commands to get the key:
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -
```

It worked, thanks.

Why do I have to get the key in this manner? And why medibuntu-keyring does not physically exist at the server?

Is it because natty right now a beta release? Or am I missing something?

---

### Post by Old_Grey_Wolf on 2011-04-10
> **mmasroorali said:**
> It worked, thanks.

Why do I have to get the key in this manner? And why medibuntu-keyring does not physically exist at the server?

Is it because natty right now a beta release? Or am I missing something?

I think the answer is that it is still in beta.

---

### Post by mmasroorali on 2011-04-11
The necessary files have been added to the repository and the command at the top of now runs without any problem.

---

