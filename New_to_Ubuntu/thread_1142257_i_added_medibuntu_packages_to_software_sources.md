---
title: "i added medibuntu packages to software sources"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-29
I added medibuntu packages to software sources and now[ATTACH]111617[/ATTACH] i get errors.[ATTACH]111618[/ATTACH]

---

### Post by Marat Galiev on 2009-04-29
Hmm...
In console type sudo apt-get -f install, and post output here.
And you can add repos manually:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
And...i see spaces in you first screenshot:
http://packages.medibuntu.org/<space here>jaunty
I think it's not true.

---

### Post by DarinB on 2009-04-29
darin@darin-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgpelaunch0 libswfdec-0.8-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
darin@darin-desktop:~$

---

### Post by DarinB on 2009-04-29
these are the errors i get after i followed the advise of the last message to autoremove the obsolete packages[ATTACH]111643[/ATTACH]

[ATTACH]111644[/ATTACH]

---

### Post by Paqman on 2009-04-29
Ok, that's fine, just go into Software Sources and uncheck the CD as an option. Then let it reload and see what happens.

---

### Post by DarinB on 2009-04-29
it seems to workbu unclicking cd  should i try reactivating the medibuntu repos that i added from the ubuntu web site as above

---

### Post by DarinB on 2009-04-29
it causes errors to use the medbuntu sources in the ubuntu pages it seems to be the keyring

---

### Post by Therion on 2009-04-29
Uncheck the CD as source.

Enable the Medibuntu repos in the Third Party Software tab and reload.

Check for upgrade, updates.

If asked to perform a partial upgrade again, DO the partial upgrade.

If you need help installing the Medibuntu repo or it's keyring see this tutorial:  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) under the "Adding the Repositories" section.

---

### Post by anjilslaire on 2009-04-29
I would not use the GUI Software Sources app. Just do it directly via the terminal
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

```

sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

```
```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

There will be an error about the keyring partway through. Ignore it, as th 2nd command will install & fix it.

---

### Post by DarinB on 2009-04-29
that just made things worse it come up over and over again
now what

---

### Post by DarinB on 2009-04-29
only if i uncheck the medibuntu in third party software sources does it stop the partial upgrade loop.

---

### Post by anjilslaire on 2009-04-30
Edit your /etc/apt/sources.list file manually, and delete the references to medibuntu:

```

sudo gedit /etc/apt/sources.list

```

Find the 2 lines that refer to medibuntu. Should be pretty easy to figure out. Delete them, and save the file and close.

then do 
```
sudo apt-get update
```

You should be at a clean slate now with synaptic. Feel free to reboot, but it shouldn't be necessary.
Then run the 2 lines of code I noted previously. Note it should prompt you to accept by pressing 'Y' during this process, between the 2 comands I believe. Make sure you run the 2 commands separately.

---

