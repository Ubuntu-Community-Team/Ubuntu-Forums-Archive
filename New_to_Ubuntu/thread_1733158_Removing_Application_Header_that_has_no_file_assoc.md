---
title: "Removing Application Header that has no file associated with it"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by RavenBrimstone on 2011-04-18
I am using Ubuntu 9.10 and have a small dilemma.  I had installed and removed Google Earth and for whatever reason, It is still listed under my applications.  If I got to applications > internet > google earth , is still listed. It won't open and I thought I had removed all the files. 
   
   My Question is, how do I remove such header so I can reinstall the actual working package and have only one listing? Any and all hope is greatly appreciated.


 Long Live Ubuntu

---

### Post by varunendra on 2011-04-19
You may have to reinstall Google Earth then select "Completely remove" this time in synaptic.

After that, try
```
sudo apt-get autoremove
```
in terminal. This will remove those modules that were installed to satisfy some dependencies but are no longer needed. Although you shouldn't need this after "completely removing" google earth.

---

### Post by RavenBrimstone on 2011-04-19
I have tried that in the past and I tried again to no avail. Thanx for your suggestion tho. I even tried sudo apt-get remove googleearth and my response is that it is not installed. 


When I click the afore mentioned application, It just shows the Google Earth start  up pic and is gone in about 1 second.

I tried moving it to the trash and i get a response of :

Operation not supported by backend.

Can we say aggravation??? !!! Followed by Frustration ?!?!:confused:

---

### Post by varunendra on 2011-04-19
How did you install Google earth and from where?

There is a package "bleachbit" in synaptic that says:
> It handles cleaning of Adobe Reader, Bash, Beagle, Epiphany, Firefox, Flash,
GIMP, **Google Earth**, Java, KDE, OpenOffice.org, Opera, RealPlayer, rpmbuild,
Second Life Viewer, VIM, XChat, and more.

I haven't tried this package or google earth myself, so may not be able to offer some specific help unless I try these myself. I'll try to if I know exactly how you installed (and then removed) it.

Is there some google or google-earth program folder sitting there in your home directory? You may have to enable viewing hidden folders to locate it.

---

