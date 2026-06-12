---
title: "Dropbox asking for authentication to run usr/bin/dropbox as the superuser"
date: 2015-01-18
forum: Networking &amp; Wireless
---

### Post by Ivan_Gil on 2015-01-18
Hi, I have been using Dropbox in my Ubuntu boxes for many time without problem but I installed Ubuntu 13.10 64bits in this box a month ago and after that I turned into Gnome (which I always do) and when I tried to install Dropbox from the Software Center it got stuck at certain point and it never finished the installation, so I looked for other ways to install it and found this page: [https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx) with the following instructions:

 64-bit:
 cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf - Next, run the Dropbox daemon from the newly created .dropbox-dist folder.

 ~/.dropbox-dist/dropboxd

I believe that I made a mistake because I am too used to always execute commands in Terminal as a su (superuser) so I prefixed both commands with the "su" word and got Dropbox working but **it is not syncing** and also every time that I log in to Ubuntu it gives me the following message:

**Authentication Required**
Authentication is needed to run usr/bin/dropbox

So I have a working Dropbox that I can't use!

I already wasted hours looking for a solution in this forum as well as on Dropbox forum and in general on Google and out of the few ideas that I found nothing appears to work.

Any help is going to be immensely appreciated.

---

### Post by ibjsb4 on 2015-01-19
Ubuntu 13.10 has reached end of life and no longer supported.  12.04, 14.04 and 14.10 are the currently supported versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I believe the software center installs nautilus-dropbox.  Be sure it is removed so not to cause conflict.

I would remove dropbox (~/.dropbox and -dist) then upgrade to 14.04 and install dropbox (using the dropbox site and not the software center).
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9)

---

### Post by Ivan_Gil on 2015-01-21
> **ibjsb4 said:**
> Ubuntu 13.10 has reached end of life and no longer supported.  12.04, 14.04 and 14.10 are the currently supported versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I believe the software center installs nautilus-dropbox.  Be sure it is removed so not to cause conflict.

I would remove dropbox (~/.dropbox and -dist) then upgrade to 14.04 and install dropbox (using the dropbox site and not the software center).
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9)


Thank you very much ibjsb4 for your response, but I already tried 14.04 and went back to 13.10 because I need to be able to configure my keyboard in Spanish and although I was able to do it in 14.04, however the keys for the accent were located over the key [ instead of the key " which is the one that I have been using for years, so I was not able to do the transition and went back. 

Is there a way to configure the keyboard in Spanish in 14.04 to make the accent to be located in the " key?

---

### Post by ibjsb4 on 2015-01-22
> Is there a way to configure the keyboard in Spanish in 14.04 to make the accent to be located in the " key?
I only use english here, so I don't know.  It would be better to start a thread on the subject.

I understand why your using 13.10, but its really necessary to run something that is supported.  Your not even getting security updates with 13.10.  Maybe you could revert back to 12.04; it is supported till 2017.

---

### Post by Ivan_Gil on 2015-01-22
OK, I am going to start a thread on the subject as you suggested. Also thank you for the link to Googl Ubuntu, I didn't know about it. Here it is for those interested in looking at google and getting only results related to Ubuntu:

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Thank you very much **ibjsb4 **for your valuable help, I appreciate it!

---

### Post by patr5ck on 2015-07-14
> **ibjsb4 said:**
> Ubuntu 13.10 has reached end of life and no longer supported.  12.04, 14.04 and 14.10 are the currently supported versions.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I believe the software center installs nautilus-dropbox.  Be sure it is removed so not to cause conflict.

I would remove dropbox (~/.dropbox and -dist) then upgrade to 14.04 and install dropbox (using the dropbox site and not the software center).
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=do+version+upgrade&sa=Search&cof=FORID:9)

Thanks this helped. I am running on Unbutu 14.04, so instead, I simply purged dropbox and nautilus-dropbox. 

```
sudo apt-get -y purge nautilus-dropbox* dropbox*
```

Then I installed from the dropbox site and it is working fine now.

---

### Post by tcolley on 2015-08-28
Solved? I had this problem today i.e. being asked to give dropbox superuser privileges. After discovering and trying a couple of other options that didn't work, I tried something else.  I simply uninstalled and reinstalled dropbox from the Ubuntu Software Centre. Program now works fine and doesn't request supersuser privileges. And this process didn't necessitate a reloading of the files stored in the dropbox directory. HTH!

---

