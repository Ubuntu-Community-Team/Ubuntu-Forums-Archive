---
title: "updating from ubuntu9.10 to ubuntustudio"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by duncanmaybury on 2010-01-19
Hello Folks
I am very new to linux/ubuntu
I want to get back into using my desktop with its audigy soundcard to controll my Roland hardware via midi and record it back in on a audio track. I like the look of Rosegarden for this.
First I installed straight 9.10, then saw that ubuntustudio9.10 looked like the thing to use so tried installing that from a dvd, it wouldn't work said something about the Grub not being able to be installed. So tried installing the 9.04ubuntustudio version, that worked but I couldn't figure out how to install rosegarden. Looked on the straight ubuntu9.10 version on my laptop, saw it was easily installed from the software centre. So I installed ubuntu9.10 again on my desktop as i could find the software centre on the 9.04studio version.
I couldn't find alsa on it and rosegarden says it cant find the jack server.
I saw that I can upgrade to ubuntustudio9.10 by typing:
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt


into the command line, It seemed to be working but then came up with the following:
[COLOR=Blue].3_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/universe xfs 1:1.0.8-5
  Could not open file /var/cache/apt/archives/partial/xfs_1%3a1.0.8-5_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/universe csound-gui 1:5.10.1~dfsg1-3ubuntu1
  Could not open file /var/cache/apt/archives/partial/csound-gui_1%3a5.10.1~dfsg1-3ubuntu1_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/universe csound-manpages 1:5.10~dfsg-2
  Could not open file /var/cache/apt/archives/partial/csound-manpages_1%3a5.10~dfsg-2_all.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/universe csound-utils 1:5.10.1~dfsg1-3ubuntu1
  Could not open file /var/cache/apt/archives/partial/csound-utils_1%3a5.10.1~dfsg1-3ubuntu1_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic-updates/multiverse mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1
  Could not open file /var/cache/apt/archives/partial/mencoder_2%3a1.0~rc3+svn20090426-1ubuntu10.1_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/multiverse transcode 3:1.1.4-0.0ubuntu4
  Could not open file /var/cache/apt/archives/partial/transcode_3%3a1.1.4-0.0ubuntu4_i386.deb - open (30: Read-only file system)
Err [http://ubuntu.retrosnub.co.uk](http://ubuntu.retrosnub.co.uk) karmic/multiverse transcode-doc 3:1.1.4-0.0ubuntu4
  Could not open file /var/cache/apt/archives/partial/transcode-doc_3%3a1.1.4-0.0ubuntu4_all.deb - open (30: Read-only file system)
Fetched 356MB in 10min 33s (563kB/s)                     
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Segmentation fault
duncan@duncan:~$ 

[COLOR=Black]Anyone know what this means, what I can do about it?
sorry for my ignorance, probably tack me a while to learn the art of linux:D.

Cheers
Dunc
[/COLOR][/COLOR]

---

### Post by zvacet on 2010-01-20
I tried link witch give you errors and they work.Any way in system>admin>software sources change server and see if that work.

---

