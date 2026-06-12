---
title: "How to install Vidalia (Tor GUI) on Ubuntu 9.04?"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by jimerik on 2009-04-24
Can anyone make a "dummy"-description on how to do this? 
All I can find about this is some complicated explanations with compiling etc, and Im a newbie so that goes above my head.

I have already installed Tor/privoxi, and would just like to put Vidalia on top of that, like I use to do in windows.

---

### Post by jimmy the saint on 2009-04-24
[http://www.google.com/#hl=en&q=vidalia+linux&btnG=Google+Search&aq=f&oq=vidalia+linux&fp=LzBiHd3LsCY](http://www.google.com/#hl=en&q=vidalia+linux&btnG=Google+Search&aq=f&oq=vidalia+linux&fp=LzBiHd3LsCY)

Google is your friend

[http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html](http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html)

should be the third result

---

### Post by norcal on 2009-04-24
I would appreciate any help in showing me how to socksify stunnel so it uses tor. i tried torsocks but am lost, it says usewithtor [application], all i get is Pidgen not found for example.

---

### Post by MasterNetra on 2009-04-28
Vidalia is in Ubuntu's repo O.o Should be easy install it would seem.

---

### Post by aNaRcHiSt on 2009-05-03
> **aNaRcHiSt said:**
> Just add

```
deb http://mirror.noreply.org/pub/tor jaunty main
deb-src http://mirror.noreply.org/pub/tor jaunty main

```

to /etc/apt/sources.list

then

apt-get update
apt-get install tor

From another thread.

---

### Post by k0shi on 2009-05-09
Before for some reason I could not download TOR from the repositories, even after updating /etc/apt/sources.list

The follow commands are what I used in order to get everything working properly.

```
sudo apt-get install libevent1 libevent-dev libssl-dev zlib1g-dev vidalia && wget http://www.torproject.org/dist/tor-0.2.1.14-rc.tar.gz && tar zxvf tor-0.2.1.14-rc.tar.gz && cd tor-0.2.1.14-rc && ./configure && make && sudo make install
```

Worked for me.

[http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html](http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html)

Older info, still works, just download the newest version of everything.

After doing all of this I found that I was able to install TOR & Vidalia both from the repositories...still not sure what my problem was before even after properly updating my sources. Hopefully this has helped.

---

### Post by Artemis3 on 2009-05-12
> Add these lines to ‘/etc/apt/sources.list’ with your favorite text-editor.

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

Next open the terminal and do the following to make sure the system sees the new repos as ‘trusted’.

gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -

And update with ’sudo aptitude update’. Now install Tor with ’sudo aptitude install tor’.

The Tor package has mysteriously disappeared from 9.04 repositories...

---

### Post by 1nfinitel00p on 2009-05-14
> **k0shi said:**
> Before for some reason I could not download TOR from the repositories, even after updating /etc/apt/sources.list

The follow commands are what I used in order to get everything working properly.

```
sudo apt-get install libevent1 libevent-dev libssl-dev zlib1g-dev vidalia && wget http://www.torproject.org/dist/tor-0.2.1.14-rc.tar.gz && tar zxvf tor-0.2.1.14-rc.tar.gz && cd tor-0.2.1.14-rc && ./configure && make && sudo make install
```Worked for me.

[http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html](http://onlyubuntu.blogspot.com/2008/03/howto-setup-vidalia-tor-gui-with-ubuntu.html)

Older info, still works, just download the newest version of everything.

After doing all of this I found that I was able to install TOR & Vidalia both from the repositories...still not sure what my problem was before even after properly updating my sources. Hopefully this has helped.


I always get  the same problem no matter what version, I get this message p, li { white-space: pre-wrap; }  Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.
then I go to settings and it shows this path /home/user/libevent-1.4.10-stable/tor-0.2.0.22-rc/contrib/tor-ctrl.sh 

and I also try changing to this path /home/user/tor-0.2.1.14-rc/contrib/tor-ctrl.sh but nothing it seems that the problem is the libevent version because you can see that the default path is libevent-1.4.10-stable/TOR-0.2.0.22-RC not 0.2.1.14-RC so what can I do? 
thanks in advance

---

### Post by 1nfinitel00p on 2009-05-14
> **MasterNetra said:**
> Vidalia is in Ubuntu's repo O.o Should be easy install it would seem.


Hi did you were able to install vidalia on jaunty?

I get a message  when I want to execute Tor 
 p, li { white-space: pre-wrap; }  Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified.
and this is the default path of the executable file, Idk whats missing

/tor-0.2.1.14-rc/contrib/tor-ctrl.sh

---

### Post by Sef on 2009-05-14
> The Tor package has mysteriously disappeared from 9.04 repositories...

No one was maintaining it, so it was outdated.   There is another thread on this that has a link to PPA repos for Tor.  If I find it,  i will post it.

---

### Post by 1nfinitel00p on 2009-05-16
> **Sef said:**
> No one was maintaining it, so it was outdated.   There is another thread on this that has a link to PPA repos for Tor.  If I find it,  i will post it.

yes please! this thing is driving me crazy, now I changed the excutable path to usr/local/bin/tor and now I get a different error:

May 16 05:08:22.809 [Notice] Tor v0.2.1.14-rc (r19307). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)

May 16 05:08:22.809 [Notice] Initialized libevent version 1.3e using method epoll. Good.

May 16 05:08:22.809 [Notice] Opening Socks listener on 127.0.0.1:9050

May 16 05:08:22.810 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?

May 16 05:08:22.810 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.

May 16 05:08:22.810 [Error] Reading config failed--see warnings above.

----------------------------------------------------------------------------------------------------------

---

### Post by Sef on 2009-05-17
Found a site with the [PPA]("http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/").  Not what i was looking for, but there was something in here not long ago.

---

### Post by kehon on 2009-06-09
searched found this and i need help on it tor wont launch says something about the config cant be found can anyone help with this

---

### Post by husunzi on 2009-11-11
Tor is still not available in the repositories for Karmic (9.10), although Vidalia is, but I'm still getting the same "Vidalia was unable to start Tor" message. Either the Vidalia in the repositories doesn't include Tor (strange, since Tor is the central component), or there's another problem. I had tried [this Jaunty fix]("http://ubuntuforums.org/showpost.php?p=7832839&postcount=10") before, but it still didn't work (after it apparently installed, Vidalia continued to say "unable to start Tor), same as several other people on these threads. Any suggestions? Will Tor or a working Vidalia ever be returned to the Ubuntu repositories? This is essential for people living in countries where important websites are blocked (regular proxies don't work for a lot of things).

---

### Post by kehon on 2009-11-11
goto the tor website an they have instruction for installing in ubuntu and debian they even have a repo for karmic. Also when you install tor then you can install vidalia because vidalia installs with or without tor

---

