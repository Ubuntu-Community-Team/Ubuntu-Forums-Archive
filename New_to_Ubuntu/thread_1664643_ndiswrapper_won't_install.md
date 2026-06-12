---
title: "ndiswrapper won't install"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by thewasteland on 2011-01-11
I made a thread earlier about trying to find the drivers for my wireless card and eventually, after hours of failing to find Ubuntu drivers, somebody suggested that I install the Windows drivers with ndiswrapper. I've now downloaded the Windows drivers, but ndiswrapper won't install. When I try it with Terminal, I get:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it."
And trying it with the Software Centre just doesn't work; I press install and nothing happens. Can anyone help me please?

To give some background on the Google Chrome thing, last night I tried to install Google Chrome and it froze on like 90% in the Software Centre so I cancelled it. Dunno what that was all about.

I'm running Ubuntu 10.10 (Maverick Meerkat) by the way, only installed it on Sunday and this is the first time I've used Ubuntu.

Thanks.

---

### Post by sriramrangan on 2011-01-11
What are you wireless card specs? Also, does this happen when you install only this package or all packages?

---

### Post by sriramrangan on 2011-01-11
Also, just try "sudo apt-get install chromium-browser" on your terminal. That will install Google Chrome and may solve the ndiswrapper problem

---

### Post by thewasteland on 2011-01-11
> **sriramrangan said:**
> What are you wireless card specs? Also, does this happen when you install only this package or all packages?

Uh, I have no idea. Nobody in the thread I started yesterday could find them for me and I got the laptop as a gift so I don't have the details. But I don't think it matters anymore seeing as thanks to this post I've realised that this is the deal with all packages. Including Chrome.

---

### Post by Hippytaff on 2011-01-11
Try
```

iwconfig

```
and
```

lspci -vv

```
for specs

---

### Post by sriramrangan on 2011-01-11
Yes, you can do what he said

---

### Post by thewasteland on 2011-01-11
> **Hippytaff said:**
> Try
```

iwconfig

```and
```

lspci -vv

```for specs

OK, however, this isn't the problem anymore. Any installation I try with Software Centre does nothing and any installation I try with Terminal gives that same message from the OP. Until I sort out this problem I can't install anything. Can anyone help me?

---

### Post by sriramrangan on 2011-01-11
Try this:
```

sudo apt-get update

```

If that doesn't work try:
```

sudo apt-get install google-chrome-stable

```
Also can you give me the output of those commands?

---

### Post by Hippytaff on 2011-01-11
Probably worth starting a new thread :-)

---

### Post by thewasteland on 2011-01-11
> **sriramrangan said:**
> Try this:
```

sudo apt-get update

```If that doesn't work try:
```

sudo apt-get install google-chrome-stable

```Also can you give me the output of those commands?

I did the update, and it did the whole thing:
"Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]           
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release.gpg                
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_ZA
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_ZA
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release.gpg [198B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [27.2kB]  
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources     
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick Release                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:5 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates Release [31.4kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [19.0kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [8,221B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [649B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [61.9kB]
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main Sources                       
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick/multiverse i386 Packages
Get:11 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main Sources [71.3kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [31.4kB]
Get:14 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted Sources [14B]  
Get:15 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe Sources [23.7kB] 
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,655B]
Get:17 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse Sources [1,068B]
Get:18 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/main i386 Packages [195kB]
Get:19 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/restricted i386 Packages [14B]
Get:20 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/universe i386 Packages [77.2kB]
Get:21 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2,522B]
Fetched 553kB in 11s (50.2kB/s)                                                
Reading package lists... Done"

However, installing stuff still doesn't work. Even trying to install Google Chrome like that gives the same message as in OP through the Terminal.

> **Hippytaff said:**
> Probably worth starting a new thread :smile:

I will soon, just giving this one some time to die.

---

### Post by wep940 on 2011-01-12
Do you REQUIRE google chrome, or are you trying it due to the message when you tried to install ndiswrapper?
 
Do yourself a favor and install ndiswrapper and it's GUI'd front-end ndisgtk right from the LiveCD.  After you've booted Linux, insert the LiveCD and let it spin up.  If a message comes up about a software source just cancel it.  Now, "Places", navigate to the following folder on the CD:
 
/pool/main/n
 
In that folder you'll find 2 other folders - ndisgtk and ndiswrapper.  Go to the ndiswrapper folder first and click on the ndiswrapper common file to install it.  Then click on the ndiswrapper utilities to install it.  Now go back to the ndisgtk folder and click on the ndisgtk file to install it.
 
Now all you need to do is go to System/Administration/Windows Wireless Drivers - this starts up ndisgtk.  Click for new device/driver, then point it to your Windows driver .inf file.  Remember, they can only be Windows XP drivers and they must match the OS type - 32 bit or 64 bit.

---

### Post by sriramrangan on 2011-01-12
This most probably will solve the problem:
```
dpkg --remove --force-remove-reinstreq google-chrome-stable
```

---

