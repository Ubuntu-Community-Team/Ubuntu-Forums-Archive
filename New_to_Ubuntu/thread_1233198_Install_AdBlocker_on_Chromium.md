---
title: "Install AdBlocker on Chromium"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-08-06
I am using Chromium (the linux version of Chrome) in ubuntu and I was wondering if there is any way to install extensions, primarily an adblocker.

Thanks

---

### Post by philinux on 2009-08-06
Dont think there is an adblocker yet.

---

### Post by abhiroopb on 2009-08-06
[http://www.adsweep.org/](http://www.adsweep.org/)

This has instructions for Windows, but not sure how to make it work in Ubuntu.

---

### Post by Anxious Nut on 2009-08-06
You could always use this method; [http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/]("http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/")

This will block all the ads in your whole system, only four simple steps;)

---

### Post by abhiroopb on 2009-08-06
Not bad...thanks!

---

### Post by philinux on 2009-08-06
Not bad at all till they sort chromium out eh. :D

It's still work in progress on linux.

---

### Post by Anxious Nut on 2009-08-06
you're welcome ;)

---

### Post by bodhi.zazen on 2009-08-06
> **Anxious Nut said:**
> You could always use this method; [http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/](http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/)

This will block all the ads in your whole system, only four simple steps;)

That is a nice method.

I wrote a script to do this for you :

[http://bodhizazen.net/adblock/adblock-0.98.sh](http://bodhizazen.net/adblock/adblock-0.98.sh)

The only problem with this technique, it does not work so well on servers =)

More info is here :

[http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm)

---

### Post by kerry_s on 2009-08-06
**sudo apt-get install bfilter**

then set chromium proxy to "127.0.0.1:8080".

there's also a gui with a tray icon if you want that, just look in synaptic.
bfilter is also available for windows to.

here's what the proxy setting looks like in my firefox.

---

### Post by bodhi.zazen on 2009-08-06
> **kerry_s said:**
> **sudo apt-get install bfilter**

then set chromium proxy to "127.0.0.1:8080".

there's also a gui with a tray icon if you want that, just look in synaptic.
bfilter is also available for windows to.

here's what the proxy setting looks like in my firefox.

Thanks for the tip kerry_s bfilter looks awesome.

---

### Post by abhiroopb on 2009-08-07
> **kerry_s said:**
> **sudo apt-get install bfilter**

then set chromium proxy to "127.0.0.1:8080".

there's also a gui with a tray icon if you want that, just look in synaptic.
bfilter is also available for windows to.

here's what the proxy setting looks like in my firefox.

What does bfilter do exactly? Is it any different to the other suggestion?

BTW The other suggestion works great, except everywhere I see a massive: WEB PAGE NOT FOUND ERROR

---

### Post by Anxious Nut on 2009-08-07
> **abhiroopb said:**
> What does bfilter do exactly? Is it any different to the other suggestion?

BTW The other suggestion works great, except everywhere I see a massive: WEB PAGE NOT FOUND ERROR

Well that's what you get for blocking for the whole system, not only a specific web browser, btw it looks Kay

---

### Post by kerry_s on 2009-08-07
> **abhiroopb said:**
> What does bfilter do exactly? Is it any different to the other suggestion?

BTW The other suggestion works great, except everywhere I see a massive: WEB PAGE NOT FOUND ERROR

