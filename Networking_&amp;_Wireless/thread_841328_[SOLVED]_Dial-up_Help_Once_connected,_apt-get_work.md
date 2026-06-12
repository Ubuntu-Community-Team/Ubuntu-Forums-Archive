---
title: "[SOLVED] Dial-up Help? Once connected, apt-get works, firefox doesnt"
date: 2008-06-26
forum: Networking &amp; Wireless
---

### Post by Joshuwa on 2008-06-26
I seem to have a strange problem with my dial up connection.

I'm using a Trendnet external serial modem.

I used ppconfig to set up my connection, making sure to enable Dynamic DNS.

When I use "pon" or gnome-ppp to connect, it goes through the routine and connects just fine.

But then comes the strange thing: Some services work, others do not.

Firefox says page cannot be found, asks to be put it online mode. Pidgin timesout and will not connect.

**However**, I can ping google w/ 0% packet loss. I can use apt-get perfectly. In fact, I used apt-get to install xchat (which also works fine) to seek help that way, but to no avail. I then even installed lynx, and it will surf websites fine as well.

For kicks, I even fired up World of Warcraft, and it logged in and I was playing with no trouble.

Any idea why this might be occurring, and how I can go about correcting it?

Thanks in advance!

---

### Post by superprash2003 on 2008-06-26
are you able to open [http://64.233.187.99](http://64.233.187.99)

---

### Post by Nopposan on 2008-06-26
Wow.  You're able to use a dial up modem with Linux.  That'd be nice if I could do the same.

'Hope you succeed.  'Cause if you do, then I might just go out and get an external modem just like yours.  We can get free dial-up through our library card access as long as we renew once per month; although I have a wireless card that also works, the dial-up would be something nice to fall back on.

Cheers.

---

### Post by Joshuwa on 2008-06-26
> **superprash2003 said:**
> are you able to open [http://64.233.187.99](http://64.233.187.99)

With Firefox, no. With Lynx, I can open anything.

After doing some research and digging through bug reports, it seems it is a bug with Network Manager, compacted with (in my opinion) poor design in Firefox3 and Pidgin.

Apparently, Network Manager does not recognize a network is connected and fails to set status to "online." Since both Pidgin and Firefox3 rely on Network Manager to enable their offline/online status, they never get triggered into online mode either. This, I think is a design flaw. If one is not online, Firefox or Pidgin simply won't work; no reason to disable something (the software) that is by default already disabled (the network).

If anything, they should opt for the likelihood that the connection is "on" as default, even if it isn't; not many people use web browsers and chat while offline, so why default to this state? Strange, I think.

This is a bug that existed in Gutsy beta, and after 110+ bug reports, made it all the way to Hardy release :/

I'm going to try using [Wicd ]("http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html")over network manager and see if that solves the problem tonight.

> **Nopposan said:**
> Wow.  You're able to use a dial up modem with Linux.  That'd be nice if I could do the same.

'Hope you succeed.  'Cause if you do, then I might just go out and get an external modem just like yours.  We can get free dial-up through our library card access as long as we renew once per month; although I have a wireless card that also works, the dial-up would be something nice to fall back on.

Cheers.
The external modem (serial) works perfectly, no configuration needed. I got mine on Newegg for about $25. Works great when I boot to Windows, and if I can get the issue above fixed (which is related to software, rather than the modem), I'll be just as happy in Ubuntu :)

Here is the modem, if you'd like more info:
[http://www.newegg.com/Product/Product.aspx?item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?item=N82E16825134002)

---

### Post by Nopposan on 2008-06-26
That's good to know.  I'll think about it.  Thank you.

You don't know of any compact dial-up modems that plug into a laptop's pcmcia slot, do you?  The major use would be if I were on the road with my linux laptop and had to stop somewhere that didn't have wireless access I could use.

---

### Post by Joshuwa on 2008-06-27
After installing Wicd, which removes network manager, the problem was solved.

And unfortunately Nopposan, I'm not very familiar with laptops at all, so I don't know of any components that would or would not work for that situation.

---

### Post by brunolabs on 2008-06-28
Is this problem with Network Manager going to be solved?

---

