---
title: "Home networking ubuntu and windows"
date: 2008-07-04
forum: Networking &amp; Wireless
---

### Post by knipknup on 2008-07-04
I have just recently installed ubuntu on a laptop and desktop in my home.  I also have another laptop and desktop running windows vista.  These are all on the same router.  All can see the internet.

My problem is that from the ubuntu boxes, I can see the windows vista file systems but cannot seen the ubuntu boxes.  One ubuntu box cannot see the other, either way.  However, both ubuntu boxes can see both windows vista boxes.  I read through the networking sticky and did a search, but confess that I am a ubuntu noob.  The sticky looks to address seeing windows boxes, which is the opposite of my problem.  If anyone can help me to get these ubuntu boxes to see one another on the same router, I would really appreciate it.

All boxes, ubuntu and vista are all on my internal network with 168.192.2.... IPs.

Thanks in advance.

---

### Post by superprash2003 on 2008-07-05
do you have firestarter or anything similar running in ubuntu??are windows pcs able to see ubuntu pcs?

---

### Post by knipknup on 2008-07-05
> **superprash2003 said:**
> do you have firestarter or anything similar running in ubuntu??are windows pcs able to see ubuntu pcs?

No.  The ubuntu boxes can see the windows domains but the windows pcs cannot see the linux.  I don't believe I have firestarter running or installed, unless it installs by default.  I do not see a firewall option under system/preferences or system/administration menus.

---

### Post by issih on 2008-07-05
What exactly do you mean by one computer seeing the other?

How are the IP addresses being assigned? statically or via dhcp.

Can the different machines ping each other?

If they are all atttached to the same router I'd assume chances are its dhcp and that all the machines can ping each other, although not necessarily via hostname.

If you are talking about windows file and printer sharing (i.e. smb) then you need to know that ubuntu doesn't enable any shared folders by default. Therefore you wouldn't see anything in the network neighbourhood on a windows machine or indeed in the Places->Network section on an ubuntu machine, as there are no shares to display.

If you install the package nautilus-share.

```
sudo apt-get install nautilus-share
```

you will be able to administer folder sharing from the right click menu in the file browser. Once you have shared a folder, hopefully the machine will appear as if by magic:)

Hope that helps

---

### Post by knipknup on 2008-07-05
I can ping each device on the router successfully.
I can see windows file systems from the ubuntu systems and browse, etc.
I cannot see ubuntu file systems from the windows systems.

On my ubuntu laptop, I right-clicked on the home folder in the file system, went to the share tab and enabled.  This pulled up a thing to let me install nautilus.  I did it.  I will report back if it succeeded, I have to run an errand and my wife won't be happy if I spend more time dinking with this now.
Thanks for you help.

---

