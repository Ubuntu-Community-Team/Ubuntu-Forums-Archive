---
title: "upgrading grub2  1.97beta4 to grub2 1.98"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-04-18
I have seen there is a release of the 1.98 version of Grub2.

It appears to have been released as a tar ball here:
[http://grub.enbug.org/FrontPage](http://grub.enbug.org/FrontPage)

As I understand it, you can upgrade the legacy grub using an apt-get command in terminal.

What I haven't seen are any posts regarding upgrading to the latest version of Grub 2.

In my case, going from the 1.97beta4 version that came with Ubuntu 9.10 to the 1.98 version that has been released.

Now, I have downloaded it and read the install and Read Me files, but they were not very helpful.

Does anyone have the procedure for doing this properly?

Thanks in advance for the help!  :)

---

### Post by QIII on 2010-04-18
If I were you, I would not undertake something like that unless you are pretty sure what you are doing.  There is a greater likelihood that you will end up unable to use your system than that it will work.

My advice, if you are a novice, is to leave well enough alone for now.  If you upgrade or fresh install Lucid when the final release comes out, it will either come with 1.98 or it will be upgraded when you issue apt-get upgrade.

---

### Post by GMHilltop on 2010-04-19
I am not too worried about messing it up, as I am working on a new system, and I have imaged the clean install of the 3 operating systems.

I am quite familiar with manipulating the MBR with Ranish 2.43  -- Ubuntu is just new to me and I want to learn by playing with it.

I am not to worried about losing data as there is really nothing to lose.

I have just found the Synaptic Package Manager and it said I could upgrade the 1.97 version of Grub 2 so I did --- not much changed.  (I thought that it might upgrade it to the 1.98 version)

Anyhow, if there is a simple way to upgrade to 1.98 (or a difficult way with commands) I don't mind trying.  As long as there isn't too much typing on your part.  Or a link to something that I can read would be good too.

The 'Install' file that came in the 1.98 tar ball didn't help much (because I didn't quite get some of what they were saying)  I thought it might have a more step by step -type "THIS" and hit "Enter" kind of guidance.  Oh well.

Anything you might be able to contribute would be handy.

Like I said, I am not too worried about losing anything, because the system is basically clean.

Thanks again.  :)

---

### Post by wilee-nilee on 2010-04-19
Lucid updated synaptic screenshot.
[ATTACH]153729[/ATTACH]

I would say since you want to mess around and you have stuff backed up go for Lucid I have been using it since the first available download, some hiccups nothing major.

---

### Post by warfacegod on 2010-04-19
Download Lucid and create a CD or USB of it. Then read part .13 here: [http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics")

---

### Post by drs305 on 2010-04-19
As *warfacegod* suggests, you can install Grub 2 1.98 by using a Lucid CD. When you use the method described by the link he provided (Section 13), it will install the Grub version found on the CD, which is 1.98.

---

### Post by GMHilltop on 2010-04-19
Sounds Good - Thanks

---

### Post by ratcheer on 2010-04-19
Or, you can just wait until Lucid is released in 10 days and the upgrade will upgrade your grub2.

Tim

---

### Post by GMHilltop on 2010-04-21
Used the live CD 10.04 LTS beta2.  Worked like a charm

---

