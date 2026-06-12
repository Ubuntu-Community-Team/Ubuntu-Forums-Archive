---
title: "Ubuntu server will not alow me to see it from my win XP laptop"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by Mtrboat01 on 2010-09-20
I have logged in to my server from it's desktop. used my keyboard mouse video switch to start up my XP desktop computer. I have no trouble seeing my server and the files i have on it with that computer. when i try to get to the server from my laptop it says i need to contact my system administrator i do not have permission to access. Would you help? i have not got a clue as how to get the two to talk. (remember the laptop is running XP) If anyone can help that would be great.

---

### Post by sandyd on 2010-09-20
> **Mtrboat01 said:**
> I have logged in to my server from it's desktop. used my keyboard mouse video switch to start up my XP desktop computer. I have no trouble seeing my server and the files i have on it with that computer. when i try to get to the server from my laptop it says i need to contact my system administrator i do not have permission to access. Would you help? i have not got a clue as how to get the two to talk. (remember the laptop is running XP) If anyone can help that would be great.
how are you trying to access it?

---

### Post by Mtrboat01 on 2010-09-21
I have a HP dv5000 notebook and i went in to my network neighborhood and clicked on the work group name. when i do this on my other computers it pops up a user name and password box where i can type in the name and password. this does not happen on my notebook computer. hope this helps. kinda stinks having to go right on my server i have a AMD chip and it hates the video card so everything is so big it is almost not worth using other then the three raid drives. (no idea why nvida and ubuntu can not co exist) any way.

---

### Post by bradleypariah on 2010-09-21
Have you set up Samba file sharing for the directories you want Windows to be able to see on the Network?
When you say "Server", do you mean an Internet server, or Home Network Server?

---

### Post by Mtrboat01 on 2010-09-21
I have a ubuntu server, server board single hard drive with operating system on it and three striped hard drives plugged in to the raid. there are three computers that access the server and two out of the three can see it. I have not opened a port on my router because it is a home server and have no desire to have anyone VPN in. hope this is enough information.

---

### Post by anewguy on 2010-09-21
Did you match the workgroup name on the laptop to that on the server?

---

### Post by Mtrboat01 on 2010-09-21
Yes i have the same workgroup and all . i can hit the web no prob just not able to get in the server .

---

### Post by anewguy on 2010-09-22
Another dumb question - are the userid and password set so they match?

---

### Post by sandyd on 2010-09-22
> **Mtrboat01 said:**
> I have a HP dv5000 notebook and i went in to my network neighborhood and clicked on the work group name. when i do this on my other computers it pops up a user name and password box where i can type in the name and password. this does not happen on my notebook computer. hope this helps. kinda stinks having to go right on my server i have a AMD chip and it hates the video card so everything is so big it is almost not worth using other then the three raid drives. (no idea why nvida and ubuntu can not co exist) any way.
here.
```

sudo apt-get install samba
sudo nano /etc/samba/smb.conf

```change 
WORKGROUP to your workgroup.
Change 
```

# security = user
```to ```

security = share

```

You can also transfer files through FTP.
to install an ftp client, run
```

sudo apt-get install pure-ftpd
```You can then use a FTP client such as filezilla on your main machine to access the server.

Note that you will have to create a seperate user, and login as it when using FTP.

---

### Post by Mtrboat01 on 2010-09-22
i would not know about the log in window where you put in the user name and enter a password. it never gets that far it makes this windows default sound for you have done something wrong and then the message pops up you need permission to even get to a log in prompt. (i miss my ubuntu8.4)

---

