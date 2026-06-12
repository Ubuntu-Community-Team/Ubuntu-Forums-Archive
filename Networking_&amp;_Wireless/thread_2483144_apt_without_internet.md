---
title: "apt without internet"
date: 2023-01-21
forum: Networking &amp; Wireless
---

### Post by whitecat-sudo on 2023-01-21
hello.

i am trying to install a wifi driver, but i need to use apt to install dkms and make and all their dependencies to even get the wifi driver, but apt wont work as it cannot find any servers due to lack of internet.

installing the driver works flawlessly when booting from the live installation on my flash drive, but that is because it has all the packages on the flash drive.

**_so how do i get apt to use my flash drive to find packages, just like on the live installation?_**

---

### Post by TheFu on 2023-01-21
Ref thread: [https://ubuntuforums.org/showthread.php?t=2483100&p=14127319#post14127319](https://ubuntuforums.org/showthread.php?t=2483100&p=14127319#post14127319)

[https://askubuntu.com/questions/306971/install-package-along-with-all-the-dependencies-offline](https://askubuntu.com/questions/306971/install-package-along-with-all-the-dependencies-offline)
Provides a few answers.
* apt-offline
* Synaptic can be used to generate a list of dependencies
* keryx

All three have problems, in that they aren't included by default in the installation. Another chicken/egg problem.

---

### Post by Holger_Gehrke on 2023-01-21
If you have downloaded all the packages you need (from packages.ubuntu.com for example), there are two ways of installing things:
[LIST]
[*] Use 'dpkg -i package-file-name'. 'dpkg' is a 'lower level' tool which can only install packages it finds locally. Since dpkg doesn't know or care about repositories and the internet, you have to install the dependencies first.
[*]Use 'apt' and give local paths to the files (not just the package name). I could be wrong, but having all the packages you need to install in one directory, changing to that directory and using 'sudo apt install ./*.deb' could work.
[/LIST]

Holger

---

### Post by jeremy31 on 2023-01-21
This issue was likely fixed by another route in [https://ubuntuforums.org/showthread.php?t=2483103](https://ubuntuforums.org/showthread.php?t=2483103)

---

