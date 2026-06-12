---
title: "[SOLVED] Can't Edit Privliges"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by RoseKnight on 2009-01-08
I'm trying to make access to changes easier for my main user account.

I can't change anything in the "System/Admin/Users and Groups" and I can't change File Permissions.

/edit
by "File Permissions" I mean when you right click on a file such as one that is in the "usr/bin" directory, and click Properties then go into the permissions tab.

Little things like the above are really getting annoying.

Is their anyway to make it possible for my Main Account to be able to change and edit these without getting too complicated. As well as having the system ask for the password before allowing a change, of course.

---

### Post by pipyui on 2009-01-08
You may need to try unlocking the user. Highlight your user, there should be an "unlock" button at the bottom of the window. Afterwards, you should be able to edit your permissions.

---

### Post by RoseKnight on 2009-01-08
> You may need to try unlocking the user. Highlight your user, there should be an "unlock" button at the bottom of the window. Afterwards, you should be able to edit your permissions.
well, theres one down. I still can't edit the file permissions tho. 

it keeps telling me: "you can't change these permissions, you are not the owner."

when I right click on a file and go into the permissions tab.
And I certainly am the owner.

---

### Post by handydan918 on 2009-01-08
> **RoseKnight said:**
> well, theres one down. I still can't edit the file permissions tho. 

it keeps telling me: "you can't change these permissions, you are not the owner."

which.. I certainly am the owner.

OOOHHH, no yer not. 
Root is. You can assume root powers by use of sudo, gksu, etc.

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
>  which.. I certainly am the owner.

Is your user in the admin group ?
You can check that quickly with this command in a terminal :
```

groups

```

---

### Post by RoseKnight on 2009-01-08
yea yea, I know sudo. It's fun.

But I'm wondering if theres a way to make it so a admin user can change file permissions (providing they know the sudo password) without having to leave the graphical display and go into terminal.

---

### Post by RoseKnight on 2009-01-08
> **albinootje said:**
> Is your user in the admin group ?
You can check that quickly with this command in a terminal :
```

groups

```

well.. I am now. 

but it still says "you are not the owner, so you cannot change these permissions"

/edit
when I right click on a file in an area such as: user/bin
and click on the permissions tab.

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
> well.. I am now. 

but it still says "you are not the owner, so you cannot change these permissions"
... [edited]
OK. I've misread your post. Still thought you were talking about this :
> 
I can't change anything in the "System/Admin/Users and Groups"


Which permissions do you need to change ? 
Because you are you running a webserver perhaps ?

---

### Post by Vantrax on 2009-01-08
> **RoseKnight said:**
> yea yea, I know sudo. It's fun.

But I'm wondering if theres a way to make it so a admin user can change file permissions (providing they know the sudo password) without having to leave the graphical display and go into terminal.

File permissions are handled by chmod and chown, I dont believe there is a graphical interface for those programs available.

---

### Post by ranch hand on 2009-01-08
The reason that Ubuntu is more secure than some other OS you may run into is that it takes a password to get to these types of files.

You could be spending your time doing virus scans and updating your security.

You can set a launcher for terminal on your desktop or on the panel, I have it and synaptic side by side.

Changing permissions, or ownership is not generally a good idea.

---

### Post by RoseKnight on 2009-01-08
Nope, no go.

(for those who might be lost at this point: when I try to change a files permissions, eg:
When I go into "usr/bin/" and right click on a file such as.. unetbootin and click properties and then the "permissions" tab it says I'm not the owner and cannot change permissions.) Just a little clarification, just in case. :D

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
> 
When I go into "usr/bin/" and right click on a file such as.. unetbootin and click properties and then the "permissions" tab it says I'm not the owner and cannot change permissions.) Just a little clarification, just in case. :D

Sounds like you have no valid reasons to change those permissions.
Before you make a security hazard out of your secure Ubuntu installation, read the following carefully :

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

---

### Post by RoseKnight on 2009-01-08
> **albinootje said:**
> Sounds like you have no valid reasons to change those permissions.
Before you make a security hazard out of your secure Ubuntu installation, read the following carefully :

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)

