---
title: "Delete Open Java cache"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Mobjerkn on 2010-08-15
Hi,
I'm trying to login to a website that requires Java to authenticat. I get an error that are custom to this website so posting it here would not help. Called the company that I'm trying to login to and they told me to delete my Java cache. 

I've found the SUN/ORACLE way to delete this in Windows but are experiencing it hard to resolve this by my self, Google or Ubuntu forum.

I'm running Ubuntu all patched up and I can see that Ubuntu by default uses Open Java and that there is no support for SUN Java at Ubuntu at this time.
My question is:
1. Does Open Java have a cache storage
2. How do I delete Java cache from "Open Java"
3. Should I try to install Java from Sun instead?

All help would be appreciated.
In advance thank you very much....
Regards
Morten

---

### Post by lykeion on 2010-08-15
Hi
The Java browser plugin of OpenJDK is called icedtea
Cache location is ~/.icedteaplugin/cache

To clear it you could simply delete the cache folder like this:
```
rm -rf ~/.icedteaplugin/cache
```

But my guess is that clearing the cache won't help anyway, and I'd advice you to install Sun Java plugin instead.
Here's a quick step-by-step:

1. Enable partner repository (this is where you have Sun Java packages)
System > Administration > Software Sources
Select Other Software tab
Make sure partner repository is ticked
Click close

2. Remove OpenJDK and IcedTea plugin
System > Administration > Synaptic Package Manager
Enter "openjdk" in the quick search field
Mark package openjdk-6-jre for complete removal
(icedtea6-plugin will be selected as well)
Click apply

3. Install Sun Java JRE and plugin
While still in Synaptic
Enter "jre" in the quick search field
Mark packages sun-java6-jre and sun-java6-plugin for installation
Click apply

4. Make sure plugin is installed
Restart your browser 
Enter ```
about:plugins
``` in the address field
You should find "Java(TM) Plug-in 1.6.0_20" among the plugins

---

### Post by Mobjerkn on 2010-08-15
Hi,
Thank you for your reply. As you guessed removing the cache didn't help and I'm now trying to install SUN JRE. I've installed open jre but still there is a lot of open java references in the software repository (see attached screen shot).
I can't find the SUN Java when searching for JRE. I've attached the software source screenshot also. Not really sure what I'm doing wrong but something I'm not able to install SUN Java.
Regards
Morten

---

### Post by gandaran on 2010-08-15
> **Mobjerkn said:**
> Hi,
Thank you for your reply. As you guessed removing the cache didn't help and I'm now trying to install SUN JRE. I've installed open jre but still there is a lot of open java references in the software repository (see attached screen shot).
I can't find the SUN Java when searching for JRE. I've attached the software source screenshot also. Not really sure what I'm doing wrong but something I'm not able to install SUN Java.
Regards
Morten
you have to update the package list after enabling the canonical partner repository, click the reload button in synaptic or run in terminal 
```
sudo apt-get update
```
then you will find the sun-java in synaptic.
and remove all openjdk-java packages, you wont need them unless you have some application installed that depends on openjdk-java.

---

### Post by Mobjerkn on 2010-08-15
> **gandaran said:**
> you have to update the package list after enabling the canonical partner repository, click the reload button in synaptic or run in terminal 
```
sudo apt-get update
```
then you will find the sun-java in synaptic.
and remove all openjdk-java packages, you wont need them unless you have some application installed that depends on openjdk-java.

I've run the sudo apt-get update from my shell but still I can't get SUN Java up in the list.
Any ideas?
Regards
Morten

---

### Post by gandaran on 2010-08-15
> **Mobjerkn said:**
> I've run the sudo apt-get update from my shell but still I can't get SUN Java up in the list.
Any ideas?
Regards
Morten
type sun-java in search box, should be there if the repo is enabled!
or run the install command from terminal and post the errors here
```
sudo apt-get install sun-java6-plugin
```
question; which ubuntu version do you have? on some older versions the sun-java is in the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository so try adding the medibuntu repository.

---

