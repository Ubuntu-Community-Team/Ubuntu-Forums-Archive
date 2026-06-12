---
title: "Add-on Error code, GUFW, Firestarter, No-scripts, Private Browsing"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by woofy on 2010-01-03
Long time listener, first time caller...Thanks for having me.

My experience with Linux, Ubuntu specifically, dates back to Saturday morning -- two days ago. Done some research and can't find answers to four of the issues below. The other two are thrown in because I wanted to make the most of this post. Please bear with me and thanks in advance for the help.

1- I read that one does not need to keep the GUFW open to provide firewall service since the GUFW's purpose is simply to provide a GUI to make changes to the iptables. Is this true for Firestarter? 

I know now through experimentation that I can only use one or the other and I like the GUFW for it's simplicity, but I also like Firestarter because it shows me in the simplest form my current program/network activity. (I know I'm supposed to keep track of it, but I can't make heads or tales of the log file. I see English words, but it still reads like a foreign language.)

2- Is it safe to keep Firestarter, or other system applications, open? I read that since we must use our password (I guess through sudo) to open Firestarter and the like, having a system application open leaves us vulnerable to attack. Is this correct? Can't tell you where I read it, and can't really say that I'm sure that's what I read. I've been through a lot of information this weekend.

3- I keep getting a popup (png file attached to this post) when I attempt to use the add-on feature in Firefox. I get around this by going to the add-on website to add anything. Still, it pops up every time I open the add-on tool/thing and I can't use the add-on tool to install add-ons. After I 'okay' out of the error code, I can manage the add-ons.

4- Using the no-scripts add-on in Firefox is a lot of work, but I don't mind having to add sites to a white list. In fact, doing so gives me a huge sense of security (false sense or not?). However, since I consider my web use quite safe, is the no-scripts add-on a must have for everyone. Still using it, but curious about the impact of having it off during a safe/secure browsing session.

5- Had Firefox preferences set to automatically start the browser in a private session but could not access one of my secure sites. I managed to log into the main site (after adding a few exceptions) but it couldn't redirect me to its webmail feature. Unchecked the auto private session option and it works okay now. Still got the 'accept cookies' box unchecked and I added my site to the cookies exception. Is the setup safe enough without being in a 'private browser session'?

6- GUFW doesn't maintain it's settings. I haven't been using Firestarter. I just check the 'enable' box in the GUFW and exit the program. It unchecks itself on restart as well. Is this normal?

Wish I could come up with some clever Linux quip for a signature but I'm still new to the game. Will work on one.

---

### Post by meborc on 2010-01-03
can't give you specific answers, but a good suggestion is to read this thread - [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

even though it is dated a few years back, it is a very good read

---

### Post by 3rdalbum on 2010-01-03
> **woofy said:**
> 

1- I read that one does not need to keep the GUFW open to provide firewall service since the GUFW's purpose is simply to provide a GUI to make changes to the iptables. Is this true for Firestarter? 

True, but don't use Firestarter anyway - it's unmaintained, unfriendly, has several bugs and features that frighten new users, and I've had no end of troubles whenever I've tried to use it. Just use GUFW and put the System Monitor applet onto your panel (which will show network activity).

> 2- Is it safe to keep Firestarter, or other system applications, open? I read that since we must use our password (I guess through sudo) to open Firestarter and the like, having a system application open leaves us vulnerable to attack. Is this correct? Can't tell you where I read it, and can't really say that I'm sure that's what I read. I've been through a lot of information this weekend.

I don't see the problem with this - it's not like Firestarter directly responds to incoming connections or works with a lot of local files. But generally it's good practice not to run a program as root unless you need to.

> 4- Using the no-scripts add-on in Firefox is a lot of work, but I don't mind having to add sites to a white list. In fact, doing so gives me a huge sense of security (false sense or not?). However, since I consider my web use quite safe, is the no-scripts add-on a must have for everyone. Still using it, but curious about the impact of having it off during a safe/secure browsing session.

I tried it, but it became so incredibly inconvenient having to add each new site to the whitelist. Obviously though, it's a first line of defence against browser attacks that use Javascript (not that you hear a lot about these at the moment). I've never seen one AFAIK and I look at pr0n.

**Finally...**

I do wonder what you want with a personal firewall. A personal firewall stops any incoming connections (except for what you explicitly allow) before any programs respond to them. Now, with a default install of Ubuntu, there are no programs running that will respond to incoming connections anyway!

