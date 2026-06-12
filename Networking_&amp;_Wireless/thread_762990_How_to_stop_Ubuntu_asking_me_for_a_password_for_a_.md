---
title: "How to stop Ubuntu asking me for a password for a shared folder in Windows"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by Giak on 2008-04-22
I have shared a folder from Ubuntu. When I try to access it through a windows machine in network. When I double-click on it I am prompted for a username and a password to access the index of the shared folders on my Ubuntu box. I do not want that to happen. What can I do to solve it?

[img]http://img389.imageshack.us/img389/935/76323607nf7.png[/img]

PS: I searched for Google on this and I landed on a thread with the same problem, but I could not understand how to fix it. Please give it to me pea by pea, I am green in Linux.

---

### Post by jabeez on 2008-04-22
Can't tell from that screenshot, but I seem to recall when I did this in Windows that there is a "remember password" option. That's the only way around it I know of, don't think you can do anything on the Ubuntu side.

---

### Post by Giak on 2008-04-23
Hmm well I can't really log in with the username/password I use on the Ubuntu server (desktop server). I could do this in Xubuntu, logging in with the username/password I normally log in with. I was also helped in the Xubuntu IRC-channel on how to fix this, they helped me change some samba config file, something like that, but I can't remember how now and I've changed to Ubuntu.

---

### Post by owenll on 2008-04-23
> **Giak said:**
> 
PS: I searched for Google on this and I landed on a thread with the same problem, but I could not understand how to fix it. Please give it to me pea by pea, I am green in Linux.

Maybe if you could post a link to that thread someone might be able to simplify it for you.

---

### Post by Giak on 2008-04-23
[http://ubuntuforums.org/showthread.php?t=710599](http://ubuntuforums.org/showthread.php?t=710599)

---

### Post by jonandrews on 2008-04-23
Have a look at my Windows / Ubuntu networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

I hope it helps.

---

### Post by jabeez on 2008-04-23
> **Giak said:**
> Hmm well I can't really log in with the username/password I use on the Ubuntu server (desktop server). I could do this in Xubuntu, logging in with the username/password I normally log in with. I was also helped in the Xubuntu IRC-channel on how to fix this, they helped me change some samba config file, something like that, but I can't remember how now and I've changed to Ubuntu.

Oh sorry I misunderstood your post, I thought you could access the share but didn't want to keep entering name/psswd. So yes, you need to create a samba user/password. Try these...


sudo smbpasswd -L -a ubuntu_username
sudo smbpasswd -L -e ubuntu_username


replacing with your username..........

---

### Post by Giak on 2008-04-23
No I have both those problems. My number one goal is that you should access the shared folders (and printers etc) from browsing the network without being prompted for any username/password. Secoundly, can I ask what that command does? Because I already have a username and a password for my computer. If it sets a password for my user I already have one.

---

### Post by Giak on 2008-04-23
> **jonandrews said:**
> Have a look at my Windows / Ubuntu networking guide:

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

I hope it helps.

Yup, it did. :)I typed that on the guide you had for Ubuntu networking. I have now added my user there. I rebooted and now I can view my files there. Preferably I want no login in the first place to view the index, but some folders still password protected. Is this possible? If not I can just solve it by getting an FTP-server. But still, a no-login in the first place is the best.

---

