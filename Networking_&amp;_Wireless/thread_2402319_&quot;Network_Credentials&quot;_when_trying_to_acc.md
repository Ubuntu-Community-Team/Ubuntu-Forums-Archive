---
title: "&quot;Network Credentials&quot; when trying to access Ubu share from Windows?"
date: 2018-09-28
forum: Networking &amp; Wireless
---

### Post by Mugsy323 on 2018-09-28
I'm trying to access a shared folder on a computer running Ubu 18.04.1 LTS from a tablet running Win10.

I found the folder on the network, but when I try to access it, I'm prompted for "Network Credentials". Two fields, one of which is pre-populated with my Linux username.

The only thing I could find on the subject is [this 9 year old post]("https://ubuntuforums.org/showthread.php?t=1201809") that reached no answer.

I tried entering my Linux username & password, but that didn't work. What "Network Credentials" is it referring to? TIA

---

### Post by TheFu on 2018-09-28
Ooops - for some reason, I had this backwards. No good excuse.  

The credentials for the ubuntu login that has allowed sharing.

If you think about it, there's no way a Windows machine would get Linux credentials unless you setup that (which is a non-trivial thing) so the same accounts were made available for the entire network (usually via LDAP or AD).  The pre-filled information is handled from the Windows side.  The pre-filled info is a guess and might be wrong.

For example, I use different logins for Unix and Windows.  "thefu" is my Unix/Linux login, but on Windows I use my first name, "the".  From Windows, the pre-filled credentials has "the" which won't work for the Linux authentication.

If you search for "samba" and "windows10" in these forums, you might find some other aspects for making the connections. 

I see Morbius is here. Do what he says.

---

### Post by Morbius1 on 2018-09-28
Did you do what the link said to do?

If your share requires credentials and you are accessing it with your Linux user name you need to add that user name to the samba password database:
```
sudo smbpasswd -a mugsy323
```

---

### Post by Mugsy323 on 2018-09-28
> **Morbius1 said:**
> Did you do what the link said to do?

No. I'm not using Samba (AFAIK.)

---

### Post by Morbius1 on 2018-09-28
Fair enough. So what are you using to create the "share"?

Let me ask this another way. Run these commands:
```
testparm -s
```
```
net usershare info --long
```
If you get output from either or both of those you are using Samba.

---

### Post by Mugsy323 on 2018-09-28
Thanks for the reply.

All I did was right-click the folder from the File browser and clicked "Local Network Share", which auto-installed the necessary networking apps.

It appears "Samba" is part of Ubu now and I do have it. So I tried "smbpasswd" and it worked (setting the password for my network connection.) Since I enabled "Others can make changes to this folder", I wasn't prompted for a password this time. Windows simply opened the folder.

Thanks.

---

