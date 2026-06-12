---
title: "Alter dns settings to enable access to UK content"
date: 2020-01-26
forum: Networking &amp; Wireless
---

### Post by xyeovillian on 2020-01-26
I have subscription to dns4me so as I can access TV shows etc from countries outside my present location here in NZ.

I can get it to work on Windows or IOS as they have tutorials on dns4me but alas nothing for Linux.

I have tried in the past but no success does anyone have an easy way or do I forget Linux for this option?

---

### Post by CelticWarrior on 2020-01-27
If you can configure it at the router itself that would be the best solution for everything connected to it: [Example for DD-WRT]("https://dns4me.net/guides/routers/dd-wrt").

If not, you may also be able to edit the *hosts* file in Ubuntu and edit the DNS servers provided by the service there. It's true they don't have guides specifically for Linux but you should be able to extrapolate the very simple instructions for the specific use in Ubuntu. After all this is just a proxy service, once logged in, you are given two DNS servers to use, anyone knowing just a little bit of how this works won't need any guide.

---

