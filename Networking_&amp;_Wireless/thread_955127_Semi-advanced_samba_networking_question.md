---
title: "Semi-advanced samba networking question"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by haydnc on 2008-10-21
I am trying to figure out if there is a nice middle-ground between security and ease of use when setting up a Windows/Ubuntu network.

Specifically, I have discovered in the past that the easiest way to set things up so that windows machines can see and access files on the network is by modifying the smb.conf file during your 'network setup' process so that it uses *security = share* instead of *security = user*. 

It is very convenient to be able to control what is visible and what isn't by simply changing the permissions on a given file, however I have seen it said in more places than I can count that this method severely compromises the security of the network setup.

My problem is that I don't want to have to set up user accounts on each Ubuntu machine for any/all of the users of whatever windows machines might need access on my network. It is time consuming and inconvenient, particularly if the Ubuntu machine in question is acting as a file server of some kind and could have anywhere from 1 to 200 users wanting to access files on it.

I could maybe deal with needing to set up 1 user account for access, but not a shifting population of 200 (as an example number).

At the same time I don't really want to set up one 'network access' account that windows users could use to access the shared files. Mostly this is because I don't want the remote users to have to remember an additional password beyond their own.

Is there some way to set things up similar to (dare I admit it) Windows server 2003 (or any windows box for that matter) where people accessing a share remotely using \\share-on-ubuntu-box\ would be able to see all shared folders but they'd only be able to get into the 'open' ones (as if network security was set up security = share and permissions were set to 755). 

For any of the other visible folders they'd have to put in an authorized user name and password - which might be their own, or it might be the previously mentioned 'network-user user name and password'. Essentially this would mean that I could put 'general access' files into the open share, and put administrator access files into the password locked share for when I needed to access them remotely on the network.

If anyone has any suggestions or help and could let me know, or even point me at some useful reading online I'd appreciate it.

---

### Post by dmizer on 2008-10-22
Obviously, my word is not the end all and be all of samba configuration, but I would highly suggest just biting the bullet and inputing the 200+ user accounts.

Ease of use is subjective. Avoiding the use of accounts on your server may give you less headache during setup, but it will give you more headache down the line because your 200+ users will be scratching their heads in frustration over the hows and whys of your server configuration.

It will be more time consuming and inconvenient to train each and every one of those 200+ users, not to mention the time and inconvenience involved with giving support later when they don't fully understand ("I can see it, why can't I open it?!"). Saving work during initial setup does not mean less work for you overall. Entering user accounts really is the easiest way both for security and for client use.

It's also way easier to control access across shares by creating groups than it is by changing individual file or folder permissions.
```
valid users=@groupname
```

In my sig, I've linked the thread I found most helpful in learning how a samba server works. I have also made extensive use of this: [http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by haydnc on 2008-10-22
Thanks dmizer, I had a feeling that might be the case. I was just hoping for the 'easier way'.

I'll have a look through the link you've provided, but if you could just confirm a couple of things for me:

1. The user accounts on the Ubuntu machine don't need home drives set up.

2. The user accounts set up need to match the windows usernames (obviously) but do user passwords need to match the windows user passwords or can they be set up blank?

---

### Post by dmizer on 2008-10-22
Generally speaking, security often sacrifices perceived "usability" concerns.

> **haydnc said:**
> 1. The user accounts on the Ubuntu machine don't need home drives set up.
This shouldn't make any difference.

> **haydnc said:**
> 2. The user accounts set up need to match the windows usernames (obviously) but do user passwords need to match the windows user passwords or can they be set up blank?
Both usernames and passwords should be identical, otherwise the mount will not be transparent.

You *can* get around this in Windows by mapping the drive (right click "My Computer" > "Map network drive ...") and using the "Connect using a different username" option, but this means you would have to hand configure the Windows machine in question.

---

