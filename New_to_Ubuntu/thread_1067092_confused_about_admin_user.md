---
title: "confused about admin user"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by dieter964 on 2009-02-11
Just installed Ubu 8.10 and created one user and a password.  when i boot, it "automatically" goes to the desktop (without loggin in), showing hte user in the upper right hand corner, and I'm able to do pretty much everything from that deskop. When i logout, after 8 sec. it goes right back to the desktop, again without login.

1.  Is there a way to complete logout all users?
2.  Is there a way to run the desktop as ROOT or Su user whereby i'm able to run apps and manage files from the gui on the desktop (not from the terminal screen)?
3.  Can you recommend some reading materials on USERS and GRoups?

---

### Post by bodhi.zazen on 2009-02-11
I do not know why you are automatically logged in, sounds as if you are still running the live CD perhaps ? Certainly not the default behavior.

In terms of admin / root why do you want to run x as root ? Not a good idea at all.

See : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dieter964 on 2009-02-11
I would like to create an admin user (will all permissions everwhere thruout the filesystem) that can do anything from the GUI desktop, without having to go into terminal mode. For example, I would like to copoy any file to any folder i wish from the graphical interface.

How do i create such a user and how do i give him all permissions?

---

### Post by bodhi.zazen on 2009-02-11
> **dieter964 said:**
> I would like to create an admin user (will all permissions everwhere thruout the filesystem) that can do anything from the GUI desktop, without having to go into terminal mode. For example, I would like to copoy any file to any folder i wish from the graphical interface.

How do i create such a user and how do i give him all permissions?

The link I gave you explains how to do this. You use sudo in the terminal and gksu with graphical applications such as nautilus.

I suggest you take the time to learn how linux works, including permissions and ownership before you take such actions.

On the other hand the worst thing you can do is break your system and then re install, so go for it ;)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by dca on 2009-02-11
It's not generally best practices in a *nix environment.
 
at CLI:  *gksudo nautilus &*

---

### Post by jjpcexpert on 2009-02-11
edited.

---

### Post by bodhi.zazen on 2009-02-11
> **jjpcexpert said:**
> well yes, go in as you, then ```
 sudo su root 
``` and then type your password, and then type ```
 startx 
```

I am sorry to say but that is just bad advice.

There is almost no reason to log in as root, let alone run X as root. Doing so is certainly both a security risk as well as a risk of causing damage / breakage to a users system.

The risks are even greater in this case as we have what appears to be a new user who does not understand linux permissions, let alone security or the implications of running X as root.

If you wish to give such advice please be sure to give proper warnings and links to appropriate references. keep in mind we are here to teach, not give rote answers to new users and turn a blind eye to the consequences of our bad advice.

---

### Post by dieter964 on 2009-02-12
Granted, jjpcexpert, that I'm new to linux and Ubu.  Coming from a Windows environment, having to learn the linux commands for simple admin tasks is very frustrating to me.  It would seem that I should be able to create a user which can modify .conf files belonging to ROOT, VIA A GRAPHICAL USER INTERFACE.

Is there such a way?

I tried running the recommended commands, but got the following warning message:

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

All I want to do is to be able to edit, copy, delete files belonging to ROOT, from a GUI.

This is my own computer, so I'm not concerned about rendering it useless by my mistakes.

---

### Post by jerome1232 on 2009-02-12
> **dieter964 said:**
> Granted, jjpcexpert, that I'm new to linux and Ubu.  Coming from a Windows environment, having to learn the linux commands for simple admin tasks is very frustrating to me.  It would seem that I should be able to create a user which can modify .conf files belonging to ROOT, VIA A GRAPHICAL USER INTERFACE.

Is there such a way?

I tried running the recommended commands, but got the following warning message:

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

All I want to do is to be able to edit, copy, delete files belonging to ROOT, from a GUI.

This is my own computer, so I'm not concerned about rendering it useless by my mistakes.

Did you ever follow those links bodhi.zazen gave you? They explain how to do this.

you use sudo and gksu for cli and gui apps respectivly. For example you want to browse your file-system as root user using a gui file-manager, you would hit alt+f2 then type "gksu nautilus" to run nautilus (the file manager) as root, giving you full access to system files.

I think you should review bodhi.zazens posts and follow some of the helpful links he gave which will explain the permissions systems for you.

---

### Post by dieter964 on 2009-02-12
> **jerome1232 said:**
> Did you ever follow those links bodhi.zazen gave you? They explain how to do this.

you use sudo and gksu for cli and gui apps respectivly. For example you want to browse your file-system as root user using a gui file-manager, you would hit alt+f2 then type "gksu nautilus" to run nautilus (the file manager) as root, giving you full access to system files.

I think you should review bodhi.zazens posts and follow some of the helpful links he gave which will explain the permissions systems for you.

Thank you, thank you, thank you!! gksu nautilus - worked. I missed the original link from bodhi.zazen.

---

### Post by jerome1232 on 2009-02-12
I forgot to mention, exercise caution when running any application as root. It may seem silly but it's very easy to make a mistake that will destroy your system. 

There is a nifty nautilus script called nautilus-gksu that add's a right click option which will open a file as the root user.

This way you can open nautilus as a normal user, browse to your system file, right click it and click "Open as admin", then gedit will be open as root allowing you to edit the file and save it.

Just search synaptic for the script, it's called nautilus-gksu

---

