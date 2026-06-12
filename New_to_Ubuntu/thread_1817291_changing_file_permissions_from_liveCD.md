---
title: "changing file permissions from liveCD"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by macaklinka on 2011-08-03
Hi, everyone!

My Ubuntu 11.04 does not want to boot anymore. I decided to reinstall, but I need to save my files first. I boot from liveCD, and I find them in home/user BUT I dont seem to have permission to access most folders and I cant copy them :( says im not the owner :confused:

I wanted to try changing permissions from terminal, but the paths to directories dont seem to work anymore, for example when I say cd $HOME/user it tells me no such file or directory. copying the location address from properties doesnt work eather.

I dont know the commands for terminal, can someone please help me? Can I somehow tell it that Im the owner of the files?

Thank you.

---

### Post by mikewhatever on 2011-08-03
Instead of changing permissions, launch Nautilus with admin privileges, and copy away:
```
gksudo nautilus
```

---

### Post by garvinrick4 on 2011-08-03
When you use a live cd when you mount a drive it is in /media
Use your own user name and sda#

sudo mkdir /media/lucid
sudo mount /dev/sda5 /media/lucid
cd /media/lucid/home/rick/Documents
ls (just ls gives you what is in Documents)
ls -lh (gives you name and who owns it)
sudo chown rick:rick (name of Document)   

Or if whole directory:
sudo chown -R rick:rick /media/lucid/home/rick/Documents

---

### Post by macaklinka on 2011-08-03
That was so easy, ha ha :)

Thank you so much!

---

### Post by amiacamal on 2011-08-04
Well chown would have helped me last night, had the same problem!

sudo chmod +r home 

solved my problems 
:)

---

