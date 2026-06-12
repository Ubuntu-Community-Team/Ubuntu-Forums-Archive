---
title: "Broadcom BCM4312 802.11 b/g LP-PHY (Rev 01)"
date: 2014-03-19
forum: Networking &amp; Wireless
---

### Post by nina3 on 2014-03-19
):P Hello everyone,

Well, I'm a new user for ubuntu and still migrating and recovering from the big kick of XP.
Must tell, I feel satisfy and very happy with this new O.P (GREAT JOB GUYS)

But only last one little thing and that is the wireless conection. Most clarify that I'm not a literate about this, then I'm looking for a bit of help so won't make any huge mistake.

To summarize:

-Select OP start (running on dual just in case)
-Select area
 Ubuntu 
[LIST]
[*]Black screen: Talking about firmware and to visit certain website:```
 [www.wireless.kernel.org/users/drivers/b43]("http://www.wireless.kernel.org/users/drivers/b43")
```+[number and other things]
[/LIST]

The problem is that it does last less than 12 secs to get all the data, nevertheless did visit the site and found a lot but got confuse... so, used the code found in a similar case, to get certain info:

```
lspci | grep -i network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


```

After this, I do not know how else to  surely proceed. (would be great if it is from the terminal)
In advance I'm thankful for all the help that will be provided.

---

### Post by westie457 on 2014-03-19
Welcome. with a working cable connection open a terminal and run this ```
sudo apt-get install linux-firmware-nonfree
``` unplug the cable. 

Let us have your report.

---

### Post by nina3 on 2014-03-19
> **westie457 said:**
> Welcome. with a working cable connection open a terminal and run this ```
sudo apt-get install linux-firmware-nonfree
``` unplug the cable. 

Let us have your report.

:) Thank you so much.

Did tried the code and worked as follows:

```

sudo apt-get install linux-firmware-nonfree
[sudo] password for nina: 
Reading packages... Done
Building dependency tree 
Reading state information ... Done 
The following NEW packages will be installed: 
   linux-firmware-nonfree 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
Need to get 3,943 kB of archives. 
8,982 kB of additional disk space will be used after this operation. 
Des: 1 http://hn.archive.ubuntu.com/ubuntu/ saucy / multiverse firmware-linux-nonfree all 1.14ubuntu1 [3,943 kB] 
Downloaded 3,943 kB in 12sec. (314 kB / s) 
Selecting the linux-firmware-nonfree previously deselected package. 
(Reading database ... 197043 files and directories currently installed.) 
Unpacking linux-firmware-nonfree (from ... / firmware-linux-nonfree_1.14ubuntu1_all.deb) ... 
Configuring linux-firmware-nonfree (1.14ubuntu1) ...

nina@ubuntu:~$

```

Then, unplugged the cable but still without working...
Edit:
After restart everything began to work wonderfully, thank you so much!

---

### Post by westie457 on 2014-03-19
Great, glad it's working. Also happy you did not try any of the other recommended solutions on the internet that do not work.

Could you mark this as '[COLOR=#ff0000]solved[/COLOR]&#8203;' using 'Thread Tools' at the top of the page.

---

