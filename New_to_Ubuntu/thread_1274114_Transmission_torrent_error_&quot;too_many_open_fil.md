---
title: "Transmission torrent error: &quot;too many open files&quot;"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-09-24
I randomly get an error on some torrent files in Transmission:
```

too many open files

```

Usually, clicking on "Start" resolves this error. Any thoughts?

---

### Post by ankspo71 on 2009-09-24
Hi,
I haven't personally seen that error in transmission before, but I found a link that might have a possible solution for you.
[https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/406486](https://bugs.launchpad.net/ubuntu/+source/transmission/+bug/406486)
Hope this helps.
James

---

### Post by abhiroopb on 2009-09-24
Thanks that was really helpful! Usually I ignore Launchpad bug reports as they are VERY long and don't really have any conclusion, but glad this helped. Of course I don't know if this worked (will have to add torrents and see if the error appears again).

The fix is:

```

$ sudo -s
$ echo "* - nofile 1536" >> /etc/security/limits.conf
$ exit

```

---

### Post by cmcanulty on 2009-09-24
I get permission denied on that even though I did sudo and password.

---

### Post by ankspo71 on 2009-09-24
Hi cmcanulty,
If the above codes don't work you could always open the file directly.
```
sudo gedit /etc/security/limits.conf
```
Then add the following line to the end of limits.conf .
```
* - nofile 1536
``` 
So that it appears like this:
> 
#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

# End of file
* - nofile 1536
Hope that helps.
James

---

### Post by hosts on 2012-04-08
the sugestion of ankspo71
worked for me

thanks

:guitar:

---

### Post by overdrank on 2012-04-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

