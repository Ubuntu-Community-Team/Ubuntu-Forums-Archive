---
title: "PPA Error - Need Help to Resolve This"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by marl30 on 2011-01-05
So, I saw this new Nautilus plugin on Webupd8:[http://www.webupd8.org/2011/01/nautilus-columns-update-brings-pdf.html](http://www.webupd8.org/2011/01/nautilus-columns-update-brings-pdf.html)

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install nautilus-columns
nautilus -q
```After following the above terminal command to add the PPA and install, I started getting the following error whenever I try to open Synaptic Package Manager, or sudo apt-get update in terminal: ```
E: Type 'ttp://ppa.launchpad.net/nilarimogard/webupd8/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/nilarimogard-webupd8-maverick.list
E: The list of sources could not be read.

```Please help me to get this sorted out.

---

### Post by marl30 on 2011-01-05
Let me also add that I went to source list and deleted the PPA I added, but still getting the error.

---

### Post by jcolyn on 2011-01-05
Open synaptic then click settings-repositories-other software then look for the ppa and see if it has a check mark in the box next to it. If not check it then close. You will be asked to reload. Do so in synaptic then try it.

If it does not work the ppa may be down at the moment which is not unusual..Give it a few hours and try again..

Looking at the below error it is missing "h" notice ttp:// in the first line
```
E: Type 'ttp://ppa.launchpad.net/nilarimogard/webupd8/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/nilarimogard-webupd8-maverick.list
E: The list of sources could not be read.
```

---

### Post by marl30 on 2011-01-05
> **jcolyn said:**
> Open synaptic then click settings-repositories-other software then look for the ppa and see if it has a check mark in the box next to it. If not check it then close. You will be asked to reload. Do so in synaptic then try it.

If it does not work the ppa may be down at the moment which is not unusual..Give it a few hours and try again..

Synaptic only gave the same error message before closing. I Got it solved though. Here is what I did. I went to the source directory: /etc/apt/sources. I then opened it as administrator and looked for the file and deleted. When I ran sudo apt-get update it ran without any issue. Thanks for the help nonetheless. :)

---

