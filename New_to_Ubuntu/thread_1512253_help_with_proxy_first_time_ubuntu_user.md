---
title: "help with proxy? first time ubuntu user"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by acornty on 2010-06-17
so I've just started using ubuntu and I'm LOVING it. it's way better then vista in my opinion :). everythings working fine, had a bit of network troubles at the begining, but thats been sorted out. my question now is how to use a proxy with ubuntu. everytime i search for one i get taken to a proxy called "squid" i looked up tutorials on how to download, install, and configure it and i still just cant figure it out. is this the right proxy i should be using? is their another? when i was using vista, i used tor and apparently it can be used with ubuntu but like i said i just started using it so its super confusing to me lol.  also here's some details on my computer. dell inspiron 1545. ubuntu installed with wubi so i can dual boot to vista or ubuntu. as far as i know, I'm using the latest version of ubuntu. is there any other information i can give you guys? if so please tell me. thanks!

---

### Post by alphacrucis2 on 2010-06-17
> **acornty said:**
> so I've just started using ubuntu and I'm LOVING it. it's way better then vista in my opinion :). everythings working fine, had a bit of network troubles at the begining, but thats been sorted out. my question now is how to use a proxy with ubuntu. everytime i search for one i get taken to a proxy called "squid" i looked up tutorials on how to download, install, and configure it and i still just cant figure it out. is this the right proxy i should be using? is their another? when i was using vista, i used tor and apparently it can be used with ubuntu but like i said i just started using it so its super confusing to me lol.  also here's some details on my computer. dell inspiron 1545. ubuntu installed with wubi so i can dual boot to vista or ubuntu. as far as i know, I'm using the latest version of ubuntu. is there any other information i can give you guys? if so please tell me. thanks!

Installing it? Very easy - just ```
sudo apt-get install squid
```

Configuring it can be quite complicated but IIRC the default config file contains a lot of information in comment lines about what to put where. There may be graphical front ends such as webmin that make it easier to configure but I don't know how well that works with Ubuntu.

---

### Post by acornty on 2010-06-17
> **alphacrucis2 said:**
> Installing it? Very easy - just ```
sudo apt-get install squid
```Configuring it can be quite complicated but IIRC the default config file contains a lot of information in comment lines about what to put where. There may be graphical front ends such as webmin that make it easier to configure but I don't know how well that works with Ubuntu.
it seems to easy....lol thanks! but what do i do from there? like i said I'm a total noob :p

---

### Post by alphacrucis2 on 2010-06-17
> **acornty said:**
> it seems to easy....lol thanks! but what do i do from there? like i said I'm a total noob :p

When you want to install programs in Ubuntu, the first place to look is the Ubuntu repositories as the software in there is packaged specifically for Ubuntu. There are other sources designed for Ubuntu such as Medibuntu, Getdeb and various PPA's on launchpad.net. Only after having no success there would you resort to attempting other installation methods like downloading from the website of the program developer. You can see what's available in you Ubuntu repositories by looking in applications - Ubuntu Software Center, or if you want to know a bit more about what is going on you can run Synaptic under System - Administration - Synaptic Package manager. The method I gave is to use a terminal command which is actually easier to explain via a forum post as you can just copy and paste the command into the terminal. Once squid is installed, what you do next depends on what you are trying to achieve with squid. The config file, by the way, is called /etc/squid/squid.conf. If you open via ```
gksu gedit /etc/squid/squid.conf
```, you will be able to see what is in the default config. Don't change anything initially just have a look. It would also be advised to make a backup copy of the file.

---

### Post by bodhi.zazen on 2010-06-18
There are several proxies you can use, one question would be what do you want to use a proxy for ?

As an alternate to squid, I suggest you look at Privoxy.

Privoxy is very easy to install and configure, easier then squid. Privoxy offers, IMO, better privacy and superior add blocking.

IMO squid is best if you are on a LAN and have several clients you need to proxy.

```
sudo apt-get install privoxy
```Then point firefox to use localhost port 8118 ;)

See:

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

Privoxy can be configured via the web gui interface, but it is unlikely you will need to do much, if anything, with the defaults.

Squid is a nice tool, but it is a bit complex and last time I looked the config file was several thousand lines long, lol

---

