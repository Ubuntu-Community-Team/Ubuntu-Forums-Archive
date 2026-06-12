---
title: "Setting up a Linux Workgroup"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by jamescox84 on 2008-08-10
Hi there,
I was wondering if anyone knows of any nice tutorials or info about how to setup a workgroup like network using Linux. 

What I'm looking for is to set up a server that handles authentication of users, and host the users home directories.

Then to configure workstations to log into the server using the authentication on the server and to mount the users home directory.

This is the setup I'm used to at work, using Windows 2003 Server and Windows XP Pro workstations. It might be though, that there is a far better setup for Linux that is not a direct analogue of this model. Ether way, any pointers would be appreciated.

Many Thanks,
  James

---

### Post by dkronst on 2008-08-10
hi,

If I understand your question correctly, you are looking for an analogue for an "Active Directory" in windows, with a Network Share.
The old way to do it is to use NIS/NIS+ for the authentication and NFS for the home-directories.
Depending on the size of your network, you would probably want to use autofs to automatically mount your users home-directories.

NIS howto:
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

AutoFS howto:
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

You can also follow the NFSServer howto from there.
You are probably looking for an NFS-AutoFS-NIS setup which is quite standard in Linux.

The "new" way is using LDAP for the user database but it's a little more complicated if you don't know LDAP (or simpler if you do :)


Hope this helps..

---

### Post by jamescox84 on 2008-08-10
Thanks for the info, I will look into these technologies and see if I cant get a simple server workstation setup. I would be itersting to see how you go about using LDAP. Is LDAP a *better* way of authenticating users?

---

### Post by dkronst on 2008-08-12
NIS is better in specific use cases, LDAP, however, is the standard solution for larger organization. 
I guess if you need the network authentication to be very secure and scalable you'd want LDAP authentication and not NIS.
NIS is less secure and doesn't have all the authentication features that LDAP has but is easier to install (both client and server), at least in my experience.

---

