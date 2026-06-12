---
title: "cannot find programs in the repository..."
date: 2009-01-10
forum: New to Ubuntu
---

### Post by akimatsu123 on 2009-01-10
Hi,

I am trying to download airsnort-ng , aircrack-ng, etc to crack a WEP encryption for a friend. His parents are out of town and he needs to connect to his wireless but he doesnt know the password. 

That being said, that's when i noticed that i had this problem. Ubuntu kept telling me that it couldn't find airsnort, aircrack, etc in the repository. Then when i checked synaptic, I noticed that i was missing A LOT of programs. I couldn't even get the compiz window manager, as it just did not appear in synaptic. 

I tried under "software sources" but it always hangs at around "downloaded 36 out of 42" or something like that. 

How can i fix this? Thanks

---

### Post by JoshuaRL on 2009-01-10
Well, first make sure that all the software repos are enabled.  Then, go to the terminal and do:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

```
If there's any gremlins in the machine, that should clean them out.  Any errors come up?

---

### Post by akimatsu123 on 2009-01-10
I tried what you suggested:

```
sudo apt-get update
```

Gave the error:

```
W: GPG error: http://archive.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Other than that, everything is fine. If it helps, I am using the main server.

---

### Post by JoshuaRL on 2009-01-10
Run it again to see if it can fix itself.

If not, run this:
```

sudo apt-get update -o Acquire::http::No-Cache=true

```

---

### Post by 2hot6ft2 on 2009-01-10
> **akimatsu123 said:**
> Hi,

I am trying to download airsnort-ng , aircrack-ng, etc to crack a WEP encryption for a friend. His parents are out of town and he needs to connect to his wireless but he doesnt know the password. 

That being said, that's when i noticed that i had this problem. Ubuntu kept telling me that it couldn't find airsnort, aircrack, etc in the repository. Then when i checked synaptic, I noticed that i was missing A LOT of programs. I couldn't even get the compiz window manager, as it just did not appear in synaptic. 

I tried under "software sources" but it always hangs at around "downloaded 36 out of 42" or something like that. 

How can i fix this? Thanks
I don't think airsnort-ng is in the repos. aircrack is though. You didn't say which version of ubuntu you have and compiz-fusion comes with 8.10 and is already installed.
Applications>System Tools>Compiz Fusion Icon
or
```
ccsm
``` in a terminal
Applications>Accessories>Terminal

Might try changing servers for the signature error too.

---

### Post by cariboo on 2009-01-10
Have you got all the repositories enabled? Aircrack-ng is in the universe. To fix you gpg key problem do the following:

from: [www.babblestorm.co.uk](www.babblestorm.co.uk)
> * Start system/administration/synaptic package manager
* Go to Settings / Respositories
* Select the Authentication tab
* Click on "Restore Defaults" 

Jim

---

