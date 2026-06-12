---
title: "Securing Home Folder"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by pradeepbp on 2010-01-16
I am using Ubuntu 9.10.
I can see that no other user can access folders in my home directory when logged in from their own accounts. But when I pop in another live linux distro and mount the disk, files in my home folder is easily accessible without authorisation.So how would I secure those files from unauthorised access?

---

### Post by Paqman on 2010-01-16
You could chmod the files to 600 but you'll b0rk your home folder if apply it across the whole folder, so use with caution. Realistically if someone has physical access to your machine, they can access any data you have on it, no matter what steps you take to obscure it. 

About the most effective measure would be encryption. You can set up an encrypted private directory in your home folder really easily, or you could go as far as encrypting the whole of /home, or even your whole disk.

---

### Post by pradeepbp on 2010-01-16
Well, Thanks for the reply. I guess encrypted folder is the best solution for me. I googled it and found out the way to do it. And for the benefit of others who want to know how to create encrypted directories, here is the link [https://help.ubuntu.com/community/EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory")

---

### Post by Darce on 2010-01-16
When installing Karmic, you have the option to encrypt your home folder. That way it is auto mounted when you log in.

---

### Post by HermanAB on 2010-01-16
Howdy,

You can encrypt it after the fact if you have some idea of what yu are doing.  See this guide and wizards for some ideas: [http://www.aeronetworks.ca/luks-usb-howto.html](http://www.aeronetworks.ca/luks-usb-howto.html)

---