it removes ad's. you won't get errors. :D
i find it faster than all other options, theres no speed hit & it's very clean. plus you don't have to setup anything, it works great on install just set the proxy.
read the site: [http://bfilter.sourceforge.net/](http://bfilter.sourceforge.net/)
point me to a page of ad's & i'll give you a pic what it looks like. for now here's a look at hotmail.

---

### Post by bodhi.zazen on 2009-08-07
enable the proxy , go to doubbleclick

disable the proxy and re-load the page.

---

### Post by kerry_s on 2009-08-07
> **bodhi.zazen said:**
> enable the proxy , go to doubbleclick

disable the proxy and re-load the page.

is that meant for me?

---

### Post by kerry_s on 2009-08-07
here's what the gui looks like for bfilter.

---

### Post by kpkeerthi on 2009-08-07
bfilter looks sweet. I checked its website and currently it lacks blocking text ads capability, which is important for me.

---

### Post by kerry_s on 2009-08-07
> **kpkeerthi said:**
> bfilter looks sweet. I checked its website and currently it lacks blocking text ads capability, which is important for me.

actually, it does work, but is a bit hit or miss. 
i haven't really noticed them, but it's not like i'm looking.
on mine i don't even bother messing with the settings, i just install & set it to the proxy & pretty much forget about it, which is why i don't even bother with the gui.

i think you should just give it a try, if you don't like it, it's easy to remove with synaptic. the gui is "bfilter-gui".

a step up would be privoxy, which is a little complicated & does have noticeable slow downs on ad heavy pages.

---

### Post by philinux on 2009-08-07
Interesting. bfilter will be getting test very soon.

---

### Post by abhiroopb on 2009-08-07
bfilter works great for me, but there is a bit of a hiccup...

I use Chromium (as I said in the beginning), and to change proxy settings in Chromium you need to change system-wide proxy settings (i.e. unlike firefox which has its own proxy configuration, with Chromium I need to change Gnome's proxy settings). The problem this causes is that I am unable to connect to MSN and GTalk through pidgin.

When I remove the proxy settings I can connect to the IM clients but then the ads re-appear.

I assume there is someway to fix this, but I am worried that using bfilter will affect other internet connections if I have to use system-wide proxy settings.

Any thoughts?

---

### Post by kerry_s on 2009-08-07
that sucks, i can't believe they didn't think beyond using ie's settings. :lolflag:

anyways, looks like you add a line to the launcher "chromium-browser --proxy-sever=127.0.0.1:8080"

is there even a man page you could check what the switches are?

---

### Post by abhiroopb on 2009-08-07
Thanks for that...

when I launch chromium in the terminal like that: chromium-browser --proxy-server=127.0.0.1:8080 --enable-plugins

it launches fine (and I don't see the ads)

But when I launch it using the launcher (with the switches) the ads still appear.

---

### Post by abhiroopb on 2009-08-07
Somebody in the comments has posted a list of switches here: [http://lifehacker.com/5045795/get-more-omnibox-suggestions-in-google-chrome#c7637405](http://lifehacker.com/5045795/get-more-omnibox-suggestions-in-google-chrome#c7637405)

---

### Post by kerry_s on 2009-08-07
hold on a bit, i just installed, let me get a feel & get back to you.

small problem, where did you get your deb? mine installed as google-chrome. i got mine here:
[http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux)

---

### Post by kerry_s on 2009-08-07
> **abhiroopb said:**
> Thanks for that...

when I launch chromium in the terminal like that: chromium-browser --proxy-server=127.0.0.1:8080 --enable-plugins

it launches fine (and I don't see the ads)

But when I launch it using the launcher (with the switches) the ads still appear.

i dont know mine works in the launcher.

---

### Post by abhiroopb on 2009-08-08
Thats strange...

I don't know why it doesn't work for me. Its especially strange since the --enable-plugins works (as I can view flash videos on youtube).

---

### Post by ubulette on 2009-08-08
> **abhiroopb said:**
> Thanks for that...

when I launch chromium in the terminal like that: chromium-browser --proxy-server=127.0.0.1:8080 --enable-plugins

it launches fine (and I don't see the ads)

But when I launch it using the launcher (with the switches) the ads still appear.

a while ago, I've introduced /etc/chromium-browser/default in the Ubuntu package, you can add any flag you want there, they will survive the upgrades. No need to tweak the desktop launcher, not for aliases or wrappers.

I don't provide any value by default, because i want users to have the upstream experience. Once upstream thinks a feature is ready, it becomes default and the corresponding flag disappears.

While I'm there, i should mention that there's also chromium-browser-l10n for people with non en-US desktops.

---

### Post by abhiroopb on 2009-08-08
Thanks...just put it in...will report back!

**UPDATE:** Works great...better to do this than mess with the launcher!

---

### Post by kerry_s on 2009-08-08
wow, wish i had that.

hey abhiroopb,
 you said when you set the proxy it would block your pidgin, my pidgin works fine. im using "export HTTP_PROXY=127.0.0.1:8080" in my ~/.profile cause i use xfce4 and don't have a network manager.

also pidgin has a network setting where you can select "no proxy" to bypass the proxy just to be sure.

---

### Post by abhiroopb on 2009-08-08
That actually seems to work. But I prefer doing this on a per-app basis rather than it taking over all internet connections on my computer!

---

### Post by kerry_s on 2009-08-09
> **abhiroopb said:**
> That actually seems to work. But I prefer doing this on a per-app basis rather than it taking over all internet connections on my computer!

:lolflag: yeah, i'm sure they will eventually fix it, i mean they got the button, just need to do the proxy gui for chromium.

i went back to firefox(iceweasel) the page loading was just to slow & it's not a true 64bit program, so i'll just wait. 
i do miss the startup though, it's damn fast, even from a cold start.
can't wait till they make a true 64 version.

---

### Post by shae on 2009-08-09
Whenever I use bfilter, I usually have problems (browsing is really slow) browsing while flash is downloading a video in another tab.  Does anyone else have that problem?

---

### Post by kerry_s on 2009-08-09
> **shae said:**
> Whenever I use bfilter, I usually have problems (browsing is really slow) browsing while flash is downloading a video in another tab.  Does anyone else have that problem?

i think thats more of a flash problem, on mine they took a while to load, with & without bfilter it was the same. i did do a quick google on it & basically just says plugins is work in progress.

did you try with bfilter off? if your using the gui version with the tray icon just click the bypass to test.

---

### Post by shae on 2009-08-09
BFilter On, Flash loading in one tab, browsing in another = browsing slow
BFilter off, Flash loading in one tab, browsing in another = normal speed

I think BFilter uses some sort of filter on flash to check if it is ads and it chokes down the process?

---

### Post by abhiroopb on 2009-08-18
A much cleaner solution for blocking ADs is outlined here ([http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html))

Essentially, it installs the AdSweep extension in Chromium.

This means you don't need to mess around with bfilter.

---

### Post by kpkeerthi on 2009-08-18
> **abhiroopb said:**
> A much cleaner solution for blocking ADs is outlined here ([http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html](http://penguininside.blogspot.com/2009/08/how-to-setup-chromium-google-chrome.html))

Essentially, it installs the AdSweep extension in Chromium.

This means you don't need to mess around with bfilter.
Thanks for that. I guess I can give Google Chrome a spin now.

---

### Post by kerry_s on 2009-08-18
nevermind

---

### Post by titan_90 on 2009-11-01
> **Anxious Nut said:**
> You could always use this method; [http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/]("http://aaobloggers.wordpress.com/2009/03/06/how-to-block-ads-ubuntu/")

This will block all the ads in your whole system, only four simple steps;)

Works great, many thanks:D

---

