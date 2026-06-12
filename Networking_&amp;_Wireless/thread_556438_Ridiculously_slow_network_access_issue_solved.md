---
title: "Ridiculously slow network access issue solved"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by inanutshellus on 2007-09-21
Earlier this week my internet access at work was slowed to a crawl. A stand-still, even. 

I'd type in a URL, hit enter... the title of the page would come up in the browser's header then the app would freeze up for 5-10 minutes, after which the page would suddenly materialize in its entirety. 

I banged my head against the wall for a good long while. It seemed to be an Ubuntu-only issue, as the three Ubuntu users were having the issue but neither the Windows users nor the Red Hat user were affected.

The network guys maintained (and still maintain) that nothing on their side changed, that we Ubuntu users must have installed an update or something to cause the issue to happen simultaneously for us. Only... I don't have automatic updates enabled (has issues behind the proxy) and one other guy had only just started using his system again. 

At any rate, I'm posting here for two reasons. 

One being that I was able to get help from some smart guys and they figured out that the reason the Ubuntu users were having issues and the Red Hat users weren't. So I thought I'd post here, in case it was of any help to anyone in the future.

It was because of the **/etc/nsswitch.conf**. 

Ubuntu default:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Red Hat default: 

```
hosts:          files dns
```

Changing Ubuntu to match this line fixed the problem. 

The second reason for my posting is to ask for suggestions on what could have changed, so I can ask the Network guys about it.

Obviously *something* changed in the network (presumably something to do with DNS, DNS servers, etc., but also presumably not an obvious change... maybe somebody changed a config file or something), but the network guys say they did nothing and we should use Red Hat anyway as it's the pseudo-supported OS (really Windows is the only supported OS... I'm just glad they don't force it on us!).

---

