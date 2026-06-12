---
title: "Any way of sharing files between Windows and linux computer over network?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by shebaw on 2010-05-12
Hello everyone,
I have solved almost all of the problems I faced except this one. I have been experiencing this problem both on Ubuntu 9.10 and Ubuntu 10.04. I use Samba to share files between linux and Ubuntu computers over a network. I can copy to the windows machine at about 2 mbps, which is bad since I used to copy at 10 mbps when I was using windows but it's tolerable. What's annoying is that it take ages to copy files from the windows machine to the linux running machine. I get 40 kbps max. Is there any way of doing it right? 

I really really need this! 
Thanks in advance!

---

### Post by bodhi.zazen on 2010-05-12
Hard to know without more information. What kind of network ? Wired or wireless ?

You can use an alternate protocol such as ssh (scp) or nfs (nfs is faster the samba, but can be hard to set up on Windows).

On a LAN you could also try FTP.

One way transfers with http.

---

### Post by Munk3y on 2010-05-12
Like a year ago I had a similar issue and I was 99% sure it was Ubuntu/Samba's fault because Windows to Windows was fast, both ways. Then I updated my network card drivers on the Windows machine and it fixed the slow transfer speed issues from/to the Ubuntu machine. I'm not sure if it's the same situation for you but it's worth a try.

---

### Post by shebaw on 2010-05-12
> **bodhi.zazen said:**
> Hard to know without more information. What kind of network ? Wired or wireless ?

You can use an alternate protocol such as ssh (scp) or nfs (nfs is faster the samba, but can be hard to set up on Windows).

On a LAN you could also try FTP.

One way transfers with http.

It's a wired connection. I have tried to copy files from different windows running machines to my computer but the copy speed is way slow. It won't be a problem if FTP works out though. How do I set it up? I mean do I make my computer a server and copy files to it? Any guide/link on how to do it on linux would be appreciated since I'm new to both linux and FTP. I've never used it (knowingly) before on my windows computers.

---

### Post by shebaw on 2010-05-12
> **Munk3y said:**
> Like a year ago I had a similar issue and I was 99% sure it was Ubuntu/Samba's fault because Windows to Windows was fast, both ways. Then I updated my network card drivers on the Windows machine and it fixed the slow transfer speed issues from/to the Ubuntu machine. I'm not sure if it's the same situation for you but it's worth a try.

I don't think I'm having the same issue since I have tried it on multiple machines running windows.

---

### Post by bodhi.zazen on 2010-05-12
> **shebaw said:**
> It's a wired connection. I have tried to copy files from different windows running machines to my computer but the copy speed is way slow. It won't be a problem if FTP works out though. How do I set it up? I mean do I make my computer a server and copy files to it? Any guide/link on how to do it on linux would be appreciated since I'm new to both linux and FTP. I've never used it (knowingly) before on my windows computers.

Did you try any of the numerous on ling guides ?

FTP is easy to set up, most people spend time on securing it, which may not be necessary on your LAN.

There are several ftp graphical clients , both for Linux and Windows.

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

[http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/](http://www.cyberciti.biz/faq/ubuntu-vsftpd-ftp-service-server/)

---

### Post by shebaw on 2010-05-12
Thank you for the guides, I will try them out tomorrow when I have physical access to the network and will update you my result.

---

### Post by Munk3y on 2010-05-12
> **shebaw said:**
> I don't think I'm having the same issue since I have tried it on multiple machines running windows.

Nope, doesn't sound like the same issue. However, that's why more info up front is a good idea :)

---

