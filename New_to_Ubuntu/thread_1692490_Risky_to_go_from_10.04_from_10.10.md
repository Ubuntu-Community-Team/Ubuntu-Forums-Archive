---
title: "Risky to go from 10.04 from 10.10?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Cerapter on 2011-02-21
I'm very happy with the way things work on my Ubuntu 10.04 right now, but I'm tempted to upgrade to 10.10 so I can install the new Amarok. I'm very afraid of things not working as perfectly anymore if I do so. Do I have a reason to fear?

---

### Post by ankspo71 on 2011-02-21
Hi,
I think the safest thing to do first is download a copy of the Ubuntu (or Kubuntu) 10.10 Live CD and burn it to disk and try out Amarok. This way you can try out a newer version of Amarok without harming your current setup, and you will already have a copy of Ubuntu/Kubuntu 10.10 for when you need it.

Also, to install the latest version of Amarok (2.4) on Ubuntu 10.10, the people using Ubuntu 10.10 would have to enable the Kubuntu Backports PPA repository. [https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports). Amarok 2.4 will be included in the next release of Ubuntu, version 11.04.

However, since the latest Amarok isn't yet available for Ubuntu 10.04, Ubuntu 10.04 users can upgrade to Amarok version 2.3.2 which is the same version of Amarok that Ubuntu 10.10 uses by default, by enabling the same repository as above.

Hope this helps.
PS: Make sure you make backups of your important data before attempting any upgrades. Usually things go well during upgrades, but sometimes they don't.

---

### Post by sviola on 2011-02-21
You don't have any reason to fear, since version 10.10 is a stable release. Just be sure to follow the [directions for upgrading]("https://help.ubuntu.com/community/MaverickUpgrades"), and you'll be fine. (Of course, it's always a good idea to have a backup just in case something goes wrong.:))

Edit:
I just read ankspo71's post, and I'm not sure if I understood the question right... I hope between the two of us, we answered your question... :)

---

### Post by tea for one on 2011-02-21
> **Cerapter said:**
> I'm very happy with the way things work on my Ubuntu 10.04 right now, but I'm tempted to upgrade to 10.10 so I can install the new Amarok. I'm very afraid of things not working as perfectly anymore if I do so. Do I have a reason to fear?

Good evening

Download the 10.10 iso
Create a live USB device with persistence via System > Administration > Startup Disk Creator
Add Amarok via Software Centre

Experiment with the new OS and see if it is suitable for your hardware.

---

### Post by Dutch70 on 2011-02-21
> **Cerapter said:**
> **I'm very happy with the way things work on my Ubuntu 10.04 right now**, but I'm tempted to upgrade to 10.10 so I can install the new Amarok. I'm very afraid of things not working as perfectly anymore if I do so. Do I have a reason to fear?

I would never discourage anyone from the joy/risks of upgrading or any other changes you want to make to your system. However, when they start off with "I'm very happy with my system" I find it hard not to at least tell you some things to consider before you do.

1. 10.04 is an LTS so it is more stable.
2. 10.10 is not that much different from 10.04.
3. 11.04 is coming out in 2 months. (scheduled release is April 28th)
4  ankspo71 & tea for one gave you good alternate solutions.
5. If it aint broke, don't fix it. Hahaa, yeah right.
 Also, if you've got a /home partition, you really don't have much to lose by doing it. If you don't, whenever you do the upgrade/install may be a good time to back up your documents & create one.

Good luck

---

### Post by maqtanim on 2011-02-21
I personally think, if you donot have any problems with 10.04 you do not need to install 10.10. I am using 10.04 and did not upgrade to 10.10. In fact I do not have any intension to upgrade any versions other than the LTS. I am a LTS-person! :)

---

### Post by Cerapter on 2011-02-22
Thanks for your replies! For now, I'm going to put 10.10 on a memory stick and try it out like that.

---

### Post by Chronon on 2011-02-22
> **Dutch70 said:**
> 
1. 10.04 is an LTS so it is more stable.


That's not automatically true.  LTS is supported for longer, so there's more time for bugs to be found and squashed.  However, at the time of release it's not necessarily any different from any other release.

---

### Post by rburkartjo on 2011-02-25
cer also if you have your home folder mounted on a separate partition you could always go back to 10.04 your preferences would be saved. you just might have to reinstall a few programs.

---

### Post by Dutch70 on 2011-02-26
> **rburkartjo said:**
> cer also if you have your home folder mounted on a separate partition you could always go back to 10.04 your preferences would be saved. you just might have to reinstall a few programs.

+1 This is the way to go.

---

