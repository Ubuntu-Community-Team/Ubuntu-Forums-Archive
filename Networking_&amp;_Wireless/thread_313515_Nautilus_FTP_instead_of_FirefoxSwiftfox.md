---
title: "Nautilus FTP instead of Firefox/Swiftfox"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by iraiscoming223 on 2006-12-06
Hello everybody!
I've always been using Nautilus as my default FTP client.
From some days on, Ubuntu tends to open every FTP address with Firefox (Swiftfox), with no way to get nautilus working ("Nautilus cannot display ####### - Please select another viewer and try again")..
How could I get it back to work?
Thank you in advance!
Marco

P.s.(I've tried to use "Open with other application" command, but as long ftp is a network place and not an application this command is not shown in the "context menu").

---

### Post by Myrgen on 2006-12-07
I have the same problem, and this is how I solved it:

1) Get the icons for your ftp servers in your Network Servers Nautilus windows by using Places ->Connect to Server: enter the ftp (with login) or Public ftp  server address, other relevant informations, and a Name to use for that connection. Click connect.

2) Click on Places--> Network Servers.

3) Right click on the icon of the server you want to go to, and select: Open in new window. 

And voila: it opens in Nautilus.

Hope that helps!

---

### Post by iraiscoming223 on 2006-12-09
All right!!! This works fine!! THANK YOU SO MUCH!
Anyway, it's a "bitchy" way... It was so confortable a double-clik con the icon on my desktop...
Did you also find a way to set nautilus as default ftp server? :confused: 

eheheh :mrgreen:

---

### Post by lamelos on 2008-02-05
To set Nautilus as the default application for opening FTP:

[LIST=1]
[*]Open up your terminal by hitting ALT+F2 and typing
```
terminal
```
[*]type 'gconf-editor' and hit return
```
gconf-editor
```
[*]Browse to "desktop -> gnome -> url-handlers -> ftp"
[*]Change the value of command to your desired application. For Nautilus use:
```
nautilus "%s"
```
[*]Close gconf-editor and watch the result by double-clicking on one of your network places on your desktop. Have fun!
[/LIST]

---

### Post by ganglio on 2008-04-15
> **lamelos said:**
> To set Nautilus as the default application for opening FTP:

Thanks a lot mate!

I needed to install Opera for working reasons and it messed up with my configurations.
Now everything is fixed again (and I've discovered an amazing command :þ )

---

