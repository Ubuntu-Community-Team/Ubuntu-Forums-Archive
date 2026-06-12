---
title: "install desktop on server"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by webmiester on 2008-12-30
Hi guys,

after downloading Ubuntu Linux Gutsy Gibbon and installing it, I found that it doesnt have a GUI because I downloaded a server version.  What commands should I do, or what else can I do to make this into the desktop version?

---

### Post by TomasJancik on 2008-12-30
just isntall the package ubuntu-desktop
"sudo aptitude install ubuntu-desktop"

---

### Post by Partyboi2 on 2008-12-30
in the terminal type
```
sudo apt-get install ubuntu-desktop
```

---

### Post by gvoima on 2008-12-30
For Gnome desktop:
```
sudo apt-get install ubuntu-desktop
```

And for KDE:
```
sudo apt-get install kubuntu-desktop
```

[EDIT]
Almost forgot. There is also a package for XFCE desktop environment:
xubuntu-desktop
[/EDIT]

---

### Post by jerome1232 on 2008-12-30
And if your going to be using this computer as a desktop might want to install the generic kernel.

```
sudo apt-get install linux-generic
```

---

### Post by webmiester on 2008-12-30
> **TomasJancik said:**
> just isntall the package ubuntu-desktop
"sudo aptitude install ubuntu-desktop"

Hi, it gave me the error that the repositories were not found.

I think that Im not connected to the internet yet, as it serches for the files on the CD.  On the desktop, it usually automatically connects to the LAN and internet, but in this server version, it probably doesnt.  How do I connect to my LAN internet so I can overcome this situation?

---

### Post by RomeReactor on 2008-12-30
Hi. Did you install Ubuntu offline--that is, not connected? If that's the case, the sources would be commented out. Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by OneMixDJ on 2008-12-30
> **jerome1232 said:**
> And if your going to be using this computer as a desktop might want to install the generic kernel.

```
sudo apt-get install linux-generic
```

Hi Jerome,

Stupid question from a newbie if you don't mind. :)

Does installing desktop and generic kernel take away the server capabilities?

I have a server (Hardy) with a dual NIC that I'm using for a number of simple tasks such as local DNS, SSH jump server connectivity, and also TACACS (hopefully) for my Cisco devices. 

Will I wipe out my efforts by implementing desktop?

Thanks!

---

### Post by levelup3 on 2008-12-30
I have the same problem and now it has been sorted!

---

### Post by webmiester on 2009-01-05
> **RomeReactor said:**
> Hi. Did you install Ubuntu offline--that is, not connected? If that's the case, the sources would be commented out. Please post your sources.list:
```
cat /etc/apt/sources.list
```

I downloaded the Gutsy Gibbon server CD using windows, burned it using windows then used that to reboot and install.  After installation, it appears that the gutsy gibbon server doesnt connect ot my LAN, or at least I dont know how to access it.

---

### Post by lazyart on 2009-01-05
I'd say to download the LiveCD and see how it works with your hardware.  And toss out Gutsy; it's two iterations old.  Go with Hardy (LTS) or Intrepid, which are both considered to be current.

---

### Post by RomeReactor on 2009-01-05
Have you tried pinging google or using w3m to see if you can load a website?

Also please post the output of:
```
ifconfig -a
```

EDIT: I agree with lazyart with regard to using a newer version.

---

