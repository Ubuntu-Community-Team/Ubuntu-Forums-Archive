---
title: "Ftp help"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by HybridTheory on 2007-02-04
How do I go about hooking my Xp to my Linux box with FTP? I'm using Kftp grabber and I type my Ip in host and stuff not sure what to put in the username or pass box tho nor port can I get some help? :(

---

### Post by melancholeric on 2007-02-04
You could clarify some things a bit.

Are you trying to connect from the linux box to winxp or vice versa?

In any case, make sure you have the ftp server installed. For linux you'd probably use vsftpd or proftpd.

Then, the username. You'd either allow anonymous ftp or use an existing user of that box. For example, your username on the linux box is "Hybrid" and password "Theory". So, you connect from the xp box to the linux box via ftp, you'd use that username and password.

If you're trying to set up an ftp server on an xp box I honestly don't have a clue what to do since I've never done that. And wouldn't do, either.

---

### Post by HybridTheory on 2007-02-04
Ok sorry I'm trying to hook the Linux box to the Xp using Kftp and at a major loss erm in user name would I just type my Xp computers name in the box? and the pass I use to log in with? the Ip is like 

Xp ip: 192.168.0.2 
Linux: 192.168.0.1 


I don't know what to set on port

(Note: Ubuntu is the main computer I'm hooking Xp to it)

---

### Post by melancholeric on 2007-02-04
The port is 21. You may need to open both 20 and 21 if you have a firewall between the boxes or on the xp box I think.

---

### Post by HybridTheory on 2007-02-04
Do I have to install something on Xp? cuz I dont know what I'm doing wrong 

I set the Ip of my Xp box in host set the username and pass to what i use to log onto the xp computer with and port 21 and it still isnt working lol

---

### Post by melancholeric on 2007-02-04
Do you have an ftp server running on the xp box? You kind of need that first. Sorry, I don't know where to get that or how to set it up.

But once you have it up and running things should work.

---

### Post by tturrisi on 2007-02-04
sounds like you may be misunderstanding what ftp is.

FTP = File Transfer Protocol
It is a protocol used by an ftp client to connect to an ftp server.  Just like HTTP = Hyper Text Transfer Protocol is a protocol used by an http client (web browser) to connect to an HTTP server (web server).

To use an ftp client you need to configure it so it can connect to the desired ftp server:
Host or Server: ip address or domain name
Username:  xxxxxxxx
Password:  xxxxxxxx
Port:  21 (port the ftp server uses)

So, to use an ftp client on your lan you need a computer that has a ftp server installed on it and running.  To install the ftp server on linux, install pro-ftpd or wu0ftpd, etc.  To install a ftp server on a windows comp install Bulletproof FTP server or similar.

KFTP is a ftp client.

If all you want to do is have ability to swap files between computers then just setup networking and share files & folders on each comp.

---

### Post by glabouni on 2007-02-04
> **melancholeric said:**
> Do you have an ftp server running on the xp box? You kind of need that first. Sorry, I don't know where to get that or how to set it up.

But once you have it up and running things should work.

try this one: [filezilla server]("http://filezilla-project.org/wiki/index.php/FileZilla_FTP_Server")

---

