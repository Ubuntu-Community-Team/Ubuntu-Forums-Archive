---
title: "Getting a permission denied message"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by T&amp;H on 2008-12-05
Let me start with I am very new to Ubuntu, I have been using it for about five months and only have a few probably small problems.  The first is I share this computer with my wife and two teenage daughters.  I am the only one with administrator privileges.  I would like to share all music files with them so we don't have to take up extra space loading the same stuff over and over.  I put the files in the public folder but they only show to me, I tried to change the properties of the folder to allow sharing so they can use it but I get this message:

[COLOR="Red"]net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/COLOR]

Now my question is how do I resolve this or am I trying to do this simple task all wrong?  And if I am the only one in the admin group how can I not have permission?  I am using Hardy Heron as built from Ubuntu no mods.

Thanks ahead of time.
T&H

---

### Post by theozzlives on 2008-12-05
> **T&H said:**
> 
[COLOR="Red"]net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/COLOR]



I don't know what you typed or clicked to get that, but I create a share on my network by right-clicking on the folder and go to "sharing options" and check the boxes that apply.

---

### Post by DGortze380 on 2008-12-05
> **T&H said:**
> Let me start with I am very new to Ubuntu, I have been using it for about five months and only have a few probably small problems.  The first is I share this computer with my wife and two teenage daughters.  I am the only one with administrator privileges.  I would like to share all music files with them so we don't have to take up extra space loading the same stuff over and over.  I put the files in the public folder but they only show to me, I tried to change the properties of the folder to allow sharing so they can use it but I get this message:

[COLOR="Red"]net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.[/COLOR]

Now my question is how do I resolve this or am I trying to do this simple task all wrong?  And if I am the only one in the admin group how can I not have permission?  I am using Hardy Heron as built from Ubuntu no mods.

Thanks ahead of time.
T&H

Are you trying to create a network share? Or is it just one machine?

---

### Post by handydan918 on 2008-12-05
An error message is good, but only in the context of the command or action that generated it.

---

### Post by T&amp;H on 2008-12-06
Bare with me I'm kind of new at this everyone.

> **theozzlives said:**
> I don't know what you typed or clicked to get that, but I create a share on my network by right-clicking on the folder and go to "sharing options" and check the boxes that apply.
That is what I did.  The following steps are my actions:
Clicked on "Places"
Clicked on the Home folder
Right clicked on "Public"
Doesn't matter if you choose sharing options or if you go to properties both yield the same error message.

> **DGortze380 said:**
> Are you trying to create a network share? Or is it just one machine?
This is one machine shared by the family.  As I explained earlier I'm just wanting to share this one folder that way we can all have access to its contents (music and a few text files.)

Sorry I should have explained a little better hope this helps you with helping me.

Thanks T&H

---

### Post by f37u5g0d on 2008-12-06
I had this same problem!  You want to do to is make a folder that is accessible (full read, write, and execute permissions) by all the users on your system.  What you are trying to do is make a folder that is shared on your network.  To make a folder that is accessible by anyone on your system you simply hput that folder in a place where everyone can access it.  Somewhere underneither /home will have those permissions.  I suggest you place it somewhere in /home/*your home folder*  so that this is easier.  Than change the permissions so that "others" have full access or was much access as you want to give them.  You can view the permissions of any file or folder in nautilus by right clicking it and going to the permissions tab.  If you have any more questions just post here again.

---

### Post by T&amp;H on 2008-12-09
> **f37u5g0d said:**
> I had this same problem!  You want to do to is make a folder that is accessible (full read, write, and execute permissions) by all the users on your system.  What you are trying to do is make a folder that is shared on your network.  To make a folder that is accessible by anyone on your system you simply hput that folder in a place where everyone can access it.  Somewhere underneither /home will have those permissions.  I suggest you place it somewhere in /home/*your home folder*  so that this is easier.  Than change the permissions so that "others" have full access or was much access as you want to give them.  You can view the permissions of any file or folder in nautilus by right clicking it and going to the permissions tab.  If you have any more questions just post here again.
I have tried this several times, problem persists.
T&H

---

### Post by DGortze380 on 2008-12-09
Try creating a new directory under root (/) with 770 permissions... putting it in /home can some accessibility issues.

Then create a group called something like shareAccess, add users you want to access the share to that group, use the chgroup command that set the directory to that group.

---

### Post by T&amp;H on 2008-12-11
> **DGortze380 said:**
> Try creating a new directory under root (/) with 770 permissions... putting it in /home can some accessibility issues.

Then create a group called something like shareAccess, add users you want to access the share to that group, use the chgroup command that set the directory to that group.

I will now sound like the newbie I am, how?  I'm a little nervous about accessing anything in the root file as my pre-windows experience is very outdated and that was a section one just didn't mess around in unless you really knew what you were doing.
T&H

---

### Post by Viranh on 2008-12-11
Perhaps you could change the permissions on the directory you would like everyone to use? This can be done from the command line with chmod.

For example, if I want to give all users read and write access my home directory, I would type the following in the terminal:

chmod a+rw /home/viranh

so the general form is chmod <users>+<permissions> <path to file or dir>

a= all users
u= owner
o= other users
g= group

r=read
w=write
x=execute 

I don't believe that making a directory in root is harmful. Nautilus isn't giving me an option to make a folder here, so I believe sudo must be used. You could make the folder with sudo, then sudo chmod the permissions as explained above to whatever you want. If you aren't that comfortable with the command line, you can launch nautilus with root privileges by typing in the terminal "gksudo nautilus" then typing your password. You will then be able to make the folder and change its permissions. As a side-note, permissions can be expressed in numbers as well as the letters I listed above. I don't remember them exactly though.

PS: Mark Sobell's *A Practical Guide to Linux* is an excellent reference. I used to it to make sure I was remembering everything correctly, and it has helped me learn alot.

---

### Post by bodhi.zazen on 2008-12-11
> **DGortze380 said:**
> Try creating a new directory under root (/) with 770 permissions... putting it in /home can some accessibility issues.

Then create a group called something like shareAccess, add users you want to access the share to that group, use the chgroup command that set the directory to that group.

Actually, best to make a shared directory in your home directory.

The problems occur if you share your home directory itself.

---

