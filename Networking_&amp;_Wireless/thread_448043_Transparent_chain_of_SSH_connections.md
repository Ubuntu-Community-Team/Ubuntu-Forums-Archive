---
title: "Transparent chain of SSH connections"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by lauge on 2007-05-18
Hi,

I have a problem: A friend of mine is hosting a server on a closed network in his dorm. There is access to his computer from the university we're at (since they are on the same network), but not from my appartment down town.


**My home -> Uni -> His dorm**


Now, I can SSH from home to uni, and from there to his computer, but I can't figure out how to do this transparently (like by using the 'Connect to Server...' tool).

Is there a clever way to do this without needing to install anything on the computer I connect to on Uni (which I don't have permission to do)


Thanks in advance,
Lauge

---

### Post by ricrac on 2007-05-18
transparently and clever, I am not sure what you mean.

You could use keys and port forwarding, wrap it in a script if needed.

---

### Post by lauge on 2007-05-18
Sorry, perhaps I should have stated in my initial post that I have VERY little experience with SSH.

Keys and port forwarding, you say, how would I do that?

---

### Post by ricrac on 2007-05-19
I have no idea what you're trying to do by your post, and there will be many ways to do it once I know.

Transparent chain of ssh implies you are using ssh twice, once to connect to the university, once more to connect to your friends machine.

Univ - 10.0.0.1
friend's server - 192.168.1.1
web server on friend's machine running on port 80 only available locally, 127.0.0.1

These two in a script.
ssh  -l myuserid  -L 7777:192.168.1.1:22  10.0.0.1  cat -
ssh -l myuserid -L 8888:localhost:80 localhost:7777 cat- 

lynx localhost:8888 displays web page from friends web server.

If your friend's server is available to the univ you may need only one ssh.
ssh  -l myuserid  -L 8888:192.168.1.1:80  10.0.0.1  cat -
lynx localhost:8888 displays web page from friends web server.


You throw in odd ports (8888,7777) so not to stomp on the same port potentially being used locally.

Search for ssh tunneling or ssh port forwarding...
[http://www.rzg.mpg.de/networking/tunnelling.html](http://www.rzg.mpg.de/networking/tunnelling.html)
[http://www.ccs.neu.edu/howto/howto-sshtunnel.html](http://www.ccs.neu.edu/howto/howto-sshtunnel.html)

---

### Post by lauge on 2007-05-21
Ok:

1] I can SSH from my computer to the computers on UNI
2] I can SSH from the computers on UNI to my friends computer
3] I need to be able to copy files from and to my friends computer

In ubuntu you can go to the top of your screen and click in the bar there on **Places**. In that menu you can click on **Connect to sever...**. In the windows that appears you can mount, amongst other things; SSH connections.

When you open such a connection you get a window listing the contents of a folder on that remote connection. The _clever_ part is that you can copy files into, and out from, this window just as if the folder was located on your own computer. That is what I call _transparrency_ (Wikipedia: [http://en.wikipedia.org/wiki/Transparency_%28computing%29]("http://en.wikipedia.org/wiki/Transparency_%28computing%29"))


My only question is: Can this be done through a chain of SSH connections?

---

### Post by ricrac on 2007-06-24
Yes.

Either exec the second ssh from the first.  Bad, UNI should fix so this is NOT allowed.
Port forward, using local .ssh/config
"Connect to" UNI with a port forward for the friends computer 
"Connect to" friends computer over forwarded port.
```

#Start of /home/username/.ssh/config
Host UNIwithforward
    Hostname UNI
    Port 22
    User username
    Localforward 127.0.0.1:2222 friends_ip:22
    ServerAliveInterval 60
Host friend
    Hostname 127.0.0.1
    User username
    Port 2222
    ServerAliveInterval 60
#End of /home/username/.ssh/config

Use:
	ssh UNI
	ssh friend
Or 
  "Connect to" UNI,  establish connection, then
  "Connect to" friend

```

See my other post for more info [http://ubuntuforums.org/showthread.php?t=483294](http://ubuntuforums.org/showthread.php?t=483294)

---

