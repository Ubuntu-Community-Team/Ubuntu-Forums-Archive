---
title: "Lenovo Yoga 13 - Wireless Hardware Off"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by amdserver on 2014-05-15
Long story short is I tried to dual boot my brand new laptop and it soft bricked the wireless card. 

I've been able to find what seems to be a promising solution here: [http://ubuntuforums.org/showthread.php?t=2215044&page=3&p=13001552#post13001552](http://ubuntuforums.org/showthread.php?t=2215044&page=3&p=13001552#post13001552)


Since I don't have any network connectivity, and this laptop doesn't have a NIC card (disappointed about this) how would I go about this? Can I bring the files over on a flash drive? I'm just not sure where to begin with that.

I should also mention that this occurred installing Linux Mint. I installed GRUB to / and used EasyBCD to edit Windows Boot Menu, but it doesn't want to boot.


I'm honestly at the point that I just want my WiFi back, is it possible to resolve this with Ubuntu Live CD? Or should I install it? It appears the fix requires rebooting Ubuntu, not sure how that would work with the Live CD.



Thank you guys!

---

### Post by varunendra on 2014-05-17
Having no idea of the actual reason of the problem, or what exactly the fix you referred to does, posting ONLY what you asked - how to do that offline, in case you are still stuck..

The only commands in the post you linked to that need internet connection are -
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
and
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
```
(note that the above command means a user must also install 'git' since it is not installed by default, but not relevant in your case since we are going to download the package manually). Rest of everything mentioned there is to be done offline. So to the alternative ways to do above two steps offline are -

**A.** To install the headers and build-essential packages offline :

[indent]**1)** Use the following command -
```
apt-get install **[COLOR="#0000CD"]--print-uris[/COLOR]** linux-headers-$(uname -r) build-essential
```
The '--print-uris' option will force apt to give you download links of the packages instead of actually downloading and installing them itself. These download links will be printed at the bottom of the output. Note them down and use them to download the packages on a different computer that has Internet connection.

**2)** Once the packages have been downloaded, copy them all onto a new, empty folder on your Ubuntu Desktop. Let us name this folder 'packages' to avoid confusion.

**3)** Assuming the '**packages**' folder is on your Desktop, and ALL the required packages are in it, open a terminal and run the following commands to install them -
```
cd Desktop/packages
sudo dpkg -i *
```
The '*****' means 'everything' (that is in the folder, that's why we need to keep only that stuff in it that we want to install).[/indent]

**B.** To download a 'Snapshot' of the git repository of the development kernel, you can manually browse to it at this URL : [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=shortlog;h=refs/heads/master](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=shortlog;h=refs/heads/master) and click on "**snapshot**" link in front of "**master**" repository (the top item in the list, marked as "master"). It may take a few seconds to start downloading, then the package will be downloaded in ".tar.gz" archive format.

Once downloaded, extract it to your home directory, then proceed with the rest of the process as mentioned in the guide post. You may have to manually rename the extracted directory to "ubuntu-trusty" if its name is different.

---

### Post by amdserver on 2014-05-21
Thank you for your response, I've been busy with work.

> **varunendra said:**
> Having no idea of the actual reason of the problem, or what exactly the fix you referred to does, posting ONLY what you asked - how to do that offline, in case you are still stuck..

There is a bad module in the kernel that disables the WiFi and my laptop has no hardware switch, the post I referenced is a hack that allows me to turn it back on.

> **varunendra said:**
> 
The only commands in the post you linked to that need internet connection are -
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
and
```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-trusty.git
```
(note that the above command means a user must also install 'git' since it is not installed by default, but not relevant in your case since we are going to download the package manually). Rest of everything mentioned there is to be done offline. So to the alternative ways to do above two steps offline are -

**A.** To install the headers and build-essential packages offline :

[indent]**1)** Use the following command -
```
apt-get install **[COLOR="#0000CD"]--print-uris[/COLOR]** linux-headers-$(uname -r) build-essential
```
The '--print-uris' option will force apt to give you download links of the packages instead of actually downloading and installing them itself. These download links will be printed at the bottom of the output. Note them down and use them to download the packages on a different computer that has Internet connection. 


I was able to install build-essentials but I'm missing some of the dependencies. It looks like this might go on forever as the dependencies have dependencies. I've tried this offline scrips to read the dependency list and print out a text file with all the download links but none of them are populating any info.

Any ideas?


[INDENT]Reading package lists...
Building dependency tree...
Reading state information...
build-essential is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 dpkg-dev : Depends: libdpkg-perl (= 1.17.5ubuntu5.2) but 1.17.5ubuntu5 is to be installed
            Recommends: fakeroot but it is not installable
            Recommends: libalgorithm-merge-perl but it is not installable
 g++ : Depends: g++-4.8 (>= 4.8.2-5~) but it is not installable
[/INDENT]

> **varunendra said:**
> 

**B.** To download a 'Snapshot' of the git repository of the development kernel, you can manually browse to it at this URL : [http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=shortlog;h=refs/heads/master](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-trusty.git;a=shortlog;h=refs/heads/master) and click on "**snapshot**" link in front of "**master**" repository (the top item in the list, marked as "master"). It may take a few seconds to start downloading, then the package will be downloaded in ".tar.gz" archive format.

Once downloaded, extract it to your home directory, then proceed with the rest of the process as mentioned in the guide post. You may have to manually rename the extracted directory to "ubuntu-trusty" if its name is different.

I was able to download and extract the kernel.

---

### Post by varunendra on 2014-05-22
> **amdserver said:**
> I was able to install build-essentials but I'm missing some of the dependencies. It looks like this might go on forever as the dependencies have dependencies.

Unless you manually installed some individual packages (standalone .deb files without their dependencies), this situation shouldn't have arisen. The '--print-uris' option prints the download URIs of all the dependencies as well, but only of the packages that it is going to install. Since you installed 'build-essential' from some different method, you'll need to purge it first (plus any other offending packages using the same following method) -
```
sudo dpkg -P build-essential
```
Then run the 'apt-get --print-uris...' command again, followed by the respective installation method I mentioned above.

---

### Post by amdserver on 2014-05-22
> **varunendra said:**
> Unless you manually installed some individual packages (standalone .deb files without their dependencies), this situation shouldn't have arisen. The '--print-uris' option prints the download URIs of all the dependencies as well, but only of the packages that it is going to install. Since you installed 'build-essential' from some different method, you'll need to purge it first (plus any other offending packages using the same following method) -
```
sudo dpkg -P build-essential
```
Then run the 'apt-get --print-uris...' command again, followed by the respective installation method I mentioned above.

My problem was that command never printed out the URLs I needed.

I removed the package and issued the command, here is the output:

```
E: Package 'build-essential' has no installation candidate
```

I am getting a USB to Ethernet adapter tomorrow that claims to be compatible with Linux. That should allow to me to download all the packages I need. Then I should be golden.

Thank you for your help.

---

