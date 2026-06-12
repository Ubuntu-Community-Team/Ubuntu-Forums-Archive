---
title: "Firewall setup"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by lolol i r linux noob on 2009-04-12
is there an easy to setup firewall for ubuntu?

i no its pretty much virus free but a like to keep my pc safe anyways.

---

### Post by Paqman on 2009-04-12
You've got one installed already, it's just not turned on because it doesn't need to be on the default install. Try Gufw or Firestarter if you want a GUI to configure it.

---

### Post by zerhacke on 2009-04-12
sudo apt-get install firestarter

It has a GUI.

---

### Post by lolol i r linux noob on 2009-04-12
it doesnt seem to have a wireless option

any firewalls that work with wireless

---

### Post by cariboo on 2009-04-12
What do you mean it doesn't work with wireless and which app are you using to set the firewall rules?

I've never felt the need for an extra firewall, as my router has one builtin. I you aren't running any services like ssh, apache, mysql etc, there are no ports listening for activity. 

I would suggest you have a look at this [thread=510812]sticky[/thread], it deals with Ubuntu security.

Jim

---

### Post by lolol i r linux noob on 2009-04-12
i use firestarter and its only got ethernet support.
ive tried all the options none work.

---

### Post by hyper_ch on 2009-04-12
(1) firestarter is no firewall

(2) what do you think you need a firewall for?

---

### Post by lolol i r linux noob on 2009-04-12
just to be safe really

---

### Post by hyper_ch on 2009-04-12
then you don't need it...

---

### Post by MrWES on 2009-04-12
> **lolol i r linux noob said:**
> just to be safe really

Run your connection through Shields Up!

[https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

I doubt you need a firewall.

Bill

---

### Post by connorh123 on 2009-04-12
Go into add/remove and type firewall, their's a program for it.

---

### Post by Paqman on 2009-04-13
> **lolol i r linux noob said:**
> just to be safe really

Good news! You're already safe.

The default install of Ubuntu has no services listening on any ports. What that means is that there's nothing an attacker can connect to. It's the same as having all those ports locked down. By contrast, a default Windows instal has a lot of ports vulnerable. That's why a firewall is recommended on Windows, but not on Ubuntu.

If you install any kind of server software, then you might have created a vulnerability. If you haven't, don't worry about it.

---

### Post by 3rdalbum on 2009-04-13
1. If you're using wireless networking, then your router already has a firewall and NAT built-in that will prevent incoming connections.

2. What do you mean "It doesn't work with wireless"? Ufw works on all incoming traffic, it doesn't discriminate between network interfaces. You can enable Ufw on the command-line or install gUfw (which appears as System > Administration > Firewall Configuration).

---

### Post by PukingPenguin on 2009-04-13
> **lolol i r linux noob said:**
> i use firestarter and its only got ethernet support.

And if you aren't using ethernet, you are using...what? A token-ring network?
Wireless is still ethernet. It just doesn't use the cable.

---

### Post by lolol i r linux noob on 2009-04-13
A got the firewall working but now a cant get on the internet. atall.

---

### Post by Paqman on 2009-04-13
> **lolol i r linux noob said:**
> A got the firewall working but now a cant get on the internet. atall.

Turn the firewall off then. You've obviously got it set waaaay too strict.

---

