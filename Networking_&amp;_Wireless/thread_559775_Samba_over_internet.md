---
title: "Samba over internet"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by Zoney on 2007-09-25
I found an old dell with a broken wirless card, so I installed ubuntu 7.04 and put the laptop under my xbox mediacenter, and I stream videos and music through it, works like a charm (using ftp).

Now I started to check out samba, and I got it working perfectly in my little LAN, but I have the Linux-dell as DMZ in my router, and I would like to connect to it through the internet, not only localy, is this possible (ssh works fine)?
Because, when I try, this happens: 
Normal scenario:
Connects with \\192.160.0.11 and I can browse my folders like I want.
Through internet:
Connects with \\something.mysite.com and I can only see two folders, the samba "root" folders: "homes" and "my user". When I go into the folders they are empty, so... I can connect, but nothing else.. 
Is this normal? Is it because I connect using an IP that the NIC doesn't recognice? Do I have to set up some kind of secure connection to be allowed to se my folders over the internet? Or is it some settings in the smb.conf that can solve this? 

Hope my problem is understandable, sorry for my english ;)

---

### Post by kidders on 2007-09-27
Hi there,

The Windows networking protocols are not designed to work over the internet. Having said that, you *can* manipulate them into letting you access files remotely with an SSH tunnel, but tbh I would suggest switching to a more suitable protocol, for convenience ... WebDAV maybe?

> **Zoney said:**
> Connects with \\something.mysite.com and I can only see two folders, the samba "root" folders: "homes" and "my user".Setting something up that would allow you to address a remote host directly like that is _highly dangerous_. You should absolutely never allow Samba (or Windows' own file sharing service) to bind to an externally accessible network interface, even for a few minutes. You'll attract malicious activity like moths to a flame!

As I mentioned already, I would suggest considering WebDAV over SSL. It would fulfill basic off-site file sharing needs safely.

---

