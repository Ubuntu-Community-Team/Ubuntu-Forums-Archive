---
title: "cant update Ubuntu"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-06-04
Hi,
I've had this issue before....Anyone can help me? I keep getting this error message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Rocket2DMn on 2011-06-04
Does it work if you run
```
sudo apt-get update
```

That should refresh the package lists.  Then you can try upgrading graphically from Update Manager or by running
```
sudo apt-get upgrade
```

---

### Post by skyzthelimit230 on 2011-06-04
nope, nada. sudo apt-get update yields the following error:
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
fil@ubuntu:~$ 

synaptic fails too load too

---

### Post by matt_symes on 2011-06-04
Hi

Try this. Copy and paste this into the terminal.

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

Kind regards

---

### Post by skyzthelimit230 on 2011-06-04
thanks! That did the trick!

---

