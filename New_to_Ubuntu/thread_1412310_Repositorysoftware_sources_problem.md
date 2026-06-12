---
title: "Repository/software sources problem"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by Br11 on 2010-02-21
The synaptic manager/software sources/update manager is not working for me. I look everywhere and I couldn't find how to fix this.

If I search for Best Server it says:
[I]No suitable download server was found
Please check your Internet connection.[/I]

If I do some change and I want to Reload, it says:
[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
[/I]
and then for example:

[I]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
[/I]


I tried to install again Jabref, which wasn't working right, and I got an error, and now it's not even in the synaptic package manager list.

The update manager is also giving me the "Could not download all repository indexes" 


HELP!

(Thanks!)

---

### Post by garvinrick4 on 2010-02-21
[QUOTE=Br11;8858725]The synaptic manager/software sources/update manager is not working for me. I look everywhere and I couldn't find how to fix this.

If I search for Best Server it says:
[I]No suitable download server was found
Please check your Internet connection.[/I]

If I do some change and I want to Reload, it says:
[I]Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
[/I]
and then for example:


You do not have an internet connection.

If you have tried to get on to internet with a browser and are able to then only recourse is to
change your repositories in Software sources. Click tab in download from and choose other
Take your choice of the 328 other mirrors. But as of now you do not have an internet connection.

---

### Post by Br11 on 2010-02-21
Hi, I've fixed it!! It was the proxy setting, I just removed them, and everything worked. It seems that i can't do updates with the proxy on.

Thanks anyway for the fast answer.

---

### Post by Br11 on 2010-02-21
How do I put the SOLVED thing in the thread?

---

### Post by dmaxel on 2010-02-21
At the top of the page is a link called Thread Tools. A menu appears, with the last option saying, "Mark thread as SOLVED"

---

### Post by Br11 on 2010-02-21
Done it, thanks!

---

### Post by aadd on 2011-10-28
> **Br11 said:**
> Hi, I've fixed it!! It was the proxy setting, I just removed them, and everything worked. It seems that i can't do updates with the proxy on.

Thanks anyway for the fast answer.

I am having the same problem, but I do not really understand hoq to fix it. Could you be more concrete? Thanks and sorry for my ignorance, I am really new in the Linux environment..

---

### Post by Paqman on 2011-10-28
> **aadd said:**
> I am having the same problem, but I do not really understand hoq to fix it. Could you be more concrete? Thanks and sorry for my ignorance, I am really new in the Linux environment..

He means that if you're behind a proxy server, temporarily disable it in the Network Proxy tool and try to update again.

If you're behind a proxy, that probably means you're on somebody else's network, so any details you could provide would be handy.

---

### Post by aadd on 2011-10-28
> **Paqman said:**
> He means that if you're behind a proxy server, temporarily disable it in the Network Proxy tool and try to update again.

If you're behind a proxy, that probably means you're on somebody else's network, so any details you could provide would be handy.

Well, the funny thing is that firefox works, using the same configuration ("Direct connection to the internet"), which I suppose means that I'm not using any proxy server...

I've tried to connect with many repositories (both http and ftp), getting the same unsuccessfully result.

---

### Post by Paqman on 2011-10-28
> **aadd said:**
> Well, the funny thing is that firefox works, using the same configuration ("Direct connection to the internet"), which I suppose means that I'm not using any proxy server...

I've tried to connect with many repositories (both http and ftp), getting the same unsuccessfully result.

Odd. I don't suppose you've set up an APT proxy at all then? If you did it would be listed in the file /etc/apt/apt.conf, which is a file that I don't even think exists if you haven't set it up.

---

### Post by aadd on 2011-10-28
> **Paqman said:**
> Odd. I don't suppose you've set up an APT proxy at all then? If you did it would be listed in the file /etc/apt/apt.conf, which is a file that I don't even think exists if you haven't set it up.

Indeed, I did not set up it, and so there is no apt.conf in /etc/apt.

PS: for the case it's relevant, I'm using a XubuntOS VM running in VMWare Player, which is installed in Windows 7.

---

