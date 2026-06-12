---
title: "Banned: Tor freenode is hidden-service-only"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by crhylove on 2008-05-17
Boy howdy, I've tried about 20 different things so I can chat in #ubuntu (and everywhere else on freenode), but no matter what I do I get the following message:

(notice) *** Banned:  Tor freenode is hidden-service-only (mejokbp2brhw4omd.onion) - see freenode.net/irc_servers.shtml. (2008/04/20 16.57)

I'm pretty sure I didn't do anything to violate their terms or anything, I think I just have something futzed wrong in Pidgin.

Any ideas?  Anyone got a specific walk through of how to fix this in Pidgin?

PS I have been using TOR in pidgin as without it my ISP disables AOL instant messenger if I send my brother mp3s of my band.  Even though it's MY band, and I'm fully within my rights.....

---

### Post by Arand on 2008-05-17
I've found Mibbit.com to be very handy for IRC purposes.

To get into #ubuntu you will have to first try connecting, which will normally direct you to #ubuntu-proxy-users, which yells at you...

If you then wait a while and try joining #ubuntu from within this channel it will normally work.

- Arand

---

### Post by Sp|ke on 2008-05-23
Reading between the lines I would guess freenode (like dalnet) doesn't allow tor connections. But **unlike** dalnet it has set up a hidden service irc server which you **can** connect to. (You can actually connect to dalnet with tor but it requires a little exit node hopping to find a good one)

From freenodes site.
> Accessing Freenode Via Tor

The current Tor hidden service address for freenode is mejokbp2brhw4omd.onion For users of Tor with gpg keys that don't mind being identified by them, we offer another hidden service of 5t7o4shdbhotfuzp.onion The latter hidden service is authenticated with a nick and password combination and subsequently will not get blocked during periods of general tor abuse. Mailing tor at freenode dot net with your nick and a password hash signed together. The required hash can be generated with either

    on irc: /quote makepass <password>

or

    at a shell prompt: mkpasswd -H md5

This will get the process started. Also, if you'd rather your hash be encrypted, you may encrypt to 0x035D6B1D. The canonical way to do this would be to execute something like:

    echo '<nick> <passwordhash>' | gpg --gnupg -sea -r 035D6B1D 

We have to have a copy of your public key in order to verify the signature, so make sure to include a copy if it's not available on the keyserver network.

Latencies are improving all the time and can be quite reasonable. You can always find a pointer to our Tor hidden service in freenode.net DNS, in an unresolved CNAME record, irc.tor.freenode.net, which can be retrieved, for example, via the *nix shell command:

    dig  +short  irc.tor.freenode.net  cname 

If your IRC client can handle socks5 with remote dns, you can just connect to the .onion address directly. Otherwise, use Tor's "mapaddress" feature to fake it. (We do not recommend that you use Privoxy with irssi. It's unnecessary. Just use the 'mapaddress' approach and torify irssi to start it up.) Add a line to your torrc, as in this example:

    mapaddress  10.40.40.40  mejokbp2brhw4omd.onion
    mapaddress  10.40.40.41  5t7o4shdbhotfuzp.onion 

Be sure to HUP (reload) Tor if you change your torrc. After you've made the change, just connect your torified IRC client to the IP you specified in your mapaddress statement for the freenode service. Tor will do the conversion for you internally and you'll connect to freenode. In addition to providing location privacy, the Tor hidden service gives you end-to-end encryption, providing benefits similar to those of ircs / irc-ssl.

That's all it takes. We appreciate your accessing freenode via the Tor hidden service. If you'd like to help us maintain quality access, please consider providing "middleman" bandwidth to the Tor network. Just set your host up as a Tor server and specify how much bandwidth you want to provide. You don't have to be an exit node&#8212;you can set your exit policy to "reject *:*" and still help us make up for the bandwith we use for freenode's hidden service. 

---

### Post by IndyGunFreak on 2008-05-23
Pidgin is a great IM client, but in my opinion, a horrid IRC client.  Use Xchat, Kvirc, irssi, etc.  There's a lot of free options for a good IRC client.

IGF

---

### Post by Sp|ke on 2008-05-23
> **IndyGUnFreak said:**
> Pidgin is a great IM client, but in my opinion, a horrid IRC client.  Use Xchat, Kvirc, irssi, etc.  There's a lot of free options for a good IRC client.

IGF

I would tend to agree. Or you could use mIRC under wine, it runs great. (I'll wash my mouth out now :lolflag: )

---

### Post by holizz on 2008-08-04
I'm getting the same problem with irssi. I added the mapaddress lines to my torrc and SIGHUPped it, but it still won't work.

Can anybody provide more detailed (and less vague) instructions?

Nevermind, found this: [http://blog.aizatto.com/2006/09/02/connecting-to-freenode-with-tor-using-xchat/](http://blog.aizatto.com/2006/09/02/connecting-to-freenode-with-tor-using-xchat/)

---

