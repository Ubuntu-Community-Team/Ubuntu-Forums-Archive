---
title: "need help with gnump3d media server"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by jmd9qs on 2009-02-04
hi all,

recently installed and successfully configured a new gnump3d server. its actually pretty cool... however, i'm a little worried about security. first of all, i realize i can block users by their ip address, but i want to be able to access from ANY computer (and allow family, friends to as well); thus it would be incredibly tedious to use ip verification. i've searched the web, and it seems as if the password option with gnump3d was canceled because it wasn't really very secure, and it didn't play well with various media players.

i'm not very good with this kind of thing, but i was trying to maybe have the index.html redirect to a login.php script i created (more like cut and pasted :D), and then verify from there. thinking about it though, i'm not sure if that's even possible. after that, i looked into .htaccess from apache2, but that was pretty confusing too.well, after a few hours of unsuccessful googling, i've given up.

can anyone suggest how i might require authentication to my server? is it even possible? i'd really like to think it is, and am hoping for a relatively simple solution (although i did learn a lot today:D)

thanks,

jmd9qs

edit-

p.s. - i'm also open to configuring the media server through something else. i don't care if i need to switch from gnump3d, even though it's kinda cool.

---

### Post by petervk on 2009-02-04
You could restrict the server to the localhost ip (127.0.0.1) and run everything through a ssh tunnel. This would require you to have either a static ip for your computer or to run a dynamic dns client on your router or computer. Also, before you could connect on the remote machine you would have to launch ssh (or putty) and setup the tunnel each time.

It would work, but it takes a bit of work to setup and you would have to run a ssh client on the computers you were accessing the information from. ssh would also put a bit of overhead into the stream as it encrypts all the data sent through it.

---

### Post by jmd9qs on 2009-02-04
thanks for the reply!

i had considered setting it up like that; however, the computers at my school are restricted in that, even if they had an ssh client, i would be unable to access it. also, i doubt if the admins would make an exception seeing how all i want to do is stream media.

i guess what i'm looking for is a way to force authentication on the server itself, so that to access you must enter a password (username + password would be preferred). i learned a little about MYSql last night and created a database for this purpose, i'm just absolutely clueless as to what needs to be done next

---

### Post by petervk on 2009-02-04
The thing with security is that it is hard to do right, and really, really easy to screw up. Geniuses wrote and maintain ssh so you can trust it.

Even if you use the ip address filter built into the gnump3d server anyone at that ip can still access your media. And at most locations many computers share one public ip address. (i.e. to access it from your school you would most likely have to add the school's public ip address to the allowed list, which would allow anyone on your school's network to access the server)

I think you can do proxying through php, but I don't know how it's done. Again, you would limit the ip connections to the localhost and use some php function/library to proxy the data from the public web to the localhost interface. Theoretically you could then authenticate against a mysql database. 

An issue with doing it via php/mysql/http is that unless you setup openssl (a https connection) the username and password will be sent in the clear and anyone on the school network will be able to see that data. Not that most people sniff network traffic, but if they did they would see the username and password.

The putty ssh client for windows doesn't need to be installed, it can be run from a usb key. Most "restricted" environments still allow the application to be run. They may have blocked port 22 (the ssh port), but all you need to do then is change the port on both the server and in the ssh client. Try the default first, if that doesn't work try something above 1024 (usually open above that) and if not try port 80, the http port which I will bet is open.

Putty download link:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by jmd9qs on 2009-02-04
thanks for the reply!

i didn't think about putty on a usb, i'll definitely try that, thanks!

i still don't really want to go the ssh route, though. i guess if it comes down to it, this thing doesn't really need to be that secure. what i'm looking for, in reality, is the *semblance* of security. if i could somehow have a simple html login page that would be accessed before the index.html (which i could't figure out how to do), i'd be happy. i don't plan on giving the server address out to many people so i'm not too worried, i just want it to at least LOOK secure, even if it won't fool the 
pros.

---

