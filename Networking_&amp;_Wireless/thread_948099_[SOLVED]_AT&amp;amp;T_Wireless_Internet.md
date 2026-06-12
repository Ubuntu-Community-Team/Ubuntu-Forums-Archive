---
title: "[SOLVED] AT&amp;amp;T Wireless Internet"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by luiznetto on 2008-10-14
I just moved in with a roommate who has AT&T Wireless Internet connection, which I want to share. I go to internet cafés all the time with my Ubuntu laptop, and I have no trouble connecting. When I try to connect to my roommate's AT&T, though, Network Manager gives me a strange prompt that asks me for a "wireless network key" or "secret phrase - cryptography key" - what the heck is that? To connect from a Windows laptop, all you need is the password. AT&T gives no Linux support; that doesn't necessarily mean that it doesn't work with Linux, only that you're on your own. Does anybody know the answer to these questions: Does AT&T Wireless Internet work with Linux at all? And, in case it does, how to make it work with my Ubuntu?
Thanks in advance.
Luiz

---

### Post by tgalati4 on 2008-10-15
Your roomate needs to give you a 10-digit hexidecimal key.  He can get this by logging into the router from a browser (typically  [http://192.168.1.1](http://192.168.1.1)).

You can sometimes use a simpler password that then generates the required 10-digit key.

---

### Post by luiznetto on 2008-10-18
Sorry, tgalati4, but your reply has not been useful. My roommate says he has no idea what I'm talking about. He says he doesn't have a router. He says the guy from AT&T came in to insall the network, asked him to make up a password, and all he needs to connect is his user name and his password. All other roommates in the house just do the same. I'm using a Windows laptop that I borrowed from a friend now at home with my roommate's wireless, and when I try to access [http://192.168.1.1](http://192.168.1.1) from Firefox, all I get is an error message: "Page Load Error: The server is taking too long to respond."

---

### Post by bionnaki on 2008-10-18
192.168.1.254 on a connected computer.

---

### Post by oohyeah on 2008-10-18
You have to install the wireless internet device on your PC.  You can detect the network, but it not built to act as a router.  The wireless broadband cards provided by cell phone companies don't generally act as routers -- only wireless modems for the one computer that they are installed on.

---

### Post by luiznetto on 2008-10-20
Thanks, tgalati4; I finally managed to connect. What I didn't realize is that what my roommate gave me **was** the hexadecimal key, not a password; and it's an open system, not shared key as per Gnome Network Manager. But now there's another problem: when I go to an internet café, they only give me the password once; next time I visit the café, it detects the network and works automatically, without asking any questions. Things don't work the same here: I have to input that long hexadecimal key every time I connect. That's a minor problem, I acknowledge; but it's an irritant anyway. I'm stating to get fed up with AT&T; and plus I found information online that it **spies on its customers**. Maybe that's a subject for another section of this forum, but now each time I connect I get a prompt from Network Manager that says:
"The application nm-applet (usr/bin/nm-applet) wants access to the standard keylock, but the same is locked." Then it asks for my password, with the options "deny" or "ok". I don't know what that means, but just for caution I changed my Ubuntu password, and removed all the cookies that seemed to be from AT&T from my browser.

Thanks to all who helped me.

---

