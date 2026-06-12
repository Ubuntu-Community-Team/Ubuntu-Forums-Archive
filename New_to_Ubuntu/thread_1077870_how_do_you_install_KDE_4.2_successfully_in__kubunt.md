---
title: "how do you install KDE 4.2 successfully in  kubuntu 8.10?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by coops351 on 2009-02-22
hey i just installed kubuntu 8.10 today on my machine, and as you all know it comes with KDE 4.1 as standard but i wanna try KDE 4.2, how do you install that properly??

Cheers

Luke

---

### Post by ikisham on 2009-02-22
You must enable Intrepid proposed in Software Sources>updates

---

### Post by SuperSonic4 on 2009-02-22
```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

```
sudo apt-get update
```

it should then appear in the upgrade notifier (you can also do) ```
sudo apt-get upgrade
```

[Article at Kubuntu]("http://www.kubuntu.org/news/kde-4.2")

---

### Post by ikisham on 2009-02-22
There's a big difference in usability from 4.1 to 4.2 but then you may have to pay attention to install only the kde updates if you don't want to install all the most recent but maybe not much tested updates.

---

### Post by coops351 on 2009-02-22
does this all go into the konsole?

---

### Post by snova on 2009-02-22
> **coops351 said:**
> does this all go into the konsole?

Follow the instructions SuperSonic4 linked, here: [http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by coops351 on 2009-02-22
i dont understand the 1st part of it lol, i know im such a noob lol

---

### Post by snova on 2009-02-22
> **coops351 said:**
> i dont understand the 1st part of it lol, i know im such a noob lol

That's what we're here for. :)

> 1. Remove the koffice-data-kde4 package if you have it installed. The current koffice2 packages in the kubuntu-members-kde4 PPA are incompatible with the KDE 4.2 packages since they try to install icons to the same locations.

Unconcerning. I doubt very much you have this package installed.

> 2. Follow the Kubuntu Repository Guide to enable Recommended Updates and add the following to your 'Third-Party Software' tab:

Ok, open System -> Administration -> Software Sources. Go to Third Party Software, press Add, and paste this in:

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```

Now, open a terminal (Applications -> Accessories -> Terminal) and type this in:

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

So that the package manager can verify the integrity of the packages we will shortly download.

> 4. Old Plasma packages are not compatible with KDE 4.2, you should uninstall any plasmoids.

Unimportant. If you were upgrading, it might be of concern- but we're not.

> 5. You can now update any existing KDE 4 installation to the most recent version using the Adept Updater tool in your system tray.

Ok... it seems to assume we're *on* KDE already. Since we're not.

Open Synaptic (System -> Administration -> Synaptic) and press Reload (unless you already have- I think Software Sources may have prompted you to already). Search for and install the **kde** package.

Logout, and at the login screen, press the Options button at the bottom left, and select "Sessions" (or whatever it's called). Choose KDE from the list and proceed as usual.

Should work.

---

### Post by coops351 on 2009-02-22
for the kde package, so what do you search for? just kde?

---

### Post by coops351 on 2009-02-22
right its downloading the packages, we'll find out in 5mins if it has worked :) 

thanks for your help mate :), made it really easy to understand

Cheers

Luke

---

### Post by coops351 on 2009-02-22
this error message just appeared when i was installing the software, any ideas?


E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_all.deb: trying to overwrite `/usr/share/doc/kde4/HTML/en/kcontrol/windowbehaviour/index.cache.bz2', which is also in package kde-window-manager

---

### Post by snova on 2009-02-22
> **coops351 said:**
> this error message just appeared when i was installing the software, any ideas?


E: /var/cache/apt/archives/kdebase-workspace-data_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_all.deb: trying to overwrite `/usr/share/doc/kde4/HTML/en/kcontrol/windowbehaviour/index.cache.bz2', which is also in package kde-window-manager

Hmm, strange. It's not in my package...

Oh well, we'll simply remove it.

```
sudo mv /usr/share/doc/kde4/HTML/en/kcontrol/windowbehaviour/index.cache.bz2 /root
```

