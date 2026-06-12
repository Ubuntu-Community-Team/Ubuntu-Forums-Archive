---
title: "Need help with samba and private directories"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by hatchek on 2007-10-16
What I have is a single server computer running ubuntu, responsible for giving windows machines IP addresses.

The windows machines are lab computers but there is only a guest account. Many users will use these machines and I want to create a safe place on the server for the individual users to store their files with samba.

So what I want is that if I am user hatchek, I can view the shares (from windows \\polaris) but if I try to access any of those shares, the server would prompt me for a username and a password, where the username is the name of the share and the password is whatever. This username/password combo would only allow the user to access the associated share.

How would I go about this? (Note: I don't want to use home directories, as I don't want people to be able to use the accounts on the server computer)

I'm thinking something like,
Create a linux user
add this user to samba (smbpasswd)
edit the samba config
restart samba

---

