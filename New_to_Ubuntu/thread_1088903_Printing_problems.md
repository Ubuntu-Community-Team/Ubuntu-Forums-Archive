---
title: "Printing problems"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-03-06
Hi there everyone,

I'm having a nightmare trying to set up a printer on my machine. I've used the exact same steps before with other machines and never had a problem. Here's what's going on:

1) CUPS isn't listed in my System > Administration > Services, so I can't start it.

2) I've tried "sudo /etc/init.d/cups start" and it says "command not found"

3) System > Administration > Printing doesn't look anything like it does on other machines. Basically, it's blank, and almost all the options are greyed out.

I followed the tutorial here ([http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703)). Like I said, it's never been a problem before, but for some reason on this machine, it just won't work for me. I get the LPD driver installed and the CUPS wrapper installed (at least, I think I have), and nothing shows up in Printing.

Help!

---

### Post by thtrgremlin on 2009-03-06
have you tried installing cups?

and I assume you have checked out system -> administration -> printing?

---

### Post by doctorbighands on 2009-03-06
CUPS is installed. I just double-checked in Synaptic to be sure.

Any other ideas?

---

### Post by sneeks on 2009-03-06
what printer is it?

---

### Post by doctorbighands on 2009-03-06
It's a Brother MFC210C.

---

### Post by doctorbighands on 2009-03-06
bump

---

### Post by plucky on 2009-03-06
Post output of ```
dpkg  -l  |  grep  Brother
``` to see if the drivers are installed.


You should see ```
ii  brscan2                                    0.2.4                                 Brother Scanner Driver
ii  cupswrappermfc210c                         1.0.2-3                               Brother MFC210C CUPS wrapper driver
ii  mfc210clpr                                 1.0.2-1                               Brother lpr Inkjet Printer Definitions

```


If they are not installed,use the Synaptic Package manager to install them.Search for **MFC-210C**


Also open Firefox and in the address bar put ```
http://localhost:631/
``` will open the Cups interface,you can add the printer there.


Good Luck

---

### Post by handydan918 on 2009-03-06
> **doctorbighands said:**
> 
2) I've tried "sudo /etc/init.d/cups start" and it says "command not found"


Try ```
sudo /etc/init.d/cupsd start
```

---

### Post by doctorbighands on 2009-03-06
That command returns
```

ii  cupswrappermfc210c                         1.0.0-1                                              Brother MFC210C CUPS wrapper driver
ii  mfc210clpr                                 1.0.2-1                                              Brother lpr Inkjet Printer Definitions

```

So, it looks like the drivers are there. I'll go ahead and install the brscan driver.

---

### Post by doctorbighands on 2009-03-06
> **handydan918 said:**
> Try ```
sudo /etc/init.d/cupsd start
```

I get "command not found"

---

### Post by doctorbighands on 2009-03-06
> **plucky said:**
> 

Also open Firefox and in the address bar put ```
http://localhost:631/
``` will open the Cups interface,you can add the printer there.




I get a Page Load Error when I enter either [http://localhost:631](http://localhost:631) or [http://192.168.1.1:631](http://192.168.1.1:631)

---

### Post by plucky on 2009-03-06
> I get a Page Load Error when I enter either [http://localhost:631](http://localhost:631) or [http://192.168.1.1:631](http://192.168.1.1:631)


localhost=127.0.0.1 so the line should read **[http://127.0.0.1:631](http://127.0.0.1:631)**

Check ```
cat /etc/hosts
```

Check in synaptic that you have "cupsys" installed.

Have you used this install disc before on other systems?

If not, you should check the integrity of the ISO and the Cd burn.

---

### Post by plucky on 2009-03-06
> **handydan918 said:**
> Try ```
sudo /etc/init.d/cupsd start
```

Should be ```
sudo /etc/init.d/cupsys start
```

---

### Post by doctorbighands on 2009-03-06
I do have cupsys installed.

I tried [http://127.0.0.1:631](http://127.0.0.1:631) and got the same Page Load Error.

"sudo /etc/init.d/cupsys start" returns "command not found".

Do you mean that perhaps I should reinstall Ubuntu?

---

### Post by doctorbighands on 2009-03-06
bump

---

### Post by plucky on 2009-03-06
Try to re-install cupsys first to see if that makes a difference.Use synaptic and mark for reinstallation and apply.


What about the CD,is this the first install with this CD?

Did you check the md5sum of the ISO before you burnt the CD?

Did you check the integrity of the CD? It is an option in the startup menu of the CD.

---

### Post by doctorbighands on 2009-03-06
I reinstalled cupsys. Still nothing. I checked the /etc/init.d directory, and there is no entry for "cupsys". There is a cups there.

I don't have the installation CD on hand. I didn't check the disc integrity or the md5sum, because I figured I didn't need to - it's one I ordered from Canonical. I didn't download it.

---

### Post by plucky on 2009-03-07
> **doctorbighands said:**
> I reinstalled cupsys. Still nothing. I checked the /etc/init.d directory, and there is no entry for "cupsys". There is a cups there.

I don't have the installation CD on hand. I didn't check the disc integrity or the md5sum, because I figured I didn't need to - it's one I ordered from Canonical. I didn't download it.

Just checked on my 8.10 system and the package name has indeed changed to **cups** so all the commands given previously with cupsys needs to be changed to cups.Although you seem to already have it installed but is not working.


What happens when you use ```
sudo /etc/init.d/cups start
```

Wonder why they changed it.

---

