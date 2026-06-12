---
title: "printer sharing"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by tarclee on 2006-08-28
my local printer can function but network user can't use my printer.i am using samsung scx-4100,the driver is successfuly install on each pc,just cant print it.can anyone teach me step by step how to make the printer sharing?

---

### Post by funchords on 2006-08-28
Sharing your printer and sharing your file/folder/directory over the network are closely related topics.  They all rely on a service called Samba.

[http://www.ubuntuforums.org/showthread.php?t=202605]("http://www.ubuntuforums.org/showthread.php?t=202605")

Here is one step-by-step (there are several).  There are also links of interest at the bottom.

---

### Post by tarclee on 2006-08-28
all my pc is using ubuntu.can u teach me how to make the printer sharing?the printer connect to usb port to the pc.

---

### Post by funchords on 2006-08-29
As I said, printer sharing is a function of Samba.  You need to install and configure Samba.  

Once Samba is installed on your Ubuntu computer, you will be able to share your printer with other computers.

Follow [those]("http://www.ubuntuforums.org/showthread.php?t=202605") steps.  If you get stuck or have a question, then feel free to ask.

---

### Post by tarclee on 2006-08-29
i have success share the printer within ubuntu pc,but i got 2 windows pc still cant use the printer,it ask me the username n password,what can i do?

---

### Post by Iowan on 2006-08-29
Have you added the Windows users and passwords to Samba?
Can you share files, but not the printer?

---

### Post by tarclee on 2006-08-29
not yet,is it call add samba user?how to add windows users n passwords to samba?is it need do it root enviroment?how to change it?all the ubuntu pc can c the file in windows pc,but windows cant get into ubuntu pc,it ask username n password.what can i do?i have type below command:
sudo smbpasswd -a username
but it fail,it say the username i add already exist in unix system,i have try few username also fail.i did it in user environment.pls help.

---

### Post by funchords on 2006-08-29
> **tarclee said:**
> i have type below command:
sudo smbpasswd -a username
but it fail,it say the username i add already exist in unix system,

Is this what you're getting?

```
robb@TOPOL016:~$ **sudo smbpasswd -L -a someuser**
New SMB password:
Retype new SMB password:
Failed to initialise SAM_ACCOUNT for user someuser. Does this user exist in the UNIX password database ?
Failed to modify password entry for user someuser

```

If so, then you need to create a unix account for that user.  

```
robb@TOPOL016:~$ **sudo useradd -s /bin/false someuser**
robb@TOPOL016:~$ **sudo smbpasswd -L -a someuser**
New SMB password:
Retype new SMB password:
Added user someuser.
robb@TOPOL016:~$ **sudo smbpasswd -L -e someuser**
Enabled user someuser.
```

That should do it.

---

