---
title: "Tor Repository not working on Jaunty?"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-19
I try to add the Tor repositories to my sources using the information on this [page]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian").

Though I have tried several times, editing to include jaunty in the url, I get an error message when I try and refresh the sources list.

Now my sources list is broken and won´t work at all! :(

I wonder where I went wrong.

---

### Post by halitech on 2009-04-19
can you post your sources.list file so we can take a look plus any errors you are getting

```
cat /etc/apt/sources.list
```

---

### Post by Berserker v7 on 2009-04-19
In Ubuntu 8.10, Tor comes with the official cd image and you wouldnt have to add any other repositories. Dunno if the same holds with 9.04 beta.

---

### Post by halitech on 2009-04-19
from the tor website

> Do not use the packages in ubuntu's universe. They are not maintained and most likely old and therefore miss out on stability and possibly security fixes.

---

### Post by yeehi on 2009-04-19
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) experimental-0.2.1.x-<jaunty>main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) experimental-0.2.1.x-<jaunty> main

Here it is!
btw, if you can think of some  other nice repos for me to add, please let me know :)

---

### Post by halitech on 2009-04-19
for the last 2 lines, change it to this if you want the experimental version. 
```
deb http://mirror.noreply.org/pub/tor experimental-0.2.1.x-jaunty main
deb-src http://mirror.noreply.org/pub/tor experimental-0.2.1.x-jaunty main 
```

personally I would recommend the stable release and remove those 2 lines and add
```
  deb     http://mirror.noreply.org/pub/tor jaunty main
  deb-src http://mirror.noreply.org/pub/tor jaunty main
```

looking on the site, they don't mention jaunty so it may not work

---

### Post by yeehi on 2009-04-19
> Failed to fetch [http://mirror.noreply.org/pub/tor/dists/experimental-0.2.1.x-jaunty/main/binary-amd64/Packages](http://mirror.noreply.org/pub/tor/dists/experimental-0.2.1.x-jaunty/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/experimental-0.2.1.x-jaunty/main/source/Sources](http://mirror.noreply.org/pub/tor/dists/experimental-0.2.1.x-jaunty/main/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I get this error...

---

### Post by halitech on 2009-04-19
did you try the stable package? They may not have a version released yet for jaunty.

---

### Post by yeehi on 2009-04-19
> Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-amd64/Packages](http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-amd64/Packages)  404 Not Found
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources](http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The stable route didn´t work either.

This is all rather strange. A few days ago, I managed to get OperaTor working on Jaunty.  Now if I download it, it seems not to be able to run...

---

### Post by halitech on 2009-04-19
I would hazard a guess they don't have jaunty up yet then.

what happens if you open a terminal and try and run it?

---

### Post by yeehi on 2009-04-19
Some good news! I hadn´t installed Wine, which I think I needed to use to run the OperaTor.exe. I can now run OperaTor with Tor functioning, and I have verified that Tor is working.

The problem for me now is that Vidalia cannot find the Tor executable. I unzipped OperaTor into a download folder in my /home/me folder. I try to manually set the route to the tor.exe there, but it won´t work. I guess that the Tor button extension won´t work either.

What do I need to do?

Thank you! :)

---

### Post by sefs on 2009-04-19
Traditionally Tor repos lag about approx. 1 month after the offical ubuntu release.  

What I do is to continue to use the repos for the previous release until they have set up the repos for the current release.  I check back occasionally and sooner or later they have them up and running.

I am on Jaunty currently and have installed tor from the intrepid repos, and before that i would have installed hardy tor to intrepid and so on.

I never experienced any problems doing this.

So since they are no official jaunty repos from tor as yet thats why you get the error when changing the line in sources.list to jaunty.

