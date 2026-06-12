---
title: "Fixing wireless on Dell Laptops! Mine works now!!"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by Rain724 on 2008-09-01
Ok, well, after searching like crazy, asking questions here and on every other forums possible, I started searching through the wiki at linux.dell.com. I found this page which explained how to update the packages to search for updates in from dell itself (from 7.10 to 8.04). I did a fresh install of 8.04 and installed all of the updates on my XPS M1530 and then added the dell packages to the sources.lst file. When I ran the update again, i got the option to install a kernal 19-dell1, i did this, and now my wireless in my laptop is working great! 

Here is how I fixed it:
1) Make a back up of /etc/apt/sources.list (sudo cp /etc/apt/sources.list /etc/apt/sources.list_blackup)
2) Open up the blacklist file (sudo gedit /etc/apt/sources.list)
3) Add the following lines to the end of the file:
```

##Dell Packages
deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

```
4) Then run "sudo apt-get update"
5) Finally run "sudo apt-get upgrade"

Restart and your wireless should be working!! :):):)

This worked for me, so i hope it will work for other people too!


Edit: Fixed some very bad careless errors... xD

---

### Post by coffeecat on 2008-09-01
> **Rain724 said:**
> Ok, well, after searching like crazy, asking questions here and on every other forums possible, I started searching through the wiki at linux.dell.com. I found this page which explained how to update the packages to search for updates in from dell itself (from 7.10 to 8.04). I did a fresh install of 8.04 and installed all of the updates on my XPS M1530 and then added the dell packages to the sources.lst file. When I ran the update again, i got the option to install a kernal 19-dell1, i did this, and now my wireless in my laptop is working great! 

Here is how I fixed it:
1) Make a back up of /etc/modprobe.d/blacklist (sudo cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist_blackup)
2) Open up the blacklist file (sudo gedit /etc/modprobe.d/blacklist)
3) Add the following lines to the end of the file:
```

##Dell Packages
deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main

```4) Then run "sudo apt-get update"
5) Finally run "sudo apt-get upgrade"

Restart and your wireless should be working!! :):):)

This worked for me, so i hope it will work for other people too!

I think you've got something seriously muddled here. Those two repository lines belong in /etc/apt/sources.list. The file /etc/modprobe.d/blacklist is to list those kernel modules you don't want loaded at bootup. Adding the repo lines to the blacklist file won't help you do a successful update or upgrade with apt-get.

Do you want to comment?

---

### Post by AlcoholicDoc on 2008-09-01
> **coffeecat said:**
> I think you've got something seriously muddled here. Those two repository lines belong in /etc/apt/sources.list. The file /etc/modprobe.d/blacklist is to list those kernel modules you don't want loaded at bootup. Adding the repo lines to the blacklist file won't help you do a successful update or upgrade with apt-get.

Do you want to comment?

The address for the page he found is: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry")

I suppose it may work if entered into the correct file (/etc/apt/sources.list) although it did nothing for my wireless.

It's possible he just got confused and wrote the wrong file there.

---

### Post by coffeecat on 2008-09-01
> **AlcoholicDoc said:**
> It's possible he just got confused and wrote the wrong file there.

That's what I thought. I posted because I didn't want an inexperienced user copying this. I don't know what effect those lines would have in the blacklist file - probably none - but I'm not going to try it to find out. :)

The Dell link makes much more sense!

---

### Post by Rain724 on 2008-09-01
ROFL, wow, I really don't know what i was thinking when i posted this... yes, it goes in the sources.lst file... :lolflag:

---

