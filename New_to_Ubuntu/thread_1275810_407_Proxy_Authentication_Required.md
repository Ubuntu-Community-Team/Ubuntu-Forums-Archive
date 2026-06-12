---
title: "407 Proxy Authentication Required"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by polarbear12345 on 2009-09-26
i m using a wireless internet connection that requires authentication.
when i do
sudo apt-get update 
on my ubuntu 8.10 i get error messages 
407 Proxy Authentication Required
i have tried lots of things to resolve it without success.
1)changing network proxy+authentication in system->preferences
2)changing network proxy+authentication in synaptic manager
3)modifying /etc/apt/apt.conf file
	it currently holds values:
[HTML]	Acquire::http::proxy"http://username:password@proxy:port";
Acquire::ftp::proxy "ftp://username:password@proxy:port";
[/HTML]

NOTE:my password also has a @ character and username has a \ character
sudo apt-get update gives result:
[HTML]
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_IN
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper Release.gpg                                                    
Ign http://gb.archive.ubuntu.com dapper/main Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper/restricted Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper/universe Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper/multiverse Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-updates Release.gpg
Ign http://gb.archive.ubuntu.com dapper-updates/main Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-updates/universe Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-updates/multiverse Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-backports Release.gpg
Ign http://gb.archive.ubuntu.com dapper-backports/main Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-backports/restricted Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-backports/universe Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper-backports/multiverse Translation-en_IN
Ign http://gb.archive.ubuntu.com dapper Release
Ign http://gb.archive.ubuntu.com dapper-updates Release
Ign http://gb.archive.ubuntu.com dapper-backports Release
Ign http://gb.archive.ubuntu.com dapper/main Packages
Ign http://gb.archive.ubuntu.com dapper/restricted Packages
Ign http://gb.archive.ubuntu.com dapper/universe Packages
Ign http://gb.archive.ubuntu.com dapper/multiverse Packages
Ign http://gb.archive.ubuntu.com dapper/main Sources
Ign http://gb.archive.ubuntu.com dapper/restricted Sources
Ign http://gb.archive.ubuntu.com dapper/universe Sources
Ign http://gb.archive.ubuntu.com dapper/multiverse Sources
Ign http://gb.archive.ubuntu.com dapper-updates/main Packages
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://gb.archive.ubuntu.com dapper-updates/universe Packages
Ign http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
Ign http://gb.archive.ubuntu.com dapper-updates/main Sources
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://gb.archive.ubuntu.com dapper-updates/universe Sources
Ign http://gb.archive.ubuntu.com dapper-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com dapper-backports/main Packages
Ign http://gb.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://gb.archive.ubuntu.com dapper-backports/universe Packages
Ign http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://gb.archive.ubuntu.com dapper-backports/main Sources
Ign http://gb.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://security.ubuntu.com dapper-security Release.gpg
Ign http://gb.archive.ubuntu.com dapper-backports/universe Sources
Ign http://gb.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://gb.archive.ubuntu.com dapper/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security/main Translation-en_IN
Err http://gb.archive.ubuntu.com dapper/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security/restricted Translation-en_IN
Ign http://security.ubuntu.com dapper-security/universe Translation-en_IN
Ign http://security.ubuntu.com dapper-security/multiverse Translation-en_IN
Err http://gb.archive.ubuntu.com dapper/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security Release
Err http://gb.archive.ubuntu.com dapper/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security/main Packages
Err http://gb.archive.ubuntu.com dapper-updates/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Err http://gb.archive.ubuntu.com dapper-updates/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-updates/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Err http://security.ubuntu.com dapper-security/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/main Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/restricted Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/universe Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/multiverse Packages
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/main Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/restricted Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/universe Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://gb.archive.ubuntu.com dapper-backports/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
Err http://security.ubuntu.com dapper-security/multiverse Sources
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/HTML]

/etc/apt/sources.list holds:
[HTML]
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb http://gb.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://gb.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
[/HTML]

---

### Post by overdrank on 2009-09-26
Hi and you say that your system is ubuntu 8.10 but your repo list is of ubuntu.com/ubuntu dapper-security  6.06 which I believe has reach its [End of Life]("https://help.ubuntu.com/community/EOLUpgrades").

---

### Post by polarbear12345 on 2009-09-26
> **overdrank said:**
> Hi and you say that your system is ubuntu 8.10 but your repo list is of ubuntu.com/ubuntu dapper-security  6.06 which I believe has reach its [End of Life]("https://help.ubuntu.com/community/EOLUpgrades").

actually i changed it after refering some internet content.
what should i do now?????

---

### Post by toofbwush on 2011-02-22
I know this is an old thread - but I'm having the exact same issue. Tried editing the proxy settings each way described above and still get the same error. The only difference is I'm using BioLinux6 which is built on Ubuntu - but I don't think this will make a difference. I'm behind an ISA Proxy.

@polarbear12345 - did you ever get this resolved?

---

### Post by gmargo on 2011-02-22
What did you use in your apt.conf for the proxy settings?  I ask because the format is critical, and is silently ignored if there's a problem.  Don't forget the semi-colon.
Proper format:
```

Acquire::http::Proxy "http://[[user][:pass]@]host[:port]/";

```

---

### Post by toofbwush on 2011-02-22
This is basically what my apt-get.conf looks like

```
Acquire::http::Proxy "http://isa_domain\username:password@proxyserver:8080/";
```

I'm wondering if the "\" in my user name should be %5C instead.
Also, in my password there is a "@" character, which I've read elsewhere is a bug in Ubuntu - so I've replaced it with %40

what do you think?

Alos, in my terminal, when I type 

$ export

I get

> 
...
ftp_proxy=ftp://proxy:8080/
http_proxy=http://proxy:8080/
https_proxy=https://proxy:8080/
...


But when I try to override these manually, or by editing my .bashrc, with 

export http_proxy = "...."
etc

it doesn't have any effect. I feel like there is some global variable somewhere that is trumping all my efforts, but I can't find where it is.

---

### Post by gmargo on 2011-02-22
> **toofbwush said:**
> I'm wondering if the "\" in my user name should be %5C instead.
Also, in my password there is a "@" character, which I've read elsewhere is a bug in Ubuntu - so I've replaced it with %40

what do you think?


I think you'll be darn lucky if it works :P. "@" and "\" will probably cause problems.  I'd run wireshark or something like that, to capture the outgoing packet, to see what actually goes out.  Can you use forward slash ("/") instead?

---

