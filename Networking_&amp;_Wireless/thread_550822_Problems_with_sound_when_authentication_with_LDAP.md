---
title: "Problems with sound when authentication with LDAP"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by uris on 2007-09-14
This is the first network I am setting up using LDAP. All my users are successfully authenticating using LDAP over the network, however, those users can not access their usb drives nor is the sound card working when they log in. I reckon there must be some problem having to do with mapping users/groups in the server with those in the client, but I don't know how to do this. Can anyone plssssssssssssssssss help?

---

### Post by noob12 on 2007-09-14
Your guess might be right.  You should make the numeric UIDs of users and GID values of groups that appear in local /etc/passwd and /etc/groups files the same as those that appear in LDAP.  Many sites will remove the entries for regular users from the local files to avoid having to maintain them at all, but note that this means that user can't login if the LDAP service is down or unreachable.

Then you need to use **chown** to set all of their files to be owned by the right numeric UIDs and  GIDs (the ones from your LDAP).

---

### Post by uris on 2007-09-14
That would mean that I have to create the same users in all the clients? In my case, there are about 20 usernames and over a dozen computers. It kinda defeats the purpose of having a centralized authentication server.

---

### Post by noob12 on 2007-09-14
No.  It means that if you have any of those users listed locally in the client files, the values have to agree.  You don't have to list them.  If each host has a primary user that uses it most of the time, then you can list that one.  If users roam between boxes entirely, then you probably should list just one admin user locally or set a local root password so you can get on the box without LDAP if necessary.

If users have existing files on the hosts locally, you must change them to have the right ownership using the UID and GID values in the LDAP directory.

---

### Post by uris on 2007-09-14
I did not create the users no any of the clients., so they are not listed locally. There is a local admin user in each machine which I use for administration, but the problem is not that. The problem is that the users authenticated through ldap do not have access to sound nor usb drives. Is there a user that the system uses for authenticating users through ldap (a 'nobody' e.g.)? And if so, how is this configured?

Also, the files that the ldap users create are created with those users uid and gid, even if those uid and gid do not exist on the client. 

I am terribly puzzled.

---

### Post by noob12 on 2007-09-14
Check the group access on these devices using ls -l of the name of the device in /dev and make sure the users are in those groups.

For example:
```

% ls -l /dev/audio 
crw-rw---- 1 root audio 14, 4 2007-09-14 08:14 /dev/audio

```

This says that for access to **/dev/audio** the user needs to be in the group **audio** (gid: 29 by default).  In LDAP create a group with the unix gid 29 and put the users in that group.  Alternatively make the audio device readable and writeable by everyone.

For the USB devices, can you clarify what you mean?  Do they have trouble mounting flash drives or what?

---

### Post by uris on 2007-09-14
They can not mount usb drives.

---

### Post by uris on 2007-09-14
Thanks for the tip. To make it work with usb, i added the users to the plugdev group using LDAP.

THANK YOU VERY MUCH!

---

