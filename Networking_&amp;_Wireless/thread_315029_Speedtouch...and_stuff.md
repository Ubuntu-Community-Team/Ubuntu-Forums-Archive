---
title: "Speedtouch...and stuff"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by SpongeBob SquarePants on 2006-12-08
I currently connect to the net via Pipex, using an ADSL USB Speedtouch 330 modem. Anyway, it works ok....bar the farting about required after a re-install. But I keep hearing in magazines how you can buy an ethernet router and modem for less than 25 quid...all you have to do is plug it in, whack in your details and off you go...no software installation at all.

Now to be honest, I don't really know what ethernet is (a net for catching "ethers" presumably). I do however know that my mobo has a built in ethernet adapter, and that Linux recpongises it. So that's a bonus right? But I'm just one guy, on one home computer, no network, requiring just a bit of net access for emails and stuff.

Firstly, will I be able to connect to my Pipex account using an ethernet adapter and one of these mythical modem router thingies?

And presuming for a moment that the answer is yes...where on earth do you get them from? Could someone provide a few examples of hardware that might work? I went into my local computer shop and mentioned "hardware modem"..."linux"....."no software" and he appeared to have a breakdown on the spot. In the end he just said that Speedtouch modems word. I thanked him, told him I already had one...as I'd already explained if he'd bothered listening...and left the shop in a right royal huff.

Can anyone help me?

---

### Post by dbott67 on 2006-12-08
Basically, what you're looking for is a broadband router for cable or DSL.

Common vendors include Linksys, D-Link & Netgear and prices start from about $20.00 US on sale (sometimes even less, after mail-in rebates).

Here's an example from D-Link:
[http://www.dlink.com/products/?sec=1&pid=62](http://www.dlink.com/products/?sec=1&pid=62)

There are also wireless versions for those with wireless cards, laptops, PDAs and the like.

As for [ethernet]("http://en.wikipedia.org/wiki/Ethernet")... the short answer might best be summed up as '[COLOR="RoyalBlue"]the thin blue cable with the big phone jack on the end[/COLOR]' (but of course, that's not a very accurate description, especially since it comes in many colours and can be used for other things!).

-Dave

---

### Post by SpongeBob SquarePants on 2006-12-08
Thanks Dave,

And just as an afterthought, do all DSL routers run without software? Or is that something I'm going to have to watch out for?

---

### Post by dbott67 on 2006-12-08
The DSL/Cable routers all have embedded firmware (basically a stripped down version of linux with DHCP server, a DNS forwarder, a NAT firewall, a PPPoE client (for certain DSL clients) and a few other goodies).

The router takes care of the internet connection.  You need to program it with settings from your ISP.

You should not need to install *any* software from your ISP on your computer (such as a PPPoE client like Access Manager).  The router takes care of everything.

-Dave

---

