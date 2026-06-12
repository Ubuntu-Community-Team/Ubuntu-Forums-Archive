---
title: "Switching proxy settings based on network connection"
date: 2008-01-01
forum: Networking &amp; Wireless
---

### Post by Webspot on 2008-01-01
I have a laptop that I take to different wireless networks. On my school's wifi network, I am required to use a proxy to access the internet. At the moment I am having to go to System -> Preferences -> Network Proxy and then type in the proxy server myself. And then when I return home, I have to switch the proxy to my personal squid server.

What I'd like to know is whether there is a way to automate this. I'm guessing this could be done by looking at what wireless network I am connected to.

I have a nokia n800, and this has the functionality to do what I require. And the nokia n800 is run on maemo (a linux based operating system). I'm guessing this is possible somehow then.

---

### Post by agimei on 2008-01-07
Deleted post because was answer to different question..sorry.

---

### Post by dragon_788 on 2008-02-12
Hi webspot, I believe there are Firefox extensions to do what you want. Search their site a bit and if you are still having trouble come back and let us know some more info.

---

### Post by sawjew on 2008-02-17
Hi Webspot,

did you find an answer to this?  I was about to post a similar question when I saw yours.  I currently use xyz proxy to switch proxies in Firefox but that is not the only proxy setting I need.

I work at a university and have to use the proxy to access the net but I don't use any proxy at home.  Currently I have to set the system wide proxy, Thunderbird proxy, Firefox proxy and Synaptic proxy (if I happen to need synaptic) all individually when I switch locations.  Does anyone know of a way to make these all switch automatically depending on which wireless connection the computer is currently using?

Any help would be greatly appreciated.

---

### Post by Webspot on 2008-02-18
Unfortunately not. I've scowered the web, and have been unable to find anything.

---

### Post by tora201 on 2008-04-02
Did anybody solve this? I am in the same situation.......
A little annoying having to do it all by hand depending on location. Help, please?

Cheers

---

### Post by dbkungfu on 2008-04-02
hi

check this out
firefox add-on [https://addons.mozilla.org/en-US/firefox/addon/125]("https://addons.mozilla.org/en-US/firefox/addon/125")

---

### Post by tora201 on 2008-04-04
Hey mate. Thanks for that. I should have checked add ons for Firefox before. The plugin link you provided certainly does make things easier. I just wish that there was a system wide solution.

Cheers

---

### Post by takmsdsm on 2008-04-08
A system wide one step proxy for all programs would be great, im in the same boat. I cant even install certain programs while im at work if the install involves downloading dependencies from the terminal. They work just fine at home. :(

---

### Post by balak on 2008-06-23
I agree - having a systemwide proxy that is accepted by firefox, thunderbird and synaptic will be useful.

I would go ahead an say that this proxy should be set based on which wireless network you are connected to.


> **takmsdsm said:**
>  I cant even install certain programs while im at work if the install involves downloading dependencies from the terminal. They work just fine at home. :(

Actually, you can set the proxy at the terminal:
> export http_proxy="myproxy:80"

After this, you should be able to install packages from the terminal through the proxy.

---

