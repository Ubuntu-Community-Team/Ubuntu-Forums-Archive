---
title: "Problem with Samba in Ubuntu - windows system"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-12-22
I finally got Samba working to some extent, where I was able to move files from one computer to the other. There are some problems tho, I created a account using

```

sudo smbpasswd -a User_Name

```
but when I connected to the server through windows did was I unable to chose or select any account name, instead was it set to "Guest" and I was only able to enter a password. Tho this wasn't the same as the password for User_Name.

To get around this problem did I simply allow guests to access the server using the standard GUI for this. With this workaround did I transfere files to the server the strange part is that those files transfered did the server not have any rights to. It simply said.

```

User: Nobody
Group None

```

Why is this happening?

---

### Post by lykwydchykyn on 2008-12-22
First of all, what version of Windows are you using?  That makes a difference in what kind of networking abilities it has.

Second, as you probably know, samba accounts and linux accounts are kept in separate databases.  Samba maps its accounts to local linux accounts, so that if you have samba user "joe" mapped to linux user "ted" (not that you normally would), logging in to samba as "joe" and creating files on the share will result in files owned by linux user "ted".

By default, the samba user "guest" is mapped to linux user "nobody" and linux group "nogroup".  So if you use guest mode, you'll have files owned by "nobody" and "nogroup".

Please post your /etc/samba/smb.conf file as well.  thanks.

---

### Post by Kellemora on 2008-12-22
Hi SA

I'll start by saying I'm a noob too, three months and I haven't figured this one out myself yet either.

I have 8 computers in this office, only 2 are Doze machines, the rest are all Ubuntu.

I have a workaround that has worked just fine for us for over two months now with no messups.  But it might not work in your situation.

It's simply this, we NEVER PUT a file onto another computer or the file server!
We ONLY FETCH files FROM other computers and the file server.
This way all the permissions stay perfectly intact.

When a person works on a file they pulled from the file server, they simply save the file on their own computer, and at different times during the day, 10AM, Noon, 3PM and at night, the file server FETCHES those files back from the computers they are on.

If we need a file that is on Computer A for use on Computer B we NEVER (while at computer A) put that file onto computer B.  Instead, we go to computer B and FETCH the file from computer A.

This may sound counterproductive, but in the long run it speeds up our whole operation.  Due to no downtime while I manually change permissions on files that were PUT somewhere!  No one here is allowed to save a file to any location other than on their own computer and into one of two working directories (files), one for in progress and one for finished work.  The file server will fetch them back from their machine so they are then where they belong for others to find them later.

I know it's probably something I have set wrong somewhere!
But no time to try to resolve the issue anymore.  Two months of messing with it was long enough!  It was just easier to regrow my hair and issue the ultimatum that nobody PUTS a file anywhere!

TTUL
Gary

---

### Post by SpinningAround on 2008-12-23
I checked the smb.conf file and it simply make no sence I know for sure that I got maps shared but they don't show up in the conf file, the config is the same as it was from the start. 

Is there some easy guides in howto set up a local network between a windows computer and a ubuntu computer because those I have found isn't very easy to understand.

---

### Post by SpinningAround on 2008-12-23
I checked the smb.conf file and it simply make no sence I know for sure that I got maps shared but they don't show up in the conf file, the config is the same as it was from the start. 

Is there some easy guides in howto set up a local network between a windows computer and a ubuntu computer because those I have found isn't very easy to understand.

I'm thinking about installing windows again since it wasn't this difficult to set up :(

---

### Post by quinnten83 on 2008-12-23
[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

try the link, it still works the same in the new ubuntu's.

---

### Post by eder.apt-get on 2008-12-23
Please, post the output of cat /etc/smb.conf

---

### Post by theozzlives on 2008-12-23
> **SpinningAround said:**
> I checked the smb.conf file and it simply make no sence I know for sure that I got maps shared but they don't show up in the conf file, the config is the same as it was from the start. 

Is there some easy guides in howto set up a local network between a windows computer and a ubuntu computer because those I have found isn't very easy to understand.

I'm thinking about installing windows again since it wasn't this difficult to set up :(

check the line under Global that says:
```
workgroup=WORKGROUP
```
make sure it's the same as your Windows workgroup (like mine is MSHOME so I had to change it).

---

### Post by lykwydchykyn on 2008-12-23
> **SpinningAround said:**
> I checked the smb.conf file and it simply make no sence I know for sure that I got maps shared but they don't show up in the conf file, the config is the same as it was from the start. 

Is there some easy guides in howto set up a local network between a windows computer and a ubuntu computer because those I have found isn't very easy to understand.

If you would post the information requested, we'd be more than happy to help you though this.

---

### Post by SpinningAround on 2008-12-24
Sorry for the hold up and thanks for all your reply's but since I had such problem getting everything to work did I install windows. Windows is most likely slower but one since it did work at once was it easier to go with windows this time.

I guess it would have been easier to set up network with two ubuntu systems since NFS seem to be ALOT easier on small home networks then samba. But samba wasn't the reason I changed it was VNC, I tried to get VNC working but it simply didn't work.

---

