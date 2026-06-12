---
title: "Ftp"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by illy123 on 2010-02-23
I've found several guides for installing the software but haven't been able to find much on using it. 

At the moment I created an unprivileged account (called him ftpuser) and use that to log into my ftp site. I use the sudo nautilus command to navigate and copy over the files to ftpuser's home folder and then change the permission so that group and owner is ftpuser (or upload them directly from my windows pc via filezilla).

I would like to share this with a few friends (hence why I created a second account) - however, if I have got VNC, SSH running, can that second account be used to connect to them? Also, I don't want my friends being able to delete files (in case they make a mistake). Would creating a 'virtual account' be possible for a newbie or will it involved a lot of mysql manipulation?

The reason why I don't want to enable anon access is that I have a feeling it might drain my home broadband connection.

---

### Post by illy123 on 2010-02-23
Wow this got off the frontpage quite quickly.

---

### Post by stlsaint on 2010-02-23
mysql? can you explain why you would need mysql? just setup ssh with a very strong password for each user. and create groups and edit the permissions for those groups of what each user can do.

---

### Post by illy123 on 2010-02-24
> **stlsaint said:**
> mysql? can you explain why you would need mysql? just setup ssh with a very strong password for each user. and create groups and edit the permissions for those groups of what each user can do.

I saw a post on a linux blog that virtual accounts can be created to access the ftp site rather than local user accounts. :confused:

At the moment I have got openssh setup to only allow my account (I don't want the ftp account to have ssh or vnc access) and I have given it a strong 20char password and forwarded it on my router (incomming 443 going to listening 1232. I have VNC running so that I can access it remotely by tunneling it through the SSH.

However I'm sure of how to configure FTP. When you mention SSH are you suggesting using SFTP?

Ideally I would like to have full access to the ftp and create an account that can only view one folder and upload to another - I guess I could accomplish this by chmod-ing the main folder as 775 and create an upload folder with 777?

Thanks again for your help

---

### Post by illy123 on 2010-02-24
I would really appreciate some help on this: create an account just to view ftp (no vnc, ssh, access etc) and have my main account possess full read and write.

Also would SSL be necessary to stop people sniffing out the passwords?

---

### Post by illy123 on 2010-02-24
How does this idea sound:

Configure vsftpd's settings so that only a local user can read it - then I can use my ssh connection to connect via sftp and upload files and then access them through the 'read' only account.

My only concern with this - would the ftp user be able to use services such as vnc, ssh (though I've specified in the openssh config that I'm the only user who has access to it)? I wouldn't want to give out this account to people if it comprises my security.

I will read up if there is a way to do this with chmod 775 for read only and 777 for a folder than they can upload to.

---

