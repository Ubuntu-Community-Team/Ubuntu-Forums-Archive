---
title: "ubuntu tweak accident, now i have no disk space"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-06-25
Hello,
Today I was downloading a few applications via UbuntuTweak and I, errr, accidentally took up too miuch disk space. I cancelled the downloads so the applications didn't get installed. Yet, disk space still hasn't recovered.

Also, I can't uninstall them from the Software Center since they never installed.

Where are these packages, and how do I get rid of them so I can free up disk space? Thanks

---

### Post by josephmills on 2011-06-25
you might have to purge them ```
sudo apt-get remove --purge what ever program
```

---

### Post by Frogs Hair on 2011-06-25
You can also use the Ubuntu Tweak package cleaner to clean the cache after removing the programs.

---

### Post by nomko on 2011-06-25
> **skyzthelimit230 said:**
> Hello,
Today I was downloading a few applications via UbuntuTweak 

That's your biggest mistake! Ubuntu doesn't use Ubuntu tweak for downloading and installing software. To install/remove programs there's a very handy tool to be found under System > Administration and is it called Synaptic package-manager! Else there's a tool called Software Center and this tool can be found under Applications (at the bottom).

> 
and I, errr, accidentally took up too miuch disk space. I cancelled the downloads so the applications didn't get installed. Yet, disk space still hasn't recovered.

Also, I can't uninstall them from the Software Center since they never installed.Of course not! You stopped the download/installation of a program and as long it isn't installed completly you won't find it under Software Center or Synaptic.

> 
Where are these packages, and how do I get rid of them so I can free up disk space? ThanksTry this:
Open a terminal and type:
```
sudo apt-get autoclean
```and/or:
```
sudo apt-get autoremove
```and:
```
sudo apt-get purge {package name}
```And now my tip to you:
_REMOVE UBUNTU TWEAK!!!_
It's only a reason to get problems. And as you experience now, serious problems! Ubuntu Tweak is **NOT** the tool to install programs. It bypasses the security system of Ubuntu (Linux) and you really don't know where Ubuntu Tweak get's it's PPA from. In some cases you even end up with unstable packages which corrupt your system. Also Ubuntu tweak won't ask for authentication keys since Ubuntu Tweak bypasses this security system so the risk in this is adding software without any checking.

---

