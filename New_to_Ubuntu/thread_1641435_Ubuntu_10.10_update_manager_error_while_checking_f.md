---
title: "Ubuntu 10.10 update manager error while checking for updates"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by raju50 on 2010-12-09
Failed to download repository information

Check your Internet connection.

Details:
W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 46B4E34C17CF995E, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  403  Forbidden
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2010-12-09
Go to Software Center > Edit > Software Sources and select the Main Server.

Regarding the error with Launchpad PPA authentication, Software > Center > Edit > Software Sources > Other Software Tab and disable the offensive Launchpad ppa for the moment.

And then,
```
sudo apt-get update
```

---

### Post by raju50 on 2010-12-09
I did just that. I disabled four repositories where it was written ppa.launchpad.net and then also did  sudo apt-get update. And then once again I clicked Check button in Update Manager and this time I got the following error:

Failed to download repository information

Check your Internet connection.

Details:
W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/source/Sources.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  403  Forbidden
, W:Failed to fetch [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  403  Forbidden
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sikander3786 on 2010-12-09
Post the output of this command.

```
cat /etc/apt/sources.list
```

While posting, press the # icon in post menu and paste your text in between the generated code tags ;-)

---

### Post by think13 on 2010-12-09
It looks like something is wrong with that mirror. I can only see dapper drake there: [http://ubuntu.mirror.cambrium.nl/ubuntu/dists/](http://ubuntu.mirror.cambrium.nl/ubuntu/dists/)

The official mirror site also says it's last known update time is unknown: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Try changing your software sources to point to one of the up to date mirrors listed in the above link (preferably one close to home).

---

### Post by raju50 on 2010-12-09
Output of cat /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick main restricted
deb-src http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick universe
deb-src http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick multiverse
deb-src http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu/ maverick-security restricted main multiverse universe
deb http://ubuntu.mirror.cambrium.nl/ubuntu/ maverick-updates restricted main multiverse universe

```

---

### Post by sikander3786 on 2010-12-09
sources.list seems ok.

Did you follow this step from my first post?

> Go to Software Center > Edit > Software Sources and select the Main Server.


---

### Post by raju50 on 2010-12-09
Yes. Canonical-supported Open Source software(main) is already tick marked.

---

### Post by mcduck on 2010-12-09
I don't think he's asking you to enable the "main" repository, but to change the server to Ubuntu's main server. Or, really, anything else than the mirror you are now using.

(It's the "Download From"-dropbox on the Ubuntu Software-tab)

---

### Post by raju50 on 2010-12-09
Yes I did that. Thanks. Now I'm not getting any error. :p

---

### Post by sikander3786 on 2010-12-09
Thanks to **mcduck** for explaining what I intended to say. My mistake, I should have made that clear.

Glad to know the issue is solved.

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by apvet on 2010-12-11
I have recently moved to Ubuntu 10.10 and have been encountering a similar issue but it appears to be more of a connectivity issue. The message I get is:

[I]W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (110: Connection timed out)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (110: Connection timed out)
[/I]
Forgive me if this is a stupid question, as I am a newbie here.Can anyone recommend  a fix to this?

---

### Post by gordintoronto on 2010-12-11
You're better off starting a new thread rather than adding to one which is solved.

I think you have a DNS server problem. Can you browse the web?

---

### Post by apvet on 2010-12-11
Sorry about that. . I did  end  up staringt another new thread on this several minutes ago. Yes. I have no issue browsing or navigating the web.

---

### Post by idea3 on 2012-04-23
Hi!
I have a similar problem: when I try install a program from Ubuntu Software Center, it starts to Update cache but at the the end a message appears :  
FAILED TO DOWNLOAD REPOSITORY INFORMATION
Check your Internet connection

Details:

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.92.170). - connect (110: Connection timed out) [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.92.191). - connect (110: Connection timed out) [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http:
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Unable to connect to extras.ubuntu.com:http:
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-amd64/Packages.gz)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I am connected in Internet and I checked in Edit->Sofware sources..that main server is selected.

The source.list is   

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maveri
ck main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted main multiverse uni
verse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiv
erse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-backports main restricted un
iverse multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) maverick-backports main restricte
d universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main multi
verse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse


I don't know what I must do...
Thanks!

---

### Post by clrn0979 on 2012-11-30
I had the same prob after installing 12.04. after i followed the afore mentioned no probs. cudos

---

### Post by clrn0979 on 2012-11-30
did the afore mentioned and it worked for me, cudos.

---

### Post by wildmanne39 on 2012-12-01
Old thread closed.

---

