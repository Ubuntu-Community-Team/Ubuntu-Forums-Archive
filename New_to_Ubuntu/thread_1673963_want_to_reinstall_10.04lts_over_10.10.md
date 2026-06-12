---
title: "want to reinstall 10.04lts over 10.10"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by navidson on 2011-01-23
i am currently running the new version of ubuntu 10.10. things were fine with 10.04. now skype and internet don't run properly. i have a dual boot with windows xp but i really enjoy linux when it runs properly. how would i go about putting 10.04 LTS back on? thanks.

---

### Post by yopnono on 2011-01-23
> **navidson said:**
> i am currently running the new version of ubuntu 10.10. things were fine with 10.04. now skype and internet don't run properly. i have a dual boot with windows xp but i really enjoy linux when it runs properly. how would i go about putting 10.04 LTS back on? thanks.

Reinstall the "/" partition = root filesystem/base system
But keep the "/Home" partition = all your personal settings

---

### Post by TBABill on 2011-01-23
What you'll need to know during the install is which partition your ext4 partition is that has Ubuntu on it. When you get to the point where you decide WHERE to install the system, just check the option to do so manually. The screen that comes up will list your partitions. The first few will probably be Windows partitions (NTFS?) and then you should see your Ubuntu partitions (ext4 and swap). Just highlight the one with ext4 and click change or edit....can't remember which it says. It will take you to another screen where you set the size (you probably just want to leave it the same size) and you select the mount point. For the OS you want to choose "/" which is root. If you created a /home partition then that should care for itself and not need changed. If you did not, then doing it the way I mentioned will install the entire OS with home directory to one partition. I assume as a new user that is how you have it already and you can search the forum if you need instructions to create a new partition for /home and reinstall 10.04 to /. It's not difficult, just a bit more in depth than your question. 

You'll also choose to format that partition during the process. It's just a checked box, then install as you did before. Make sure you do NOT choose any Windows (non ext4) partition to protect your data. And DO backup your files (my docs probably) from your Windows partition just in case.

---

### Post by navidson on 2011-01-23
thanks so much i will try it out and see how it works and if so i'll mark it solved. thanks again for taking the time to help.

---