(Rather than actually delete it, we'll stash it someplace safe...)

Try the installation again. Quick terminal command:

```
sudo apt-get install kde
```

---

### Post by coops351 on 2009-02-22
new message appearing in the konsole;


luke@luke-desktop:~$ sudo apt-get install kde
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  gwenview: Depends: libkipi6 but it is not going to be installed
  kde: Depends: kde-core (>= 5:48ubuntu1) but it is not going to be installed
       Depends: kdeedu (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegames (>= 4:4.1.1) but it is not going to be installed
       Depends: kdetoys (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeaccessibility (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeadmin (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeartwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegraphics (>= 4:4.1.1) but it is not going to be installed
       Depends: kdemultimedia (>= 4:4.1.1) but it is not going to be installed
       Depends: kdenetwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdepim (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeutils (>= 4:4.1.1) but it is not going to be installed
       Depends: kdewebdev-kde4 (>= 4:4.1.1) but it is not going to be installed
  kdebase-workspace-bin: Depends: kdebase-workspace-data (= 4:4.2.0-0ubuntu1~intrepid1~ppa7) but it is not going to be installed
                         Recommends: dontzap but it is not installable
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

---

### Post by snova on 2009-02-22
> **coops351 said:**
> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these:
The following packages have unmet dependencies.
  gwenview: Depends: libkipi6 but it is not going to be installed
  kde: Depends: kde-core (>= 5:48ubuntu1) but it is not going to be installed
       Depends: kdeedu (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegames (>= 4:4.1.1) but it is not going to be installed
       Depends: kdetoys (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeaccessibility (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeadmin (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeartwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdegraphics (>= 4:4.1.1) but it is not going to be installed
       Depends: kdemultimedia (>= 4:4.1.1) but it is not going to be installed
       Depends: kdenetwork (>= 4:4.1.1) but it is not going to be installed
       Depends: kdepim (>= 4:4.1.1) but it is not going to be installed
       Depends: kdeutils (>= 4:4.1.1) but it is not going to be installed
       Depends: kdewebdev-kde4 (>= 4:4.1.1) but it is not going to be installed
  kdebase-workspace-bin: Depends: kdebase-workspace-data (= 4:4.2.0-0ubuntu1~intrepid1~ppa7) but it is not going to be installed
                         Recommends: dontzap but it is not installable
E: Unmet dependencies. Try &#8216;apt-get -f install&#8217; with no packages (or specify a solution).

Hmm. Well, try the command it suggested.

```
sudo apt-get -f install
```

---

### Post by coops351 on 2009-02-22
this is the reply i got from the konsole;


luke@luke-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-workspace-data libkipi6
The following packages will be REMOVED
  libkipi-common libkipi5
The following NEW packages will be installed
  kdebase-workspace-data libkipi6
0 upgraded, 2 newly installed, 2 to remove and 55 not upgraded.
2 not fully installed or removed.
Need to get 0B/7441kB of archives.
After this operation, 12.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 110680 files and directories currently installed.)
Unpacking kdebase-workspace-data (from .../kdebase-workspace-data_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-workspace-data_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_all.deb (--unpack):
 trying to overwrite `/usr/share/doc/kde4/HTML/en/kcontrol/windowbehaviour/index.cache.bz2', which is also in package kde-window-manager
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-data_4%3a4.2.0-0ubuntu1~intrepid1~ppa7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by coops351 on 2009-02-22
ive restarted the system and when i re-logged in the screen in completely white and a little message appeared in the top right corner briefly and then it disappears. the box says nepomuk data storage in bold letters at the top and the writing inside it says, rebuilding full nepomuk text index for new feature, this will only be done. ???
 
thats whats left is a cursor and white screen??

i havent got a clue what this is? any ideas now lol?

sorry guys, bloody noobs

---

### Post by abn91c on 2009-02-22
> **coops351 said:**
> ive restarted the system and when i re-logged in the screen in completely white and a little message appeared in the top right corner briefly and then it disappears. the box says nepomuk data storage in bold letters at the top and the writing inside it says, rebuilding full nepomuk text index for new feature, this will only be done. ???
 
thats whats left is a cursor and white screen??

i havent got a clue what this is? any ideas now lol?

sorry guys, bloody noobs
you needed to use the Kubuntu website guide, to install the kubuntu desktop the command is```
sudo apt-get install kubuntu-desktop
```

---

### Post by abn91c on 2009-02-22
> **snova said:**
> That's what we're here for. :)



Unconcerning. I doubt very much you have this package installed.



Ok, open System -> Administration -> Software Sources. Go to Third Party Software, press Add, and paste this in:

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```

Now, open a terminal (Applications -> Accessories -> Terminal) and type this in:

```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

So that the package manager can verify the integrity of the packages we will shortly download.



Unimportant. If you were upgrading, it might be of concern- but we're not.



Ok... it seems to assume we're *on* KDE already. Since we're not.

Open Synaptic (System -> Administration -> Synaptic) and press Reload (unless you already have- I think Software Sources may have prompted you to already). Search for and install the **kde** package.

Logout, and at the login screen, press the Options button at the bottom left, and select "Sessions" (or whatever it's called). Choose KDE from the list and proceed as usual.

Should work.
He already has Kubuntu 8.10 installed, the above menu choices are for Ubuntu

---

### Post by snova on 2009-02-22
> **abn91c said:**
> He already has Kubuntu 8.10 installed, the above menu choices are for Ubuntu

](*,) This is at least the second time I've overlooked the [kubuntu] prefix...

Oh well. Please post the contents of /etc/apt/sources.list, just to check.

---

### Post by coops351 on 2009-02-23
how do you do that considering when i log back into my system its just a blank screen and i can't do anything?

---

### Post by abn91c on 2009-02-23
> **coops351 said:**
> how do you do that considering when i log back into my system its just a blank screen and i can't do anything?ctr+alt+f1 will get you to a command prompt then type sudo apt-get install kubuntu-desktop

---

### Post by coops351 on 2009-02-23
it says kubuntu-desktop is already running the newest version.

it then says runs apt-get -f install to correct these

---

### Post by coops351 on 2009-02-23
and then when i do run apt-get -f install

it comes with errors, and says dpkg returned with error codes

so i think this install has really corrupted my system unless theres ways you think you can help out

---

### Post by abn91c on 2009-02-23
> **coops351 said:**
> and then when i do run apt-get -f install

it comes with errors, and says dpkg returned with error codes

so i think this install has really corrupted my system unless theres ways you think you can help out
one of the follwing might help 
sudo apt-get check
sudo apt-get autoremove
sudo dpkg --configure -a
or sudo aptitude reinstall kubuntu-desktop(last resort), then try the 4.2 upgrade again

---

