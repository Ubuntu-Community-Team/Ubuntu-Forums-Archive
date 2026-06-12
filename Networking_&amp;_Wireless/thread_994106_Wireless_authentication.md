---
title: "Wireless authentication?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by freestyleren on 2008-11-26
I'm trying to set up my the internet(WPA) with a wireless netcard, which worked fine the first time, but now whenever it tries to connect, the authentication box keeps popping up. How do i fix this?

---

### Post by visionviper on 2008-11-26
I have the same problem. It's a bug in Ubuntu and I am yet to find anything that fixes it for me.

---

### Post by freestyleren on 2008-11-26
So i can't connect to wireless net using ubuntu?

---

### Post by visionviper on 2008-11-26
Well, not without an answer to the bug. The bug actually only appears on certain drivers. When I was using the default Ubuntu drivers for my wirless card I had no problem connecting at all, but performance was absolutely horrid. Using ndiswrapper and the windows driver for my card I get great performance, but I now suffer from the same bug you are seeing.

I have been trying several things to get my wireless working with my WPA key but I am yet to find anything.

---

### Post by freestyleren on 2008-11-26
but i'd be able to make it work using ndiswrapper?
EDIT: sorry i just realized that i'm already using a windows driver..

---

### Post by visionviper on 2008-11-26
I would say probably not, since its when I used ndiswrapper that I started having problems with the bug.

EDIT: Seems like I have come up with a workaround. Let me test it and I will post it if I find out it works.

---

### Post by freestyleren on 2008-11-26
oh my.. another reason to switch back to windows.

---

### Post by icanfly0307 on 2008-11-26
Hopefully, I haven't replied so late that you've switched back to Windows. :lolflag:

I know how to get your wireless authentication working. Yes, its a bug on NetworkManger's part. Its actually present in every Linux distro. To get around this problem, you'll have to change your security encryption on your router from WPA to WEP 128bit Shared Key. The good news it that WEP is way more secure that WPA so no regrets there. Try it out and let me know if it works.

---

### Post by visionviper on 2008-11-26
If you were having this problem in Windows what would you think then?

Bugs happen. It's not the end of the world. Give the community a chance to help. I'm sure someone here has figured out a solution - give it time for it to surface.

The workaround I thought I found is working on and off. It will connect sometimes and not other times. I am going to keep testing.

---

### Post by icanfly0307 on 2008-11-26
Trust me guys. Switch to WEP. It's more secure and it works flawlessly in Ubuntu. Give it a shot!

---

### Post by freestyleren on 2008-11-26
Will do. Thanks for the advice.

---

### Post by freestyleren on 2008-11-26
Isn't WPA the safest form of encryption?

---

### Post by icanfly0307 on 2008-11-26
Well, you really can't say that one encryption is safer than the other. Each one has its strength. However, I can tell you this. WEP is WAY WAY WAY more hard to crack that WPA. With WPA, all that you have is an itty bitty little passphrase. However, with WEP, it creates a random code based on your passphrase. That code is somthing like 30 characters long (i'm sure that no one will remember that!). So going with WEP is a good thing.

---

### Post by visionviper on 2008-11-26
> Switch to WEP. It's more secure and it works flawlessly in Ubuntu.

If WEP is more secure why is it that everywhere I look says WEP is less secure.

---

### Post by syko21 on 2008-11-26
WEP 128 bit can be cracked in about 5 minutes with aircrack-ng and 20 dollar wifi card. WPA2 with AES is the most secure form of encryption right now.

[http://www.youtube.com/watch?v=IeQmuY-Qqxs](http://www.youtube.com/watch?v=IeQmuY-Qqxs)

I've tested on my home network, it is RIDICULOUSLY easy to crack WEP.

---

### Post by icanfly0307 on 2008-11-26
I didn't mean to give you the wrong information, but think about it this way: WPA only has a single passphrase. WEP on the other hand has a passphrase *and* a key. Wouldn't that make it more secure? And unless you really think that someone wants to hack into your network intentionally, I doubt that it will make much of a difference.

---

### Post by syko21 on 2008-11-26
> **icanfly0307 said:**
> I didn't mean to give you the wrong information, but think about it this way: WPA only has a single passphrase. WEP on the other hand has a passphrase *and* a key. Wouldn't that make it more secure? And unless you really think that someone wants to hack into your network intentionally, I doubt that it will make much of a difference.

It may make sense logically but in practice it is completely untrue. I'm not well versed in network security but from experience WPA is nearly impossible to crack by your average wardriver. WEP has been cracked for several years now.

---

### Post by icanfly0307 on 2008-11-26
Wow. That's kinda frightening to know. I've had WEP for almost 6 years!!!

---

### Post by dkrepitD on 2008-11-26
It's actually rather scary how fast WEP can be cracked nowadays... minutes. WPA2 with AES is today the most secure way to encrypt a wireless connection, but you have to deal with digital certificates and the sort, for the home user it's pretty secure to use the WPA-PSK TKIP. you can actually user longer phrases if you wish, which inevitably make it more secure. 
So.. back on the topic I still have a problem with the WPA connection... how will I solve this... Since it's now obvious why I can't use WEP. Can't have my neighbors stealing my WiFi.

---

### Post by visionviper on 2008-11-26
I have had spotty results with removing the ability of the wireless networking tools in ubuntu from modifying the password stored in the keyring. It has worked only a couple times for me, and the rest of the time it doesn't work. I am till trying to figure out what I did to make it work in the firstplace. I am just going to have to do some more troubleshooting.

Just for everyone's information, I use WPA on my wireless network.

---

