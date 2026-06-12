---
title: "problem using Azureus through Wireless router"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by K-a-M-u-Z-u on 2007-08-28
hi.
i'm using ubuntu feisty with WIFI connection to a D-Link Dl-614+ Router
until now, i was able to use Azureus Bittorrent client and aMule with no problems.
suddenly, i dont know how, Azureus behavior got wiered.
i want to seed a file that i have downloaded, but for some reason, it won't upload.
at the bottom of the screen of Azureus, the NAT is OK(Green),DHT is OK,the tracker is connected and i can see peers and seeds. but no activity in the UL Section.
When i start downloading a new file, the UL and DL start working for few seconds, and then go back to ZERO.
aMule is working fine,
i have Configures Port forwarding on the router and azureus is using the ports i have opened.
*i'm using MoBlock as well, But as i Said before, Everything was ok and Azureus Worked fine before.
does any one has a clue of what is wrong?
Thnx.
:)

---

### Post by ddrichardson on 2007-08-28
Try a different port - see if your ISP is throttling it, also if available use encryption. I'm assuming you're seeding some legit apps ofcourse. ;-)

---

### Post by K-a-M-u-Z-u on 2007-08-28
actually, i'm using the same ports on amule and its working ok over there...
i tried changing the ports(also opening them on the router), it shows a little activity when i start azureus and then it go back to zero...
:\

---

### Post by K-a-M-u-Z-u on 2007-08-29
update:
something weird i discovered:
when azureus is minimaized, and i wait for few seconds and during that time firefox is active,and then i restore the azureus window, i see upload activity and then its going down rapidly and back to ZERO.
what da ?? :confused:

---

### Post by K-a-M-u-Z-u on 2007-09-02
*up*
:(

---

### Post by Zorael on 2007-09-02
You could try shifting ports just for the heck of it and see if it matters, I guess. And you could try the Vuze edition, the one at Azureus' site, instead of the one in the repositories.

---

### Post by ddrichardson on 2007-09-03
> **K-a-M-u-Z-u said:**
> update:
something weird i discovered:
when azureus is minimaized, and i wait for few seconds and during that time firefox is active,and then i restore the azureus window, i see upload activity and then its going down rapidly and back to ZERO.
what da ?? :confused:

I'm not sure this is actually reflective of your problem, because it could simply be to do with how the program redraws its screen after being minimized.

Have you tried using a different port range?

---

### Post by K-a-M-u-Z-u on 2007-09-03
yes.i have tried different ports.
i think this is realated to torrent leech baning israelies ip addresses
the problem is that israeli users have bad reputation as leechers and ratio fakers.
not because we dont like to share, its beacause we have poor line capaceties...
i have an OK ration and i have no BAN warning in TL site.and other torrents are dwonloading/uploading ok...
i have posted a messege to one of the moderators over there to check the problem.
any othere israeli got a problem there?

---

### Post by ddrichardson on 2007-09-03
Have a look into tor - to hide your IP address.

---

### Post by K-a-M-u-Z-u on 2007-09-04
tor?
is this a program or some kind of option settings in azureus/router?

---

### Post by ddrichardson on 2007-09-04
Its an API - [here]("http://tor.eff.org/").

---

