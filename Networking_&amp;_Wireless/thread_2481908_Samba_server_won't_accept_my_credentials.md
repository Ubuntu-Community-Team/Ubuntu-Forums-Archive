---
title: "Samba server won't accept my credentials"
date: 2022-12-12
forum: Networking &amp; Wireless
---

### Post by halfbeing on 2022-12-12
I have tried to configure Samba to share my home folder, and I have Unix password sync enabled in my smb.conf. However, when I try to connect to from my iPad or my Mac (using the same name and password that I use when I sudo a command on the Ubuntu machine) I get told that the username or password is invalid. And when I try to connect from my Samsung phone, I see a folder called "homes" , but when I press it, I get the message "Unknown error: vfs.provider.smbj/wrong-share-name". 

I should probably also say that when I try to connect anonymously from my iPad, I see two directories, neither of which I can enter. One is called "homes", and the other is called "blah". "blah" is the kind of name that I give files when I am trying to solve problems involving how files are handled, such as getting file sharing working. So, I must have been banging my head against a wall in the past trying to get Samba working on this computer, although I can't remember doing so. What perplexes me is that I have no idea where "blah"  is stored on my file system, and I see nothing in smb.conf that corresponds to it. The only shares I have that are uncommented in smb.conf are the user home folders.

So, I have three questions:
1. How can I get SMB sharing working?
2. Why do I see this mysterious "blah" directory, and what does it tell me about whey Samba isn't working?
3. Why is setting up Windows file sharing in Ubuntu *still* so ridiculously hard?

I should also say that I do remember to run "systemctl restart smbd" every time I edit smb.conf

---

### Post by Morbius1 on 2022-12-13
Questions:

[LIST]
[*]What version of Ubuntu are you using?
[/LIST]
[LIST]
[*]What is the output of this command:
[/LIST]
```
testparm -s
```
[LIST]
[*]What is the output of this command:
[/LIST]
```
net usershare info --long
```

Observation: What seems to be missing from your description is the setting of the samba password for your user. Did you do the following:
```
sudo smbpasswd -a  halfbeing
```

---

### Post by TheFu on 2022-12-13
Just a wild guess, but did you setup the Samba userid using 'smbpasswd -a' ?  Sometimes I forget that's needed.

---

