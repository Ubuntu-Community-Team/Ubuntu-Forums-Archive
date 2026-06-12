---
title: "How to share files in homenetwork?"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by JamesNT on 2010-10-28
My pc is running Ubuntu, I need to access files on another pc running Windows 7. Please help.

---

### Post by HermanAB on 2010-10-28
The easiest way is with the FileZilla FTP client and server.  It is cross platform.  Install the server on Windows and saccess your files from Ubuntu either with your file browser File, Connect to Server optin or with the FileZilla client for Linux.

There are many other ways, but this is the easiest.

---

### Post by bioterror on 2010-10-28
> **HermanAB said:**
> The easiest way is with the FileZilla FTP client and server.  It is cross platform.  Install the server on Windows and saccess your files from Ubuntu either with your file browser File, Connect to Server optin or with the FileZilla client for Linux.

There are many other ways, but this is the easiest.


How about just plain old Samba (Window Shares?!)
In Nautilus you can just say "Share this folder" and in network places you can see other shares.

---

### Post by KeLa on 2010-10-28
Actually OP needs to get access files on his Windows pc so
that can be easy too.
In windows you share what you want to your ubuntu box to see and
on ubuntu you go Places->Network and you will find that share from there.

---

### Post by JamesNT on 2010-10-28
> **HermanAB said:**
> The easiest way is with the FileZilla FTP client and server. It is cross platform. Install the server on Windows and saccess your files from Ubuntu either with your file browser File, Connect to Server optin or with the FileZilla client for Linux.
 
There are many other ways, but this is the easiest.
 Hi, does this mean that I have to turn the Windows pc into a server? I downloaded FileZilla server and install it in Windows but it asked me to connect to a server. Should I ramdonly connect a ftp server then I can use a filezilla client in Ubuntu to connect to the server and transfer files via it ? I'm sorry I did't quite understand how it works.  
I then checked documents on the website it too ask me to connect to a server. I realy don't know what server to connect.

---

### Post by JamesNT on 2010-10-28
> **KeLa said:**
> Actually OP needs to get access files on his Windows pc so
that can be easy too.
In windows you share what you want to your ubuntu box to see and
on ubuntu you go Places->Network and you will find that share from there.
 I found this on the web :
#sudo mount -t cifs -o username=username,password=password,iocharset=utf8 //192.168.1.1/soft /mnt
can this possibly work? I don't know what should the path be if I wanted to browse the public folder .Should it be //192.168.1.1/c/users/public  ?

---

### Post by Verbeck on 2010-10-28
as KeLa already posted above, if its the files on windows you want to see
just share it in windows ( some where in file properties) then in ubuntu, go to places>network

---

### Post by Grenage on 2010-10-28
If you're just after basic shares, **bioterror** is quite correct; it's very easy using the GUI.

As in Windows, you just right-click on a folder and click on the *share* tab.  No terminal or service work required.

---

### Post by irv on 2010-10-28
Have you ever thought about using UbuntuOne or DropBox. I use them both, and the nice things about this is no matter where I am or what ever computer I am on I can get to my files. I use it to transfer files from the Church PC to my home and the other way around. Both are easy to setup and use.

---

