---
title: "Why i hate dansguardian"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by Archangelos on 2011-07-19
I constantly hear praise for this piece of software. I hear that it is highly customizable and does a great job at filtering internet. That's great. That's all wonderful. I love to hear those things. And this is probably true if one thing is true...the user can actually get this stupid piece of garbage TO WORK RIGHT!](*,)

I'm not going to lie to you. I** HATE** dansguardian. And installing Webcontentcontrol doesn't make it better. It just reinforces why I started to loathe the flimsy cornhusk app way back in Ubuntu 8.10. Now I run 11.04.

There has never been a time I've used dansguardian that I have consistently been able to make it work. This time is no different. At first, it actually did work, then it B**ROKE and DOESN'T WORK** anymore. And how did this happen? I  didn't do anything different. I didn't have to. It just broke on it's own. You know why? **BECAUSE IT'S DANSGUARDIAN!**

It's either the stupid FireHOL (woe be that firewall!), or TinyProxy (may that proxy live in infamy!).

**I hate it, I hate it, I hate it! **A user interface is a wonderful thing, if it actually helps the user to set up something right. But it's not the user interface's fault, is it? No, it's not. It's that wretched, awful, loathsome conglomeration of BUGS and ERRORS known as Dansguardian!

I do despise it. I hate you Dansguardian!

---

### Post by Archangelos on 2011-07-19
I know what you're thinking. You're thinking, Hahaha! Look at that n00b trying to get Webcontentcontrol to actually function! What a loser! If he knew anything at all about Linux, Ubuntu, or even life in general he would know that there IS NO WAY TO GET DANSGUARDIAN TO WORK AT ALL! HAHAHHAHAHAHAH!

Let's just see how long he squirms around reading one useless howto after the next.

---

### Post by bodhi.zazen on 2011-07-19
Actually I am thinking you need to learn how to ask for help =)

Dansguardian works flawlessly for me, here is how I configure it

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)
[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

But if you need help you will need to:

1. Tell us what tutorial you are following.

2. How did you configure dansguardian.

3. What other proxy are you using, and how did you configure that ?

4. What do you mean it is broken ?

Simply stating you are frustrated does not do much for providing support.

This is a classic link:

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

---

### Post by jtarin on 2011-07-19
Someone trying to give DANSGUARDIAN a bad rap......so it will show up in Google search as such.....let's see who is the competition?=;

---

### Post by bodhi.zazen on 2011-07-19
> **jtarin said:**
> Someone trying to give DANSGUARDIAN a bad rap......so it will show up in Google search as such.....let's see who is the competition?=;

Could be, but configuring proxies is not so easy. Sure as with all things one you do it a few times it becomes familiar, but how do you enforce such proxies on all users on all browsers on all OS with the minimal amount of work ?

---

### Post by jtarin on 2011-07-19
Many different things are difficult to accomplish......for some near impossible, but to ascribe any feelings to a piece of software is useless and non productive. Either ask for help in configuring or find an alternative or.....do without. It's not worth the time and effort to vent.:P

---

### Post by MyR on 2011-07-20
I use content-filtering across my entire home network with opendns.  No software installation required!

Edit: jatir: Thanks for the link in your sig!! That's awesome!

---

### Post by Jordy_224 on 2011-07-27
Dansguardian requires effort to setup, but its worth it. Don't give up.

---

### Post by Untold on 2011-07-31
Bodhi:the privoxy how-to was awesome.  I too had some issues where after a day of dansguardian working, it just decided to stop letting any connection through.  I hope this works.

---

### Post by Rasa1111 on 2011-07-31
wow! :o
That's a lot of hate for something as silly as a little app. O_o
you ok?

---

### Post by Paqman on 2011-07-31
Dansguardian is a pain, and not really worth the hassle IMO. As already mentioned you can do all your filtering on the content before it reaches you by switching your DNS provider to OpenDNS or DynDNS and enabling their content filtering options. They'r both free, you enable them by changing the DNS settings in your router.

If you want a desktop option I'd suggest [Gnome Nanny](apt:nanny), it's in the Ubuntu repos. It's a relatively new piece of software Gnome have brought out, so isn't quite 100% yet, but it's already a lot better than Dansguardian.

---

### Post by bodhi.zazen on 2011-07-31
> **Untold said:**
> Bodhi:the privoxy how-to was awesome.  I too had some issues where after a day of dansguardian working, it just decided to stop letting any connection through.  I hope this works.

You are welcome .

> **Paqman said:**
> Dansguardian is a pain, and not really worth the hassle IMO. As already mentioned you can do all your filtering on the content before it reaches you by switching your DNS provider to OpenDNS or DynDNS and enabling their content filtering options. They'r both free, you enable them by changing the DNS settings in your router.

Depends on how much flexibility you need. Changing your DNS provider as you suggest is easy, but it really does not give a per user flexibility the way Dansguardian does.

Also I find there is not single blacklist that will please everyone, Dansguardian allows one to have a little more flexibility.

The bottom line, these are tools, use the right tool for your needs.

> If you want a desktop option I'd suggest [Gnome Nanny](apt:nanny), it's in the Ubuntu repos. It's a relatively new piece of software Gnome have brought out, so isn't quite 100% yet, but it's already a lot better than Dansguardian.

I have not tried gnome nanny as I find Dansguardian is easy enough to configure.

Thanks for the suggestion, hope it helps someone.

---

### Post by Untold on 2011-07-31
> **jtarin said:**
> Someone trying to give DANSGUARDIAN a bad rap......so it will show up in Google search as such.....let's see who is the competition?=;

When I first looked for dansguardian in google, I did not see it.  :-\"

---

### Post by hollerith on 2011-10-20
OpenDNS / DynDNS sounds good for stopping it at source but sometimes I want to see things that the kids shouldn't be looking at such as reddit.  

There isn't a problem with dansgaurdian configuration per se, as usual there is lots of help (legions of people with problems with dansguardian helping each other) but dansguardian doesn't even build from sources anymore, moans about libpcre (depends on slax? pcre-devel).  

It fails to start from the deb either - bad syntax in the version number.  I've seen this kind of thing before.  The guy plainly hates us back - have you seen the docs???

I like the look of Gnome Nanny or maybe squidguard if it does the job and the transparent proxy links mean you don't have to configure dozens of web browsers.  

So yes I too 'hate' dansguardian now but at least I have bodhi's links and my googlefoo is low currently 

thx!!!

---

