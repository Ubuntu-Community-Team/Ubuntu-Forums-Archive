---
title: "Sharing an executable file"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by japhyr on 2011-01-13
Hello,

I have Ubuntu 10.04 Desktop edition running on one computer, and I want to share an executable file with other Ubuntu 10.04 computers.

The executable file is in a directory on an ext4 partition.  I clicked Sharing Options, installed necessary software, and enabled sharing. I can open the file on other computers, but when I look at permissions I get the message "The permissions of 'filename.sh' could not be determined."

Is there a way to make shared files executable?  Google is  getting me lost with posts about servers and Windows shares,  etc.

---

### Post by Kirboosy on 2011-01-13
From what I'm understanding you should just be able to run this command on the host computer in the terminal and fix your problems...

```
sudo chmod 777 'thefileyouwanttochange'
```Hope that helps.

Wow I'm so sorry! My Browser crashed and must of kept hitting the server with posts!

---

### Post by Kirboosy on 2011-01-13
deleted!

---

### Post by Kirboosy on 2011-01-13
deleted!

---

### Post by Kirboosy on 2011-01-13
deleted! again

---

### Post by Kirboosy on 2011-01-13
deleted!.

---

### Post by Kirboosy on 2011-01-13
deleted! i feel like such a retard...

---

### Post by Kirboosy on 2011-01-13
deleted! Sorry

---

### Post by japhyr on 2011-01-13
I tried this, and I don't see any different results.  I can access the file on the second computer, but permissions are unknown on the second computer.  Permissions are -rwxrwxrwx on the host computer.

Is there something simple I am doing wrong?  Is there a setting on the client computer that allows files on network shares to be executable, or a samba setting on the host computer that sends permissions to the client computers?

---

### Post by Kirboosy on 2011-01-13
> **japhyr said:**
> I tried this, and I don't see any different results.  I can access the file on the second computer, but permissions are unknown on the second computer.  Permissions are -rwxrwxrwx on the host computer.

Is there something simple I am doing wrong?  Is there a setting on the client computer that allows files on network shares to be executable, or a samba setting on the host computer that sends permissions to the client computers?

Try installing the package "system-config-samba" It will give you a GUI so you know exactly what your settings are.

Or you can check your current samba config by looking at /etc/samba/smb.conf
```
sudo gedit /etc/samba/smb.conf
```Possible config
```
[japhyrdocs] 
path = /home/japhyr/Documents
read only = [FONT=Verdana]no[/FONT]
write list = user1 user2 '(If you don't want everyone to have the same permissions)
'writeable = yes 'if you want everyone to write to it
```

---

### Post by japhyr on 2011-01-14
I am fairly comfortable with configuration files, but I installed system-config-samba as well.  To make this simple, I granted everyone access to this file, set it executable by everyone, and gave read/write access to everyone.

When I access the share on the client computer, I still  get "unknown" for permissions.  This seems to me that the client is seeing the shared directory, but is unable to access the permissions for some reason.  There are windows computers on this network, but the shared file  is on an ext4 partition.

The relevant part of smb.conf is:```
[shared_directory]
  path = /home/path_to_dir/shared_directory
  writeable = yes
  guest ok = yes
```

Should those settings let the client computer see the file's permissions?

---

### Post by Kirboosy on 2011-01-14
I would think it should work. I don't know why it wouldn't. I don't have any files being shared right  now because I'm the only computer on the network so I can't anything.

---

### Post by japhyr on 2011-01-14
Thanks. If nobody replies to this I'll ask again in Programming Talk.

---

