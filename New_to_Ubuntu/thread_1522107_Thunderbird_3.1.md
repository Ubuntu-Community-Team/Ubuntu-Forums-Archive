---
title: "Thunderbird 3.1"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by keheikev on 2010-07-01
I have been trying to install the latest version of Thunderbird 3.1 unfortunately I tried these directions but adding the ubuntizilla repository is not working.  I get an error when I download this  key [http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCCC158AFC1289A29]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xCCC158AFC1289A29") when I tried to import the key for the authentication in software sources it says may not be a valid gpg file?
I am using Ubuntu 9.04
 Pentium D 
:kihei

---

### Post by fooman on 2010-07-01
try opening a terminal, and copy/paste the following command into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com c1289a29
```see if that helps.

edit:  just to clarify: what you do is run the command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com <*key number goes here*>
```

and add the last 8 digits of the key in place of "<*key number goes here*>"

---

### Post by keheikev on 2010-07-01
I think it was keyserver problem finally got the key to import in terminal using
```
sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys C1289A29
```

I got that from this link [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation")
It is starting up fine now but it overwrote my configs and messages. I did back them up but I don't know how to get them to the right folder to get it working right.
almost there!
:kihei

---

### Post by keheikev on 2010-07-01
I did get it working and I am impressed with the updated program. I had to move my backed up profile to the .thunderbird folder from my .mozilla-thunderbird.backup folder.:KS

---

