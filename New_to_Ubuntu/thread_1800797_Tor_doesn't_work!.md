---
title: "Tor doesn't work!"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by ctult on 2011-07-09
I tried to install Tor.  It worked for a while, then just stopped working.  
When I try to restart Tor, it gives me this message:
```

root@bt:~/Desktop# /etc/init.d/tor restart
Stopping tor daemon: tor.
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Jul 09 13:12:08.989 [notice] Tor v0.2.1.30. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 09 13:12:08.993 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jul 09 13:12:08.994 [notice] Opening Socks listener on 127.0.0.1:9050
done.
root@bt:~/Desktop# 

```I also tried to use Privoxy.  It just said this:
```

root@bt:~/Desktop# /etc/init.d/privoxy restart
 * Restarting filtering proxy server privoxy                                                                                                          [fail] 
root@bt:~/Desktop#

```Please help!

EDIT: Privoxy works now.  It was because of Polipo.  But I still can't use it with Proxychains or Torbutton.

I still need help.

---

### Post by ubudog on 2011-07-09
Hmm... it appears Tor did indeed start.  Try this:

```
/etc/init.d/tor restart
```

Then, post the output of this:
```
ps ax | grep tor
```

---

### Post by ctult on 2011-07-09
1102 ?        S      0:04 /usr/sbin/tor
14538 pts/5    S+     0:00 grep --color=auto tor

---

### Post by ubudog on 2011-07-09
Yep, that shows it as running.  Be sure you installed it correctly though.  Here is a guide, I hope it helps:
[http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html](http://www.ubuntugeek.com/how-to-install-tor-to-surf-anonymously-in-ubuntu-feisty-with-firefox.html)

---

### Post by jtarin on 2011-07-09
[Here's a link that might help]("https://www.torproject.org/projects/torbrowser.html.en").

---

### Post by roodypoo on 2011-07-09
Open terminal and at the prompt type
```
sudo /etc/privoxy/config
```Then type in your password. Scroll down to the line
```
forward-socks5   /               127.0.0.1:9050 .
```and remove the # at the beginning of the line (leave the '.'). Then hit Ctrl-O and select yes, then Ctrl-x to exit. Then restart tor and privoxy and you should be good to go.

---

### Post by ctult on 2011-07-10
It still doesn't work.  It used to work, but now Torbutton just hangs.


> **roodypoo said:**
> Open terminal and at the prompt type
```
sudo /etc/privoxy/config
```

Don't you mean ```
sudo **nano** /etc/privoxy/config
```?

---

### Post by josephmills on 2011-07-10
> forward-socks5   /               127.0.0.1:9050 .  

I think that this is just proxying you to your own home address I could be wrong though I am also learning from this thread.

---

