---
title: "Wireless issue"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by leoroberts on 2009-02-06
friends,

I am VERY new to all this - please don't shout at me!

I've searched the forums for an answer to my problem but can get nowhere ...

The issue is this:

I can connect to the internet through my router's wired system but not through the wireless.

Ubuntu recognises my network but, when I try to connect, it says that the network requires authentication and asks me to put in my wireless security password. I do this and a few seconds later, the same dialogue box re-appears but, this time, there is a whole string of dots in the password box (far more than are required for my network key). If I press 'connect' the same thing happens again, if I delete and re-enter my password - the same thing happens. After 4 unsuccessful tries I am told that the network connection has been disconnected.

I am using an ACER Travelmate 2420, with an Atheros 802.11 wireless LAN card, Ubuntu 8.10 and my wireless router is a D-LINK N

Is that enough information? I'm afraid that I'm about as technical as a housebrick - all this talk of 'terminals' and 'code' makes me want to eat chocolate!

I hope you can help me. Many thanks

Leo

---

### Post by Hospadar on 2009-02-06
Some wireless cards have wierd issues with different types of wireless passwords, before we go into what kind of wireless password you're using and whether or not they work on your card, etc, etc.  I would try disabling your router's wireless password alltogether and see if your card works then.  If it does, we know for sure that yes, your card works, and yes, the problem probably has something to do with passwords.

If you set a wireless password on your router, I think we can safely assume you are able to unset it.  If not, check your manual.  It will generally involve connecting with a cable (since your wifi doesn't currently work) pointing firefox to 192.168.something.something and clicking some buttons.

---

### Post by superprash2003 on 2009-02-06
are you connecting to a WPA network?

---

### Post by leoroberts on 2009-02-06
Hospadar and Superprash,

I set security to 'none' ... and it connected fine. So this presumably means it's a password issue.

I was connecting through WPA2 security .. I now have none - what should I do?

any ideas?

---

### Post by mikewhatever on 2009-02-06
I'd try wpa instead of wpa2.

---

### Post by leoroberts on 2009-02-06
right, having got it all working without security ... I then reinstated (at WPA-personal) with my original password.

guess what? exactly the same thing happens ...no connection, loads of dots (which I assume is the encrypted password), a denial of access, re-enter ... blah, blah, blah.

I'm very frutrated - just don't understand it!

I get asked for a password to the key link - which I input with no problems, but it doesn't make any difference.

On my Vista (sorry if that's a dirty word in here) laptop, I just put in my password (unencrypted) and everything connects just fine.

any more ideas?

---

### Post by leoroberts on 2009-02-06
scrap that ... my son came home from work and sorted it ... apparently (he tells me) the keyboard was set up as a US layout (rather than UK) so the password I was inputting was not what I thought it was! 

there have been many times when I have felt like a fool - none more so than this one! 

I am awfully sorry to have wasted your time. Thank you all for your help.

---

### Post by leoroberts on 2009-02-06
thanks for your help

---

