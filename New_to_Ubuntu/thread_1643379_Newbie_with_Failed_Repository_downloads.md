---
title: "Newbie with Failed Repository downloads"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by apvet on 2010-12-11
I  am a newbie convert to Ubuntu 10.10 and have been encountering a  problem with failed downloads. The  message I get is:

[I]W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ck/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg")  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (110: Connection timed out)
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...slation-en.bz2]("http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2")  Unable to connect to 192.168.0.1:8080:
, W:Failed to fetch [http://archive.canonical.com/ubuntu/...ck/Release.gpg]("http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg")  Could not connect to 192.168.0.1:8080 (192.168.0.1). - connect (110: Connection timed out)
[/I]
Forgive me if this is a stupid question, as I am a newcomer.Can anyone recommend what I would need to do to solve this?

---

### Post by karthick87 on 2010-12-11
Edit the apt.conf file,

```
sudo gedit /etc/apt/apt.conf
```Delete the folllowing line and update again.
> Acquire::http:: proxy "http://192.168.0.1:8080";```
sudo apt-get update
```

---

### Post by apvet on 2010-12-11
Thanks, I just performed the steps you listed. It still appears not  be working . This is the message I just received on the terminal window screen : 

:[I]W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.0.1:8080:

E: Some index files failed to download, they have been ignored, or old ones used instead.

[/I]Is there something else I could be doing wrong ?

---

### Post by karthick87 on 2010-12-11
Did you run update after deleting that line??

Post the complete output of,```


sudo apt-get update
```

---

### Post by apvet on 2010-12-11
Yes. The message in the terminal window is what I received after I attempted the update.

---

### Post by karthick87 on 2010-12-11
Are you behind a proxy server??

---

### Post by apvet on 2010-12-11
I do not believe so. How would I check to make sure? Is there away to detect a transparent proxy server?

---

### Post by karthick87 on 2010-12-11
What is the output of 

```
echo $http_proxy
``````
sudo apt-get update
```

---

### Post by apvet on 2010-12-12
Thanks for the all help!!!  Problem solved . I went back and I checked  the proxy configuration . The configuration information had not been set system-wide After setting it system wide I am now able to receive downloads..

---

### Post by karthick87 on 2010-12-12
If your problem has been solved.Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

