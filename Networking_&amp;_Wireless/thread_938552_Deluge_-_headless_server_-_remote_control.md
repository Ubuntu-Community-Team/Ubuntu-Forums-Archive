---
title: "Deluge - headless server - remote control"
date: 2008-10-05
forum: Networking &amp; Wireless
---

### Post by jimmy the saint on 2008-10-05
So I gather that Deluge has seperated their front and back ends to allow for better remote control capabilities.  I cannot seem to find anything about how to implement this.  I would like to put deluge on my headless server (still running Gutsy) and control it via the gtk interface on my laptop.  The website says I can do it, but not how!!

I am sure this is relatively easy.  Anyone know how, or a good guide?

Thanks

JTS

---

### Post by smeerbartje on 2009-03-05
Any news on this? I also would like to install a torrent client on my Ubuntu server 8.04 LTS. I don't need a lot of options, my only requirement is that the client is able to automatically move completed files to another directory (Torrentflux does not have this option).

---

### Post by jimmy the saint on 2009-03-15
the deluge version in the repos should be able to do that.  What was tripping me up was that the versions in the repos had not yet been updated to the version that had the capabilities I needed. simply having the file moved is a basic feature and should be present in the repo version

---

### Post by smeerbartje on 2009-04-09
I have just installed the repos version of Deluge on my desktop version of Ubuntu 8.10. This version is able to move completed downloads to a specific directory. I only don't know how to separate the GUI with the 'server'. Can anyone help me out?

At the website I read that I need to start deluge with 'deluge --ui web'. Unfortunately I get the error: no such option (ui). Jimmy the Saint, are you absolutely sure that the repos version is able to separate the GUI?

---

### Post by jimmy the saint on 2009-04-22
no.  I am sure the version in the repos has the ability to move files once they are downloaded.  I dont know if the version in the repos can seperate the gui because I just use the current version from the Deluge project repos

---

### Post by smeerbartje on 2009-04-23
> **jimmy the saint said:**
> no.  I am sure the version in the repos has the ability to move files once they are downloaded.  I dont know if the version in the repos can seperate the gui because I just use the current version from the Deluge project repos

Okay, then we're sure that the repo-version does not support that :). Is it difficult to install the latest version on Ubuntu server 8.04??

---

### Post by jimmy the saint on 2009-04-24
you can get the appropriate repository from here
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

You will want to choose your Ubuntu version from the dropdown list and then add the appropriate line to your /etc/sources.list or add them via synaptic.

This will give you an up to date release.  Alternatively, if you upgrade to Jaunty, it seems that a newer >1 version is available in the Ubuntu repositories.

---

### Post by smeerbartje on 2009-04-25
> **jimmy the saint said:**
> you can get the appropriate repository from here
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

You will want to choose your Ubuntu version from the dropdown list and then add the appropriate line to your /etc/sources.list or add them via synaptic.

This will give you an up to date release.  Alternatively, if you upgrade to Jaunty, it seems that a newer >1 version is available in the Ubuntu repositories.

Hi! Thank you for your reply. I have edited /etc/apt/sources.list and added the two lines for hardy. But now what? I'm using the server edition.

---

### Post by kaivalagi on 2009-04-25
> **smeerbartje said:**
> Hi! Thank you for your reply. I have edited /etc/apt/sources.list and added the two lines for hardy. But now what? I'm using the server edition.

The following should update your sources and prompt for the newer version deluge upgrade...

```
sudo apt-get update && sudo apt-get upgrade
```

If not just uninstall and reinstall through synaptic...

Once setup you should be able to run the same version of deluge on your laptop and go to the connection manager to add a new host to point to your server address and connect...

---

