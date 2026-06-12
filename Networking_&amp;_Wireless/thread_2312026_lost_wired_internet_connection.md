---
title: "lost wired internet connection?"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by garyed on 2016-02-01
Using Ubuntu Studio 14.01 on my desktop, internet has been working for about a year. Once or twice this has happened & rebooting solved the problem but it doesn't help any more. I'm dual booting with Windows 7 & the internet works fine booting into Windows so I assume it's an Ubuntu or driver problem. Any ideas where to go from here?

---

### Post by howefield on 2016-02-01
If you have the proposed repositories enabled, have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=2311705&page=3](http://ubuntuforums.org/showthread.php?t=2311705&page=3)

---

### Post by garyed on 2016-02-01
I'm a little lost trying to figure out that thread.
I didn't do any updates or download anything but my internet was working last night before I turned my desktop off & it's not working this morning. When I click on the network toolbar icon informationit gives me an error & says "no valid active connections found". What's strange is that it said that even when my internet was working.
One other thing i should mention is that I can still network with my other wired computer on the same router & copy files back & forth. It's just the internet that I can't connect to, but if I boot into Windows on the same computer it connects to the internet fine.

---

### Post by garyed on 2016-02-01
I found some really weird stuff happening also. If I type an ip address in the the browser then it will eventually show the web page but not correctly. If I type a url name it will not work at all. If I ping the url name I just get unknown host but if i ping the ip address it works normally. Does that give any clue to where my problem lies?

---

### Post by wodonn on 2016-02-01
Lost internet in Ubuntu after downing updates also, reinstalled the OS and works great again. Have to be careful about what gets updated it seems. Tried looking for a different solution but not successful.

---

### Post by garyed on 2016-02-01
I didn't download anything but a few months ago I changed internet providers. I don't know if that could have something to do with this problem but I remember my router changed from 192.168.1.1 to 192.168.0.1

---

### Post by garyed on 2016-02-02
This keeps getting weirder. I went to /etc/NetworkManager/NetworkManager.conf & changed the line "managed=false" to  "managed=true".  I then opened up the network manager & added an ethernet network using all the auto defaults.  Now when I click on the ethernet network it works for about 30 seconds & then my connection drops out. Everytime I open my network icon on the toolbar & click on ethernet connection it works for about 30 seconds & then disconnects throwing me back offline. I know its working for 30 seconds because it will open up new pages I've never been to & then just get stuck on resolving host. If I don't find a solution soon I'm going to reinstall but I'm a little disappointed that I can't find an answer for this problem.

---

### Post by garyed on 2016-02-02
I'm still trying to get this figured out. I've made some progress by editing  ethernet connection 1 in network connections & leaving all the fields blank. Now when I boot up if I click on the ethernet 1 connection from the network toolbar menu everything works O.K. until i shut the computer down. So for now it's working & all I have left to do is figure out how to get it working automatically without having to manually click on every boot up.

---

