---
title: "Setting up Remote Access"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Java Geek on 2009-11-09
Hello, 

I have done SOME googling on how to set up a remote access so that i can access my home computer from any of my school's windows machines. I have found several guides, none of which are for kubuntu or are pre-karmic!

Do you know how? Or know of a good guide? thanks.

---

### Post by lavinog on 2009-11-10
There are two ways to go about this: ssh and vnc.
ssh: [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
vnc: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

ssh is more secure and you can tunnel vnc through ssh to encrypt your vnc connection.

ssh is usually used in a terminal (you can use putty for windows)
You can use gui apps over ssh, but you generally don't use a full desktop...(helps to know how to use the terminal)

---

