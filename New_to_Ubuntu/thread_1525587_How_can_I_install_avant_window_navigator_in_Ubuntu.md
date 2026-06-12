---
title: "How can I install avant window navigator in Ubuntu 10.04 LTS"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by nakama1925 on 2010-07-06
Hi I'm a Linux newbie and i cant find way to install Avant Window Navigator on my desktop.
I am using a fresh install Ubuntu 10.04 LTS.

Please help.

---

### Post by Zzl1xndd on 2010-07-06
Access Applications > Ubuntu Software Centre > then search for Avant. 

I believe it should be the first option listed. Select it and click install.

---

### Post by bigsmitty64 on 2010-07-06
Synaptic Package manager has the newer version. 

System>Administration>Synaptic Package Manager

type in "avant" it will bring up a list. Choose "avant-window-navigator-trunk" click the check box and  "mark for installation", then click the "apply" button. this will install it.

Then it will be in Applications>Accessories>AWN

---

### Post by nakama1925 on 2010-07-07
> **bigsmitty64 said:**
> Synaptic Package manager has the newer version. 

System>Administration>Synaptic Package Manager

type in "avant" it will bring up a list. Choose "avant-window-navigator-trunk" click the check box and  "mark for installation", then click the "apply" button. this will install it.

Then it will be in Applications>Accessories>AWN

Thanks for the reply.

Using your instructions it give me this error 

"Could not mark all packages for installation or upgrade.
 The following packages have unresolvable dependencies. Make sure that all required repositories are added and enable in the preferences. "

---

### Post by NightwishFan on 2010-07-07
Go to System -> Administration -> Software Sources. Ensure it looks like this (the four first boxes are checked).

Close the Software Sources dialog box, it will ask you to reload. Do so.

Then click here to install awn, or do as the above posters suggested.
[_Install Avant Window Navigator_]("apt://avant-window-navigator")

---

### Post by nakama1925 on 2010-07-07
> **tweakedenigma said:**
> Access Applications > Ubuntu Software Centre > then search for Avant. 

I believe it should be the first option listed. Select it and click install.

I also try using this instruction but it tells

"Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time."

---

### Post by nakama1925 on 2010-07-08
> **tweakedenigma said:**
> Access Applications > Ubuntu Software Centre > then search for Avant. 

I believe it should be the first option listed. Select it and click install.

Hi Guys,

I got it all working now!

There must be something wrong with my Ubuntu installation . 
I try to reinstall it again and then this instruction work.

I really appreciate your help!

Thank you very much!

:popcorn::P

---

### Post by Joeasaurus on 2010-07-08
Sounds like you just needed to update some software, did it tell you some updates before the awn installation worked?

---

### Post by nakama1925 on 2010-07-09
I don't really know what actually happen.
I just reinstall the whole Operating System.
Then i run this command "sudo apt-get update".
Then i search and install Avant in Ubuntu Software Center and it worked.

---

