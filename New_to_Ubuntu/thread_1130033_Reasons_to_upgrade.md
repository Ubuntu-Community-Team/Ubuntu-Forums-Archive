---
title: "Reasons to upgrade?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by blueridgedog on 2009-04-19
I was looking at a few posts talking about upgrading or doing clean installs with 9.04.  I skimmed the Ubuntu site looking for a change log to help me decide if an upgrade was warranted but could not find anything.

Can anyone share a list of the changes in 9.04 that would help me decide if I need to upgrade?  I am very happy with 8.10 and have generally gotten it the way I want at this point.

---

### Post by Paqman on 2009-04-19
> **blueridgedog said:**
> 
Can anyone share a list of the changes in 9.04 that would help me decide if I need to upgrade?  I am very happy with 8.10 and have generally gotten it the way I want at this point.

If the changes you've made to 8.10 are stuff like appearance and application settings, then you can carry them over whether you upgrade or reinstall. It's only changes to the core system that would be lost.

Program settings, appearance customisations, etc all live in your /home folder (hit ctrl-H to see all the .directories that contain the settings). If you upgrade they'll all be retained. If you reinstall you can simply take a backup of those folders and copy them back into your new profile after installing. Easy peasy.

The decision to either upgrade or reinstall is a matter of opinion. Some people favour one or the other. Personally i've never had an upgrade go wonky on me, so I don't see the point in reinstalling, but some folks swear by it.

As for staying on 8.10, you can do that too. Support for Intrepid lasts until April next year. After that you'll have to upgrade or reinstall.

---

### Post by ELD on 2009-04-19
You could always try the livecd, that will probably give you the best experience other than virtualizing it or installing it on a seperate partition.

---

### Post by ddrichardson on 2009-04-19
Desktop features
----------------

Faster boot times:  improvements to Ubuntu's start-up process mean you can
spend less time waiting and more time being productive with your Ubuntu
desktop.

Notification system:  notifications, those alerts that signify a change of
status on your system or whether someone is contacting you, have been made
consistent across applications to provide a pleasing, intuitive experience
for users.

Server features
---------------

Cloud computing:  Ubuntu Enterprise Cloud (powered by Eucalyptus) puts you
in control of your own cloud computing infrastructure, compatible with
Amazon's Elastic Compute Cloud (EC2) but running on your own servers behind
your firewall.  Ubuntu Server Edition 9.04 will also see Ubuntu available
on Amazon EC2 -- making it the most complete cloud environment available
today.

Turn-key mail servers:  the dovecot-postfix package in Ubuntu 9.04 provides
an all-in-one solution for deploying SMTP, POP3, and IMAP services with
integrated server-side filtering support.

Netbook Remix features
----------------------

Built-for-purpose interface: favourite applications and websites are just a
click away, making Ubuntu Netbook Remix a great choice for netbook users.

Faster boot times: improvements to Ubuntu's start-up process mean you can
spend less time waiting and more time being productive with your Ubuntu
Netbook desktop.

Ubuntu Netbook Remix is known to work on these netbook models:
Asus Eee PC 900
Acer Aspire One
Dell Mini 9

Kubuntu features
----------------

Kubuntu, built on the amazing KDE 4.2, brings users a complete,
full-featured KDE4 desktop with many new applications and innovations.

