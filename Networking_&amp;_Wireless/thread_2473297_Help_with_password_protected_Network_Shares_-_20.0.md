---
title: "Help with password protected Network Shares - 20.04 LTS"
date: 2022-03-31
forum: Networking &amp; Wireless
---

### Post by msb101 on 2022-03-31
Hello,
I have installed Ubuntu 20.04 LTS and would like to create several folders with their own username/passwords to be used by different people at home.

I created the folders, right clicked on them and went through the process of installing Samba and sharing the folder. I am able to access the folder through Windows when I check the option to Allow Guest Access. If I uncheck this, I cannnot access it even when using my admin username and password.

I have scanned through various posts on the forum but cannot find a solution thats working for me.

I would be very grateful if someone can tell me how to assign a username and password to a shared folder that requires the person accessing it from another computer to use this username/password.

Thanks in advance.

---

### Post by Andrew_Welham on 2022-03-31
what do the samba logs say ? smb.log and nmb.com
if you do a tail -f filename and watch the entries they should give you a good idea

---

### Post by msb101 on 2022-03-31
> **Andrew_Welham said:**
> what do the samba logs say ? smb.log and nmb.com
if you do a tail -f filename and watch the entries they should give you a good idea

Thank you for your quick reply. I'm kind of new to ubuntu/linux and not sure how to do this. Could you please elaborate and let me know what to look for?

---

### Post by Andrew_Welham on 2022-03-31
type
cd /var/log/samba

The log files should be there
type
ls -als
This should list the files and the last data changed

look at  the files which have most recently changed and type

tail -f   then the file name

access the share and see what shows

---

### Post by Morbius1 on 2022-04-01
> **msb101 said:**
> Hello,
I created the folders, right clicked on them and went through the process of installing Samba and sharing the folder. I am able to access the folder through Windows when I check the option to Allow Guest Access. If I uncheck this, **[COLOR="#0000FF"]I cannnot access it even when using my admin username and password[/COLOR]**.

There is one thing missing from your description of what you did. You never stated if you added your user name to the samba password database.

```
sudo smbpasswd -a morbius
```
*[COLOR="#FF0000"]Change morbius to your Linux user name.[/COLOR]*

---

### Post by ngumuntu on 2022-04-01
Hi msb101,

This may help.[URL="https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs"]

[https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs](https://wiki.samba.org/index.php/Setting_up_a_Share_Using_Windows_ACLs)
[/URL]
Try leaving *Allow Guests *checked on the Ubuntu shared folder and then set the folder permissions from one of the windows computers.

---

