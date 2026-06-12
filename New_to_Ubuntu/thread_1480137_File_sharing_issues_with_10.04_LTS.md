---
title: "File sharing issues with 10.04 LTS:"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by lazzzlo on 2010-05-11
File sharing issues with 10.04 LTS:

I seem to be missing some packages to help me "share files over the network".  I can do it via Bluetooth but that appears to be it.  The area I am looking for is grayed out.

I'm still a newbie w/ Ubuntu.  Rather than upgrading, I opted to install 10.04 LTS as a clean install on my networked Linux box.  Everything went perfect.  I can see my Windows box and the Windows box can see my Ubuntu box.  I have Samba but I can't talk to the 2.

I updated the repositories but I think there are some packages that I still have to install.  I'm not sure which ones.  The way I would look at this in Windows would be a file and print sharing issue.  

I have tried to use a separate user but that shouldn't be necessary.

What packages am I missing?

edit:  is there a sudo command that I need to use?


Any help would be greatly appreciated.


lazzzlo

---

### Post by jd65pl on 2010-05-11
There is a lot of documentation on this around take a look [here]("https://help.ubuntu.com/community/SettingUpSamba").

---

### Post by lazzzlo on 2010-05-11
I have Samba plus your bottom links all produce 404 errors.

Let me rephrase:  I would like to add or know how to search for the proper packages that will enable my install of 10.04 to be able to complete a network sharing package of multiple computers with different operating systems.

---

### Post by jd65pl on 2010-05-11
Windows file sharing -> [Samba]("https://help.ubuntu.com/community/SettingUpSamba")
Mac OS X file sharing -> afp [netatalk]("https://help.ubuntu.com/community/AppleTalk")
Unix file sharing -> [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

Each of those documents give you instructions on how to set up both the client and the server. I've removed the links thanks.

---

