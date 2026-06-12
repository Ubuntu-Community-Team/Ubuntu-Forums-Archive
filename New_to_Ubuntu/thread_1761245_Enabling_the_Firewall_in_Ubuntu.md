---
title: "Enabling the Firewall in Ubuntu?"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-17
Hello, how do you enable the firewall in Ubuntu?

---

### Post by NormanFLinux on 2011-05-17
Download and install Gufw - the graphical front end to the ufw firewall in Ubuntu and tick the enable firewall checkbox.

That's all you need to do to enable it in Ubuntu.

---

### Post by TAspr on 2011-05-17
> **NormanFLinux said:**
> Download and install Gufw - the graphical front end to the ufw firewall in Ubuntu and tick the enable firewall checkbox.

That's all you need to do to enable it in Ubuntu.

Does this also apply to puppy linux?

---

### Post by NormanFLinux on 2011-05-17
Puppy Linux on bootup comes with its own GUI firewall. I think you have to enable it once and that's it.

---

### Post by TAspr on 2011-05-17
> **NormanFLinux said:**
> Puppy Linux on bootup comes with its own GUI firewall. I think you have to enable it once and that's it.

Man, that puppy linux is a fast one.  Whew!

---

### Post by SynonM on 2011-05-17
What's controlling your firewall good for anyway?:roll::roll:

---

### Post by TAspr on 2011-05-17
> **SynonM said:**
> What's controlling your firewall good for anyway?:roll::roll:


Are you serious or kidding?

---

### Post by mcduck on 2011-05-18
> **SynonM said:**
> What's controlling your firewall good for anyway?:roll::roll:

Not much, really, unless you install some server applications (and they lack the ability to restrict their connections the way you'd want to).

The default install of Ubuntu has no running services that would listen for incoming network connections, which makes a firewall pointless.

---

### Post by SynonM on 2011-05-18
> **TAspr said:**
> Are you serious or kidding?

Let me rephrase that. 
What is better about your own, instead of the systems default firewall?

:popcorn:

I mean why not use some good proxies.

CoDeen network

let somebody else do the dirty work...

---

### Post by TAspr on 2011-05-18
> **SynonM said:**
> Let me rephrase that. 
What is better about your own, instead of the systems default firewall?

:popcorn:

I mean why not use some good proxies.

CoDeen network

let somebody else do the dirty work...

Tell me how to do this please.

---

### Post by Nerotriple6 on 2011-05-18
> **TAspr said:**
> Hello, how do you enable the firewall in Ubuntu?

```
sudo ufw enable

```

---

### Post by SynonM on 2011-05-18
> **TAspr said:**
> Tell me how to do this please.

watch this [http://www.youtube.com/watch?v=urPMFhyBI4U](http://www.youtube.com/watch?v=urPMFhyBI4U)

go here: [http://hidemyass.com/proxy-list/](http://hidemyass.com/proxy-list/)

add the proxies w/  the letter's "PL" in yellow.

change the url settings on your proxy to your needs

mine is usu.

blacklist ([https://*](https://*)) cause ---> most proxy hosts deny https:// or SSL
whitelist ([http://*](http://*)) cause ---> essentially everything else

the *  is to show variable suffix or prefix

example .... for all .com's

*.com*

You can go crazy with other things like a proxy just for facebook...
but remember proxies are enabled in order
like
Proxy 0
Proxy 1
Proxy 2
etc...
Default <-- your IP & ISP IP

:popcorn:

P.S. proxy ports don't last forever.
Hope this helps

---

