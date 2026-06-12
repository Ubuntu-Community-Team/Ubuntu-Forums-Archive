---
title: "Cannot &quot;Add&quot; with users-admin while VNC"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by oregonbob on 2008-12-11
I have a Ubuntu Intrepid 8.10 server with Gnome and VNCserver installed. I would think a nice system administration gui or web app should have been part of standard install on server.

My problem is if I vnc into the server and run Administration -> Users and Groups, which runs program "users-admin", it starts up OK, but the "Add" user button is disabled. Is there any fix for this? I tried "gksu users-admin &" in a shell and it had same problem. Maybe I need to add privilege somewhere?

---

### Post by Ong on 2008-12-11
did u click the unlock button?
:confused:

---

### Post by Frogbarf on 2008-12-12
When you install Ubuntu, it asks you to specify a user id and password. This becomes your administrative user id (though you can create others).

To use sudo, gksudo, or any graphical program such as the users & groups dialog, you have to be logged on with that id, and you have to also repeat the password in some manner.

In System > Administration > Users & Groups, click the "unlock" button first. It'll ask for your privileged id password, and when you give that, the functions of the dialog will be activated so you can fiddle around with your users & groups.

I accidentally (stupidly) fouled up my admin id after I last installed Ubuntu and had to re-install, though I think there are other ways of dealing with the problem.

Does this solve your problem?

---

### Post by oregonbob on 2008-12-15
I didn't notice the Unlock button, but that is because it is grayed-out and disabled too. 

First I log in as the administrative user I setup when installed, with ssh. Then I run vncserver on the command line, then I login vncserver and give my password.

I know what you mean by needing to re-enter password to gksu. But it does not ask my password again when I start users-admin.

After installation I did give root a password, which enables the root user. But I don't want to vnc as user root.

If I run "gksu users-admin", it asks password, but everything is still disabled. I notice programs like Synaptic Package Mgr ask for password on entry just like it should.

---

### Post by D-Tux on 2010-11-11
Is there a solution for this problem? I have the same in Ubuntu 10.10 when i'm connected true vncviewer

---

### Post by SlugSlug on 2010-11-11
you could open a terminal and issue
```

sudo adduser [username]
```

---

### Post by toekneewood on 2010-11-11
Take a look at [http://www.webmin.com/]("http://www.webmin.com/")

---

### Post by CharlesA on 2010-11-11
It's a security thing. When you are connected via VNC, you don't have the same permissions as if you were connected to the console.

Closing the thread since it's a major necro.

---

