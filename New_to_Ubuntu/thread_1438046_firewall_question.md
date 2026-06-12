---
title: "firewall question"
date: 2010-03-24
forum: New to Ubuntu
---

### Post by now_here on 2010-03-24
so i want to configure the firewall, and i assume the best way to do that would be to disallow everything, and then selectively allow the programs i need. however i noticed that when i used ufw (i checked enable, and by default reject, with no additional rules), i was still able to access the web using firefox, and use transmission to download files. shouldn't this all be blocked until i specifically allow them?

---

### Post by andrewthomas on 2010-03-24
> **now_here said:**
>  shouldn't this all be blocked until i specifically allow them?It blocks all new incoming connections.  You can surf the web and use transmission because it does not block established incoming connections.
You can read this post for more info.  It is a great resource. [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by now_here on 2010-03-24
i'm not exactly sure what you mean by established incoming connections. if i start a new torrent should it be blocked? if i quit transmission, and open it again should it be blocked? if i restart the computer should it be blocked? 
everything i've tried to do to block it hasn't worked. if none of those should do it, how can i block transmission?

---

### Post by J V on 2010-03-24
You don't block transmission, you block reception.

You can send data to another computer, but they can't send it back to you unless one of your programs asked for it in the first place.

By default there are no apps listning on ubuntu ports, meaning no firewall neccesary unless you install a web server or something...

See premade post
> **Firewall**
Ubuntu comes with a fantastic firewall known as iptables. It is inactive by default, because no applications are "Listening" to the ports (Doorways) on your computer anyway, so there is no need for a firewall unless you install a server of sorts (And if you are installing servers you should know this already)

Iptables is actually very hard to configure, you need to edit configuration files, know the program, its just much more advanced. Luckily, there are tools that make this easy.

The most often advised firewall interface is "Firestarter", but nowadays its a bad idea to use it. It hasn't been developed for ages now, and because ufw (A command line configuration tool) is installed, Firestarter will conflict with already running services.

On top of that, while it runs, it runs as root, so if someone were to exploit a vulnerability in Firestarter, it would give them complete access to your system.

The current interface suggestion is "[gufw]("apt://gufw")" (Click to install) which, once again, is not a firewall, but a means to configure the default firewall.

---

### Post by JKyleOKC on 2010-03-24
If you don't want to use transmission at all, go to Synaptic and remove it. That will guarantee that it's blocked, since it won't be there to listen on any ports.

That's what I've done to all of my systems, since I don't use P2P at all for any purpose. The one time I tried it to download a Linux distribution, it was so much slower than the older FTP and HTTP downloads that I canceled it after the first hour of what should have been a 20-minute effort...

---

