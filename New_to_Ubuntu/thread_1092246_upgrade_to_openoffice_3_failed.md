---
title: "upgrade to openoffice 3 failed"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by rkakkar on 2009-03-10
i pasted the following in repositories in synaptic:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

but when i click on reload, it gives the following error:

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
```

---

### Post by cptrohn on 2009-03-10
I just did this last night... only in the step by step that was given to me they didn't say to refresh in synaptic

it was ```
sudo apt-get update
```

and ```
sudo aptitude safe-upgrade
```


That worked for me, I think the name of the thread was "Whats the easiest way to upate Open Office?"


Hope this helps.

---

### Post by snowpine on 2009-03-10
You need to add the "key", check out the paragraph starting with "Right click HERE..."

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by warped6 on 2009-03-23
Thank you. I knew I had forgot a step somewhere, couldn't find it though.

---

### Post by presence1960 on 2009-03-23
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

this worked for me in hardy & intrepid. Note: make sure the filenames in the commands match the file you download.

---