### Post by jimv on 2010-06-18
Why are you guys telling him how to install Squid when he wants a program like Tor?  Squid is if you want to run your own proxy, which I'm pretty sure you're not wanting to do.  You want to use a proxy.

See these instructions: [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

---

### Post by bodhi.zazen on 2010-06-18
> **jimv said:**
> Why are you guys telling him how to install Squid when he wants a program like Tor?  Squid is if you want to run your own proxy, which I'm pretty sure you're not wanting to do.  You want to use a proxy.

See these instructions: [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

That is why I asked what the OP wanted to use a proxy for.

Squid is quite flexible and can be used for several purposes, but in general squid is over kill.

TOR increases privacy, but does not have adblock ...

We really need to understand the purpose of the proxy.

---

### Post by acornty on 2010-06-18
well i tried to install Tor because thats what i used to use on vista and it did exactly what i wanted it to do, keep my browsing habits private, but i got very lost at the part where it says to add ```
deb     http://deb.torproject.org/torproject.org <DISTRIBUTION> main
``` in the /etc/apt/sources.list file. [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) that's the guide i tried to follow. I'm trying to follow option 2.

---

### Post by bodhi.zazen on 2010-06-18
Honestly, IMO, the easiest way to use TOR is via the bundle

[http://www.torproject.org/torbrowser/dist/linux/](http://www.torproject.org/torbrowser/dist/linux/)

[http://www.torproject.org/torbrowser/dist/linux/tor-browser-gnu-linux-i686-1.0.7-dev-en-US.tar.gz](http://www.torproject.org/torbrowser/dist/linux/tor-browser-gnu-linux-i686-1.0.7-dev-en-US.tar.gz)

[http://www.torproject.org/torbrowser/dist/linux/tor-browser-gnu-linux-x86_64-1.0.7-dev-en-US.tar.gz](http://www.torproject.org/torbrowser/dist/linux/tor-browser-gnu-linux-x86_64-1.0.7-dev-en-US.tar.gz)

You extract the archive

cd tor-browser-en-US

./start-tor-browser

---

### Post by alphacrucis2 on 2010-06-18
> **acornty said:**
> well i tried to install Tor because thats what i used to use on vista and it did exactly what i wanted it to do, keep my browsing habits private, but i got very lost at the part where it says to add ```
deb     http://deb.torproject.org/torproject.org <DISTRIBUTION> main
``` in the /etc/apt/sources.list file. [https://www.torproject.org/docs/debian](https://www.torproject.org/docs/debian) that's the guide i tried to follow. I'm trying to follow option 2.

Just start System Adminstration Software Sources. Click the 'Other Software' tab and click Add. Copy the line below

```
deb  http://deb.torproject.org/torproject.org lucid main
```

and paste into the APT line displayed by the Software Sources program.

assuming you are running lucid. Ie you replace <DISTRIBUTION> with the version you are running. The two gpg lines import the authentication keys so your package manager will accept the torproject repository.

Edit: There is a slight error on that page. You have to put sudo in front of the two apt-get lines. Anyway I have successfully installed tor following that page. BTW sorry I was misled by your question about squid. squid is a proxy server not a proxy client like tor.

---

### Post by acornty on 2010-06-18
> **alphacrucis2 said:**
> Just start System Adminstration Software Sources. Click the 'Other Software' tab and click Add. Copy the line below

```
deb  http://deb.torproject.org/torproject.org lucid main
```and paste into the APT line displayed by the Software Sources program.

assuming you are running lucid. Ie you replace <DISTRIBUTION> with the version you are running. The two gpg lines import the authentication keys so your package manager will accept the torproject repository.

Edit: There is a slight error on that page. You have to put sudo in front of the two apt-get lines. Anyway I have successfully installed tor following that page. BTW sorry I was misled by your question about squid. squid is a proxy server not a proxy client like tor.
ahh ok thanks! I'll try it out later today.
EDIT: ok so i succesfully installed tor, i think. i use the terminal to  start tor by typing tor. but then it gives me this error. > Jun 18 12:01:03.585 [notice] Tor v0.2.1.26. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jun 18 12:01:03.587 [notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Jun 18 12:01:03.587 [notice] Opening Socks listener on 127.0.0.1:9050
Jun 18 12:01:03.587 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jun 18 12:01:03.587 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Jun 18 12:01:03.587 [err] Reading config failed--see warnings above.


---

