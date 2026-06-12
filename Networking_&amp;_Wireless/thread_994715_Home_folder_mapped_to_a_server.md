---
title: "Home folder mapped to a server"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by namdung on 2008-11-27
We're planning to migrate all computers in our school to Ubuntu from XP. We currently have Roaming profile and folder redirection in our Windows environment. This way the teachers and the students are able to access their files from any PC as their work is saved in the server.

I'm looking for a similar solution where the home folder for all users are automatically mapped to a centralized Samba/NFS Server from Ubuntu.

We are able to logon using Windows credentials via Likewise-open. As we have different policies set for teachers and students, can the policies adopted in MS AD be applied when logged to a Linux PC? If not is there another alternative where user policies are defined centrally in a server?

Looking forward to a positive response.

---

### Post by sammy_pal on 2008-11-27
This may be of help to you.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by namdung on 2008-11-29
> **sammy_pal said:**
> This may be of help to you.
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

Thanks for the reply. We've actually already deployed LTSP with Ubuntu server and about 13 thin clients.

The solution I was looking for is for individual PCs with the home folder of all users saved in a centralized server.

Any help?

---

### Post by sammy_pal on 2008-11-29
For allowing logging in from any machine, and enforcing different policies for different users you need to setup a NIS server, and for allowing centralised file sharing for the users, you have to set up a NFS server. The following HowTos may be useful:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)
[http://tldp.org/HOWTO/NIS-HOWTO/index.html](http://tldp.org/HOWTO/NIS-HOWTO/index.html)

---

### Post by namdung on 2008-12-16
Will iFolder suffice my needs? Users should be able to sit in any PC and their work folders to be synced with a centralized server. The authentication used is AD.

---

### Post by namdung on 2009-04-02
NFS has done the trick. Thanks all.

---

