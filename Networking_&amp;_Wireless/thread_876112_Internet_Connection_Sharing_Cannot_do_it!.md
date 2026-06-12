---
title: "Internet Connection Sharing Cannot do it!"
date: 2008-07-31
forum: Networking &amp; Wireless
---

### Post by renegadeandy on 2008-07-31
Hi!

I am on Ubuntu Hardy Heron 8.04 and have tried to follow various guides to setup Internet Connection sharing between my desktop - and my Xbox 360. One time I got it to work, i restarted and everything went completely crazy and I ended up having to reverse everything I did to get normal internet access on the desktop back.

Can somebody PLEASE give me a simple set of steps which will allow me to setup ICS and keep the changes so they are not forgotten on restart etc.

Thanks in advance,

Andy

---

### Post by pytheas22 on 2008-07-31
Do you mean that you want to use your Ubuntu box as an Internet gateway, and allow other machines to connect to the Internet through it?  Is everything wired or is wireless involved, and if so, on which parts of the network?  Also, which guides did you follow before?  With that information I'll try to help you figure it out.

---

### Post by renegadeandy on 2008-07-31
Ok all wired.

One ethernet card internet comes into, one is free - connected to the xbox.

I have tried the dnsmasq and ipmasq approach it worked once then all fell over etc.

For some I have also now buggered up the ip tables and firewall rules so badly that when i login to ubuntu the gui takes abotu 5 minutes to fully load because i think the firewall is blocking something it shouldnt :@

Dam.

So any help on how to revert this stuff and make what i need would be great!

---

### Post by pytheas22 on 2008-08-01
> For some I have also now buggered up the ip tables and firewall rules so badly that when i login to ubuntu the gui takes abotu 5 minutes to fully load because i think the firewall is blocking something it shouldnt :@


Try installing Firestarter, a nice GUI for configuring iptables:
```

sudo apt-get install firestarter
```

and see if you can figure out what's going on.  Editing iptables by hand can be a huge pain and it's easy to make mistakes, but Firestarter is pretty simple.

In the meantime, I'll see if I can figure out steps that will get you to where you need.  If I don't reply within a couple of days, please remind me.

---

### Post by dmizer on 2008-08-02
If you cannot get firestarter to work correctly (it's a real pain sometimes), you can take a look at this howto: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by allmywebsite1 on 2008-08-02
hii.... friends

i can get that how to see the free tv on internet and it`s very easy to use and operate......

---

