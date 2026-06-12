---
title: "better way of sharing files then chmod 777?"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by shortridge11 on 2008-12-03
I have a home server and i let my roommates share files on it and access and modify/create files on it.  However, this is very unsafe and i'd like to stop doing that.  I think i tried doing the samba thing where you have to log in with a usr/pass but i encountered problems.  Also, that may not even be possible and i might have been doing something completely different.  Anyways whenever i want my files to be shared i just 
sudo chmod -R 777 /media/
and then everyone can see/modify/create who's in my network.  Is there a safer way to share my files, or a better command that would be a little more secure?

Thanks

---

### Post by davidbilla on 2008-12-03
Do you want your files to be editable by others over the network or not?

If you do, then chmod 777 is the right way. If you want to prevent others from deleting your files, you can do 'chown' on that file and make 'root' as the owner of the file.

If you don't want others to be able to edit your files, then just give r/x permissions. chmod 755.

---

### Post by Titan8990 on 2008-12-03
I would just create a group for the people you need to share files with. Change the ownership of the folders you want to share to that group.

---

### Post by hyper_ch on 2008-12-03
have a look at MySecureShell... you can setup system accounts and set them to use that shell
then you can give them access to one specific location and you can force permissions and ownership there

---

### Post by binbash on 2008-12-03
I am using ftp server for similar purposes.Also check  Titan8990's comment

---

### Post by shortridge11 on 2008-12-03
right now the people who have access to these files have windows and are not good with computers.  Needless to say they probably couldn't handle more then - try to access the folders, if a box comes up type this usr/pass in. 
And what is MySecureShell?

also, if i created a group for them, how would i let them log into that group from a windows machine.  Does samba take care of that if i set it up? As in does it give you a box to type usr/pass and log you on to that group?

---

### Post by hyper_ch on 2008-12-03
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

[http://www.howtoforge.com/mysecureshell_sftp_debian_etch](http://www.howtoforge.com/mysecureshell_sftp_debian_etch)

---

### Post by shortridge11 on 2008-12-03
mysecureshell seems very cool, but can un-savy windows users benefit from using it? my other primary use will be through older modded xboxs that i use for media streamers.  I'm fairly certain they can use sftp, and that shouldn't be a problem

---

### Post by hyper_ch on 2008-12-03
well, they will need to get winscp:  [http://www.winscp.com](http://www.winscp.com) (free and open source) and it will be like a 2-pane ftp program.... they can also use other ftp programs the support sftp.... basically you need to know the (a) hostaddress (b) username (c) password

---

### Post by Titan8990 on 2008-12-03
I just use scp at my home but I don't have to worry about other users accessing it.

You could control access via group permissions as I mentioned earlier and your users could use winSCP which shouldn't be difficult, even for a windows user since it is very similar to an FTP client.


You have tons of options.

---

### Post by shortridge11 on 2008-12-03
awesome.  Thanks a lot, i'll get started immediately and let you know if i have any problems implementing this

---

