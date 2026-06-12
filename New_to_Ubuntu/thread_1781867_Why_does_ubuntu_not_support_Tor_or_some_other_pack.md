---
title: "Why does ubuntu not support Tor or some other package"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by manners2345 on 2011-06-14
This question may tick off a few people or maybe a lot.
  
Since UBUNTU means "Humanity towards others".

 Various governments around the world are not being humane towards its citizens, Middle East, Burma, China, US is stepping up spying on citizens. 

Why does Ubuntu not support Tor or Tork or some other way, for ordinary people to have SECURE communications!!

I have tried for over 3 years to install. Cannot figure it out!!!

I have Tor portable tor for windows,on USB, flash drive. Have not figured out how to use skype on it

---

### Post by inameiname on 2011-06-14
Tor works just fine for me with Ubuntu. I can use it through Firefox or through the terminal just fine. 

1. Check out [http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en) for use with browsers. 
2. For Firefox, use the Torbutton, found here: [https://addons.mozilla.org/en-US/firefox/addon/torbutton/](https://addons.mozilla.org/en-US/firefox/addon/torbutton/).
3. And for the terminal, check this out: [http://www.webupd8.org/2010/10/how-to-set-proxy-for-terminal-quick.html](http://www.webupd8.org/2010/10/how-to-set-proxy-for-terminal-quick.html).

---

### Post by DanneStrat on 2011-06-14
> **manners2345 said:**
> This question may tick off a few people or maybe a lot.
  
Since UBUNTU means "Humanity towards others".

 Various governments around the world are not being humane towards its citizens, Middle East, Burma, China, US is stepping up spying on citizens. 

Why does Ubuntu not support Tor or Tork or some other way, for ordinary people to have SECURE communications!!

I have tried for over 3 years to install. Cannot figure it out!!!

I have Tor portable tor for windows,on USB, flash drive. Have not figured out how to use skype on it

There is an official tor package available for ubuntu. All you need to do is to add the tor repository to your software sources.

Go to system > administration > software sources

On the "other software" tab, add a new deb line like this

```
deb http://deb.torproject.org/torproject.org <DISTRIBUTION> main
```

Replace <DISTRIBUTION> with the codename of your ubuntu release(lucid, maverick etc.)

After this, open up terminal and import the repository key by doing:

```
gpg --keyserver keys.gnupg.net --recv 886DDD89 && gpg &#8211;export &#8211;armor 3E5C1192 | sudo apt-key add - && sudo apt-get update
```

Now install tor from the repository...

---

### Post by 3rdalbum on 2011-06-14
> **manners2345 said:**
> 

Why does Ubuntu not support Tor or Tork or some other way, for ordinary people to have SECURE communications!!

Tor does not allow for secure communications, it only allows for anonymous communications.

Tor can be spied on by governments or private organisations; all they need to do is create an exit node and they can see your traffic. They might not know yet whose traffic it is, but given enough information they might be able to make a guess.

> I have tried for over 3 years to install. Cannot figure it out!!!

I haven't tried it for a while, but have you looked for a HOWTO? I got it working a few years ago, it's easier than compiling software.

> I have Tor portable tor for windows,on USB, flash drive. Have not figured out how to use skype on it

I'm glad. You shouldn't use Tor for Skype; not only would the latency and packet loss be horrible for VoIP calls, but it would put an unreasonable amount of strain on the Tor network. IM-only, please; no voice calls.

---

### Post by jtarin on 2011-06-14
> **manners2345 said:**
> 
I have tried for over 3 years to install. Cannot figure it out!!!
He,he....are you that way with all software? That's tenacity!!!:p

---

### Post by manners2345 on 2011-06-14
Being Scottish, enough said!!!

---

### Post by manners2345 on 2011-06-14
OKAY I will not use Skype!!!

---

### Post by manners2345 on 2011-06-14
That is why if I could ever get it to run I do a relay, which is supposed to make it more secure.

---

### Post by manners2345 on 2011-06-14
I have done that, it is my repositories and the key

---

### Post by jtarin on 2011-06-14
[More complete instructions for installing in Ubuntu.]("https://www.torproject.org/docs/debian.html.en")

---

