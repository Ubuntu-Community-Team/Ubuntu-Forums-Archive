---
title: "Enabling ufw v/s Wireless network settings"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by avnd on 2011-05-29
Hello!

I'm new to linux guys. I have gone through the forums looking for a solution. I'm pretty sure there is a solution posted already. But being glued to Windows for a decade and less than a week into this OS, I find most of the posts Greek and Latin. My questions are the following.

1. I learnt that Ubuntu by default has no open ports. But when i run netstat -lptu thingy, there is quite a few showing on the list. Can someone tell me why? (I had setup a wireless account. I don't know if that did anything to that. Pardon me if I sound too newbie. I had to actually use the rfkill thingy to set that wireless up). 
2. Now, I thought I'd enable UFW. Will that mess the wireless setup up?
3. I've read that for all practical purposes, there are no Linux viruses out in the wild. Does that also mean there are no equivalents of the spyware, keyloggers etc, here? (I actually did some reading about this. I haven't gotten the understanding I'd like). Do these things have to be 'installed' to be able to operate? I understand they can't get 'installed' automatically when I'm not running as root. Can they like be downloaded and reside in my hard disk and operate from there?

Thanks for putting up with the length of the post. I did read the security sticky by bodhi.zazen. I'll probably get the hang of it in a month or so. But I'd just setup a dual boot; I like the feel of Ubuntu and would like to get started and learn on the way. :)

---

### Post by wolfen69 on 2011-05-29
Most people can just go with ubuntu's default setup when it comes to ports, and enabling a firewall isn't necessary for most people. If you go to the [Shields Up]("http://www.grc.com/x/ne.dll?rh1dkyd2") website and do the penetration testing, you will see that linux is extremely secure.

About the only chance you'll have of getting malware is if you tried to install a malicious deb file, and of course, you would have to give it permission. Viruses are really not much to worry about.

---

### Post by avnd on 2011-05-30
Thanks for the reply Wolfen69. Can you give me a possible explanation for the listed open ports?

---

### Post by Paqman on 2011-05-30
By default Ubuntu doesn't have all ports closed. What it does have is no services listening on any ports. If there's nothing to connect to on a port, it doesn't matter whether it's open or not, nothing can connect.

---

