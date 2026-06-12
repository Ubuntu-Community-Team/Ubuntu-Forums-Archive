---
title: "Unable to install programs for LUBUNTU"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by nick987654321 on 2010-10-23
[SIZE=2]I tried both Synaptic Package Manager and Terminal Command "sudo apt-get install" to install 'Anomos' and 'Lubuntu-Control-Center'.  But neither worked.

Can anyone walk me through how to install these on Lubuntu?
[/SIZE]

---

### Post by clhsharky on 2010-10-23
nick987654321

Neither are in Lubuntu repos, so apt-get wont install.
There is no Lubuntu-Control-Center.
I know nothing of Anomos.


Sharky

---

### Post by nick987654321 on 2010-10-23
On [www.lubuntu.net](www.lubuntu.net) there is a screencast for lubuntu control center.  So I'm assuming it should be installable.

As for Anomos, I can go to their website and download files for Linux, but I don't know how to install it.

---

### Post by mister_playboy on 2010-10-23
> **nick987654321 said:**
> As for Anomos, I can go to their website and download files for Linux, but I don't know how to install it.

First you need to have these installed: ```
sudo apt-get install openssl python-m2crypto
```

Then you start the GUI by moving to the download folder and running: ```
python anondownloadgui.py
```

---

### Post by nick987654321 on 2010-10-24
Thanks, I was able to get Anomos to work, but I still can't install lubuntu control center.

---

### Post by sandyd on 2010-10-24
> **nick987654321 said:**
> Thanks, I was able to get Anomos to work, but I still can't install lubuntu control center.

```

sudo apt-add-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-control-center

```

---

### Post by nick987654321 on 2010-10-24
> **sandyd said:**
> ```

sudo apt-add-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-control-center-package

```

I tried that and it says:   E: Unable to locate package lubuntu-control-center-package

---

### Post by Davsdu on 2010-10-24
Hi there.

Add " deb [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu) maverick " to the repositories. That should do it.

---

### Post by sandyd on 2010-10-24
> **nick987654321 said:**
> I tried that and it says:   E: Unable to locate package lubuntu-control-center-package

typo. fixed.

---

### Post by nick987654321 on 2010-10-24
The code below worked.  The developers may want to add this to their next release, or update the screencast on lubuntu.net

sudo apt-add-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install lubuntu-control-center

---

