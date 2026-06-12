---
title: "Requires installation of untrusted packages"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by surfcast23 on 2011-06-27
I know that this has been discussed before, but I could not find an answer to my problem.
After searching through some threads I tried

```
sudo apt-get update
```which printed


```
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
Get:2 http://archive.canonical.com hardy Release.gpg [198B]              
Ign http://archive.canonical.com/ubuntu/ hardy/partner Translation-en_US
Get:3 http://us.archive.ubuntu.com hardy-backports Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com lucid-updates Release.gpg [198B]     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/multiverse Translation-en_US
Get:5 http://archive.canonical.com hardy Release [9,343B]            
Get:6 http://archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com lucid-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Get:8 http://us.archive.ubuntu.com hardy-backports Release [51.2kB]
Ign http://archive.canonical.com hardy Release   
Ign http://us.archive.ubuntu.com hardy-backports Release
Hit http://archive.canonical.com hardy/partner Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Get:9 http://archive.ubuntu.com lucid Release [57.2kB]
Hit http://archive.canonical.com hardy/partner Sources                       
Get:10 http://archive.ubuntu.com lucid-updates Release [44.7kB]        
Get:11 http://archive.ubuntu.com lucid-security Release [44.7kB]               
Get:12 http://archive.ubuntu.com lucid-backports Release [38.5kB]      
Ign http://archive.ubuntu.com lucid Release                                    
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Ign http://archive.ubuntu.com lucid-updates Release                     
Hit http://archive.ubuntu.com lucid/main Packages                       
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Ign http://archive.ubuntu.com lucid-security Release
Ign http://archive.ubuntu.com lucid-backports Release
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Packages
Hit http://archive.ubuntu.com lucid-backports/main Packages
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Sources
Hit http://archive.ubuntu.com lucid-backports/main Sources
Hit http://archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://archive.ubuntu.com lucid-backports/universe Sources
Fetched 1,185B in 1s (669B/s)
W: GPG error: http://archive.canonical.com hardy Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com hardy-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```I then tried

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 54422A4B98AB5139

``` getting 

```
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
student@ubuntu:~$ gpg --export --armor 54422A4B98AB5139 | sudo apt-key add -
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

``` I also tried changing servers, and checking source code etc... in the software sources

Any help would be appreciated. Thanks in advance

---

### Post by alphacrucis2 on 2011-06-27
> **surfcast23 said:**
> I know that this has been discussed before, but I could not find an answer to my problem.
After searching through some threads I tried

```
sudo apt-get update
```which printed


```
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US 
Get:2 http://archive.canonical.com hardy Release.gpg [198B]              
Ign http://archive.canonical.com/ubuntu/ hardy/partner Translation-en_US
Get:3 http://us.archive.ubuntu.com hardy-backports Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com lucid-updates Release.gpg [198B]     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ hardy-backports/multiverse Translation-en_US
Get:5 http://archive.canonical.com hardy Release [9,343B]            
Get:6 http://archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com lucid-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Get:8 http://us.archive.ubuntu.com hardy-backports Release [51.2kB]
Ign http://archive.canonical.com hardy Release   
Ign http://us.archive.ubuntu.com hardy-backports Release
Hit http://archive.canonical.com hardy/partner Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Get:9 http://archive.ubuntu.com lucid Release [57.2kB]
Hit http://archive.canonical.com hardy/partner Sources                       
Get:10 http://archive.ubuntu.com lucid-updates Release [44.7kB]        
Get:11 http://archive.ubuntu.com lucid-security Release [44.7kB]               
Get:12 http://archive.ubuntu.com lucid-backports Release [38.5kB]      
Ign http://archive.ubuntu.com lucid Release                                    
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Ign http://archive.ubuntu.com lucid-updates Release                     
Hit http://archive.ubuntu.com lucid/main Packages                       
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Ign http://archive.ubuntu.com lucid-security Release
Ign http://archive.ubuntu.com lucid-backports Release
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Packages
Hit http://archive.ubuntu.com lucid-backports/main Packages
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Sources
Hit http://archive.ubuntu.com lucid-backports/main Sources
Hit http://archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://archive.ubuntu.com lucid-backports/universe Sources
Fetched 1,185B in 1s (669B/s)
W: GPG error: http://archive.canonical.com hardy Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com hardy-backports Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```I then tried

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 54422A4B98AB5139

``` getting 

```
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
student@ubuntu:~$ gpg --export --armor 54422A4B98AB5139 | sudo apt-key add -
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC

``` I also tried changing servers, and checking source code etc... in the software sources

Any help would be appreciated. Thanks in advance

Is Hardy still supported? IIRC it was 8.04 LTS over three years old. Strange that you are using a mixture of Hardy & Lucid repos.

---

### Post by Frogs Hair on 2011-06-27
8.04 has support for server only .

---

### Post by jerrrys on 2011-06-27
you have a mix of Hardy and Lucid sources.  if your running Lucid, you need to comment out those hardy entries...

---

### Post by surfcast23 on 2011-06-29
> **jerrrys said:**
> you have a mix of Hardy and Lucid sources.  if your running Lucid, you need to comment out those hardy entries...


 Sorry I just got this reply I had no notification under subscriptions.

 How do I go about doing that? More precisely where can I find them

---

### Post by surfcast23 on 2011-06-29
okay  commented out the hardy entries tried 

```
sudo apt-get update 
```


and got


```
 student@ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com lucid Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:2 http://archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com lucid-security Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:4 http://archive.ubuntu.com lucid-backports Release.gpg [198B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Get:5 http://archive.ubuntu.com lucid Release [57.2kB]
Get:6 http://archive.ubuntu.com lucid-updates Release [44.7kB]
Get:7 http://archive.ubuntu.com lucid-security Release [44.7kB]
Get:8 http://archive.ubuntu.com lucid-backports Release [38.5kB]
Ign http://archive.ubuntu.com lucid Release
Ign http://archive.ubuntu.com lucid-updates Release
Ign http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main Packages
Ign http://archive.ubuntu.com lucid-backports Release
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Packages
Hit http://archive.ubuntu.com lucid-backports/main Packages
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Sources
Hit http://archive.ubuntu.com lucid-backports/main Sources
Hit http://archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://archive.ubuntu.com lucid-backports/universe Sources
Fetched 787B in 1s (423B/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
student@ubuntu:~$ 

```

---

### Post by jerrrys on 2011-06-29
#1  your system clock, is it showing the right date?

#2  [http://ubuntuforums.org/showthread.php?t=1484848](http://ubuntuforums.org/showthread.php?t=1484848)

more here, but basically the same thing, just different methods

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=m6&sa=Google+Search&lang=en#986](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=m6&sa=Google+Search&lang=en#986)

---

### Post by surfcast23 on 2011-06-30
> **jerrrys said:**
> #1  your system clock, is it showing the right date?

#2  [http://ubuntuforums.org/showthread.php?t=1484848](http://ubuntuforums.org/showthread.php?t=1484848)

more here, but basically the same thing, just different methods

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=m6&sa=Google+Search&lang=en#986](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Unknown+error+executing+gpgv&as_qdr=m6&sa=Google+Search&lang=en#986)


 Thank you the first link had the solution

---

