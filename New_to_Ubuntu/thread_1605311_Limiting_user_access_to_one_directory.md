---
title: "Limiting user access to one directory"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by dazz100 on 2010-10-25
Hello

I want to set up a ssh server to allow downloading of images from a webcam.  I am using the application "motion" to capture the webcam images.

I want to set up a user account that has access strictly limited to read only access to the home directory.  The directory will only contain a read-only link to one (the most recent) webcam image.

The aim is to allow access to a third party so they can scp images to their website.  I do not want to allow access to any other part of the server.  The purpose of using Openssh and scp is to make the server invisible on the internet.  

I want to minimise the unecessary data traffic. The webcam is at a remote site connected via cellular WAN. The server will be accessible via the internet. Data is money. 

I have read all about file permissions but I can't figure out how to confine a user to read-only access to their home directory.  The only program they need to run is scp.

I have setup a separate account that I will use for remote admin access.

How do I confine one user to their home directory?

---

### Post by Nostalos on 2010-10-25
Chroot Jail is built in to OpenSSH.

[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

