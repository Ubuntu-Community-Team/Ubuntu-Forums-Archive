---
title: "Remote Desktop help needed"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by DFreeze on 2006-10-16
I’m going to get my mum online within short. I can already hear the phone ringing twice a weak, having her asking questions about settings, hardware quirckyness and whatnot. 

Can I remotely access her desktop (Win98), when her computer is behind a router and in a private LAN, and I’m behind a router (and private LAN) as well. Am I jeopardizing her LAN when I enable such functionality in her system / router (e.g. having to open ports or something).

I’ve scanned the forums and saw FreeNX, VNC, grdesktop mentioned, but what is the way to go? My mum should not have to do anything for me to have access (except enabling remote help once). Which option would you recommend? Where can I look up more docs about remote management (to learn what I’m actually doing) and protocols like SSH?

Thanks in advance!

---

### Post by dmizer on 2006-10-16
> **DFreeze said:**
> Can I remotely access her desktop (Win98), when her computer is behind a router and in a private LAN, and I’m behind a router (and private LAN) as well.
yes you can do this, but it will require you to poke holes in her router, and impliment ip forwarding (best done with static ip on the local network).

> Am I jeopardizing her LAN when I enable such functionality in her system / router (e.g. having to open ports or something).
yes, you are very much jeopardizing her lan by opening up a vnc port ... especially since her machine is a (very insecure) win 98 box.

> I’ve scanned the forums and saw FreeNX, VNC, grdesktop mentioned, but what is the way to go? My mum should not have to do anything for me to have access (except enabling remote help once). Which option would you recommend? Where can I look up more docs about remote management (to learn what I’m actually doing) and protocols like SSH?

Thanks in advance!

i believe you can enable remote desktop on win98 via netmeeting.  i have no idea if it's possible to vnc via ssh tunneling to a windows box.

---

### Post by DFreeze on 2006-10-17
So what you are saying is that it might not be a good idea to do this remote thing with her computer after all? I don't want to impose more virusthreat on her system for the sake of easy servicing. The net balance would be zero, since I probably have to untangle her system more often because I want to do it from a distance.

But then again, how do 'the big guys' do it? I assume Google doesn't locally maintain their servers, because of the risk of opening it up to remote servicing. 

Can someone advise me in this? Can I get this done without thrashing her network and computer, or do you think I should not want this?

---

### Post by dmizer on 2006-10-17
> **DFreeze said:**
> So what you are saying is that it might not be a good idea to do this remote thing with her computer after all?
yes, that is exactly what i am saying.

> **DFreeze said:**
> But then again, how do 'the big guys' do it? I assume Google doesn't locally maintain their servers, because of the risk of opening it up to remote servicing.
well, first (and probably most critically) ... "the big guys" aren't using windows 98 for their servers.

secondly, the big guys aren't remotely connecting to desktop end user systems ... they're connecting to (in the case of google) linux servers.

thirdly, "the big guys" aren't relying on retail level software and hardware for security and connectivity.

> **DFreeze said:**
> Can I get this done without thrashing her network and computer?
you might be successful in setting up a vpn network ... but i would have no way of being able to help you figure that out.  plus, i would still be skeptical of win98's ability to do even this with a reasonable amount of security.

---

### Post by DFreeze on 2006-10-18
Ok, I catch your drift. I might be able to upgrade her system to WinXP (I think it's capable of running it), but that leaves the other issues you mentioned intact. 

...guess I just have to start converting her to Linux, then ;)

More seriously, I thought this to be an excellent opportunity to learn something new and useful. But I guess I'll keep such experimenting within the boundaries of my private LAN.

Thanks for your insights, anyway. I'll just have perfect my layman-instructions-by-phone skills, or drive up there on occasion. :)

---

### Post by merkur2k on 2006-10-18
One solution I have seen used by the 'big guys' is ultravnc. It is a fork of vnc, and is therefor free as well. It does require a public webserver somewhere (doesnt necessarily have to be at your location) and a hole through *your* firewall to an accessible ultravnc daemon on your machine. Nothing special is required at the other end since it makes a conection back to you, and nothing even needs to be installed. The beauty of this solution is that no connection can happen unless action is taken by both parties. The user has to hit the website with the hosted client software and agree to allow the connection, and you have to accept the request before any remote control can happen. All you would have to do on her end is make a bookmark to the web server.
the details are at: [http://www.uvnc.com/addons/singleclick.html](http://www.uvnc.com/addons/singleclick.html)
Ultravnc also has many other features that go way above and beyond the standard vnc distribution. If the single click feature isnt exactly what you want, you might also look at the nat-to-nat connector feature.

---

### Post by dmizer on 2006-10-20
ultravnc looks interesting, i'll have to check it out.

i've been giving this lots of thought and i think i may have a solution for you.  it may not be the fastest solution, but i think it might be useable.

set up a headless linux server as an intermediary between the router and the win98 machine (any old junk pIII will do).  you could forward port 22 from the router to the linux box and ssh -X from your location to the server.  then start your vnc session from the server cli (the server would need x installed, but nothing more).  mind you, it will be slow, but it will also be encrypted and secure while providing an extra layer of insulation between win98's swiss cheese and the internet.

maybe more complex than you're looking for, but it could be a viable solution?

---