Please see [https://wiki.kubuntu.org/JauntyJackalope/RC/Kubuntu](https://wiki.kubuntu.org/JauntyJackalope/RC/Kubuntu) for details.

Xubuntu features
----------------

Xubuntu comes with the light-weight Xfce 4.6 desktop environment for those
who want a desktop that is easy to use, but places particular emphasis on
conserving system resources.

Please see [https://wiki.ubuntu.com/Xubuntu/JauntyJackalope/RC](https://wiki.ubuntu.com/Xubuntu/JauntyJackalope/RC) for further
details.

Ubuntu Studio features
----------------------

Ubuntu Studio includes updates to input hardware and sound device
management from Ubuntu Desktop and a complete suite of tools for generation
of audio, video, and graphic content.

Ubuntu Studio 9.04 also features a streamlined installation process, giving
you a familiar Ubuntu desktop and all of your studio applications in a
single step.

The realtime kernel flavor (linux-rt) has returned and is again used by
default in Ubuntu Studio.  The rtirq script ([http://alsa.opensrc.org/Rtirq](http://alsa.opensrc.org/Rtirq))
is also now included in the ubuntustudio-audio package.  It is recommended
that users not use the new EXT4 filesystem with the linux-rt kernel on
production systems due to some reports of instability.

Jack-audio-connection-kit now includes support for the Free Firewire Audio
Drivers (FFADO, [www.ffado.org]("http://www.ffado.org/")).

Mythbuntu features
------------------

As of 9.04, Mythbuntu fits better into the Ubuntu ecosystem by using the
same build methods as all other remixes and derivatives.  Because of this,
9.04 has been a focus around stability and preparing for an easy transition
to the next version of MythTV (0.22) later this year.

Unfortunately, the main Mythbuntu website, [http://mythbuntu.org]("http://mythbuntu.org/") is
temporarily down due to a problem with the hosting provider.  RC images
will still be available at
[http://cdimage.ubuntu.com/mythbuntu/releases/jaunty](http://cdimage.ubuntu.com/mythbuntu/releases/jaunty) .  We'll restore the
other mirrors as soon as the main site returns.

A more complete tour of the features new in 9.04 can be found at
[http://www.ubuntu.com/getubuntu/releasenotes/904overview](http://www.ubuntu.com/getubuntu/releasenotes/904overview)
[]("http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce")

---

### Post by 3rdalbum on 2009-04-19
The biggest change that I've noticed is a very quick boot. Every time I turn on my netbook running Jaunty RC, I do something else and then look back at the machine and think "Geez, it's already booted!".

When it's officially released, there will be a document detailing the biggest changes.

---

### Post by Bölvaður on 2009-04-19
I would say stay. But in 2 months try make your system a dual boot and see if you like 9.04 (that is when the worst bugs have been ironed out and flattened and probably been utilized as accessories for poor people).

ext4 (the new file system) just crashed for me so I am atm doing a reinstall of jaunty with ext3 (well the odds of ext4 going bad 2 times in a row might not be huge and it takes short time to set everything up (Im almost done with everything and updates are going to be finished in 10 min... so that makes it 30 min from live cd to updated new os with all the old data on it... pretty good... Im getting off subject so......)

---

### Post by ddrichardson on 2009-04-19
> **3rdalbum said:**
> The biggest change that I've noticed is a very quick boot. Every time I turn on my netbook running Jaunty RC, I do something else and then look back at the machine and think "Geez, it's already booted!".

When it's officially released, there will be a document detailing the biggest changes.
Dude, I just posted the bulk of it! Fresh from Steve Langasek to my email inbox!

---

### Post by blueridgedog on 2009-04-19
> **ddrichardson said:**
> Desktop features
----------------

Faster boot times:  improvements to Ubuntu's start-up process mean you can
spend less time waiting and more time being productive with your Ubuntu
desktop.

Notification system:  notifications, those alerts that signify a change of
status on your system or whether someone is contacting you, have been made
consistent across applications to provide a pleasing, intuitive experience
for users.



Excellent!  Thanks.  I will do a fresh install on my eeePC and keep the desktop at 8.10 for a bit.

---

### Post by blueridgedog on 2009-04-19
> **Paqman said:**
> If the changes you've made to 8.10 are stuff like appearance and application settings, then you can carry them over whether you upgrade or reinstall. It's only changes to the core system that would be lost.


Most of the configurations I have made have been in the areas of making it operate the way I want such as automatically mounting a collection of hot swap SATA in a specific place for rsync backups, getting my home directory setup with symlinks to my files on a documents drive, installing my favorite applications (floola, handbrake, pan, DeVeDe etc), setting up repositories that link to those sites so I have their latest code, and finally getting my three Sun Virtual box installations up and running for the occasional need for XP or Vista (especially talking another person through a tech support issue with those OS's).

I will run it on my netbook for a while and see and perhaps go "all in" when 9.10 comes around.

Thanks.

---

### Post by Paqman on 2009-04-19
> **blueridgedog said:**
> Most of the configurations I have made have been in the areas of making it operate the way I want such as automatically mounting a collection of hot swap SATA in a specific place for rsync backups


That's just a matter of copying the relevant lines from /etc/fstab.

> 
getting my home directory setup with symlinks to my files on a documents drive


If you back up /home or have it on a separate partition, these owuld be preserved.

> 
installing my favorite applications (floola, handbrake, pan, DeVeDe etc)


You can reinstall any packages you got from a repo [automatically]("http://ubuntuforums.org/showthread.php?t=261366").

> 
setting up repositories that link to those sites so I have their latest code


Just lift the relevant lines from /etc/apt/sources.list

> 
and finally getting my three Sun Virtual box installations up and running

By default Virtualbox stores the VM files in your /home, so if you back up that or have a separate home then they'd be safe. Just reinstall Virtualbox and point it at the ready-made .vdi files.

---

