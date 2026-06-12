---
title: "GPG Error: Could Not Download All Repository Indexes"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by mcgreenw on 2010-01-17
Every time I run my update manager, I receive this in response: 

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

I have no idea what to do to remedy this situation! I was having a similar, if not almost exactly the same, message pop up in regards to a Google app, I assume Chrome since I just downloaded it, but that was apparently resolved in place of giving me this all the time. 

Any ideas? I appreciate it. I'm sorry for being such a n00b :(

---

### Post by fooman on 2010-01-17
open a terminal (applications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```then press enter....that should fix it. 

btw,  thats not so much an error as it is a warning telling you that the repository you have added may not be trusted.  by adding the GPG key,  you are in a sense, verifying that it is.  the updates will still work even with the error present...but i hates to see it myself.  

hope that helps.

---

### Post by ibuclaw on 2010-01-17
> **mcgreenw said:**
> Every time I run my update manager, I receive this in response: 

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

I have no idea what to do to remedy this situation! I was having a similar, if not almost exactly the same, message pop up in regards to a Google app, I assume Chrome since I just downloaded it, but that was apparently resolved in place of giving me this all the time. 

Any ideas? I appreciate it. I'm sorry for being such a n00b :(
Also, it kind of looks like the file on the google repository is malinformed.

If the above doesn't resolve it, the quick fix would be to remove dl.google.com from your list of sources and retry.

Regards
Iain

---

### Post by mcgreenw on 2010-01-18
> **tinivole said:**
> Also, it kind of looks like the file on the google repository is malinformed.

If the above doesn't resolve it, the quick fix would be to remove dl.google.com from your list of sources and retry.

Regards
Iain

Since the aforementioned suggestion didn't quite clear the problem and I think your solution may help, how exactly would I go about this? 
When I type "/etc/apt/sources.list" into my Terminal, it says access denied. I tried "sudo /etc/apt/sources.list" and it said it could not recognize the command. I see the list file in there but I cannot get to it to remove it. Ideas?

Thanks in advance.

---

### Post by mcgreenw on 2010-01-18
> **fooman said:**
> open a terminal (applications > accessories > terminal) and type or copy/paste the following into it:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0C5A2783
```then press enter....that should fix it. 

btw,  thats not so much an error as it is a warning telling you that the repository you have added may not be trusted.  by adding the GPG key,  you are in a sense, verifying that it is.  the updates will still work even with the error present...but i hates to see it myself.  

hope that helps.

I ran that and am still having issues with the dl.google list file. Argh, so frustrating! Thank you though:)

---

### Post by drs305 on 2010-01-18
> **mcgreenw said:**
> 
When I type "/etc/apt/sources.list" into my Terminal, it says access denied. I tried "sudo /etc/apt/sources.list" and it said it could not recognize the command. I see the list file in there but I cannot 


Since it is a file owned by "root", you must use admin to open it. If you are using a graphical app such as gedit, you use "gksu". You will be asked for your password:

```
gksu gedit /etc/apt/sources.list
```

Some repositories aren't listed in sources.list, but in a file in /etc/apt/sources.list.d  
If you don't find the listing in sources.list, you can try to remove it via GUI: Open Synaptic, Settings, Repositories > Third Party/Other Software and untick the entry for Google. Then press "Reload" on the main Synaptic menu.

---

### Post by mcgreenw on 2010-01-18
> **drs305 said:**
> Since it is a file owned by "root", you must use admin to open it. If you are using a graphical app such as gedit, you use "gksu". You will be asked for your password:

```
gksu gedit /etc/apt/sources.list
```

Some repositories aren't listed in sources.list, but in a file in /etc/apt/sources.list.d  
If you don't find the listing in sources.list, you can try to remove it via GUI: Open Synaptic, Settings, Repositories > Third Party/Other Software and untick the entry for Google. Then press "Reload" on the main Synaptic menu.

:KS HALLELUJAH! Thank you, thank you, thank you. All is well now!

---

### Post by Mr_Cynical on 2010-03-16
Are you using a Dell Mini? I get the same error (on my Mini 10v) and I suspect that the reason is the Mini's use of LPIA rather than i386 for packages. APT looks on the Google server for an LPIA repository, and of course there isn't one, hence the error. I'm looking to see if it's possible to make it use i386 (since the i386 Chrome in the original download deb works fine) to fix the problem without borking Chrome updates.

---

