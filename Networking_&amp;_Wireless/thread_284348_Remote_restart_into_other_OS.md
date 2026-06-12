---
title: "Remote restart into other OS"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by phersotty on 2006-10-25
Hello,

I am excited that I finally figured out how to configure the Westell 6100 that Verizon sent with my DSL package to cooperate with my Belkin router in allowing me to make a remote vnc connection in XP.  Now I want to do it with Linux!

My current configuration is a triple boot system Ubuntu/Suse/xp.

I can make a remote desktop connection in XP but not yet in Ubuntu.  I've sent myself an email invitation, checked the box to allow remote access, and created a username and password.  I tried the same in Suse but still no connection.  Since the remote connection works in XP I am assuming its not a router configuration issue.  My guess is that I am either not configuring the vnc correctly in linux or that there is a firewall enabled in both distros blocking access.  ](*,) 

mnt /dream/vision/forsomethingcool

I would like to have the ability to reboot my machine remotely into any os I choose.  I noticed that in Suse, with KDE, there is an option to choose which os to boot on restart.  So if I make Suse the default os then I can theoretically remotely wake up my computer (through lan awake) boot Suse and then restart into any OS I choose.  Actually what would even be better is if there is a way to access Grub remotely, but I'll settle for just booting to a default os.

Any ideas :-k  on why I can connect to XP through vnc but neither of my linux distros?  Thanks

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-10-25
Now i am not an networking pro,
but check to see if remote connect in xp uses the same port as in linux << i dont even know if linux uses ports. i am a nebie to linux but thats my best gess.

---

### Post by phersotty on 2006-10-25
Thanks.  They are using ports 5900 5800 and 5500 on xp.  On linux I think its just port 5800.

---