I however seem to recall there may also be an ubuntu person/team maybe on launchpad who actively packages tor for ubuntu, which is probably what is present in each release, or maybe you can search launchpad ([http://launchpad.net](http://launchpad.net)) for tor

---

### Post by sefs on 2009-04-30
Tor just updated their repos to reflect jaunty....

[http://mirror.noreply.org/pub/tor/dists/](http://mirror.noreply.org/pub/tor/dists/)


The repos would be

```

deb http://mirror.noreply.org/pub/tor jaunty  main
deb-src http://mirror.noreply.org/pub/tor jaunty main

```

---

### Post by asbesto on 2009-07-21
Ok, and what about the key?

> W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: You may want to run apt-get update to correct these problems


](*,)

---

### Post by husunzi on 2009-07-26
> **asbesto said:**
> Ok, and what about the key?

> W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: You may want to run apt-get update to correct these problems



Yes, I'm having the same problem. Running apt-get update doesn't seem to work. After adding the repos to the sources list & getting that error message, when I try to apt-get install tor anyway, this is what I get:

```
husunzi@husunzi-laptop:~$ sudo apt-get install tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libevent1 socat tor-geoipdb tsocks
Suggested packages:
  mixmaster mixminion anon-proxy
The following NEW packages will be installed:
  libevent1 socat tor tor-geoipdb tsocks
0 upgraded, 5 newly installed, 0 to remove and 2 not upgraded.
Need to get 2623kB of archives.
After this operation, 6746kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tor tor-geoipdb
Install these packages without verification [y/N]? y
Get:1 http://ubuntu.dormforce.net jaunty/main libevent1 1.3e-3 [44.7kB]
Get:2 http://ubuntu.dormforce.net jaunty/universe tsocks 1.8beta5-9.1 [276kB]  
Err http://mirror.noreply.org jaunty/main tor 0.2.0.35-1~jaunty+1
  404 Not Found
Err http://mirror.noreply.org jaunty/main tor-geoipdb 0.2.0.35-1~jaunty+1
  404 Not Found
Get:3 http://ubuntu.dormforce.net jaunty/universe socat 1.6.0.1-1 [315kB]
Fetched 636kB in 4s (128kB/s) 
Failed to fetch http://mirror.noreply.org/pub/tor/pool/jaunty/tor_0.2.0.35-1~jaunty+1_i386.deb  404 Not Found
Failed to fetch http://mirror.noreply.org/pub/tor/pool/jaunty/tor-geoipdb_0.2.0.35-1~jaunty+1_all.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
husunzi@husunzi-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
```


I also tried installing an older version of tor from [here]("http://packages.ubuntu.com/intrepid/i386/tor/download"), & that seemed to work, but when I try to run that through Vidalia (which is included in the basic Jaunty repos, along with Privoxy & Torbutton, just not Tor), I get the following error log from Vidalia:

> Jul 26 18:14:03.163 [Notice] Tor v0.2.0.31 (r16744). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Jul 26 18:14:03.311 [Notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 26 18:14:03.312 [Notice] Opening Socks listener on 127.0.0.1:9050
Jul 26 18:14:03.313 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Jul 26 18:14:03.313 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Jul 26 18:14:03.313 [Error] Reading config failed--see warnings above.


Not sure if that means I'm already running Tor, but I don't seem to be, since it doesn't appear in the system monitor under the name "tor," & when I enable Torbutton in Firefox & go to "whatismyip.com," my IP hasn't changed. 

(Something I don't understand is why I'm able to access anything with Torbutton enabled [& I checked my Firefox network settings to make sure it was enabled], & why I get a Privoxy "503 - connect failed" page when I try to go to blocked pages [I'm in China, by the way], including [the official Tor test page]("http://serifos.eecs.harvard.edu/cgi-bin/ipaddr.pl?tor=1"). I only get that Privoxy error page when going to blocked websites; unblocked websites open normally. When I disable torbutton, blocked websites instead give the usual "page load error" message. Another strange thing is that Privoxy doesn't appear in my system monitor either - perhaps the Privoxy error page just reflects the fact I'm using Torbutton?)

When I try to run tor through the command line, I get the same error message as I got from Vidalia (above).

Any suggestions about how I can use at least some version of Tor in Jaunty? Please put any directions into as simple terms as possible.

---

### Post by mshtawythug on 2010-01-24
this is how you solve it open Terminal 

```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

```

---

