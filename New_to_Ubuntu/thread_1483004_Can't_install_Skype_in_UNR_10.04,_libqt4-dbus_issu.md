---
title: "Can't install Skype in UNR 10.04, libqt4-dbus issue"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by Iamiko on 2010-05-14
Help, I have a slight problem with installing Skype 32bit on my Samsung NC10.

Am getting a "dependency is not satisfiable" error on the install with the following reason: libqt4-dbus (>= 4.4.3)

Is this an issue with UNR or have I done something blindinlg stupid? The install of UNR is pretty much a fresh install and I have skype running on my 10.04 Ubuntu desktop.

---

### Post by ajgreeny on 2010-05-14
All the same repos are available to both versions of Ubuntu so this does not make sense.  Do you need to enable any repos in the UNR version so as to get that library?

---

### Post by dalee on 2010-05-14
Hi,

I've had this problem too. What my problem was, I was using a different repository server on my netbook vs my desktop. For what ever reason the servers were slightly different. I changed the servers to match and I was good to go.

Might not be your problem, but it's cheap and easy to check and change.:)

dalee

---

### Post by Sealbhach on 2010-05-14
> **Iamiko said:**
> Help, I have a slight problem with installing Skype 32bit on my Samsung NC10.

Am getting a "dependency is not satisfiable" error on the install with the following reason: libqt4-dbus (>= 4.4.3)

Is this an issue with UNR or have I done something blindinlg stupid? The install of UNR is pretty much a fresh install and I have skype running on my 10.04 Ubuntu desktop.

How are you installing Skype? From the package manager or from the Skype website?

.

---

### Post by ajgreeny on 2010-05-14
> **Sealbhach said:**
> How are you installing Skype? From the package manager or from the Skype website?

.
Skype is no longer available from the repos with the package manager, so I assume it must be direct from the skype website.  Are you using the .deb available from there or trying to use something else?

---

### Post by Sealbhach on 2010-05-14
> **ajgreeny said:**
> Skype is no longer available from the repos with the package manager, so I assume it must be direct from the skype website.  Are you using the .deb available from there or trying to use something else?

Right, what I did was install Ubuntu Tweak, added the Skype repo and installed from there.

.

---

### Post by manso.manu on 2010-10-24
> **$sudo apt-get install skype**

Error
skype: Depends: libqt4-dbus (>= 4:4.5.3) but it is not going to be installed
E: Broken packages
[B]
$sudo apt-get install libqt4-dbus[/B]
Error
The following packages have unmet dependencies:
  libqt4-dbus: Depends: libqt4-xml (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.1 is to be installed
               Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.1 is to be installed
E: Broken packages
Setting  "Update" option correctly in Repositories from Synaptic Package Manager will do the trick.Go to 

[B]System> Administration > Synaptic Package Manager >Settings>repositories >updates
[/B]
and check these in Ubuntu updates


[LIST]
[*]Important security updates(lucid-security)
[/LIST]

[LIST]
[*]Recommended updates(lucid-updates)
[/LIST]

[LIST]
[*]Pre-released updates(lucid-proposed)
[/LIST]
Then enter

[LIST=1]
[*] Skype in Quick Search in Synaptic Package Manager.
[*]Check the required skype package and other skype plugins like skysentilas - extra Functionalites for Linux Skype Client.
[*] Apply and wait for skype to get installed.
[*]Done.
[/LIST]

 :smile:

---

### Post by prisoner849 on 2010-11-06
hi guys, thanks manso.manu for the post, it fixed things for me. I had to run an APT fix before running the deb package downloaded from skype, but it's all workin now.

Cheers.

---

