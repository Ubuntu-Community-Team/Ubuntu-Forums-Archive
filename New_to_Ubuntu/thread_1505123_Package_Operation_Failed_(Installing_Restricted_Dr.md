---
title: "Package Operation Failed (Installing Restricted Drivers)"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by Badmonkey005 on 2010-06-08
[QUOTE="Package Operation Failed"]installArchives() failed: 
Extracting templates from packages: 42%
Extracting templates from packages: 85%
Extracting templates from packages: 100%

Preconfiguring packages ...


Extracting templates from packages: 42%
Extracting templates from packages: 85%
Extracting templates from packages: 100%

Preconfiguring packages ...

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 122860 files and directories currently installed.)

Preparing to replace tzdata 2010i-1 (using .../tzdata_2010j-0ubuntu0.10.04_all.deb) ...

Unpacking replacement tzdata ...

Setting up tzdata (2010j-0ubuntu0.10.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

Errors were encountered while processing:

 tzdata

Setting up tzdata (2010j-0ubuntu0.10.04) ...

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66.

Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67.

Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68.

Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109.

dpkg: error processing tzdata (--configure):

 subprocess installed post-installation script returned error exit status 128

[/QUOTE]

I got this when attempting to install the restricted drivers for ubuntu. I do not know if this is caused by the fact that ubuntu is installed on my Flash drive.

The process I used to install is:

Disconnected HD's
Plugged in USB
Booted via ubuntu CD
Erased all data on USB and installed ubuntu (no partitions)

It boots up fine.

If anyone could tell me what's wrong I would greatly appreciate it. Thank you.

More information:
AMD 64 bit comp but running x86 version of Ubuntu 10.04 LTS

---

### Post by Autodave on 2010-06-08
> **Badmonkey005 said:**
> I got this when attempting to install the restricted drivers for ubuntu. I do not know if this is caused by the fact that ubuntu is installed on my Flash drive.

The process I used to install is:

Disconnected HD's
Plugged in USB
Booted via ubuntu CD
Erased all data on USB and installed ubuntu (no partitions)

It boots up fine.

If anyone could tell me what's wrong I would greatly appreciate it. Thank you.

More information:
AMD 64 bit comp but running x86 version of Ubuntu 10.04 LTS

This might seem like a stupid question, but if you disconnected your hard drives, where were you planning on installing the restricted extras to?

---

### Post by Autodave on 2010-06-08
> **Autodave said:**
> This might seem like a stupid question, but if you disconnected your hard drives, where were you planning on installing the restricted extras to?


Hmmmm....if you booted from a CD, then I would think that the packages tried to install to the CD drive.........which they obviously cannot do.

---

### Post by Badmonkey005 on 2010-06-08
I think you misunderstood. I gave you the steps I used to install ubuntu on the flash drive. This is NOT a live CD but a flash drive used as an SSD which contains a fully installed version of ubuntu. The live CD is what I used to install ubuntu onto the flash drive.

I am currently booted up on a fully installed version contained on the flash drive which has plenty of space for the updates to be installed.

---

### Post by Badmonkey005 on 2010-06-08
Disregard.

Once I did the security updates the restricted extras installed fine.

Thanks for trying.

---

