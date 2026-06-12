---
title: "Router Keeps Releasing My Desktop Machine"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by rchar66 on 2008-09-19
I've had this happen a couple of times now and I'm not sure what might be causing it.

Last night I was downloading a file, during the download, my router released my desktop machine and then it had to re-connect, interupting the download.

After it re-connected, I re-started the download and within about ten minutes, it got released again. This went on for about fourty five minutes, releasing and re-connecting.

After I rebooted the machine it didn't do this anymore. About the only thing I can come up with is that just before it started, I had downloaded some updates. After the updates were done, I didn't need to re-boot the machine.

Is it probably a good idea to re-boot anyway after downloading updates? Or could this be caused by something else?

---

### Post by nixscripter on 2008-09-19
At the risk of answering the wrong question, you might try picking up the download where you left off if this happens by using wget:

```

wget -c 'http://wherever.org/file.txt'

```

The general problem sounds like a DHCP lease time being too short, or some other router configuration problem. What kind of router is it?

---

### Post by rchar66 on 2008-09-19
DHCP lease time is set to 1 week and it is a D-Link DI-624 router.

---

### Post by nixscripter on 2008-09-20
Do you connect via wireless? The Grand Oracle Of Great Expectations (a.k.a. google) dug up this for that particular router. It might be a configuration problem.

[http://www.tomshardware.com/forum/9766-43-link-disconnecting-solution](http://www.tomshardware.com/forum/9766-43-link-disconnecting-solution)

Hope this helps.

---

### Post by rchar66 on 2008-09-20
Thanks for the link! I'm going to look into it.

The problem isn't with the wireless. My laptop has never had a problem staying connected, and for several hours at a time. It's actually with the wired connection.

What's intersting to me, is that since my first post, this problem hasn't occured again and this just started happening recently after owning this router for about four years.

Oh well.......thanks for the link and I'll double check all of my settings and see what happens!

---

### Post by nixscripter on 2008-09-21
For what it's worth, I have a fairly cheap linksys router, and for some reason after I have it for a year, there are periods where it sporadically drops traffic (ping 50 times, drop all but eight). My solution, silly though it sounds: buy a new router every 18 months or so when it starts doing it too frequently. Hopefully, you won't have to do the same.

---

### Post by rchar66 on 2008-09-22
Yeah.....yeah.....I know what you mean.

My sister had a Netgear router and after about two years, it just started acting really flaky. Sometimes you could connect wirelessly, sometimes not. It even started doing that through a wired connection.

She ended up buying a new router and everything is fine again.

My router is still acting fine now. I'm going to just keep watching it and see if this keeps happening and if so, is it happening more often.

---

