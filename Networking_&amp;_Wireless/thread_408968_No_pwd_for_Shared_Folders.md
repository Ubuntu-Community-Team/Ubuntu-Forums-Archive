---
title: "No pwd for Shared Folders"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by mevets on 2007-04-14
I setup shared folders under System > Admin on my Fiesty install. I was then prompted to install the necessay services and did. I can now see both my ubuntu and windows system on my network. My problem is that when I try to connect to either one, no password seems to work. I tried the machines pwd, the users pwd, and no pwd. None of them work. Is there a default I don't know of or is there an additional step I'm skipping?

What has gone wrong?

---

### Post by amohanty on 2007-04-14
I believe (I am not a 100% sure) that the Shared Folders app uses samba behind the scenes. Take a look at /etc/samba/smb.conf If the folders you specifed are there then that is the case. If so you will need to use the smbpasswd utility to setup username and passwords for the shared drives. Or you can open them up for general access, which is not a good ides if you use wireless and WPE. 

HTH
AM

---

### Post by mevets on 2007-04-14
I took a look at that file. I didnt really know what to look for and nothing stood out. At the very bottom was:
```

[steve]
path = /home/steve
available = yes
browsable = yes
public = yes
writable = no

```
No mention of needing a password there. So I  added a password field, but it didnt work.

---

### Post by amohanty on 2007-04-15
Is your home folder something you shared?

If so:
Setting up samba properly can get to be a bit of a hassle. I would suggest reading these first:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Then, if you have a specific question post back.

HTH
AM

---

### Post by LosD on 2007-04-17
You don't need all those pages, it's quite easy, here you go:

(From the description of your problem, I guess you already installed the sharing).

open a shell, and type
```

sudo smbpassword -a TheUserNameYouWantToUse

```

Then you just enter the password for the new user (remember that sudo probably asks for a password first).

If you need to access a particular user's private folders, or write to a folder, the user name should be the same as the owner's (I THINK that Samba does the needed user name mapping for that by default, not 100% sure, though).

After that, you should be able to log in with the same username/password in Windows.

Good luck,
   Dennis

PS: The reason that Samba can't just use you normal password, is that Windows and Linux encrypts them differently, so Samba wont be able to check if they are the same.

---

### Post by amohanty on 2007-04-18
> You don't need all those pages, it's quite easy, here you go:

(From the description of your problem, I guess you already installed the sharing).


That is definitely the solution, however personally I would prefer if the user know what they were doing instead of just doing something without fully understanding it. IMO saves a lot of pain later :)

Just my 0.2.

AM

---

### Post by norton1 on 2007-04-18
[QUOTE=LosD;2467112]

open a shell, and type
```

sudo smbpassword -a TheUserNameYouWantToUse

```

-just a note, you need to write

```

sudo smbpasswd -a UserName

```

but thanks - i can know access both computers from each other - yay

---

