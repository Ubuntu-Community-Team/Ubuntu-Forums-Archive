---
title: "Different software packages for 32 and 64 bit versions?"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2011-04-27
Hi,

I'm very new to Ubuntu and just re-installed the 64 bit 10.10 over my old 32 bit 10.10.

In my 32 bit 10.10, I need to run:

sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer

To get my wireless card working (I have a b43 card).

Now, when I run this command in the 64 bit version, I receive: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-lpphy-installer

I also notice in System --> Administration --> Additional Drivers that only the Broadcom STA driver is listed.
In my old 32 bit version, it list the b43 driver and the broadcom STA driver.

Is this correct? Are different software packages (like the firmware-b43-lpphy-installer) only available in 32 bit? And if so, is there a way to get my wireless card working under the 64 bit installation?

Thanks in advance,
Chris

---

### Post by bodhi.zazen on 2011-04-27
The packages have the same names.

Try ```
sudo apt-get update
```

Then try installing again.

---

### Post by pcvchriskmg on 2011-04-27
> **bodhi.zazen said:**
> The packages have the same names.

Try ```
sudo apt-get update
```Then try installing again.

Unfortunately, I got the same result.

When I ran the update command, it had a lot of "hits" but it did end with:

W: Failed to fetch [http://mg.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz](http://mg.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-amd64/Packages.gz)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

Could not locate it via the Synaptic Package Manager either.

Chris

---

### Post by bodhi.zazen on 2011-04-27
It is in the repos, so I assume you are having an networking issue or a typo (misspelling) in your command?

[http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)

---

### Post by frank604 on 2011-04-27
Maybe the mirror you are using to update with is acting funky. 

Run synaptics package manager, click settings, click repositories, In Download From bar, choose other, then select best server on the right, it will ping all mirrors at this point and choose the fastest ping, select OK, and then get back to the synaptic package manger and click reload (or sudo apt-get update in terminal) and either use synaptic to search and download your driver or (sudo apt-get install blah blah).

IF the mirror chosen doesn't work, try manually selecting and trying each mirror in your country.  Hope this helps.

---

### Post by pcvchriskmg on 2011-04-28
> **bodhi.zazen said:**
> It is in the repos, so I assume you are having an networking issue or a typo (misspelling) in your command?

[http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)

Could I just download these files from this website and unpack/install them on my computer? What application would I use to "open" and install these files if I just downloaded them?

---

### Post by bodhi.zazen on 2011-04-28
> **pcvchriskmg said:**
> Could I just download these files from this website and unpack/install them on my computer? What application would I use to "open" and install these files if I just downloaded them?

You can manually download them and install them with dpkg (command line) or double click on them.

---

### Post by trozamon on 2011-04-28
Shouldn't he use the STA driver listed in Restricted Drivers? I thought that I heard it was recommended over the old b43 drivers.

---

### Post by pcvchriskmg on 2011-04-28
> **trozamon said:**
> Shouldn't he use the STA driver listed in Restricted Drivers? I thought that I heard it was recommended over the old b43 drivers.

I couldn't get the STA drivers to work with my card on the 32-bit version. I tried to install the STA drivers last night, but I got an error saying that I have "held broken packages."

I googled a fix for that, and am still planning on trying the STA, but it didn't work for 32 bit.

Chris

---

### Post by pcvchriskmg on 2011-04-28
> **frank604 said:**
> Maybe the mirror you are using to update with is acting funky. 

Run synaptics package manager, click settings, click repositories, In Download From bar, choose other, then select best server on the right, it will ping all mirrors at this point and choose the fastest ping, select OK, and then get back to the synaptic package manger and click reload (or sudo apt-get update in terminal) and either use synaptic to search and download your driver or (sudo apt-get install blah blah).

IF the mirror chosen doesn't work, try manually selecting and trying each mirror in your country.  Hope this helps.

This was great advice. Thanks a bunch!

---

