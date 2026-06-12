---
title: "Established connection but no access to Internet"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by lotharlorraine on 2014-02-26
Hello folks.
 
I am utterly hopeless and truly hope that someone will be able to help me. 


 After having installed Ubuntu on my THREE computers home, I have (during the three next weeks) no problem to access to Internet. 
 
But then I have no longer any access to any Internet page. 

While the network (both fixed and wifi) is recognized and the connection is established, no web browser works, I always get the "server not found" error. 


I have reinstalled Ubuntu ten times over the last year, and every time the same problem came up after three or four weeks of normal use without any problem. 


Where does that weird behavior of Ubuntu stem from? 

What can I do to handle it without having to reinstalled the whole system every time? 



I am a true layman concerning Linux, so I would be very grateful if you could give me simple and understable explanations. 


Many thanks in advance :-)

---

### Post by IvoGuerreiro on 2014-02-26
Hi, 
what is your ubuntu version or Distro?

---

### Post by IvoGuerreiro on 2014-02-26
I read somewhere about, something like that.
Perhaps you have a dnsmasq problem, try this:


Edit
/etc/NetworkManager/NetworkManager.conf
```

sudo gedit /etc/NetworkManager/NetworkManager.conf

```
Before DNS add # it should look like
#dns=dnsmasq


Then run 
```

sudo rm -f /etc/resolv.conf
sudo ln -s /run/resolvconf/interface/NetworkManager /etc/resolv.conf

```


finally reboot NetworkManager
```

sudo service network-manager restart

```


hope it helps.

---

### Post by slickymaster on 2014-02-26
> **IvoGuerreiro said:**
> <--snip-->
Edit
/etc/NetworkManager/NetworkManager.conf
```

sudo gedit /etc/NetworkManager/NetworkManager.conf

```<--snip-->

Just a quick FIY. Its's not advisable to use sudo for graphical applications so they won't potentially mess up your _~/.ICEauthority_ and other _user configuration files_.

There's a thorough explanation [here]("http://askubuntu.com/questions/270006/why-user-should-never-use-normal-sudo-to-start-graphical-application").

---

### Post by lotharlorraine on 2014-03-03
Hello! Thank you very much for your answer. 

I did everything you did but the problem came up anew several days later. 

I am still desperate and wonder what else I could do to fix this. 


Many thanks in advance for your further advice!

---

