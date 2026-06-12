---
title: "Run local application through php script"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by stiankarlsen on 2006-09-27
I'm wondering if its possible to put a php script on my webserver that can execute a command starting for isntance vlc on my computer. This was achievable in windows by using the command below, but i had to enable, or give php permissions if you will, to interact with my system like that. Anyone know how I can do something [similar]("http://www.theeldergeek.com/images/Services/Svc03.gif") in linux?

[PHP]system("(start /usr/bin/konqueror) >nul");

//or somethings like

$command= system("/usr/bin/vlc &#8211;intf=http");
echo $command;[/PHP]

---

### Post by djRobbieF on 2006-09-27
PHP is server-side.  So you could launch things on the SERVER, but not on your computer.

---

### Post by stiankarlsen on 2006-09-29
Well, the computer is the server.

---

