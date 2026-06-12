---
title: "share files password ubuntu to ubuntu"
date: 2011-07-12
forum: New to Ubuntu
---

### Post by claytonbagwell on 2011-07-12
I have two computers sharing one switch.  Both computers are running lucid lynx 10.04 32 bit.  These are not dual boot machines, they only run Ubuntu, as I said, sharing a common switch.  I want to network the two computers and share files.  In each computer I have marked the folders I want to share.  When I go to <network> I can see both computers and the folders I have marked for sharing.  When I ask to share a folder from one computer to the other I am asked for a domain password.

The previous poster was sharing between windoze and Ubuntu.  He had to delete all Windows Live files. (Presumably) this action eliminated the password request.  I don't seem to have any Windows Live files.  My computers are both Ubuntu.

What is this password?  Where is it generated?  How can I share files between to Ubuntu computers sharing a common switch?

---

### Post by compmodder26 on 2011-07-12
If you shared your folders through nautilus then you are using SAMBA to share your files.  That is basically the same way windows shares files and folders.

The quick fix for you case would be to open up a terminal issue this command:

```
smbpasswd
```

This will allow you to create a password to use for file sharing.  This password can be whatever you like.  Do this on both machines so you can share from the first to second and vice versa.

When trying to connect to a share you can then enter the password and elect to remember the password forever so you won't have to do it again.

---

### Post by claytonbagwell on 2011-07-12
Bizaar!!  When I changed the samba password at the terminal and then tried to use it to share a file, it was rejected.  I thought I should re-boot and try again.  Upon re-boot my login password (sudo) would not authenticate.  I had to use my new samba password in order to log in!!!

Then after logging in, I was asked to verify my login keyring password (old sudo password.)

Why does sambapasswd change my login password?  If the share_files domain "workgroup" password is not the samba password (also not the sudo password,) then what might it be?

---

### Post by claytonbagwell on 2011-07-13
I started out with one ubuntu computer and a windows 7 computer both connected by LAN to the same router (switch.)  For networking, the ubuntu computer could 'see' and open files on the windows machine, but not the other way around.  OK, fine, windows can't read ubuntu, but ubuntu will read windows.

Then I removed windows from the one computer and totally installed ubuntu 10.04 lucid lynx.  Now both computers have the same OS, and are wired to the same switch.  In this configuration no files are shareable.  I get a window asking for a password for the domain 'workgroup'.  

What is it that blocks Ubuntu from just sharing files?  What is the secret to set up a simple home network to share files between two Ubuntu computers?

---

### Post by claytonbagwell on 2011-07-13
just a newbie.  I am not getting any replies.  Is there a better place to take this question about files sharing?

---

