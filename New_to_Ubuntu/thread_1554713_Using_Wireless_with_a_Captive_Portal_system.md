---
title: "Using Wireless with a Captive Portal system"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by Zeppelin! on 2010-08-17
Okay, background information: Got my laptop, installed Ubuntu 9.10 as it was the liveCD I had. Found out the wireless card (its only means of connection) was only supported by a complex series of possibly recursive dependencies or by updating to 10.04 for native support. Wacky hijinks later I have 10.04 and my Realtek 8172 wireless card appears to work, given that 10.04 now recognises I have a wlan0 in ifconfig that it didn't before, and based on some anecdotes I'm going to give you.

As I don't have access to wireless of my own at the moment, I was attempting to use various public wi-fi systems to test it and ensure I had it working. Two tests were conducted.

Internet Cafe - This cafe had a "captive portal" system (for those unaware, it forces you to agree to a set of terms and conditions by automatically redirecting you to a site discussing them and not allowing any other connections until you agree). On giving the name of the network to the computer, it found it and connected at, apparently, "0%", but did not give me the captive portal page, and their tech support guy was basically using google to try to help me. I salute him for his patience and willingness to say more than 'Linux? Yeah uh *click*' Needless to say, we didn't make any headway, despite an attempt to set me up with a static ip for the cafe to bypass the portal.

Public Node - This node was run by an organization that also mandated the usage of a Captive Portal system. However, outside of the building in which it was located my laptop picked up its existence and connected to it automatically at a fairly steady "84%". However, I still did not receive the Captive Portal page and was thus still unable to use their internet.

Given the different connection values and the automatic hookup, I'm thinking my wireless card does actually work - if you can think of a way to test that let me know - but apparently I'm missing something key to get a portal page.

So, tl;dr: How do I get a captive portal page to show up?

Many thanks for any assistance you may provide.

---

### Post by Zeppelin! on 2010-08-18
Status update:

My laptop dual boots Windows, as I figured a situation like this would happen (I have terrible luck with machinery). I tried Windows out, and unsurprisingly it connected, which allowed me to acquire both the site address of the captive portal and the IP of the gateway server.

I switched to Ubuntu.

It connected, I opened Firefox, typed in the name of the portal site. It was an unending attempt to look it up.

So I pinged google - says the host is unknown or somesuch. I ping the gateway server, I near instantaneously get a response from it. I try inputting the address of the gateway server to get a redirect, and this time it connects for a split second then says something to the effect that the connection timed out. After several attempts, I saw on closing Firefox that the terminal I'd pinged with was working its way through the icmp_seq , and I let it run to 150 before shutdown.

So, yeah.

---

### Post by Zeppelin! on 2010-08-18
Okay, so I was looking over things once again. I'm close to giving up entirely, but I tend to keep soldiering until the war is won.

Anyway, I was looking at the Realtek documentation, particularly for mine, Realtek 8172, and I saw these very simple troubleshooting instructions: Just update the linux kernel from lucid-updates.

No, seriously: [https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Those are my instructions, and I haven't been able to make heads or tail of them, particularly as I cannot use Synaptic or Aptitude without being able to connect it to the internet.

---

