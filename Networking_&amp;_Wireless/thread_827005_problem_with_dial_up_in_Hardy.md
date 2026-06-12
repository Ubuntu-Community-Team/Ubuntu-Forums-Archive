---
title: "problem with dial up in Hardy"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by madkid on 2008-06-12
I just installed Hardy this morning and got the martian modem driver installed. But for some reason when I try to connect to the internet, it'll connect but I can't get FireFox to open any pages and I can't install any packages from the web. Is there a way to fix this problem? Like I said, the modem works, but something is blocking me from connecting out to the web. Any help will be appreciated.

---

### Post by madkid on 2008-06-14
Ok, I partially solved the mystery. For some reason, when I try to connect, Ubuntu is still trying to authenticate my isp password with the isp server. What's going on with it?

---

### Post by editrix on 2008-06-14
> **madkid said:**
> Ok, I partially solved the mystery. For some reason, when I try to connect, Ubuntu is still trying to authenticate my isp password with the isp server. What's going on with it?

Just some suggestions:
Are you 200% sure your password is correct? (Sorry, but I had to ask.)

I've been having a heck of a time with Kwallet, which keeps asking for a password in Kmail. I never set it up, and don't even understand how to, but it might be your problem.

---

### Post by madkid on 2008-06-14
Everything is correct.

---

### Post by editrix on 2008-06-15
I'm no expert, understand, but I can think of two possibilities:

Assuming you're using KPPP, does your account read PAP/CHAP and have you got Store Password checked?

There's also something in Kmail under Accounts/Sending that says Server Requires Authentication.

Then, in /etc/ppp/options there's this bit:

> # Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth

And the bit right under it could be relevant.
> # ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

Probably no help at all, but at least I'm bumping the thread.

---

### Post by madkid on 2008-06-17
I'm using Ubuntu, not Kubuntu. The way I get normally connect is through the terminal with the command 'pon' to connect and 'poff' to disconnect. I already configured it via 'pppconfig'. But nothing seems to work.

Thanks for the attempt though. :)

---

### Post by editrix on 2008-06-19
> **madkid said:**
> I'm using Ubuntu, not Kubuntu. The way I get normally connect is through the terminal with the command 'pon' to connect and 'poff' to disconnect. I already configured it via 'pppconfig'. But nothing seems to work.

Thanks for the attempt though. :)

Probably stupid answer but at least a bump:

I've been having troubles of my own, and noticed that there's a **lot** of problems with the network manager (in my case, knetworkmanager). So you might want to poke around in there. In fact, I found one post someplace that said to uninstall it.

---