Honestly, that is one of the most rudest things I have ever read.
"Oh, you don't really need that, you won't use it for any valid purpose."

Yes, I do have a valid reason to change those permissions, and for you to assume any other way suggests to me that you do not understand what I need them for.
Yes, I do understand that if I screw something up it could open up a security hole in my OS.

I'm sorry if I implied something else, and that I did not make clear what it was I was asking for. But thank you for helping me find it anyways.

Onward: what I did not know. Thank you for showing me that files can be owned by a different user that is not the only user on the system, and that "root" is considered a separate user from what should be your main account.

My actually question, now that I know more would be something along the lines of:

"How do you make your main account always be the owner of new files."
"what are the security risks?"

and question three:
"Should these questions be moved away from the newbie thread yet?"

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
> Honestly, that is one of the most rudest things I have ever read.
"Oh, you don't really need that, you won't use it for any valid purpose."

Yes, I do have a valid reason to change those permissions, and for you to assume any other way suggests to me that you do not understand what I need them for.

Good, then please explain why you want your main user to be the owner of the unetbooting binary ?
> 
My actually question, now that I know more would be something along the lines of:

"How do you make your main account always be the owner of new files."

Please define "new files".

Do you mean after installing software packages ?

Files unpacked from an (tar or zip) archive by your main user are normally owned and writable by the main user.
> 
"what are the security risks?"

If a binary, which is readable system-wide, is owned by your main user, and an attacker manages to sneak in via your web-browser while surfing the internet, the attacker can *modify* that binary.
If the owner of that binary was root, which is very often the case, then the attacker would need a local root-exploit first to gain root access to be able to modify those binaries.

---

### Post by RoseKnight on 2009-01-08
Well, after you install unetbootin on your system, It puts an entry in your menu. Which is completely unusable. Because it doesn't have permission to execute as program.

(needs sudo.)

I'd like it to be able to execute, providing a user provides the password. but without using the damn terminal everytime.


(ps. I am the main user, not trying to get it system wide.)

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
> Well, after you install unetbootin on your system, It puts an entry in your menu. Which is completely unusable. 


I have unetbootin installed since a while.
It does ask me for my password, and I've used it like that without problems to create bootable usb sticks.

If you hate the terminal so much, you can create a custom launcher for your (top) panel ("add to panel"), and let that custom application launcher run :
```

gksu unetbootin

```
for you.

---

### Post by RoseKnight on 2009-01-08
its not that I hate terminal, terminal is in fact, really useful. I just don't see the point of running it when I don't in particularly need it.

So, why isn't my Main account my Main account?

if you didn't have a problem with the install, why did I?

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
> its not that I hate terminal, terminal is in fact, really useful. I just don't see the point of running it when I don't in particularly need it.

So, why isn't my Main account my Main account?

if you didn't have a problem with the install, why did I?

Good question.

301-6 is the version of unetbootin which I have installed.

---

### Post by RoseKnight on 2009-01-08
I downloaded whatever the newest one is as of last week.

ran: "gksu nautilus"
and found the file via nautilus

The problem I found was that the "owner" of the file was something like: "74560"

and the group allowed access to it was: "libuuid"

which is strange... so I changed the owner to my main account and the group to admin and now everything is hunky-dory

---

### Post by albinootje on 2009-01-08
> **RoseKnight said:**
>  The problem I found was that the "owner" of the file was something like: "74560"

and the group allowed access to it was: "libuuid"

which is strange... 

Indeed..

ls -la $(which unetbootin)
-rwxr-xr-x 1 root root 514676 2008-12-22 01:05 /usr/bin/unetbootin
> 
so I changed the owner to my main account and the group to admin and now everything is hunky-dory
Well done! ;-)

---

