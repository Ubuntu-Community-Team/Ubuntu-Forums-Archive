---
title: "Software Center installation “untrusted packages” warning"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by Shahram A on 2010-07-06
Installation from Ubuntu Software Center “untrusted packages” warning

Using  Ubuntu 10.04 LTS
the Lucid Lynx - released in April 2010


Trying to install a few softwares from the built in Software Center or trying to get plug-ins for its music player with its automatic search, repeatedly I come across the following warning dialogue box:
=
Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
=
1- Does this mean that these softwares are not safe, can damage things or have spy-ware and things like that?
2- If it is safe how can they be installed? Because after the warning, installation is not allowed. Even Open Office Suite fails to install.

---

### Post by cariboo on 2010-07-06
Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```

then in the same terminal type:

```
apt-key add ~/.gnupg/pubring.gpg
```

---

### Post by lkjoel on 2010-07-06
Did you add any packages to your /etc/apt/sources.list, or Software Sources?
That is probably the reason

---

### Post by Shahram A on 2010-07-07
I am very new to Ubuntu &#8211; at zero &#8211; I have never worked with Linux before &#8211; I have experience of Windows as (advanced) user.
I don&#8217;t know what the  /etc/apt/sources.list, or Software Sources is. I also don't know what gpg keys are or do. However, when I installed Ubuntu at the beginning of this week, I updated it with the update manager. It updated all sorts of things which I am not familiar with. I also added many add-ons to Firefox and installed Mozilla Thunderbird 3 as well. 
So these were the installations whether they added any packages to etc/apt/sources.list, I don&#8217;t know.
When I tried to install the software from the software center apart from the warning sign, I noticed "certificate" at the beginning of one of the sub contents of the warning... I didn't take full note of it but it might hint at something... 
My computer is: 
Packard Bell laptop (Easy Note MH36)
250 GB Hard Disk, 2 GHZ Pentium  processor and 2 GB RAM
Half the disk is Windows 7 - 32 bit and the second half is Ubuntu.
Thank you
Shahram

---

### Post by RiceMonster on 2010-07-07
> **Shahram A said:**
> I am very new to Ubuntu – at zero – I have never worked with Linux before – I have experience of Windows as (advanced) user.
I don’t know what the  /etc/apt/sources.list, or Software Sources is. I also don't know what gpg keys are or do. However, when I installed Ubuntu at the beginning of this week, I updated it with the update manager. It updated all sorts of things which I am not familiar with. I also added many add-ons to Firefox and installed Mozilla Thunderbird 3 as well. 
So these were the installations whether they added any packages to etc/apt/sources.list, I don’t know.
When I tried to install the software from the software center apart from the warning sign, I noticed "certificate" at the beginning of one of the sub contents of the warning... I didn't take full note of it but it might hint at something... 
My computer is: 
Packard Bell laptop (Easy Note MH36)
250 GB Hard Disk, 2 GHZ Pentium  processor and 2 GB RAM
Half the disk is Windows 7 - 32 bit and the second half is Ubuntu.
Thank you
Shahram

/etc/apt/sources.list is a text file that you would have had to manually edit, or would have been changed if you went to System > Administration > Software Sources (I think that's where it is). So don't worry about that.

Did you try what cariboo907 said?

---

### Post by Shahram A on 2010-07-07
No I didn't do what cariboo907 suggested - first I am bit worried I might do more damage - second my Internet connection source is very limited so I have just seen the message.

I tried to install the Gnome office suite from the software center and below is the message that comes after the warning as details:

abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview gimp gimp-data gnome-core gnome-office gnumeric gnumeric-common gnumeric-doc inkscape libabiword-2.8 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libbabl-0.0-0 libblas3gf libgdome2-0 libgdome2-cpp-smart0c2a libgegl-0.0-0 libgfortran3 libgimp2.0 libgoffice-0.8-8 libgoffice-0.8-8-common libgtkmathview0c2a liblapack3gf liblink-grammar4 libmagick++2 libmng1 libots0 libpsiconv6 libt1-5 libwmf-bin libwv-1.2-3 link-grammar-dictionaries-en perlmagick planner python-lxml python-numpy python-renderpm python-reportlab python-reportlab-accel python-uniconvertor ttf-lyx xsane xsane-common.

However just after the above attempt the update manager started and after pressing install - the installation download started without problem.
Shahram

---

### Post by Shahram A on 2010-07-07
After the above mentioned Ubuntu update - things appear to be moving - I have tried installing Gnome Office suite - There were no more warning messages and it is in the middle of installation now. 
Probably the last Ubuntu update had not been complete or anyway the problem might have had something to do with it.
I'll try to post an other message after checking another install  tomorrow.

---

### Post by Shahram A on 2010-07-09
To close this thread, I don't know what the problem was, but I think it was probably triggered by Ubuntu updates and also again fixed by the next Ubuntu updates. The software center installations are now working without the "untrusted packages" warning.
Thanks everyone for your responses

---

### Post by Zunair on 2010-10-03
> **cariboo907 said:**
> Try repairing your gpg keys using the following commands. Open an Applications->Accessories->Terminal and type:

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
```then in the same terminal type:

