---
title: "Error message while updating"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by krishnakittu on 2009-01-08
I am using ubuntu 8.10
when i am trying to update through "update manager" its showing error.
when i click on check button in "update manager" then it showing following error
[IMG]http://i40.tinypic.com/11rygyq.jpg[/IMG]

help me out of this problem:confused:

---

### Post by Elfy on 2009-01-08
Run 

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by theinnercityhippy on 2009-01-08
> **forestpixie said:**
> Run 

```
sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Also type this into the terminal. Open it by going to 

Applications > Accessories > Terminal

This is a known bug in Medibuntu so you are not alone.

When you have the keyring manager as above type


```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Which will add the correct repository to your sources list and hopefully fetch the correct key.

GPG keys are there to ensure that the software you are downloading and installing are guaranteed to be what they say they are and not from an untrusted source which could contain viruses.

It is the major advantage Linux has over other OS's and the rason you don't need to reinstall it every 6 moths to get rid of all the spyware :-)

Hope this helps

-JimDog-

---

### Post by krishnakittu on 2009-01-17
Thanks friends....problem sloved

---

### Post by kgbudge on 2009-01-21
I'm seeing a very similar problem, but with Ubuntu 8.04 LST:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

I tried the sudo command (sudo apt-get install medibuntu-keyring && sudo apt-get update) but apt-get could not find the medibuntu-keyring package:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package medibuntu-keyring


Any further suggestions?

---

### Post by theinnercityhippy on 2009-01-24
> **kgbudge said:**
> I'm seeing a very similar problem, but with Ubuntu 8.04 LST:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

I tried the sudo command (sudo apt-get install medibuntu-keyring && sudo apt-get update) but apt-get could not find the medibuntu-keyring package:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package medibuntu-keyring


Any further suggestions?

Can you post the output of
```
cat /etc/apt/sources.list
```

And check if you have the correct medibuntu repository listed. Not sure why you would have ppa.launchpad.net in there as this is a developer area for bug-fixing i believe.

If the medibuntu repo is not listed, you can add it in one of several ways. The easiest is to use the echo command to append the repo to the end of the file as follows;

```
sudo echo "deb http://packages.medibuntu.org/ hardy free non-free" >> etc/apt/sources.list
```

(NOTE: it is very important that you include 2 >> and not 1 > as two will append it to the end of the file wheras one will replace the file with what you entered. Alternatively you could do this by hand using nano, gedit or vi (whichever you prefer to use as a text editor), opening it as follows;

```
sudo gedit /etc/apt/sources.list
```

I would probably reccommend commenting out the launchpad entry, by placing a # at the start of the line it resides on.

then update your gpg keys with the following command

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Alternatively, you could try issuing the following two commands for hardy

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Then you should be cooking :-)

Hope this works for you, let us know how you get on so hopefully we can get this thread marked as solved for other users to refer to.

-JimDog*-

---

### Post by AiRAVATA on 2009-02-13
Hey mate. I'm using 8.04 LTS DVD and I've done all of the above, but when I type "sudo apt-get update" keeps giving me the same error:

```

W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9
W: You may want to run apt-get update to correct these problems

```

Any suggestions?

Oh, by the way, my sources.list file looks like this:
```

## deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb http://packages.medibuntu.org/ hardy free non-free

```

---

### Post by AiRAVATA on 2009-02-13
I've solved it by entering the following code:

```

gpg --keyserver keyserver.ubuntu.com --recv 8B9FBE5158B3AFA9
gpg --export --armor 8B9FBE5158B3AFA9 | sudo apt-key add -
sudo apt-get update

```

Can you comment on that? Because I've read it somewhere and I'm not at all sure of what I did.

---

### Post by grumpus27 on 2009-02-20
Thanks for that - I've been meaning to fix a couple of nags in Synaptic for ages and this did the job.
The first line downloads the key from the key server, the first part of the second line extracts the contents of the key as text and feeds it to the second part which adds it to the APT list of trusted sources.  The third line isn't necessary (although it will show if you've got rid of the nag) - it just runs a package update from the command line rather than through Update Manager.

You can list the public keys registered with GnuPG by running
```
gpg --list-keys
```
and those registered with APT by running
```
sudo apt-key list
```

> **AiRAVATA said:**
> I've solved it by entering the following code:

```

gpg --keyserver keyserver.ubuntu.com --recv 8B9FBE5158B3AFA9
gpg --export --armor 8B9FBE5158B3AFA9 | sudo apt-key add -
sudo apt-get update

```

Can you comment on that? Because I've read it somewhere and I'm not at all sure of what I did.

---

### Post by forger on 2009-02-22
You have to fix your ppa links too:
[thread=1056099]**Update your Launchpad PPA repositories and apt keys**[/thread]

---

