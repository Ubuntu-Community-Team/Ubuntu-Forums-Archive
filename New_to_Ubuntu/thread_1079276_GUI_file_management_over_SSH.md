---
title: "GUI file management over SSH?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-02-24
Hi all, I was able to set up OpenSSH and public/private key authentication on my file/web server.  However, when setting up a Nautilus bookmark and connecting via SFTP it seems that many functions are unavailable to me; for instance, many files appear read-only to me.

Is there a way I can manage files (such as the web files found in /var/www/) via a GUI interface while connecting via SSH?

Thanks!

---

### Post by albinootje on 2009-02-24
> **Nixie Pixel said:**
>  Is there a way I can manage files (such as the web files found in /var/www/) via a GUI interface while connecting via SSH?


Not really, but imho you should read some more about file permissions :
[http://help.ubuntu.com/community/FilePermissions](http://help.ubuntu.com/community/FilePermissions)

By default the files in /var/www are owned by root.
I am not sure whether it's a good idea to change the permissions are set that you will be the owner.

This could be useful to read too :
[http://www.devshed.com/c/a/Apache/Setting-Permissions-in-Apache/](http://www.devshed.com/c/a/Apache/Setting-Permissions-in-Apache/)

---

### Post by porchrat on 2009-02-24
From what I recall you need to do the following:

You need to have these lines in your /etc/ssh/sshd_config file on the server:
```

X11Forwarding yes
X11DisplayOffset 10
X11UseLocalhost yes
```

When running the ssh command you need to use the "-X" option to utilise X forwarding.

You would need to start the X application from the command line though.  Keep in mind that it is slower than using the command line.

EDIT: you can use this application to check that it is working:
```
xclock &
```

---

### Post by spiderbatdad on 2009-02-24
You should have this ability via the sftp over ssh connection...depending of course on the file permissions of the files you are editing. Since you log in as a user, if the files are root owned and only writable by root...you can't edit. So choices are several, and all involve some compromise in the existing security. A light weight gui like xfce4 on the server box and you can ssh -X, this allows you to forward graphical apps to yourself...like launching gksu thunar. You could also try making yourself a member of the group www:data and iving group write permission. That's one I havent done. I use very relaxed permissions in /var/www anyway...most would not want that.

---

### Post by anaconda on 2009-02-24
I use fuse and sshfs it works wery well, and is easy to setup

If normal ssh connection works then so will sshfs.

In sshfs you mount the remote computers filesystem (or the folder you want) to a folder in your local filesystem, and you can use nautilus normally..

---

### Post by nitrofurano on 2009-03-17
Well, for this i still use WinSCP on Wine, which seems to work fine - i don't know if it's the adequate answer for your question

Btw, i'm still looking for a native tool on Linux (ok, Richard Stallman says it's GNU/Linux... ), similar to WinSCP

---

### Post by MrWES on 2009-03-17
> **nitrofurano said:**
> Well, for this i still use WinSCP on Wine, which seems to work fine - i don't know if it's the adequate answer for your question

Btw, i'm still looking for a native tool on Linux (ok, Richard Stallman says it's GNU/Linux... ), similar to WinSCP

Nautilus ? File | Connect to Server

bookmark it, it's that simple

Bill

---

### Post by jerome1232 on 2009-03-17
> **Nixie Pixel said:**
> 
Is there a way I can manage files (such as the web files found in /var/www/) via a GUI interface while connecting via SSH?

Thanks!

Either have apache store the website in your Home folder with your user permissions or change the user permissions of /var/www/ so that the user you are connecting as can access them.

---

### Post by albinootje on 2009-03-17
> **nitrofurano said:**
> i'm still looking for a native tool on Linux (ok, Richard Stallman says it's GNU/Linux... ), similar to WinSCP

Gftp (choose SSH2), FileZilla, Nautilus (use sftp://) and Konqueror (use fish://) can all serve as a scp/sftp GUI client.

---

