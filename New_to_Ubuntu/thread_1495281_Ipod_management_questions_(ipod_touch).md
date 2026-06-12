---
title: "Ipod management questions (ipod touch)"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Mezzoberanen on 2010-05-27
So, so far I've managed to get installed, all my drivers are working, and I've managed to get used to some of the terminal stuff. I'm enjoying my first Linux experience thoroughly! 

Here's the next step in my learning- ipod management.

I have Amarok (comes with base install) and while learning about the terminal I installed Banshee. Neither of them seem to have options for managing an ipod, though both supposedly can. 

Now- I've been researching and there seems to be an issue of ipod touches/iphones with the newest firmware not being able to work with open source media players. Amarok says it needs the pod/phone to be jailbroken (I have an 8gb touch with latest firmware).

Is there a Kubuntu/Ubuntu/Linux itunes alternative that I don't need to jailbreak my ipod to use? OR if there is no other option (and I realize this isn't really the best place to ask but while I'm here anyways) for an ipod (not iphone) are there many risks or issues to jailbreaking?

THANKS!!!

---

### Post by hryanjones on 2010-05-28
> **Mezzoberanen said:**
> 
Is there a Kubuntu/Ubuntu/Linux itunes alternative that I don't need to jailbreak my ipod to use? OR if there is no other option (and I realize this isn't really the best place to ask but while I'm here anyways) for an ipod (not iphone) are there many risks or issues to jailbreaking?


Yes.  I've successfully used my un jailbroken ipod touch with Ubuntu 10.04 (which natively supports all iphone/itouches) using Rhythmbox.  If you don't know what version of Ubuntu you're running you can go to System Menu > About Ubuntu, or from the command line:
lsb_release -a

You can read more about using iPhone/Touch here, [https://help.ubuntu.com/community/PortableDevices/iPhone#Ubuntu 10.04 Lucid Lynx: Support out of the box]("https://help.ubuntu.com/community/PortableDevices/iPhone#Ubuntu 10.04 Lucid Lynx: Support out of the box").

There's also another option called ifuse which I tried in 9.10, but had trouble with.

Good luck!

---

### Post by Mezzoberanen on 2010-05-30
> **hryanjones said:**
> Yes.  I've successfully used my un jailbroken ipod touch with Ubuntu 10.04 (which natively supports all iphone/itouches) using Rhythmbox.  If you don't know what version of Ubuntu you're running you can go to System Menu > About Ubuntu, or from the command line:
lsb_release -a

You can read more about using iPhone/Touch here, [https://help.ubuntu.com/community/PortableDevices/iPhone#Ubuntu 10.04 Lucid Lynx: Support out of the box]("https://help.ubuntu.com/community/PortableDevices/iPhone#Ubuntu%2010.04%20Lucid%20Lynx:%20Support%20out%20of%20the%20box").

There's also another option called ifuse which I tried in 9.10, but had trouble with.

Good luck!

The directions are helpful, but still can't get anywhere with the ipod.

In rhythmbox I can see it, if I go to import music, but can't interact with it. Otherwise my system doesn't acknowledge the ipod being there. I have installed the libraries that the info requires. Is it maybe because I'm doing this on kubuntu that it's harder?

---

### Post by Mezzoberanen on 2010-05-31
Got GTKpod to handle the management- thanks!

---

