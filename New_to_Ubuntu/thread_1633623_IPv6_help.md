---
title: "IPv6 help"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-11-29
Hey guys,

I'm trying to get the IPv6 newsgroup access going on my computer. So I'm hoping someone here has experience with this.

I'm using [_this_](http://www.ubuntu-unleashed.com/2009/03/howto-easily-get-free-newsgroup-access.html) tutorial. And when I get down to the part of typing in 'sudo /etc/init.d/tspc restart' I get this error in Terminal:


```
sudo /etc/init.d/tspc restart
/etc/tsp/tspc.conf: 50: hancock: not found
 * Restarting IPv6 tunnel tspc                                                  
Error is 1: TSP_ERROR
TSP session done
```

Now the 'hancock' part of the error is the username I'm supposed to be using(john hancock actually). And right before doing this step I follwed the step of hitting Alt-F2 and filling out the info.

So what exactly do you think I've done wrong? Did I maybe mess up the step of:

> Find the userid line and enter your useid for freenet6, then find the passwd line and enter your password you set, then set the server as broker.freenet6.net

Or is there something else going on? Because without restarting to Ipv6 I can't move along to the next step of:

> Now lets check if tspc created a new ipv6 interface:

Because when I do type in 'ifconfig' into Terminal, there is no showing of ipv6 in the results.

Thank you for any and all help.

EDIT: Ok, I just changed my username and replaced it in the config. Then I tried to restart again and I get a new error:


```
sudo /etc/init.d/tspc restart
 * Restarting IPv6 tunnel tspc                                                  
Status error 303 in tunnel negociation: 303 Unsupported tunnel mode


Error is 303: 303 is not defined as a client error, might be a TSP error?
TSP session done
```

Anyone know what that could mean?

---

