---
title: "Unable to install NVIDIA driver"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by MarvinBasa on 2009-10-17
Guys,

I just migrated from 8.10 to 9.4 and my NVIDIA driver did not installed. Tried to search this forum and advised to install "envy" but encountered error using synaptic. 

"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"

Please need your help asap.

Thanks,
Mrvn

---

### Post by falconindy on 2009-10-17
That just means you didn't run synaptic with sudo. You need root permission to install software.

Envy is outdated and doesn't need to be used. Check under 'System -> Administration -> Hardware Drivers' to see if there's an nvidia driver available for you.

---

### Post by pedro3005 on 2009-10-17
System > Administration > Hardware Drivers.

---

### Post by synapsys on 2009-10-17
Choose to activate the recommended driver.

---

### Post by MarvinBasa on 2009-10-18
Tried the above advice and encountered error.

"Sorry, the Jockey backend crashed. Please file a bug at:

  ubuntu-bug jockey-common

Trying to recover by restarting backend."

Please help

---

### Post by zaksworld on 2009-10-18
If you couldn't find envy in synaptic, then maybe your sources somehow got deleted.

Go to:

System > Administration > Software Sources

then check the appropriate sources.  I usually check the first four under the "ubuntu software" tab, and everything under the "third-party software" tab.

Close this, then open up synaptic.

System > Administration > Synaptic Package Manager

And check to see if it is there now.  If not, then download then you should try installing Envyng

You can download this on the Envy official site.  Here are instructions to install EnvyNG.
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

If you still can't get envy to work, then e-mail me at [email]zaksworld@rocketmail.com[/email] and I'll make you a deb file, so you'll just have to double click on it, and envyng will install.

Hope I can help! ;)

---

### Post by MarvinBasa on 2009-10-18
It's still unsuccessful. :confused:

---

### Post by rajeev1204 on 2009-10-18
> **MarvinBasa said:**
> Guys,
 

"E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory"


THis error usually means that some other instance of a package manager is active already.Close all such running instances then,

Just type this in a terminal :
```
sudo apt-get install nvidia-glx-180
```

---

### Post by zaksworld on 2009-10-18
Marvn i have sent you an e-mail with the deb file.

I used this code to make it.

[code]
apt-get source envyng-qt
cd envyng-qt
apt-get build-dep envyng-qt
[code]

and there you have it!

So since I have the deb file if anyone else wants it just e-mail me at zaksworld@rocketmail.com.

I checked this deb file, and it works, so if this deb file doesn't work for you then it means your synaptic can't get the requirements for this program to work.  If this is the case, then please report your error.  Thanks!

---

### Post by rajeev1204 on 2009-10-18
> **zaksworld said:**
> Marvn i have sent you an e-mail with the deb file.

I used this code to make it.

[code]
apt-get source envyng-qt
cd envyng-qt
apt-get build-dep envyng-qt
[code]

and there you have it!

So since I have the deb file if anyone else wants it just e-mail me at zaksworld@rocketmail.com.

I checked this deb file, and it works, so if this deb file doesn't work for you then it means your synaptic can't get the requirements for this program to work.  If this is the case, then please report your error.  Thanks!

Thats not recommended for getting nvidia drivers to work.What about the dependencies? 

Its always recommended to install from synaptic or the debs will also be available from packages.ubuntu.com but that will require you to download all the dependent debs too.

Envyng-qt is also in synaptic so why would you make your own deb??

---

### Post by sandy8925 on 2009-10-18
Better still download the driver from the nvidia website. Works very well. It's what I've been doing for several months now.

---

### Post by MarvinBasa on 2009-10-18
Rajeev,

Thanks for the advice and it works.

Zak,

Thanks for your help. I did what rajeev said and it works.

---

### Post by zaksworld on 2009-10-18
> **rajeev1204 said:**
> 
Envyng-qt is also in synaptic so why would you make your own deb??
 
Marvin said that he couldn't install envy with synaptic, so that's the whole reason why I made him a deb file.  That way he could install envy. ;)

Sorry i meant dependencies, not required files.  But if the dependencies aren't met, and his synaptic can't get them, then he probably won't be able to install envyng.  That's all I was saying...:popcorn:


sure thing about the help!  If you ever need help again just e-mail away!

---

