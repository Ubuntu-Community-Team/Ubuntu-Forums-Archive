---
title: "Problem installing programs from Synaptic program manager"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by ravitejuaganti on 2010-05-12
Hi All,
 
I am a complete begineer with Ubuntu. I have 8.10 currently. I was having problem downloading/installing any package from the synaptic package manager. So i did a little bit of research and found a post in this forum saying to remove all the Third-party software sources from System--> Admin-->Software sources. I tried to do the same and when i was trying to install firefox web broswer from synaptic program manager the found the following error message:
 
 
"**Could not mark all packages for installation or upgrade."**   What does this mean? How should i proceed? 
 
 
Thanks and Best Regards.
Ravi Ganti

---

### Post by Paz13 on 2010-05-12
Having a go here i'm probably even more of a beginner though, it could be beacuse synaptic is out of date in 8.10? Some packages in there could be removed from say mozzila.com? try install i using a .deb file?

---

### Post by halitech on 2010-05-12
I think 8.10 just went into EOL and isn't supported any longer. You can look up the support cycles here: [http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle)

I would recommend doing a fresh install of 9.04 or 10.04 as long as your machine will support it.

---

### Post by HarrisonNapper on 2010-05-12
Did you do a reload after you removed the other repos? It probably means that one of the dependencies for FF was in one of the repos you removed.

---

### Post by tgm4883 on 2010-05-12
Hit reload, then try installing again

---

### Post by ravitejuaganti on 2010-05-12
I tried doing a reload it went un-successful, the following is the error message:
 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/Release.gpg) Could not connect to 123.237.220.79:8118 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
...
 
W: Some index files failed to download, they have been ignored, or old ones used instead.
 
Thanks
Ganti

---

### Post by ravitejuaganti on 2010-05-12
ignore

---

### Post by HarrisonNapper on 2010-05-12
See halitec's response

---

### Post by thatguruguy on 2010-05-12
> **ravitejuaganti said:**
> I tried doing a reload it went un-successful, the following is the error message:
 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/Release.gpg](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/Release.gpg) Could not connect to 123.237.220.79:8118 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/main/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/restricted/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
W:Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/il8n/Translation-en_IN.bz2](http://archive.ubuntu-rocks.org/ubuntu/dists/intrepid/universe/il8n/Translation-en_IN.bz2) Unale to connect to 123.237.220.79:8118 
 
...
 
W: Some index files failed to download, they have been ignored, or old ones used instead.
 
Thanks
Ganti

Well, it looks like the ubuntu-rocks.org server is down, or has removed the intrepid directories.

Again, intrepid is no longer supported as of April of this year; is there any reason why you chose not to use 10.04?

---

### Post by ravitejuaganti on 2010-05-12
Ok HarrisonNapper. I have a couple of questions on mind which might help me proceed from here...
 
1. Given my laptop configuration is :  Intel Core 2 duo @2.00GHz 2.00GHz, 2GB ram, 120GB Hardisk with 90GB VISTA primary partition and rest Ubuntu 8.10. Which version do you suggest me to install 9.04 or 10.04?
 
2. How to get rid of this 8.10 before installing a newer version of ubuntu?
 
3. As i have fairly important files on my windows partition i dont want to loose any of my files while installation, so what all care should i take while doing a fresh installation?
 
4. If i want to allocate more disk space for the new ubuntu i am going to install (taken from my windows partition) how should i proceed?
 
Thanks for your quick response. 
 
Regards
Ganti

---

### Post by SKhan on 2010-05-12
i am also complete new ubuntu user and personally i prefer Ubuntu-Software-Center over Synaptic.
It seems that synaptic is more popular. Don't know if it's really any better than ubuntu software center.

---

### Post by ravitejuaganti on 2010-05-12
No thatsguruguy.  I have no issues in installing the newer version of ubuntu. But i was wondering if my system supports.
 
My config is as follows:   Intel Core 2 duo @2.00GHz 2.00GHz, 2GB ram, 120GB Hardisk with 90GB VISTA primary partition and rest Ubuntu 8.10.
 
Thanks
 
Ravi Ganti

---

### Post by halitech on 2010-05-12
With those specs 10.04 will certainly run fine on your laptop.

As far as installing it, download the new ISO, burn it to cd and then reboot with the cd in. Do a manual partition and reuse the same space that you currently have allocated to 8.10.

@SKhan - Synaptic and Software Center are both front ends to APT. The only advantage Software center has is it lists the programs, not all the libraries and other files you don't need to worry about. You can do the same thing from the terminal with

```
sudo apt-get install firefox
```

---

### Post by HarrisonNapper on 2010-05-12
> **ravitejuaganti said:**
> Ok HarrisonNapper. I have a couple of questions on mind which might help me proceed from here...
 
1. Given my laptop configuration is :  Intel Core 2 duo @2.00GHz 2.00GHz, 2GB ram, 120GB Hardisk with 90GB VISTA primary partition and rest Ubuntu 8.10. Which version do you suggest me to install 9.04 or 10.04?
 
2. How to get rid of this 8.10 before installing a newer version of ubuntu?
 
3. As i have fairly important files on my windows partition i dont want to loose any of my files while installation, so what all care should i take while doing a fresh installation?
 
4. If i want to allocate more disk space for the new ubuntu i am going to install (taken from my windows partition) how should i proceed?
 
Thanks for your quick response. 
 
Regards
Ganti

1. That configuration should be fine for all versions of Ubuntu presently available

2. First, I would suggest backing up your /home directory so you don't lose any of your settings, etc, though this may cause a few minor problems. To avoid 99% of these problems, make sure your userid is the same when you install the new version. Once you've done that, you can just install over it from a LiveUSB or LiveCD. See [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

3. The most important thing is simply not to touch the Windows partition. Meaning that when you install do NOT use the default option to erase everything on the hard-drive. Emphasis DO NOT use the whole hard-drive. You only want to format and install in the secondary partition. An easy way to determine which partition is windows is that it will be formatted in NTFS which I believe is denoted as a green partition whereas the other partition will be some version of EXT.

4. You will want to shrink the partition FROM WINDOWS. Emphasis: DO NOT use gparted to shrink your Windows partition. 1. Run a defragmentation in Windows on any drives in My Computer (any Hard Drives, rather). 2. Open the MMC using Start>All Programs>Accessories>System Tools>Computer Management. (There are lots of ways to get here, use google if that one doesn't work for you), go to the Disk Manager, right-click the C: drive and select "Shrink Volume". It will tell you how much shrink space is available and you can put whatever you want within that limit. I think when doing this, it is best to shrink the volume and then boot to a LiveCD and use gparted to remove the existing Ubuntu partition (careful, back up your /home directory first). Then format all of the empty space as ext3 or ext4 (if you're going to use 9.10 or 10.04, I recommend 4, which I would recommend either way, but there you have it). Then you don't have to worry about messing with that during install. After that, initiate install and install to free space. Your swap space should be at least 3GB.


Sorry that was long. Use PsychoCats and the Community Documentation and you should be fine.

---

### Post by ravitejuaganti on 2010-05-12
Thanks harrisonNapper and halitech. I have successfully installed 10.04 on my system and started exploring it already. I am able to download and install files from synaptic package manager too. 
 
Thanks guys for your quick and detailed replies.
 
Ganti

---

