---
title: "OMG Compiz broke!"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by outleradam on 2010-08-10
The short of it is I uninstalled a critical package which uninstalled just about everything on my computer.  Then reinstalled everything while still in the same X session.  After reboot I had no window manager.  I was able to fix it by disabling compiz and going with the standard.  

So  compiz is broke.  How do I fix it?
```
adam@adam-desktop:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins but it is not going to be installed
          Depends: compiz-gnome but it is not going to be installed or
                   compiz-kde but it is not going to be installed
E: Broken packages
adam@adam-desktop:~$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.8.4-0ubuntu15) but 1:0.8.4-0ubuntu15.1 is to be installed
                Depends: compiz-plugins (= 1:0.8.4-0ubuntu15) but it is not going to be installed
E: Broken packages
adam@adam-desktop:~$ 


```I would really like to have compiz back and I don't understand this error.

---

### Post by sandyd on 2010-08-10
> **outleradam said:**
> The short of it is I uninstalled a critical package which uninstalled just about everything on my computer.  Then reinstalled everything while still in the same X session.  After reboot I had no window manager.  I was able to fix it by disabling compiz and going with the standard.  

So  compiz is broke.  How do I fix it?
```
adam@adam-desktop:~$ sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz: Depends: compiz-plugins but it is not going to be installed
          Depends: compiz-gnome but it is not going to be installed or
                   compiz-kde but it is not going to be installed
E: Broken packages
adam@adam-desktop:~$ 

```I would really like to have compiz back and I don't understand this error.
are you using gnome or kde as your main DE?
try 
```

sudo apt-get install 
compiz-gnome
```
and post the output

---

### Post by outleradam on 2010-08-10
no dice.. 

```
adam@adam-desktop:~$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.8.4-0ubuntu15) but 1:0.8.4-0ubuntu15.1 is to be installed
                Depends: compiz-plugins (= 1:0.8.4-0ubuntu15) but it is not going to be installed
E: Broken packages
adam@adam-desktop:~$ 

```

What can I do?

---

### Post by linux18 on 2010-08-10
```
 sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```

you have broken packages this will fix them, then you can install compiz

---

### Post by sandyd on 2010-08-10
> **outleradam said:**
> no dice.. 

```
adam@adam-desktop:~$ sudo apt-get install compiz-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.8.4-0ubuntu15) but 1:0.8.4-0ubuntu15.1 is to be installed
                Depends: compiz-plugins (= 1:0.8.4-0ubuntu15) but it is not going to be installed
E: Broken packages
adam@adam-desktop:~$ 

```What can I do?
Not your fault. Seems like the people mainting the repos are messing around. They must have done a bad upload or something cause the package status shows up as deleted. [https://launchpad.net/ubuntu/lucid/amd64/compiz-core/1:0.8.4-0ubuntu15.1](https://launchpad.net/ubuntu/lucid/amd64/compiz-core/1:0.8.4-0ubuntu15.1)

---

### Post by outleradam on 2010-08-10
Ok, i got it figured out.  It must have reinstalled a package in the wrong order.  I just uninstalled compiz then reinstalled compiz-gnome and it worked great!  

Basically, when I saw that I was uninstalling 900 packages, I copied them and then pasted them and then reinstalled all of those packages.   I guess Compiz was not supposed to be the main package.  Thank you very much for your insight.

---

