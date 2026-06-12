---
title: "not able to download packages in Ubuntu 9.10"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by ahoy-hoy on 2009-12-23
Hello!

After re-installing Ubuntu 9.10 I cannot download and install any packages anymore. When I start the update-manager it tells me the following (same happens when I use apt-get or try to open the synaptic package manager):

'E:Problem parsing dependency Replaces, E:Error occurred while processing rplay-client (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
 
Does anyone know what this means and what I can do about it? I am very new to Ubuntu so might need a bit more explanation than other people. Sorry!

ahoy-hoy

---

### Post by jimingkui on 2009-12-23
Something installed failed.I'd usually try this first:
[U]sudo apt-get -f install
sudo dpkg --configure -a[/U]

If it doesn't work,try to remove error intalled package:
_sudo aptitude purge $(dpkg -l|grep ^rc|awk '{ print $2 }')_

---

