---
title: "gutsy torrent (not port forward problem!)"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by Quiane on 2007-12-22
Okay, so here is the deal.
I'm running gutsy, with an nvidia dual monitor setup.  I am fully connectable and am regularly connected with max seeds and peers. I have DSL and my torrent client is encrypting the traffic. Upnp and nat + are enabled, and i'm using deluge as the client.

  The problem is that i **am only getting under 20k/s d;ls!!**I have asked other people to benchmark torrents that i'm downloading, and they're getting 50k/s while i'm getting 4.4k/s.  
Is this a known problem with gutsy?? where would i go to log this as a bug? how do i fix it?
I tested the speeds before i started my nvidia dual monitors, and the speeds seemed fine to me (80k and up) but i didn't look long enough to make that a factor in my troubleshooting (i'll disable the nvidia card this weekend if i have time..but i want to see if anyone else has had this problem).

I know that torrents have flucuating speeds...but this is consistantly below where it should be...
any help would be greatly apprecated!!!!!!

---

### Post by mellowd on 2007-12-22
go to [www.speedtest.net](www.speedtest.net) to check what speed you should be capable of

---

### Post by finito on 2007-12-22
from my experience, non of the native clients can port forward without giving me a headache. I recommend you install wine and utorrent. I have yet to find a better combination.

Oh yeah, in utorrent change the the max connections to 400. if you are on a lan you will be able to hog all the bandwidth. the higher the better. You can't do that in XP it will just die.

---

### Post by mellowd on 2007-12-22
> **finito said:**
> from my experience, non of the native clients can port forward without giving me a headache. I recommend you install wine and utorrent. I have yet to find a better combination.

Oh yeah, in utorrent change the the max connections to 400. if you are on a lan you will be able to hog all the bandwidth. the higher the better. You can't do that in XP it will just die.

You forward the ports on your router, not the client. Once it's done on the router all you need to do when switching clients is making sure it uses the same port.

---

### Post by Quiane on 2007-12-22
the ports are forwarded on the router, and the active port in deluge is using the forwarded port..i'm fully connectable according to ipodtvnova, but still not getting the speeds i should.

On speedtest  I've got a 1540 d/l and **38 u/l** ??  Could this be my problem??
Thanks for the responses!

---

### Post by mellowd on 2007-12-22
Your upload will always be slower when using ADSL. It would only match if you had the more expensive SDSL (Asymmetric up/down as opposed to Symmetric up/down)

Your connection itself seems fine. Are you sure you are on a torrent with lots of seeds and minimum leechers?

---

### Post by Quiane on 2007-12-23
yeah, i was in the irc #ubuntu and i asked some people to benchmark for me...he was getting 50k/s and i was getting 4.4...consistantly.  I really have no idea where to turn..everyone is telling me it's a port forwarding problem, but as far as i can tell i've done everything i can on the router and have made the client use the proper port...?
Geting very frustrating !! :{

---

### Post by Quiane on 2007-12-23
oh, not sure if this matters, but i'm using PPPoE ?

---

### Post by mellowd on 2007-12-23
That shouldn't matter.

hmm, have you tried another torrent client just to test? Set it up to use the same port that you forwarded already. This will just be a test, you don't have to keep using it

---

### Post by Quiane on 2007-12-23
yep..i started on ktorrent, went to azerus, and now i'm on deluge......

---

### Post by mellowd on 2007-12-23
And the same problem on all?

---

### Post by Quiane on 2007-12-23
yep, no more than 10k/s....

---

### Post by mellowd on 2007-12-23
Hmm, if you are having problem with multiple programs and only torrents, all other traffic is fine. This leads me to think maybe your isp is filtering torrent traffic. You could try and enable encryption to see if that helps

---

### Post by Quiane on 2007-12-23
I apprecate all your responses mellowd.....i have already enabled encryption...by all rights i should be getting great speeds.....*sigh* it's such a pain!!

---

### Post by onero on 2007-12-24
Does the problem keep happening if you turn off your router's firewall? Not that I'd recommend you turn it off, but it seems to be either an ISP or router problem, so try turning the router's firewall off to see whether that's really the problem :D If so, at least it'll be easier to diagnose.

Another thing you could try is, if you have another PC / OS / etc., try downloading torrents from there while on your network to see it the same problem occurs.

Also, have you opened up the port in Ubuntu's software firewall? You can use Firestarter to open up the port in the built-in firewall.

---

### Post by bionnaki on 2007-12-25
if you are having low upload speeds, you most likely are being limited/capped by your ISP. quite common these days.

---

### Post by Quiane on 2007-12-26
I have tried the modem in DMZ mode, and still no moss, and i did contact my ISP..they say that their policy is that they dont throttle ports...i've never had this problem before (recently switched over windows user..) it's very frustrating....
and i do have another computer, using xp, and utorrent..i get "normal" speeds on there with no connection problems..AND i haven't even forwarded the ports to that machine

---

### Post by jdsampayo on 2008-02-07
Hello, I'm having the same problem that Quiane haves. I use uTorrent with wine in Gutsy, and always says that I'm blocked with a firewall/router, but, in Ubuntu Feisty I didn't have any problems, I have the port used in uTorrent open in the router. The same problem with  DMZ mode. I have another machine right now with Feisty and uTorrent with a different port number and it connects always.

It appears to be an issue of Gutsy, I think.

---

