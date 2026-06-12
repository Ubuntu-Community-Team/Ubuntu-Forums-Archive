---
title: "Have to re-enter my wireless network password after rebooting"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by ozbluenose on 2008-06-24
Hello everyone.

Please excuse my ignorance as I'm a newby to Linux - I installed Ubuntu 8.04 Hardy Heron only yesterday.  Note that I have downloaded and installed all system updates when notified by Ubuntu.

I have a problem with my wireless connection where every time I reboot, I have to re-enter my network password into system menu > administration > network to get my network and internet going again.  Once I do this, it's all fine.  I have previously saved the configuration in the Network Settings manager and when I go back into the wireless properties the settings and password are all there (password is hidden by dots).  Simply reselecting the previously saved settings from the location drop-down list and clicking the green tick button that activates does not fix it.  I've even tried re-saving the settings, first overwriting the original location name, and then as a new name, and deleting the original name.  It makes no difference.  Only re-entering the very long password I have each time seems to fix it, which is very tedious.

Any help in newby-understandable (ex-Windows XP user) terms is appreciated.

Kind regards.

---

### Post by pytheas22 on 2008-06-24
In most situations you shouldn't need to use the Administration>Network utility at all.  Network Manager (the program in the upper right corner that manages wired and wireless connections) should be able to connect you without any special configuration.  Unless NM wasn't working for you, I would try reenabling roaming mode and using NM.  If NM doesn't work, if you describe the problem in greater detail we can figure out why.  The Network utility should really only be necessary if you're using a static IP or have other special configuration requirements.

---

### Post by ozbluenose on 2008-06-24
Hello Pytheas22.

Thank you for your time and help.

Roaming mode didn't work for me.  I just tried it again and was unable to bring up a different web page, but as soon as I manually configured the network it was fine.

I assumed, in any case, that I would need to not use roaming mode as there are other wireless networks within range that are not for my use.  I am setting this up at home.  My own wireless network, like the others I see, is secured with a password.  If I select roaming mode, then it seems I cannot supply a password and so my router, or the neighbour's somewhere, doesn't allow the connection.

In my manual configuration, I selected DHCP for the IP address, which is served by my router.

I'm just not sure why the password needs to be re-entered each time I reboot, especially when it seems to have it still in place when I overwrite it.

Thanks again for your time.

---

### Post by pytheas22 on 2008-06-24
Strange that NM doesn't work, but it can be buggy for certain kinds of wireless cards.  You could try [wicd]("http://wicd.sourceforge.net") as a substitute.  It tends to work better and you can more explicitly choose which network(s) it should automatically connect to.  I think NM decides where to autoconnect just based on what you use most, but it might be doing a bad job, especially if there are unsecured networks with solid signals in range.

Also, what does the command:
```

cat /etc/network/interfaces
```

tell you?  That's the file that the Network utility should be writing to, so maybe there's a problem with how it wrote the password in.

---

### Post by walkerk on 2008-06-24
You could always give [WICD]("http://wicd.sourceforge.net") a try...

---

### Post by ozbluenose on 2008-06-26
Well hello again Pytheas22 and Walkerk.

Thank you both for your time and help.

It's taken me a while to reply as I was hesitant to try anything else, such as Wicd, without really knowing what I am doing.  Anyway, I've done it and it appears to be working okay, so thank you both.  I may have done some damage in other areas along the way, although I've not noticed anything yet; Wicd said it was automatically removing the Gnome network manager, but it didn't.  I initially couldn't get Wicd to work as I couldn't see where to put my encryption key as it's not exactly obvious.  I was still able to use Gnome NM to connect to the internet once I'd entered my encryption key into it again.  I removed Gnome NM manually from the Package Manager - this is what I'm concerned about whether I've done any damage - and then I found where to put the encryption key into Wicd and away it went - success.  It also automatically connects upon reboot, which Gnome NM wasn't doing.  So a good outcome.

Thanks again.
Regards.

---

### Post by pytheas22 on 2008-06-26
I'm glad you got it working.  Removing Network Manager isn't going to cause any problems.  As long as you have a client to get you online, you're fine.  And in any case, you'd still be alright without either NM or wicd, as you can always use the command-line to connect if it comes to that.

NM tends to be buggy for a lot of people; I'm increasingly puzzled at why Ubuntu uses it by default instead of something that's proven more reliable, like wicd.

---

