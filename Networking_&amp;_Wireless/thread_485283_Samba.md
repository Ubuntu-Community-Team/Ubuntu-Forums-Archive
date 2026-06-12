---
title: "Samba"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by chiefbutz on 2007-06-26
I am running Ubuntu 7.04 and I am trying to access some Windows Shares on another computer. I used to be able to get them, and now, after changing the workgroup they are on to the same as my Ubuntu computer, I can't see them or access them. Does anyone have any ideas?

---

### Post by Sonofmoog on 2007-06-26
> **chiefbutz said:**
> Does anyone have any ideas?

Reboot the Winbox ..

---

### Post by chiefbutz on 2007-06-26
> **Sonofmoog said:**
> Reboot the Winbox ..

Done that

---

### Post by Sonofmoog on 2007-06-26
Step Two:  Can you access the Ubuntu shares from the Windows box, and are all PC's in the net in the same workgroup?

---

### Post by chiefbutz on 2007-06-26
Yes, the windows computers (i have more than one setup) can see the other windows computers, and can access them along with the ubuntu shares. There are PCs in the same workgroup as the Ubuntu computer, and ones in a different workgroup

---

### Post by Austin_KW on 2007-06-26
Check your windows firewall. Often it starts blocking connections when configurations change.

---

### Post by chiefbutz on 2007-06-26
I checked it, that isn't it. For some reason Ubuntu isn't even able to access the shares on my Ubuntu Server.

---

### Post by doogy2004 on 2007-06-26
I am also having a similar problem and i have found that the version of samba in fiesty is not working properly according to my research.  hopefully samba will be updated in the repo to fix this.

---

### Post by chiefbutz on 2007-06-26
> **doogy2004 said:**
> I am also having a similar problem and i have found that the version of samba in fiesty is not working properly according to my research.  hopefully samba will be updated in the repo to fix this.

Yeah, hopefully. It must be something with detecting all of the computers on the network because I don't see anything under "Network"

---

### Post by ike on 2007-06-27
> **chiefbutz said:**
> Yeah, hopefully. It must be something with detecting all of the computers on the network because I don't see anything under "Network"

I am having the exact same problem trying to connect to a Debian Samba server. It worked for me 2 days ago, but now it only gives me an error message (in swedish, saying that the contents of the folder could not be shown).

I can, however, from my ubuntu laptop, list the shares on the samba server with the command:
```
smbclient -L hostname
```

I have tried to mount the share with the command:
```
sudo mount -t smbfs -o username=me,password=mysecret //server/share /media/share
```
but it also gives me an error. dmesg says:
> [11815.660000] smbfs: mount_data version 1919251317 is not supported

Does anybody have a solution to this, even temporary?

---

### Post by chiefbutz on 2007-06-27
> **ike said:**
> I am having the exact same problem trying to connect to a Debian Samba server. It worked for me 2 days ago, but now it only gives me an error message (in swedish, saying that the contents of the folder could not be shown).

I can, however, from my ubuntu laptop, list the shares on the samba server with the command:
```
smbclient -L hostname
```

I have tried to mount the share with the command:
```
sudo mount -t smbfs -o username=me,password=mysecret //server/share /media/share
```
but it also gives me an error. dmesg says:


Does anybody have a solution to this, even temporary?

I just tried all of that, it didn't even work... I think I might try reinstalling the samba client, I will post back after work, if anyone has any ideas please post them

---

### Post by ike on 2007-06-27
After installing the smbfs package everything just work! So, to those of you who are having this problem, try installing smbfs package and let us know if that helped you as well.

```
sudo apt-get install smbfs
```

---

### Post by chiefbutz on 2007-06-27
That was already installed.

I just did something, and it worked. I tried to access it by its IP, and it worked, so it leads me to believe that it has to do with the changing of host names to IPs

---

