---
title: "remote machine issue"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by johnnyw on 2009-06-02
Hi! A friend of mine set a virtual environment for me in his server. Even though things were quite slow ( the server had not the response I would like maybe due to Ubuntu eating too many resources on this humble 512mb of ram with GNOME) things worked incredibly good ( server network connection wise).

After some days I log in with my TighVNC and I notice that internet connection does not work ( even though i could log in and work in an "offline mode").

What should I look for?

Ive been told to look at /etc/resolv.conf . 

I found :
```
search local domain 
nameserver 192.168.0.2
```

Is this normal?

Thanks

---

### Post by jonobr on 2009-06-02
resolv.conf is only used for name resolution from your machine,
so if you type in google.com
the nameserver will be used to lookup that name, in your case its, 192.168.0.2

Im guessing this is not your problem.

You could originally connect yes?

Are you sure the IP address of your tightvnc has not changed?

Try pinging the IP address of the machine your tight vncing to.
See if it responds.
Also, are you doing this on the same network? Or are you doing it from outside your home lan

---

