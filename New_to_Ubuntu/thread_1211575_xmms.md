---
title: "xmms"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by icecover on 2009-07-12
Ok, first hello everyone :) I'm using Ubuntu 8.04 LTS
I'm very new in all this and i've been killing myself, literally, today trying to install xmms, and now when I've finally did it I want to erase it.
I've done some more reading and realised that xmms is a dead project and i've installed audicious instead and it is just like xmms. Or to me it is at least.
But when i've installed audicious I used "sudo apt-get install audicious" and ubuntu reads it like every other application.
On the other hand when i was installing xmms, I've manually downloaded it from the internet along with lots and lots of other libraries so i can finally install xmms. :(
And now I want to erase xmms, so normally i go with "sudo apt-get remove xmms" and i get: Package xmms is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
I've also tried using "sudo apt-get purge xmms" and i got the same message
I've also tried with "Add/Remove" and the "Synaptic Package Manager" and I still can't find it. But when i press "Alt+F2" and type "xmms" int the Run Application window xmms starts and i can play mp3s in it, exact same thing happens when i run it from the command line.
So I know it's a tough beginners luck, but help with this one please.

Thanks ...

---

### Post by wojox on 2009-07-12
Open synaptic and click search not quick search and it's listed in there.

Could also try:

```
sudo apt-get --purge remove xmms
```

---

### Post by neu2buntu on 2009-07-12
goto >system>administration>synaptic package manager and in the search icon (magnifying glass icon ) type: xmms... hopefully apt has picked up your installation ,and remove it from here.      the version i am using is called xmms2,but cant rem if 8.04 was using the same version or not

---

### Post by icecover on 2009-07-13
Well i tried the synaptic manager and it didn't listed xmms, i also tried with "sudo apt-get remove xmms" and i got this message :
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
---------------------
But ok i'll keep reading and if I don't get it done never mind. I figured I'll play with this installation 'till i learn ubuntu and than if i messd it up i'll install it again. :)

thanks anyway and if u have more suggestions please right... :)

---

### Post by cariboo on 2009-07-13
How did you install xmms? Was it from source? Was it a .deb?

---

### Post by neu2buntu on 2009-07-14
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```     this error is because you ran the apt-get remove command with the synaptic package manager still open,.. close synaptic and try to remove xmms this way....   

are you sure you clicked on the magnifying glass icon (then typed xmms) in synaptic and not just the box to the left of it?

---

### Post by neu2buntu on 2009-07-14
just reread your post and it sounds like you have installed from source (usually a tar.gz file) .... i have installed from source many times ,but never uninstalled...... i think you will have to "cd" to the extracted source file and run command ```
sudo make uninstall
```  hopefully someone will be along to verify this!

---

