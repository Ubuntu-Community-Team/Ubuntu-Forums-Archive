---
title: "Purple Screen on Updating to 10.04"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Dr Mac 24 on 2010-11-24
I've just been trying to update from 9.10 to 10.04. The downloading finished with these errors:


Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu7.3_all.deb](http://archive.ubuntu.com/ubuntu/poo...ntu7.3_all.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...u7.3_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...u7.3_amd64.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu7_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu7_amd64.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu3_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu3_all.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu3_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu3_all.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...u8.3_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...u8.3_amd64.deb) 404 Not Found [IP: 91.189.92.171 80]

Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/poo...ntu1_amd64.deb) 404 Not Found [IP: 91.189.92.171 80] 

I found solution at "https://answers.launchpad.net/ubuntu/+question/130008" and cleared fault using:
QUOTE
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
QUOTE
in the Terminal. 

Download went OK install started OK. Checked an hour later and screen had went dark, you could just see the image of the message box as things progressed but couldn't read anything.
Another hour screen blank with nothing appeared happening.
Reset after a couple of hours, which loaded to a purple screen with nothing happening.
Switched off and to bed.
The system now boots through the Grub to a bark purple screen with few dashes along the top of the screen, and that it!

I would appreciate any ones help

---

### Post by Rubi1200 on 2010-11-24
What graphics card do you have installed?

---

### Post by Dr Mac 24 on 2010-11-26
> **Rubi1200 said:**
> What graphics card do you have installed?

There is a graphics is integrated into the mother board chip set. I have'nt installed a stand alone graphic card.

---

### Post by sikander3786 on 2010-11-26
Edit the first entry in Grub menu by pressing 'e'. Navigate to "quiet & splash" delete them and type "nomodeset" in their place. Press Ctrl + X to continue boot. If successful, you'd see the desktop now.

If not, select Recovery mode from Grub menu (2nd on the list), then drop to root shell and perform the following commands.

```
dhclient eth0
```

Where eth0 is your network interface.

```
apt-get update
```

```
apt-get upgrade
```

If errors are encountered,

```
apt-get install -f
```

```
dpkg --configure -a
```

It would be handy if you please list the errors here.

And to find out your graphics chipset,

```
lspci | grep VGA
```

---

### Post by Dr Mac 24 on 2010-11-27
Sikander3786 modify the Grub but Control X didn't work so escaped back to Grub and continued booting no change, hence negating changes.

So into recovery mode, got there OK but can't change focus with arrow keys, so still stuck. 

Any other suggestions?

Cheers.

---

### Post by Dr Mac 24 on 2010-11-27
Sikander,

Managed to get into the root shell and went through the 1st 2 commands OK, on the 3rd dpkg was interrupted and system asked for 'sudo dpkg --configure  -a' to run. no other commands accepted so went ahead with 'sudo dpkg --configure  -a'

 This showed that the '/etc/kernel/header-postinst.d/dkms' configuration file has been deleted. Then ask whether to install updated version (Y or I), keep current version (N or O), show difference (D). Irrespective of entering any reply (Y,N,D) nothing happens.

After going through the same routine a few times eventuality a new header was installed along with a stack of other stuff. And ha presto the 10.04 OS it works!!

Thank you very mush for your help, much appreciated. Note that my graphic chipset is 'Radon HD 3200'.

One final issue: when running Update with the new 10.04 OS a number of fetch failures occured ieie

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.4_amd64.de](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.4_amd64.de) ..Could not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3ubuntu0.10.04.1_amd64.deb..Could](http://archive.ubuntu.com/ubuntu/pool/main/a/apr-util/libaprutil1_1.3.9+dfsg-3ubuntu0.10.04.1_amd64.deb..Could) not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.14-5ubuntu8.4_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apache2/apache2-utils_2.2.14-5ubuntu8.4_amd64.deb) ..Could not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.15.5.6ubuntu4.4_all.deb) ..Could not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.1_all.de](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.1_all.de) ..Could not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.1_amd64.deb) ..Could not resolve ‘archive.ubuntu.com’
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/gir1.0-pango-1.0_1.28.0-0ubuntu2.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/gir1.0-pango-1.0_1.28.0-0ubuntu2.1_amd64.deb) ..Could not resolve ‘archive.ubuntu.com’

and 'sudo dpkg --configure  -a' doesn't sort it. Is this because Software Source now needs updating?

Thanks again.

---

### Post by sikander3786 on 2010-11-27
Glad to know that you can boot to the desktop now :-) Hopefully, we'll resolve the other issue also.

For that, please post the output of

```
cat /etc/apt/sources.list
```

---

### Post by Dr Mac 24 on 2010-11-27
> **sikander3786 said:**
> Glad to know that you can boot to the desktop now :-) Hopefully, we'll resolve the other issue also.

For that, please post the output of

```
cat /etc/apt/sources.list
```

Note the I Hiberated the machine for a will and rerunning update it all work fine??

However, the output is:

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse restricted universe main
# deb-src [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main # disabled on upgrade to karmic
# deb [http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu](http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu) karmic main # disabled on upgrade to karmic
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe

I guess all the ones relating to jaunty should be removed, yes?

---

### Post by sikander3786 on 2010-11-27
If it is upadting correctly, it might just be a problem with your connectivity or the update server. We don't need to do anything for that unless the problem starts appearing again.

As long as the line is commented with # in the beginning, it has no effect. So you don't want to remove Jaunty or Karmic entries. Your sources.list is just fine.

For now, everything is OK and you can just enjoy.

Happy Ubuntu-ing!

[COLOR="Red"]**Edit:**[/COLOR] And you can mark the thread Solved properly by using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

---

