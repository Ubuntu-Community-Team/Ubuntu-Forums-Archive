---
title: "Problem installing wicd"
date: 2008-06-16
forum: Networking &amp; Wireless
---

### Post by dunbrokin on 2008-06-16
While following the instructions for installing wicd on Kubuntu via Synaptic (see following)


" When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you."

I get the following error message.....


"Failed to fetch cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

I am at a loss to know what is going on....how do I install wicd and get rid of the error. Thanks in advance.

---

### Post by Ayuthia on 2008-06-16
> **dunbrokin said:**
> While following the instructions for installing wicd on Kubuntu via Synaptic (see following)


" When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you."

I get the following error message.....


"Failed to fetch cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

I am at a loss to know what is going on....how do I install wicd and get rid of the error. Thanks in advance.

It is looking for the live CD that was used for the install.  There should be a checkbox there for the CD that is checked (in the third-party software--I am using Adept in Kubuntu so it might be in a different place under the Repositories).  Just unclick it and then run the update again.  If you are using Hardy, please make sure that it says hardy instead of gutsy..

---

### Post by dunbrokin on 2008-06-16
> **Ayuthia said:**
> It is looking for the live CD that was used for the install.  There should be a checkbox there for the CD that is checked (in the third-party software--I am using Adept in Kubuntu so it might be in a different place under the Repositories).  Just unclick it and then run the update again.  If you are using Hardy, please make sure that it says hardy instead of gutsy..

OK, that worked....but now I dont have a third party settings option anymore....only ubuntu and cononical now show up...no third party option!

---

### Post by Ayuthia on 2008-06-16
> **dunbrokin said:**
> OK, that worked....but now I dont have a third party settings option anymore....only ubuntu and cononical now show up...no third party option!
You can try editing your sources.list file and remove the comment for your cdrom:
```
kdesu kate /etc/apt/sources.list
```
Look for:
```
#deb cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```and remove the # at the beginning of the line.  Save the file and see if you can see the third party stuff again.

---

### Post by dunbrokin on 2008-06-16
> **Ayuthia said:**
> You can try editing your sources.list file and remove the comment for your cdrom:
```
kdesu kate /etc/apt/sources.list
```
Look for:
```
#deb cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```and remove the # at the beginning of the line.  Save the file and see if you can see the third party stuff again.

This is weird...in the terminal I can use Kate to access the files but (obviously cannot edit/save) not use sudo kate or kdesu kate....!!???

---

### Post by Ayuthia on 2008-06-16
> **dunbrokin said:**
> This is weird...in the terminal I can use Kate to access the files but (obviously cannot edit/save) not use sudo kate or kdesu kate....!!???

What is the error message that you are getting?

---

### Post by dunbrokin on 2008-06-16
> **Ayuthia said:**
> What is the error message that you are getting?

It does not recognise Kate as a command.

---

### Post by Ayuthia on 2008-06-16
> **dunbrokin said:**
> It does not recognise Kate as a command.

Did you use an upper-case K or the lower-case k?  Linux is case-sensitive and will not find Kate, but should find kate.

---

### Post by dunbrokin on 2008-06-16
> **Ayuthia said:**
> Did you use an upper-case K or the lower-case k?  Linux is case-sensitive and will not find Kate, but should find kate.

Ah...correct....

However, I now have managed to connect to the internet using Wireless Assistant.....I can get Kopete to work but not Firefox....how weird is that?

Firefox says that it is in offline mode...

---

### Post by Ayuthia on 2008-06-16
> **dunbrokin said:**
> Ah...correct....

However, I now have managed to connect to the internet using Wireless Assistant.....I can get Kopete to work but not Firefox....how weird is that?

Firefox says that it is in offline mode...
If you click on File->Work Offline, does it get you back online?  Also are you able to connect via Konqueror?

You might also check and see if you can ping anything (ping -c1 [www.google.com](www.google.com)).  If you cannot ping anything, you might try restarting your router and computer and see if everything clears up. 

I recall running into that also.  I was able to use kopete without any problems but was unable to surf the web.  After resetting everything, I found out that the pattern was with kopete.  As soon as I started using kopete, I could not go anywhere on the web.  I ended up not using kopete for the rest of the day and then the next day, all was fine.  Sorry, not a great answer and does not really provide a solution.  I just can relate to your pain.

---

### Post by dunbrokin on 2008-06-16
> **Ayuthia said:**
> If you click on File->Work Offline, does it get you back online?  Also are you able to connect via Konqueror?

You might also check and see if you can ping anything (ping -c1 [www.google.com](www.google.com)).  If you cannot ping anything, you might try restarting your router and computer and see if everything clears up. 

I recall running into that also.  I was able to use kopete without any problems but was unable to surf the web.  After resetting everything, I found out that the pattern was with kopete.  As soon as I started using kopete, I could not go anywhere on the web.  I ended up not using kopete for the rest of the day and then the next day, all was fine.  Sorry, not a great answer and does not really provide a solution.  I just can relate to your pain.

Thanks...it was a simple as File>Work Offline - darn!

---

### Post by dunbrokin on 2008-06-23
> **Ayuthia said:**
> Did you use an upper-case K or the lower-case k?  Linux is case-sensitive and will not find Kate, but should find kate.

Same problem....cannot access sudo kate it says

sudo: kate: command not found

However if I enter kate into the terminal without the sudo or kdesu it works!!

---

### Post by dunbrokin on 2008-06-23
> **Ayuthia said:**
> You can try editing your sources.list file and remove the comment for your cdrom:
```
kdesu kate /etc/apt/sources.list
```
Look for:
```
#deb cdrom:[Kubuntu-KDE4 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
```and remove the # at the beginning of the line.  Save the file and see if you can see the third party stuff again.

Nope (btw you cannot go kdesu kate - you have to specify the actual location of kate)....that did not work.

---

