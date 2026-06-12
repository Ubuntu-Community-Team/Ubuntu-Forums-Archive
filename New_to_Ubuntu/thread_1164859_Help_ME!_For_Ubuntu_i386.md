---
title: "Help ME! For Ubuntu i386"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Serjhonn on 2009-05-20
Hello!

I'm using ubuntu-9.04-desktop-i386 and i've a problem! I try to install install_flash_player_10_linux.deb for firefox browser. And package installer is warning me:

Error: Dependency is not satisfiable: libcurl3

So What is This...

thanks.

---

### Post by Bodsda on 2009-05-20
> **Serjhonn said:**
> Hello!

I'm using ubuntu-9.04-desktop-i386 and i've a problem! I try to install install_flash_player_10_linux.deb for firefox browser. And package installer is warning me:

Error: Dependency is not satisfiable: libcurl3

So What is This...

thanks.

Hi,

Dependencies are needed by the package that you are trying to install, in order for it to wok properly. You need to install libcurl3, in a terminal type/copy the following command
```
sudo apt-get install libcurl3
```

Hope this helps,

Bodsda

---

### Post by ainsworth_t on 2009-05-20
Try installing ubuntu-restricted-extras, it contains common codecs for multimedia and common plugins for browsing and installs any dependencies needed.

Can be installed from the command line:
```
sudo apt-get install ubuntu-restricted-extras
```

Or the Synaptic Package Manager (System >> Administration >> Synaptic Package Manager)

---

### Post by Serjhonn on 2009-05-20
Thank you very much. But i try this commands: 

sudo apt-get install libcurl3    and   sudo apt-get install ubuntu-restricted-extras

So;" E: Couldn't find package libcurl3 "    and    " E: Couldn't find package ubuntu-restricted-extras

Yes. I'm waiting for your help...

Thanks.

---

### Post by SunnyRabbiera on 2009-05-20
well even though I am not in the best of minds right now, I might be able to help.
Firstly make sure that no package managers are running.
Secondly what kind of connection do you have?
Thirdly there might be an issue of where you are downloading from, we might have to help you with that.

---

### Post by Serjhonn on 2009-05-20
> **SunnyRabbiera said:**
> well even though I am not in the best of minds right now, I might be able to help.
Firstly make sure that no package managers are running.
Secondly what kind of connection do you have?
Thirdly there might be an issue of where you are downloading from, we might have to help you with that.

Firstly Thanks You.

No package managers are not running.
My connection is Company connection (We've proxy server) And now is connected to internet.
I'm downloading from Istanbul, Turkey.

So can you help me?
I'm using ubuntu now...

---

### Post by waspbr on 2009-05-20
have you enabled your medibuntu repository? I am gonna assumed you haven't 

so,long story short...


go to your terminal and paste this, make sure that your synaptic or your add/remove are not open. Otherwise close them. 


```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update 
```

press enter and say yes to everything that may come up

then paste this 


```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```





then do the commmand

```
sudo apt-get install ubuntu-restricted-extras
```



while you are at it, it is always handy to have this package installed

```
sudo apt-get install build-essential
```

gl


[REF: [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")]

---

### Post by meganox on 2009-05-20
> **Serjhonn said:**
> Thank you very much. But i try this commands: 

sudo apt-get install libcurl3    and   sudo apt-get install ubuntu-restricted-extras

So;" E: Couldn't find package libcurl3 "    and    " E: Couldn't find package ubuntu-restricted-extras

Yes. I'm waiting for your help...

Thanks.


You need to enable the multiverse repository.  To do this, go to System -> Administration -> Software Sources.  On the first tab "Ubuntu Software" make sure the box "Software restricted by copyright or legal issues (multiverse)" is checked.

Now you can install ubuntu-restricted-extras using the command above.  You don't need to install libcurl3, that will be installed anyway with ubuntu-restricted-extras.

---

### Post by chemicalfan on 2009-05-20
Have you tried looking for it in Synaptic?

---

### Post by Serjhonn on 2009-05-20
Thanks For Your Help. I guess my problem is Proxy Authentication firewall protocol. I'll try to connect direct adsl internet... I'll be right back...

Thanks!

---

### Post by theozzlives on 2009-05-20
Go to Applications > Add/Remove, make sure "All Available Applications" is slelected. In the "search" box simply type the word "restricted" (without the quotes) and ubuntu-restricted-extras should come up. Check the box and click Apply. Cool huh?

---

### Post by 3rdalbum on 2009-05-20
Go to System > Administration > Software Sources and make sure that "main", "universe", "restricted" and "multiverse" repositories are ticked. If some of them aren't, then they need to be ticked, and then when you close the program you'll be asked to reload the package list; click Reload and then you won't have this problem ever again.

---