```
apt-key add ~/.gnupg/pubring.gpg
```

i was experiencing the same issue after adding medibuntu into software center but your suggestion did the right trick thanks a bunch

---

### Post by dmhalljr on 2010-11-17
I tried the code and got an error. Seems strange since I have been able to download via Ubuntu Software Center for about a week and then suddenly started getting the untrusted packages. Am I missing something simple (I hope)?

I'm running 10.10, by the way. And I am able to download via Synaptic Package Manager.

douglas@Bob:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server wwwkeys.eu.pgp.net
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
douglas@Bob:~$ apt-key add ~/.gnupg/pubring.gpg
gpg: error writing keyring `/etc/apt/trusted.gpg': file write error
gpg: can't open `/etc/apt/secring.gpg'
gpg: error reading `/home/douglas/.gnupg/pubring.gpg': file write error
gpg: import from `/home/douglas/.gnupg/pubring.gpg' failed: file write error
douglas@Bob:~$

---

### Post by lkjoel on 2010-11-18
> **dmhalljr said:**
> I tried the code and got an error. Seems strange since I have been able to download via Ubuntu Software Center for about a week and then suddenly started getting the untrusted packages. Am I missing something simple (I hope)?

I'm running 10.10, by the way. And I am able to download via Synaptic Package Manager.

douglas@Bob:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server wwwkeys.eu.pgp.net
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
douglas@Bob:~$ apt-key add ~/.gnupg/pubring.gpg
gpg: error writing keyring `/etc/apt/trusted.gpg': file write error
gpg: can't open `/etc/apt/secring.gpg'
gpg: error reading `/home/douglas/.gnupg/pubring.gpg': file write error
gpg: import from `/home/douglas/.gnupg/pubring.gpg' failed: file write error
douglas@Bob:~$
Now try:
```
sudo apt-get update

```

---

### Post by moss_skin on 2010-11-19
Hi LKJoel,

Many thanks for your help. I'm not sure what the code you typed there did, but it solved the problem. :-)

Have a great weekend,

Chris

---

### Post by lkjoel on 2010-11-19
> **moss_skin said:**
> Hi LKJoel,

Many thanks for your help. I'm not sure what the code you typed there did, but it solved the problem. :-)

Have a great weekend,

Chris
It fetches the latest repositories.
Same as Check for Updates in the Update Manager.

---

### Post by venik212 on 2010-11-21
I have added some R repositories to the sources.list and am now getting this error from the software update center.  I tried other repositories, tried to get the gpg key but all have failed.  HELP please!

---

### Post by Lucian_Nilo on 2010-11-23
I got this after trying to update via the terminal. 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
nate@Laptop:~$

---

### Post by lkjoel on 2010-11-25
> **Lucian_Nilo said:**
> I got this after trying to update via the terminal. 

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.
nate@Laptop:~$
If you are using the Terminal to update your system, it should be alright.
It should just show something like:
> Warning NOT AUTHENDICATED:
package1, package 2
Just type: y <enter>

---

### Post by fslezak on 2010-11-25
Try  to go into the System>Administration>Software Sources. Just enable everything on the main page! :)

---

