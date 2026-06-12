---
title: "Brother MFC465CN printer"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by papahoffa on 2008-01-25
I can't get my Brother MFC-465CN printer to work on a network...any suggestions?

---

### Post by froy02 on 2008-01-25
Here's a website for Brother MFC printers.  I used it to set up my mfc665.

[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

---

### Post by papahoffa on 2008-01-26
I've tried using those directions, but I can't make the directions for the MFC-465CN work.  Specifically, when I try to load  PPD files, I can't find them.

---

### Post by froy02 on 2008-01-26
To set up your printer using wired network:

Install the LPR driver first then the CUPS driver.
Set it up from the browser by typing: 'http://localhost:631'
Choose the appropriate driver e.g. MFC465CW. 
Select IPP for protocol and "socket://xxx.xxx.xxx.xxx." (your printer's IP address)
Select modify printer and you're done.

Scanner setup:
Install the scanner driver first.
Install the scan key tool.
Configure the scanner IP address and friendly name in terminal with the command: 
"brsaneconfig2 -a name=MFC465CW-SCANNER model=MFC-465CW IP=xxx.xxx.xxx.xxx"  (your mfc IP address)

---

### Post by AgentZ86 on 2008-01-27
> **papahoffa said:**
> I've tried using those directions, but I can't make the directions for the MFC-465CN work.  Specifically, when I try to load  PPD files, I can't find them.

You may need to make a symbolic link before installing cups wrapper driver ?
according to the brother site at least with my ubuntu 7.10 I had to create symbolic link

Not sure if you already did that, but anyhow here is the symbolic link you may need.

sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd

Then download cups wrapper to desktop
click on it and open with gdebi select ok to install

Then remove the symbolic link. Just delete the symbolic link located in the /etc/init.d/cupsys folder might be the only one there so it should be easy to find with an arrow just above the right hand corner.
Anyhow delete it and your printer should be there for selection now,hopefully

I hope this helps

P.S the scan key tool only work as root,so some other setting have to be changed, I'm trying to figure that out myself now,  and thus regular users won't access it, so most of my scanner programs also have to run as root because I've not figured out how to make the scan key tool and drivers work as regular user for some reason. Just FYI on the scanning part.

---

