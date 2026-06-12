---
title: "Synaptic Package Manager Error"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2010-12-01
I tried to run the 'Update Manager' and got errors, so I thought I'd check for broken packages using the Synaptic Package Manager and below is what I've received:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Can anyone help?

---

### Post by plucky on 2010-12-01
> **GaryLittlemore said:**
> I tried to run the 'Update Manager' and got errors, so I thought I'd check for broken packages using the Synaptic Package Manager and below is what I've received:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en%5fGB
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Can anyone help?

From a terminal ```
cd /var/lib/apt/lists/
ls
sudo rm gb.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en%5fGB
sudo apt-get update
```

The ls command is to make sure you are in the correct directory.
The sudo rm command will delete the file
The sudo apt-get update will create a new file and hopefully fix your problem.

Good Luck

---

### Post by rburkartjo on 2010-12-05
gary open a terminal run this command
sudo dpkg --configure -a
it will ask you for your password enter
see if it helps

---

### Post by rburkartjo on 2010-12-05
if that doesnt work gary open the spm
select broken on the left hand side
and that should fix
i had to do that myself yesterday

---

