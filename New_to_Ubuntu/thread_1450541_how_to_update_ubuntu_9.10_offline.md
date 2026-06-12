---
title: "how to update ubuntu 9.10 offline"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by blizta on 2010-04-09
hi everyone...

i've installed ubuntu 9.10 in my computer. and update is available in update manager. but the download size 250mb. (it's too large since my internet was volume based  :()

my friend have unlimited internet. can i download the update in his PC and copy it to my PC ? :)

---

### Post by Ampi on 2010-04-09
I don't think you can copy it, but I am not sure. Is it a desktop, if not you could take it to your friends and update it. 
But maybe someone on the forum knows how to save it on a usb or so and put it in your comp, good luck!

---

### Post by Johan! on 2010-04-09
You can try Keryx: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by mikewhatever on 2010-04-09
...

On the second thought, there is a much better solution. Open Synaptic package manager and click 'Mark All Upgrades', then, still in Synaptic, File->Generate Package Download Script. Now, close Synaptic, go to your friend's and run the script (./scrip_name), which will download all the required packages.

---

### Post by mac9416 on 2010-04-10
mikewhatever, 

Without Internet access, Synaptic will not know about all available updates and new applications. Generate Download Script will work fine for the first update, but then blizta be back where he started when he wants to update again or add a new application.

Keryx will not only know about the latest available packages, it will provide Synaptic with that information when you install the updates on the offline computer.

---

### Post by mikewhatever on 2010-04-10
Good point mac9416, but who said there was no internet access? The OP simply said the download size was too large and he/she wanted to do it at a friend's.

---

### Post by mac9416 on 2010-04-10
Oops, Mike, you're right. I read too fast.  :)

So, blitza, before using Generate Package Download Script, be sure to update package lists with Synaptic, Update Manager, apt-get update, etc.

Sorry for the misunderstanding!

---

### Post by blizta on 2010-04-12
thanks everyone.... :)

i try keryx project and it's so great.......

[COLOR=Black]**so, the Myth: *Linux is only usable with a persistent  Internet connection is WRONG!***[/COLOR] :lolflag:


but, can i generate package download script and download it with windows OS?

---

### Post by mac9416 on 2010-04-12
Well, you can't run the script on Windows without some modification. This page describes a couple of ways to make the script work with Windows: [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

---

