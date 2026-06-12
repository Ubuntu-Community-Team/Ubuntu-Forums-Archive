---
title: "LibreOffice... oops, please help me to install"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by Fernie Alex on 2011-01-26
Hi, firstly, I would like to stress the importance of getting LibreOffice working to me. I'm a first year at UWE studying computing. I run Ubuntu 10.10 (32). In one of my modules, all the lab work is given as a .docx with most of the importance stuff as images (examples, questions, ect). Now, these won't display at all in OpenOffice.org so I have to use XP on a VM.

Anyway, the problem. What was happening at first was that I tried to install LibreOffice from the software centre and I got something about untrusted sources, I've followed a few threads and have messed it up even more now!

It now says this: Sorry, 'libreoffice' is not avaible for this type of computer (i386).

There isn't a software package called 'Libreoffice' in your current software sources.

I think this is something to do with what I've ticked or unticked but any help would be much appreciated.

Thank you.

---

### Post by LowSky on 2011-01-26
open a terminal from Applications > Accessories

```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice libreoffice-gnome
```


Be warned LibreOffice is really just Openoffice made a bit more free.

---

### Post by Vaphell on 2011-01-26
not to mention 'developed more actively'. I've read that many patches not accepted for inclusion in OO were committed and number of active developers rose 10fold or something. LO is pretty much the same as OO now, but not for long.

---

### Post by Fernie Alex on 2011-01-26
Result from the first command:

> Error reading [https://launchpad.net/api/1.0/~libreoffice/+archive/ppa:](https://launchpad.net/api/1.0/~libreoffice/+archive/ppa:) <urlopen error [Errno 111] Connection refused>

---

### Post by marl30 on 2011-01-26
> **Fernie Alex said:**
> Result from the first command:

Refresh your source list with this command: ```
sudo apt-get update
```

---

### Post by LowSky on 2011-01-26
Fernie Alex you seem to have a connection issue to work out first.

I actually just install LibreOffice just to make sure my commands work, and they do.

---

### Post by Fernie Alex on 2011-01-26
I have used that command and still get the same error, I also get a few errors from running that command:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA

:( Thanks for the help so far though. Could it be to do with the Uni's proxy?

---

### Post by LowSky on 2011-01-26
> **Fernie Alex said:**
> I have used that command and still get the same error, I also get a few errors from running that command:



:( Thanks for the help so far though. Could it be to do with the Uni's proxy?

more than likely is an issue with the proxy. um... you could always torrent download the correct verison from there website, and then unzip and then install the deb packages. It will take more work though

basically download libreoffice from libreoffice website. make sure to get the correct deb version.

then open the file and extract it to the desktop or somewhere lese you will remember.

then open a terminal and type this (notice I used the desktop for the files) you can drag the file location into terminal if its too long to type... i used the 64 bit version so please dont copy or paste.
```
cd cd ~/Desktop/LibO_3.3.0rc4_Linux_x86-64_install-deb_en-US/DEBS/
 
```
```
sudo dpkg -i *.deb
```
the * will install the deb files in proper order.

then open the desktop integration folder inside the DEBS folder and install that deb just by clicking on it.
after installation you can delete the folder from your desktop
hope that helps.

---

### Post by cariboo on 2011-01-26
Copy and paste the complete key in the code box below into a text file:

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ETRuApgEEAKFfVq0Yu0rBdnipWkI9WOW6X1xrzrpSWE+bTakWbNASr3f5RENbk0JEOGay
oyIynRj2GHxAtD116BApkF3IdtikrEBDZKirgUOlq9EpSyP0EwbP/n40p9VcWH4KHyR9pILK
uiU1t0u70VSakvB1+KkOqs2oei0TFnDYbYH5pmWHABEBAAG0J0xhdW5jaHBhZCBQUEEgZm9y
IExpYnJlT2ZmaWNlIFBhY2thZ2luZ4i4BBMBAgAiBQJNG4CmAhsDBgsJCAcDAgYVCAIJCgsE
FgIDAQIeAQIXgAAKCRCD+6F1E3i0ROAGA/9otE7tGoigHssjm9SG9vwVTGYF+0QQX2uwiQJm
ChXdqtt1y+YRv5bq61KGfu46DNc0QlJIgaOW+6hp/L5QwTrNIp7psjDPUjTQ0qo0ZSRb67WJ
jNKeR78PGtxYRNH+S67HBEFatbF7EPVuoqTS38myroYRQtTHuXD2zwqM8WSPNokCHAQQAQIA
BgUCTTBXPwAKCRC5byMArRHL7tm0EADDPtdJwqu4RQGdbI1KONhkoh5y5H4aEc0jQDe1VjTh
XrZYnWrkBZvb3dhwtiA4CT+hWiZQnilue+SfACCdjdNQY6neP1Y4czLq6ApErVZa9rL7tvMx
rrhShLLxTDBrLrXDGsLE9AGKwe4GicuB0rh1JWiWawhygu1CZhm+7paXp7njh+IPbRTf3q8h
HLWVGeFyaro7fQiUmfi/q5ljsqMfTBDdPmL4+vOpBTvFNsUvU2vHii2C+/p/la3xZM6r3j7O
00FRDMPr64dt3hDkJgOKrX2Cxat6w6Nuw+yVw2k69WgP3zZZEieIKytBoEJ9nLycdJhdeLTo
J/7R2iZJBhdUjpMbzyQ0c9YiaUKs8YP6wZftZHbG7JsiHXpUkMqlnz9PDBWm1K3bXbaClcT9
h6ISzeYqKspLjJ4PPMejELiI7X/hNQ2+LlCe8epjENyNCC0/pdzMudOpwkgc3D8TkLo1+EH6
4gPRPNzR4EdedGWnUpWiNwtkz8eSh5EYC2Ucv1NwUfaj77GDnTprX0bOGWbYp+OiT6OxIKpo
spfcNhqZ1YxtNVM8d8cFCQKU4LiDMQZL0uQm7dsFFmUwR5rTr2ZCY+JNUfAoE7IdGWo9St50
DIVyEhPNZuwiYy5nX54MIWmhCpzv8Yr2SXtxYcfMZ6qxaGxYyyD1d3T0WrqjxNN+Eg==
=2h5K
-----END PGP PUBLIC KEY BLOCK-----
```

and save it with an easy to remember name, next go to System->Administration->Synaptic Package Manager->Settings->Repositories->Authentication and click the Import Key File button, navigate to the file you just created and click OK. Close Software Sources and update your sources list, you should now be able to install LibreOffcie.

How to do this yourself.

Go to the [ppa]("https://launchpad.net/~libreoffice/+archive/ppa") and click the Technical details about this PPA link, next click the Signing Key link, and next click the link that in this case is 1378B444, this will bring up the key,

---

### Post by ikt on 2011-01-26
After you get libreoffice installed could you give your feedback here:

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/704461](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/704461)

As to whether it fixes the docx issue.

This would be very helpful thank you :)

---

### Post by Fernie Alex on 2011-01-26
Thank you to everyone that has responded to this thread. It is LibreOffice is now up and running. Unfortunately, I still can't see any images but hopefully this will be addressed at some point in the future.

---

### Post by sabutuga on 2011-01-27
Just installed Libreoffice on my computer running ubuntu 10.10. Easier access to application from office app menu, now I can go straight to write or calc. 
I'm looking forward for the future updates/innovations.

---

