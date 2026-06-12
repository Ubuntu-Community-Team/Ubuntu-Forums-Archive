---
title: "Wired connection problems with e100 on Ubuntu Gutsy Gibon"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by justlost on 2007-12-20
Hi, I am new relatively new linux user. I've been learning linux through Fedora for the last 4 months and decided to try ubuntu for my file server.

I installed Gutsy through a USB drive, and there were no problems except the dhcp client would not pick up an ip from my router, so I continued anyways thinking I could figure it out later.

So after installation I disabled dhclient and setup an static ip. it works because I can ping my router but I keep getting 40% packate loss.

I removed IPV6 just to make sure that is not the problem, I modified the grub so that linux would boot with noapic.

I tried "sudo modprobe epro100" to see if a diferent driver would work and I get even more packate loss(70%). I can ping my xp pro box, and was able to receive some headers while doing "apt-get update" but this packet loss keeps cutting me off.

I've searched google, this forum(which I found a lot of old post with a lot of help) and I've looked for e100 and epro100 driver related issues. So now after a week of searching I'm here kindly asking for some help.

Has any one seen this behaviour with intel network cards? and how to solve them?

I should also mention the nic card is embeded on a dell dimension 3100 pc.

---

### Post by justlost on 2007-12-21
bumpy ree bump bump bump :)

---

### Post by justlost on 2007-12-26
bump

please, any body with any sugestions?

---

