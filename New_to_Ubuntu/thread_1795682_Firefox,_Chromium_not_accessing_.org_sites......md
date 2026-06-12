---
title: "Firefox, Chromium not accessing .org sites.....?"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by arvindp3 on 2011-07-03
I am using Ubuntu 10.04 installed fresh on a default boot PC.   
For last few days I am unable to browse some .org sites through Firefox 3.6.18 or Chromium 12.0.742.91 (87961) Ubuntu 10.04.

Examples - longnow.org,  gpodder.org,  Windows Live

All add-ons are disabled in firefox. Chromium is default repository version.

All these sites are accessible thru Windows on same PC.

Other .org sites like wikipedia.org are accessible without issue from Ubuntu.

So this makes me think that there is some setting in either the browsers or Ubuntu 10.04 which is causing this. 

Would appreciate if anyone has a suggestion.

Thanks

---

### Post by arvindp3 on 2011-07-03
Sorry, Windows Live is not a .org siie but still inaccessible..

---

### Post by nzjethro on 2011-07-03
I can access both longnow.org and gpodder.org, with the same Chromium version (but 10.10 instead of 10.04). It sounds as though it's not specifically because of the ".org" domain. Can you ping the sites? Try
```
ping gpodder.org
```
and post the results here.

As a thought, do you have any networking applications (e.g. Transmission) open?

---

### Post by arvindp3 on 2011-07-03
Here is output of ping.  ping to longnow doesn't seem to work.  For gpodder it seems to work, but whats that stuff sulu.thp.io?


PING gpodder.org (178.77.79.64) 56(84) bytes of data.
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=1 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=2 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=3 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=4 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=5 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=6 ttl=50 time=155 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=7 ttl=50 time=159 ms
64 bytes from sulu.thp.io (178.77.79.64): icmp_seq=8 ttl=50 time=155 ms
^C
--- gpodder.org ping statistics ---
33 packets transmitted, 33 received, 0% packet loss, time 32042ms


arvind@Ubuntu-PC:~$ ping longnow.org
PING longnow.org (184.73.212.231) 56(84) bytes of data.

--- longnow.org ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 12999ms

---

### Post by arvindp3 on 2011-07-03
Sorry didn't answer teh second question -- No, no other applications other than browser -- at least visible on desktop...

---

### Post by SeijiSensei on 2011-07-03
> **arvindp3 said:**
> Here is output of ping.  ping to longnow doesn't seem to work.  For gpodder it seems to work, but whats that stuff sulu.thp.io?

It's the name of the server that's hosting the gpodder.org site.  An unlimited number of symbolic hostnames can point to the same IP address, but the address itself can point to only one name.

---

### Post by nzjethro on 2011-07-04
I'm also having trouble with pinging longnow.org, yet I can access it. I also get the same site pinging gpodder.org (10.10, same Chromium version). Are you able to access these sites through Opera, Chrome, or some other browser?

---

### Post by arvindp3 on 2011-07-04
None of the three browsers - FF, Chromium, Opera are able to access these sites from Ubuntu, but browsers are able to access these sites from Windows on the same PC.  So this may be some issue with Ubuntu networking config or FW.  But I haven't touched any of these configs really after initial setting - which was default setting.

---

### Post by dFlyer on 2011-07-04
> **arvindp3 said:**
> I am using Ubuntu 10.04 installed fresh on a default boot PC.   
For last few days I am unable to browse some .org sites through Firefox 3.6.18 or Chromium 12.0.742.91 (87961) Ubuntu 10.04.

Examples - longnow.org,  gpodder.org,  Windows Live

All add-ons are disabled in firefox. Chromium is default repository version.

All these sites are accessible thru Windows on same PC.

Other .org sites like wikipedia.org are accessible without issue from Ubuntu.

So this makes me think that there is some setting in either the browsers or Ubuntu 10.04 which is causing this. 

Would appreciate if anyone has a suggestion.

Thanks

With 11.04, firefox5 I was able to access all the sites you listed.

---

### Post by jtarin on 2011-07-04
Have you tried reaching these sites with a proxy?

---

### Post by arvindp3 on 2011-07-06
I remember that these sites were accessible thru 10.04 for quite sometime after I started using 10.04.  Looks like something else (either an OS update, FF update or some other inadvertent change made by me) has caused the system to behave like this.  I am just trying to get help to know where I should look to resolve this.

---

### Post by arvindp3 on 2011-07-06
No I did not try to go through a proxy.   Not sure if I want to -- if it works it woul dbe a workaround, not the solution right?   The other thing is that I don't know how to do that ...:)

---

### Post by jtarin on 2011-07-06
If for some reason your ISP or the distant ISP has blocked some domains or addresses,a proxy is not a workaround.......it's a solution.

[https://addons.mozilla.org/en-US/firefox/addon/tor-proxynet-toolbar/](https://addons.mozilla.org/en-US/firefox/addon/tor-proxynet-toolbar/)

---

### Post by arvindp3 on 2011-07-06
Ok, thanks.  Will try that too.

---

### Post by arvindp3 on 2011-07-06
Update: Opera 11.50 accesses longnow.org and gpodder.org from my PC but only if Opera Turbo is ON. Now I am trying to figure out what that means...

---

### Post by arvindp3 on 2011-07-10
Attaching a snapshot of Firefox and Opera attempting to load the same site -- [www.longnow.org](www.longnow.org) 

As can be seen, Opera was very fast in loading and display. Firefox got stuck with "Waiting for..." message.

Opera Turbo seems to facilitate images loading, so now I am checking if there are any settings in Firefox that can affect images loading.   There are a number of sites where I am experiencing this problem -- longnow.org is just one of them.

---

### Post by arvindp3 on 2011-07-10
Well, I seem to have solved this through some trial and error.  But still don't know exactly why this worked.

This is what I did - I was connecting to the DSL connection using a DSL entry in Network Connections.  I deleted all networking connections entries and instead used pppoeconf to setup the DSL connection.  Thats all.   Now Firefox is accessing all those sites which were getting stuck...   I can only guess that the networking parameters must have been causing this, and they worked when I set the DSL connection using pppoeconf.  Nothing wrong with FF setting I suppose.

---

