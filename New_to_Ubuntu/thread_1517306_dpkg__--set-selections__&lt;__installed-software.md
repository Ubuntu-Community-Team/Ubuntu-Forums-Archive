---
title: "dpkg  --set-selections  &lt;  installed-software"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by cwmoser on 2010-06-24
This command does not work.

Attempting to migrate from 9.04 to 10.04.
I created a file of my current packages using:
sudo dpkg --get-selections > installed-software

Then on a virgin 10.04, I try to to run the following to install all my packages:
sudo dpkg --set-selections < installed-software

Nothing happens.  Just get the command prompt back.

What troubles me is that this command would not work on 10.04.
It worked perfectly on prior Ubuntu installations.

Carl

---

### Post by oldfred on 2010-06-25
It worked just fine for me. I did put my commands into a bash script so I can upgrade easily and install my software and configuration to multiple installs easily. Did you look at the file?

It should look like this - mine was very long:

abiword                        install
abiword-common                    install
abiword-help                    install
abiword-plugin-grammar                install
etc


apt-get update
apt-get dist-upgrade
# Finally, install all the packages from previous install
# must have saved ubuntu-files from previous install to this directory
dpkg --set-selections < ubuntu-files
dselect
apt-get -y update
apt-get dselect-upgrade

---

### Post by john newbuntu on 2010-06-25
'dselect' is not installed by default.  So, where oldfred said 'dselect', if it complains:
sudo apt-get install dselect
should do it and the rest of the instructions are the same.

---

### Post by cwmoser on 2010-06-25
Thanks guys -- what you posted solved this for me.

Carl

---

