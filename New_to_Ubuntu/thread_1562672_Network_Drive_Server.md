---
title: "Network Drive Server"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by adamjkok on 2010-08-27
Okay, so this might be really complicated, but here's what I need to pull off:

My computers:

[LIST]
[*]Gateway server (well, not exactly a "server" because it is a converted desktop with a monitor and keyboard and mouse and it runs vanilla Ubuntu)
[*]Dell Inspiron 1545 laptop running Windows 7 (no, I'm not putting Ubuntu on it).
[/LIST]

Problem:

[LIST]
[*]I would like to be able to serve up my home folder over WebDAV and only have my user be able to access it with WebDAV password.
[*]My dad is going to give me control of his new 1TB drive to serve to the entire family. I will need to give 4 users (including myself) authenticated read/write access. For the purpose of solving the problem (I am not in possession of the drive yet so IDK where it will mount), let's say that the drive automounts at /wdhdd.
[*]Secure access is preferred, but in the clear should be fine. I don't wanna mess with it if it will be too complicated, but if it's trivial to enable then I want it.
[*]I will need to mount these locations as drives on the Win7 laptop (let's say H:\ for my home folder on the local disk and K:\ for the 1TB shared drive). Let's say the domain is example.tk even though it really is a randomly-generated alphanumeric string. Other family members will only need the K:\ drive.
[*]I really need to have the correct ports forwarded. Please give the WebDAV ports. If the ports are 80 or 25, they need to be changed due to inbound ISP blocks on 80 and in/out blocks on 25.
[/LIST]

---

