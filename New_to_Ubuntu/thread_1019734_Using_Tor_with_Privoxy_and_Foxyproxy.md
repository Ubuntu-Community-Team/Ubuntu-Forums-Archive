---
title: "Using Tor with Privoxy and Foxyproxy"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by sanjeevpunj on 2008-12-23
I first installed privoxy, configured it,started it,then installed Tor and staretd it,then installed Foxyproxy, and using Foxyproxy I configured how Tor would connect. 

I used the following settings for Tor:-

Http proxy: localhost, 8118
same for others except Socks
Socks Proxy:localhost,9050
SOCKS proxy SOCKSV5

I dont know what is wrong with these settings, perhaps there is some major mistake here. I am not able to work with Tor enabled. 

I had installed Ubuntu and used it without proxies for quite a while, but now I am trying to see how it works with these proxies.

Anyone wanna tell me where I went wrong?

---

### Post by wolfen69 on 2008-12-23
anyone that "needs" tor and privoxy is doing something..... well, i won't say it. plus, this isn't the right place to ask.

---

### Post by sanjeevpunj on 2008-12-23
> **wolfen69 said:**
> anyone that "needs" tor and privoxy is doing something..... well, i won't say it. plus, this isn't the right place to ask.
I dont really need to use these, and I am surely not doing what you think, because I need to understand how these things work, period.I wouldn't have replied to you if I was doing something else that you imagined. All that can be done easily in that lowdown Windows XP Platform with great ease (ULTRASURF). I wouldn't be spending time trying to understand how TOR and PRIVOXY work in LINUX. I don't know why how easily people start moral lecturing, but surely I am not doing what you imagined, nor do I really want to do any of that. All I want is to understand the nitty gritty of Linux proxies, so that my kids do not start using proxies without my knowledge. No I am not hurt by what you said, but I think you should consider before assuming things about users.

---

### Post by wolfen69 on 2008-12-23
you're assuming i am thinking of bad things. if you take what i said literally, nothing can be assumed. i did not accuse you of anything. secondly, there are better forums to ask this question in than testimonials & experiences. perhaps the networking forum?

---

### Post by sanjeevpunj on 2008-12-24
No I am not assuming. You typed : "doing something..... well, i won't say it." is clear enough to understand what you meant. Anyway I am not taking it far, and thank you for the suggestion, I did find another forum that has helped. Merry Christmas!

---

### Post by zugu on 2008-12-25
I would suggest using Torbutton instead of Foxyproxy. Torbutton is designed to work with Tor and it keeps your Tor and non-Tor cookies and personal information in separate jars. Torbutton is the right choice if you need the anonymity Tor provides.

You might also want to install the [Vidalia]("http://vidalia-project.net") Tor frontend, although it's a pain to set it to communicate with Tor in Linux. There is no Tor-Vidalia-Privoxy-Torbutton bundle for Linux, only for Windows. 

Since your Tor installation doesn't work, after installing and configuring Vidalia, _check its message log for Tor errors_. There might be a firewall, router or proxy that prevents Tor from connecting to the internet - if that's the case, set Tor to route through unblocked ports , such as 80 or 8080. There might be other things preventing Tor from connecting, such as your ISP suddenly blocking connections to known Tor exit nodes (if that's true, then you need to use a bridge relay). The Vidalia message log will provide valuable information, and it's documentation is straightforward and helpful.

@wolfen69: you are clueless about Tor and people like you give it a bad name.

---

### Post by Sef on 2008-12-25
Moved to Absolute Beginners.

---

