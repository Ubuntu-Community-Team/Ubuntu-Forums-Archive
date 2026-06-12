---
title: "ndiswrapper-1.8 problems"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by cliff01 on 2007-03-06
When I try to install my windows drivers using ndisdriver-1.8 I get the "cannot copy yadda yadda line 144 yadda yadda stuff. Then, if I give the ndiswrapper-1.8 -l command it tells me the driver (wusb54g) is not valid. I can uninstall the driver with the "e" command. Do I need to unplug the device... is there a secret here?
Thanks!

---

### Post by teaker1s on 2007-03-06
ndiswrapper sometimes requires more than just the inf file on some installs, to be sure of this make sure all extracted driver files are in the same directory.

to remove a driver ```
sudo ndiswrapper -r nameofdriver
```

in terminal cd into extracted driver location

```
sudo ndiswrapper -i nameofdriver.inf
```

also if you have ethernet internet then install these

s```
udo apt-get install ndiswrapper-common ndiswrapper-utils ndiswrapper-utils-1.1 ndiswrapper-utils-1.8 unzip cabextract
```

if the driver you are using still fails then I suggest getting the  driver via the ndiswrappper project's page of working drivers

---

