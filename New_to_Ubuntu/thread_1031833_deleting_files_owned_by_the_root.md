---
title: "deleting files owned by the root"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by MihailKukutanov on 2009-01-05
How do I delete files that are owned by the root?

---

### Post by theozzlives on 2009-01-05
```
sudo rm filename
```

---

### Post by Ahunt on 2009-01-05
Congratulations on switiching! Welcome to Ubuntu!

Well first you have to make sure that you really want to delete them. If they are your own user files in your user account (documents, photos, etc) you can usually just right click on them and go Properties -> Permissions and change the permission to "read & write" and then you can delete them.

If it is a system file, you want to be very careful deleting it - most of those are required to run the system, which is why they are hard for users to delete them.

Assuming you know that you want to get rid of the file, then the easiest way is to go: Alt+F2 and type "gksudo nautilus" into the box that appears. This signs you in temporarily as "root". Then just navigate through the file system, highlight the file and hit "delete" and it is gone. Closing that window will return you to "user" status.

I hope that helps! If you get stuck on any issues please do post your questions here! We all started doing that and just learned our way along.

---

### Post by MihailKukutanov on 2009-01-05
Thanks people that solved a lot of stuff :D I'm trying to get the flash player right but its giving me a lot of trouble but i think ill fix it this time, this whole ubuntu thing its like some puzzle

---

### Post by Ahunt on 2009-01-05
Well when you are new at Ubuntu some parts can be a bit perplexing. I found the trick is to to take your time and learn as you go - that makes it fun to solve the puzzles. It just takes a bit of patience and most problems encountered can be solved surprisingly easily.

I wrote a diary of our experiences, in case you want to see how it went for us. There were ups and downs but we have been 100% Ubuntu in our house now for 6 months: [http://web.ncf.ca/adamandruth/ubuntu.html](http://web.ncf.ca/adamandruth/ubuntu.html)

The best part is that you have the best tech support available 24/7 right here and no one will say "Reboot - *click*"

---

### Post by donkyhotay on 2009-01-05
> **MihailKukutanov said:**
> Thanks people that solved a lot of stuff :D I'm trying to get the flash player right but its giving me a lot of trouble but i think ill fix it this time, this whole ubuntu thing its like some puzzle

Whats going on with the flash player? A simple 
```
sudo apt-get install flashplugin-nonfree
```
should be all you need to do to download/install it. Linux is different from windows, although there are times when you need to go to a website and download a file it about 99% of the time what you need is in the repositories and accessed through synaptic.

---

### Post by MihailKukutanov on 2009-01-05
donkyhotay tryed a lot of stuf it won't work is it possible to be turned of in the mozilla?

---