Server applications will respond to incoming connections, as will Transmission (bittorrent client) - but in those cases you WANT the incoming connection, so a firewall will be counter-productive.

The only time you want a personal firewall is if you want to run a testing server that can't be accessed outside your computer. That's it. Plus, of course, many routers and broadband modems already contain firewalls that will protect your whole network, making a personal firewall completely unnecessary.

---

### Post by WhiteHorse on 2010-01-03
I don't use a firewall app. You only need it if you're running services such as a webserver or remote connections like ssh. When I was running a web server, I used firestarter and it's very poor for logging attacks. Basically you refresh the list of logs and pour through them looking at IPs and ports. If you want a serious firewall, you'll need to configure IPTables and SNORT to analyze the logs. Anything else is just a false sense of security. 

Here's a better option: Set up your servers with project honeypot. Setup your desktops with OpenDNS and honey-pot detected sites blocked. Add NoScript and Ad-Block-Plus to Firefox. 

This has been working for me. Now I'm just figuring out how to deal with man-in-the-middle attacks. They keep trying to intercept my SSL sessions but it fails cause ubuntu is secure, haha.

---

### Post by dearingj on 2010-01-03
> **woofy said:**
> 
3- I keep getting a popup (png file attached to this post) when I attempt to use the add-on feature in Firefox. I get around this by going to the add-on website to add anything. Still, it pops up every time I open the add-on tool/thing and I can't use the add-on tool to install add-ons. After I 'okay' out of the error code, I can manage the add-ons.

I've seen that problem once or twice before, but not consistently. Have you installed all the software updates?

> **woofy said:**
> 4- Using the no-scripts add-on in Firefox is a lot of work, but I don't mind having to add sites to a white list. In fact, doing so gives me a huge sense of security (false sense or not?). However, since I consider my web use quite safe, is the no-scripts add-on a must have for everyone. Still using it, but curious about the impact of having it off during a safe/secure browsing session.

I use NoScript too. I really doubt its usefulness, as I haven't heard of any script-based attacks lately; I'd bet that you can safely turn it off during a private browsing session.

> **woofy said:**
> 6- GUFW doesn't maintain it's settings. I haven't been using Firestarter. I just check the 'enable' box in the GUFW and exit the program. It unchecks itself on restart as well. Is this normal?

Never seen this in GUFW before. Are you running GUFW as root (do you have to put in your password to run it?)?

---

### Post by woofy on 2010-01-04
3rdalbum -- Awesome. Thanks for the info and advice. Getting rid of Firestarter and will leave GUFW alone. Apprciate the help. Hard to get out of the MSWin mindset, but I'm gettin there.

---

### Post by woofy on 2010-01-04
Whitehorse -- I assume from the reading I've done about SSH that it's disable by default. Right? I'm going with your advice as well and will play with OpenDNS and ad-block this weekend. Already have the no-scripts thing going. Thanks for the advice. Really appreciate the help. My confidence in Linux, especially with Ubuntu, is soaring. I'm going to conduct my first banking transaction via Linux tonight!

---

### Post by woofy on 2010-01-04
dearingj -- With this post, I think I just realized that I should just reply once and include everyone rather than reply individually. I thought each reply would be associated with the poster. Sorry.

As for the error code, item #3 in my original post, I'm totally updated as far as I can tell. Ran all the updates with synaptic and everyday I log on there's usually one or more updates to install. For now I can actually handle the error code since I can manage to install add-ons via the website. I'm going to have to dig into it some more though because I'd reall like to use the add-on feature that comes wtih the browser. Should I re-install Firefox (if that's possible)?

As for GUFW, item #6 in my original post, I don't know if you'd say I was running it as root. I didn't log into the root account. But when I open the application, I am asked for my password. I know that's because I'm in the sudoers list and must be using sudo to run the program. Does that mean I'm running it as root even though I'm logged in with my user account? I just booted Linux again this evening and checked GUFW and it's disabled. Still the same problem. However, based on others' advice, I think I'm going to leave that alone for now since I guess I really don't need it. I'm on the default install with no plans for the near future to run a server or connect remotely. I should be good without it, right?

Thanks for the help. I've said it already, but I really am beginning to feel comfortable with Linux security. 

By the way, when should I mark this thread as 'solved'? I've probably got a couple lingering questions in tonight's posts, and I'm eagerly awaiting responses to those. Up to me, right?

Thanks

---

