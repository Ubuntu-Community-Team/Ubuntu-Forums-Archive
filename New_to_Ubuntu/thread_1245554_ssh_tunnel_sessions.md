---
title: "ssh tunnel sessions"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by Xubuntnoob on 2009-08-20
Hi, I've got a headless server in my basement running ubuntu 9.04 server.
I've got openssh setup on all my computers so i can tunnel into my server and start programs like rtorrent. Because my server is headless, it doesn't have a desktop environment so it's all CLI. How can I start programs through ssh and have them keep running when i close my terminal? The problem I seem to run into is like this example below.

nick@nicksbox$ssh 192.168.0.101
nick@storagebox password: ********
nick@storagebox$rtorrent
the program runs, 
but i can't close my terminal or I get the error "there is a program running, if you close this window, you will close the program as well"

or something to that effect.

should i run it in the backgrount? "rtorrent &&" <---- is that the background tag?

also, if i do run it in the background, how can i log in from another computer and bring up the same rtorrent session?

or am i just missing something completely.

thanks in advance!

Also, if i setup a desktop like gnome, i could use x11vnc, but i really don't want to have to start a desktop environment and log into x11vnc every time i want to add a torrent.

(rtorrent has that cool feature where it will scan a folder to see new torrents and auto start, but I haven't got that feature setup yet, and the situation described above is an issue for other programs i'd like to use as well)

---

### Post by zerhacke on 2009-08-20
It's been a while since I have had to do this, but I think if you press CTRL+Z it will shunt the active program on the CLI to the background.

---

### Post by scorp123 on 2009-08-20
> **Xubuntnoob said:**
> How can I start programs through ssh and have them keep running when i close my terminal?  ```
sudo apt-get install screen
```

Tutorial:

[http://www.debian-administration.org/articles/34](http://www.debian-administration.org/articles/34)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)

---

### Post by Xubuntnoob on 2009-08-21
> **scorp123 said:**
> ```
sudo apt-get install screen
```

Tutorial:

[http://www.debian-administration.org/articles/34](http://www.debian-administration.org/articles/34)
[http://www.kuro5hin.org/story/2004/3/9/16838/14935](http://www.kuro5hin.org/story/2004/3/9/16838/14935)



Perfect - Exactly what I was looking for.
Thank you!

---

