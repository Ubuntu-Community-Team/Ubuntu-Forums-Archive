---
title: "Best way to stream a video from one computer to another"
date: 2015-09-28
forum: Networking &amp; Wireless
---

### Post by CkDGTAT on 2015-09-28
Hi,

Suppose I have 2 laptops A and B linked by rj45

I want to have a videostream of the webcam of A from laptop B.

What would you suggest to use?



PS:

My idea may be to set a simple ftp server from laptop A.

---

### Post by TheFu on 2015-09-28
Don't use Plain FTP - EVER.
If you can write the file on "a", to shared storage, then "b" can play that file as it is being written. Use NFS.

However, Skype is probably easier.

BTW - you probably want to have a "router" on the network and not directly connect the two systems.  Routers handle stuff and make life easier. With a cross-over cable (direct connection), you have to manually do everything.

---

### Post by SeijiSensei on 2015-09-29
If laptop A with the camera is running a non-server version of Ubuntu with a GUI interface, a simple solution is to install **openssh-server** on the machine with the camera, then run "ssh -X laptop_A_name_or_IP" on laptop B.   Now you will be logged into the remote machine.  Run the camera software from the command prompt.  You should see its output appear on the client machine.

For instance, if you're using cheese, and laptop A has address 10.10.10.10, then
```

[user@laptop_B]$ ssh -X 10.10.10.10
Enter your password
[user@laptop_A]$ cheese &

```
The ampersand puts cheese "into the background" so you can type additional commands if needed.

With this method you're not streaming the video over the wire, but simply exporting the output of cheese to laptop B.

---

### Post by ian-weisser on 2015-09-29
A: vlc stream video source
B: vlc play (or record) network stream
Both can be done by GUI or shell.

---

