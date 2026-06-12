---
title: "Best way to install Windows XP w/Ubuntu"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by edco76 on 2010-11-02
So I switched to Ubuntu a few months ago and I'm digging it, starting to figure it out and all but there are still a few things that I cant do without windows. I was thinking of installing XP along side Ubuntu, what is the best way to do this? I have an XP CD.

---

### Post by alexan on 2010-11-02
[VMWare](https://help.ubuntu.com/community/VMware/Player)


If you need performance (gaming&video): [dual boot](https://help.ubuntu.com/community/WindowsDualBoot)



Priority to VMWare, since allow you to run Windows solely for the things/matter you really need+ no need of antivirus

---

### Post by edco76 on 2010-11-02
> **alexan said:**
> [VMWare](https://help.ubuntu.com/community/VMware/Player)


If you need performance (gaming&video): [dual boot](https://help.ubuntu.com/community/WindowsDualBoot)



Priority to VMWare, since allow you to run Windows solely for the things/matter you really need+ no need of antivirus

Really I just need to run Itunes, Blackberry Desktop, and my Ereader software. I think VMWare can handle that, looks kinda tricky to install tho. Hope I'm up to it.

---

### Post by Hippytaff on 2010-11-02
I installed vmware...if I can do it anyone can...really :-)

But you have to have a valid windows CD to be able to do that....(or one that works that is not that valid) otherwise dual boot :-)

---

### Post by edco76 on 2010-11-02
> Installing VMware Player on Ubuntu 9.04
Install required packages build-essential and linux-headers
sudo aptitude install build-essential linux-headers-`uname -r`
**Download the latest VMware player e.g. VMware-Player-2.5.2-**156735.i386.bundle (download the bundle version, not the rpm one) and run it as root using gksudo. You'll get a graphical installer that installs VMware player for you.
g**ksudo bash ./VMware-Player-2.5.2-156735.i386.bundle**
If nothing appears, you may need to make the file executable. You can do so with this command: chmod +x ./VMware-Player-2.5.1-126130.i386.bundle

After completion, VMware player is installed and should show up in the menu under Applications &#8594; System Tools &#8594; VMware Player.Do I need to
So do I need to download the player from that link? Or just enter the line in my terminal?

---

### Post by Hippytaff on 2010-11-02
I dowloaded in from the vmware site - vmware player is the free one...you have to register but it's free and does what I needed it to to [http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

---

### Post by toolmania1 on 2010-11-02
So far, this was actually really easy.  I also downloaded the VMWare Player from the vmware site.

[https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=default](https://www.vmware.com/tryvmware/p/activate.php?p=player&lp=default)

I saved this to my desktop.

Then, I opened a terminal.  Next, I cd to the desktop.  Then, I ran the sudo sh VMwa...... command.

The VMware player installed.  Then, I went under Applications -> Software Tools -> VMWare Player

I was told that some other things needed installed.  I clicked Install and they were installed.

---

### Post by alexan on 2010-11-03
Since both have free version (vmware and virtualbox) if you've free time/willing to explore, I do suggest you to try both options available.


Install XP on both system.. and check for the one who sound good to you :guitar: (intuitive, performance etc)

---

### Post by ironic.demise on 2010-11-03
Is it not worth trying Wine?
:if Itunes is for an IPod, check "GTKpod for Ubuntu"

---

