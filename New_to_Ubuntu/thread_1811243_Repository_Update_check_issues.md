---
title: "Repository Update check issues"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Veeravel on 2011-07-24
Hi,

Am Using ubunto 10.04. Check uppdates is not getting connected to the server.

Getting the following errors

The repository may no longer be available or could not be contacted because of network problems.  If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 192.168.150.5:8080 (192.168.150.5). - connect (110: Connection timed out)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.150.5:8080:

What is the issue? how to update and upgrade ubuntu11.04?

Thanks in advance.

---

### Post by amjjawad on 2011-07-24
> **Veeravel said:**
> Hi,

Am Using ubunto 10.04. Check uppdates is not getting connected to the server.

Getting the following errors

The repository may no longer be available or could not be contacted because of network problems.  If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 192.168.150.5:8080 (192.168.150.5). - connect (110: Connection timed out)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_IN.bz2)  Unable to connect to 192.168.150.5:8080:

What is the issue? how to update and upgrade ubuntu11.04?

Thanks in advance.

Hello and Welcome :)

Are you connected to the interent either via LAN or Wireless?

If yes, please open The Terminal (Applications > Accessories > Terminal) and run this command:

```
sudo apt-get clean
sudo apt-get update

```

Please, post the output of the above here and please put "CODE" tags or "#" - wrap up your text with "#" or "CODE" tags.

---

### Post by Rex Bouwense on 2011-07-24
Welcome to the forums.  Sometimes your computer cannot connect to the server for updates.  Just wait a short time and try again.  As to your second question, you will first have to upgrade to Maverick (10.10) before you can upgrade to 11.04.  Either that or download the 11.04 ISO and install it over your Lucid install.  If you do that you will lose all of your data unless you back it up because everything will be over-written (I'm not sure that is a word).

---

### Post by amjjawad on 2011-07-24
> **Veeravel said:**
> how to update and upgrade ubuntu11.04?

Sorry, I missed your other Q :)

If I were you, I would stick with 10.04 for two good reasons:

1- It's [**LTS**]("https://wiki.ubuntu.com/LTS")
2- Less Problematic than 11.04

If you want to go 11.04 route, then I'd recommend to do a fresh installation - don't forget to backup your "important" data before anything else.

Good luck!

---

