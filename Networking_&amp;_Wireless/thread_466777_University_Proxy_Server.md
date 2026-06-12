---
title: "University Proxy Server"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by nathanernest on 2007-06-07
Hey All!

I am not "new" to linux but I still consider myself basic with it.

I am duel booting my machine with vista and ubuntu 7.04. I am having problems with installing programs on my machine.

I am trying to install automatix and I get an error message saying that I do not have the proper dependencies. After some looking on the net, it turns out that the problem is my network. I am behind a authenticating proxy server at my university.

I CAN get firefox to go to the internet, but nothing else! 

What is happening is, when I try to install, the program looks online to download the updates I need before compiling/installing the program.

So, how can i get the package manager or, whatever to talk through the proxy server?

When I installed automatix last time, I was at home WITHOUT the proxy server and it worked great!!

Please Help Me!!

Nath

---

### Post by swoll1980 on 2007-06-07
You can hit  either f10 or f12 when your in your browser it's one of those. You will get an option to bypass the proxy server

---

### Post by nathanernest on 2007-06-07
What do you mean "bypass" the proxy? I need to talk through it.
Which browser do you mean? Web browser like firefox, or do you mean the xclient?
Sorry I don't understand??

Nath

---

### Post by davelitt68 on 2007-06-07
Are you using apt-get to download your programs?  If so you may need to go to a terminal session and enter 
**[SIZE="3"]export http_proxy='http://server: port'[/SIZE]**
BTW there isn't a space between : and port but because of the smilies I couldn't write :port.

---

### Post by sickrandir on 2007-06-07
If you are in gnome you can also go in System->Preferences->Network Proxy and use the gui to configure the exact URL of your University proxy.
I always use that tool at my university!

---

### Post by nathanernest on 2007-06-07
Thanks for all the help, BUT...
I have already tried entering the data into the System--> Preferences .... and didn't help me.
And to davelitt68, I am trying to install automatix to help me choose which packages to install so i dont actually know how the thing is installing. Also, remember that this is an autheticating proxy server so where do i enter the username and password?

---

### Post by davelitt68 on 2007-06-07
Ok try this then
export http_proxy='http://user:password@server:port'

---

### Post by nathanernest on 2007-06-07
Great, I'll try that!! lol faces

---

### Post by nathanernest on 2007-06-08
Hey guys, this still doesn't work! Any other ideas?
The actual error i am receiving is "error 404? proxy authentication required."

Nath

---

### Post by nathanernest on 2007-06-08
To me it sounds like the uni is blocking the ports that ubuntu. If anyone else agrees then I will email the ITS dept.

---

### Post by nathanernest on 2007-06-14
Hey guys :( .....
Still no luck :( :( :(
Really really really starting to annoy me.
If anyone else thinks this is a problem that isn't really a ubuntu problem but rather a uni problem then let me know. I want to be sure before i contact ITS

---

