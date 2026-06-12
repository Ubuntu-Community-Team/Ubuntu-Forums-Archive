---
title: "Help!!! My WRT54GS hates me... :("
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by starcraft.man on 2007-04-27
I have a serious problem it seems and I don't really know how it happened...

So it began yesterday when I was in the middle of installing a few programs into my Ubuntu clean install of 6.10 (feisty gave me some problems so had to downgrade for now). All of a sudden my dad told me that the wireless network we have wasn't connecting anymore(he and my mom still use XP, my ubuntu connects through a hardline). So I went to investigate and found that the wireless access point was wide open with no pass and default the connection named linksys. Previously of course I had a rock solid encryption on connecting to the network with a 63 character ascii pass using WPA Personal and TKIP. (Great pass generator [here)]("https://www.grc.com/passwords.htm")

I went into my control panel via 192.168.1.1 as always and found all the settings were back to factory default... most disturbing of all was that the username and pass to access my router control panel had defaulted back to linksys and admin and wan management had been on the entire time. In addition, I think that this had been wide open all night. I have never really heard of any such thing happening. I got the feeling like somehow, someone had hacked my router (A WRT54GS V 6.0 with speedbooster), I mean I don't know any other explanation. So I concluded I couldn't trust the firmware anymore as it would have been trivial for anyone to flash any firmware onto it.

So, I immediately unplugged my DSL line from the router after having downloaded the newest version of my router software and upgraded.

Sigh ><. That seems only to now have caused me other problems. The router now has a new connection name and ascii password but, things still seem very wrong. While I did that and changed the router acess password, I can't seem to modify any other settings like port forwarding and request filtering. I clearly have double checked this as is in pictures below.

So I use a program shields up by GRC.com, its a very reliable program I've used it before to test software firewalls and such when I was on XP. Oh and just a note, I don't have any firewall on my Ubuntu install that could interfere, my nat routers always been good enough.

So, as I was saying I forwarded 3 sequential ports to my given IP and then used this to test if they were forwarded and I was returned that they were all stealthed from the internet. Even more conclusive proof, I turned off ident port filter and requests and I scanned the regular ports and Ident was still stealthed.

So, I am pretty sure I have isolated the problem to my router. Anyone have a solution? I am pretty comfortable with the linksys control, is there a way for me to downgrade it back to the version right before 1.52.0. If so, is there a way to make sure its completely blanked before I do. If not, is there an alternative firmware I could use like openwrt?

Help me please!

---

### Post by patrickfromspain on 2007-04-27
I use dd-wrt with no problems.. maybe you could try.

---

### Post by starcraft.man on 2007-04-27
Is there a guide somewhere that could help me to install it onto my router, and more importantly make sure its a clean install that wipes everything? I'm no expert with firmware and things like that >.<

Edit: and DD WRT seems to be more of a paid version, I assume the free one is limited in some significant way...

---

### Post by starcraft.man on 2007-04-27
> **patrickfromspain said:**
> I use dd-wrt with no problems.. maybe you could try.

Thanks a lot, used that and my control panel works again. STUPID Linksys, they will be getting a nasty letter for breaking my firmware with their own upgrade.

---

### Post by druhboruch on 2007-04-27
I installed openwrt from [http://x-wrt.org/](http://x-wrt.org/).
And I am living happily ever after.

---

### Post by starcraft.man on 2007-04-27
> **druhboruch said:**
> I installed openwrt from [http://x-wrt.org/](http://x-wrt.org/).
And I am living happily ever after.

They apparently don't support my version 6 of wrt54gs oh well ><

---

