---
title: "How to use SQL Server 2008 Database and ASP.NET Project"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by atarikg on 2009-04-29
Hi

I am new in Ubuntu. It's been 1 day since my first installation of Ubuntu after removing Windows and I liked Ubuntu. Whatver.

I have a .net 3.5 project when I was developing under Windows and now I am using Ubuntu and don't know how to keep it developing.

What programs do I need  and how can I use them ?

- I don't know which program I need but I need a server,IDE and ms sql server. 

Thanks in advance.

---

### Post by original_jamingrit on 2009-05-01
[http://mono-project.com/Main_Page](http://mono-project.com/Main_Page)

This should be what you're looking for, but be sure to read the webpage a bit more.

---

### Post by Delever on 2009-05-01
You can run [monodevelop]("apt://monodevelop") to develop asp.net application, it is close, but not there yet. You can actually host your existing project under apache by installing [mod_mono]("apt://libapache2-mod-mono") module. I don't know actual configuration details, but they should not be too hard to find.

What you can't do is running MSSQL server under linux. You might be able to access it over network, if you have MSSQL server running on another computer. If you want to develop on Ubuntu, I suggest moving to different database, like MySQL, or making your project to support several databases. It may be hard to find hosting that has MySQL with ASP.NET, so have that in mind.

Personally I am using Visual Studio in Windows virtual machine (VirtualBox) to develop for ASP.NET. That gives me the same platform that my site is going to run on, so I have no surprises.

---

