---
title: "Hardening FireFox? - used to use &quot;Proxomitron&quot;"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-21
Hi all - a week with U8.10...I have used FireFox since back when it was Phoenix 0.4...and always with the Proxomitron - a software proxy that uses multiple configurable html (& https) filters to clean and speed up loading websites.

It is so effective that I have never bothered with worrying about scripts, pop-ups or anything else, and webpage load blistering fast. As a software proxy I would run at startup and route Opera thru it as well.

Not sure if MozillaZine would be better forum, but here goes...hehe..

I have configured FF3.06 (stock, not the UBrand clone) with AdBlock and NoScript, and ticked the FF options for blocking pop-ups. Have always allowed javascript and java to run. 

They are kinda cludgy, and intrusive, but I think effective. 

Two thoughts - can I use Wine 1.01 to install the Proxomitron and duplicate my Windows FireFox configuration?

OR; any suggestions for 'hardening' FF in addition? Not wanting paranoia level stuff, just normal smart web savvy steps?

Cheers

dmc

---

### Post by BastardNamban on 2009-02-21
Ah, Proximitron- good choice. I used that all the time too, and I haven't found anything since that works as well for gnome & modern Firefox.

You should be able to install Proximitron under Wine without any problems, but I don't know that it will work at all across Wine to modify Firefox running in Gnome. You'd need to install Firefox for windows under wine, and rig Proximitron to work with that one. I'm not sure if that will work though, as I haven't heard of it being done before. But it should work.

I'm afraid you're already well set up with no-script, so I can't recommend anything more.

---

### Post by deadmanschest on 2009-02-21
> **BastardNamban said:**
> Ah, Proximitron- good choice. I used that all the time too, and I haven't found anything since that works as well for gnome & modern Firefox....   [snipped by dmc]


Hi BastardNamban - thanks for the response. I feared as much, and I'm finding that AdBlock/NoScript seem to cull most cr*p out of sites, but hate to lose Proxo....

I won't try to set up Wine/run WindowsFF etc., just stick with the stock FF3.06 and extensions...I find the transition into U8.10 from years of Windows a little weird, so just reading on Wine to see how to install some 'must have' apps and even that is getting a little odd..hehe..

Cheers

dmc

---

### Post by oldos2er on 2009-02-21
Privoxy is in the repositories. [http://www.privoxy.org/](http://www.privoxy.org/)

---

### Post by deadmanschest on 2009-02-21
> **oldos2er said:**
> Privoxy is in the repositories. [http://www.privoxy.org/](http://www.privoxy.org/)

Hey Ann - thanks for the headsup!. I'll see if I can get it.

I have not used Privoxy, is the setup and config of filters pretty much Proxo...?

cheers

dmc

---

### Post by oldos2er on 2009-02-21
I don't know anything about Proxo; but I used to use Privoxy on OS/2. The link I gave you should give info on configuring it, which as I recall wasn't terribly difficult.

---

### Post by deadmanschest on 2009-02-21
> **oldos2er said:**
> I don't know anything about Proxo; but I used to use Privoxy on OS/2. The link I gave you should give info on configuring it, which as I recall wasn't terribly difficult.

Thanks, I'll check it out.

cheers

dmc

---

### Post by invenit on 2009-02-21
> Two thoughts - can I use Wine 1.01 to install the Proxomitron and duplicate my Windows FireFox configuration?

I definitely use Proxomitron with my Web browsers in Ubuntu 8.10. Firefox is already well provided for with some fine extensions, but other browsers (Epiphany, etc.) are not. Still, I chain Firefox through Prox as well. Prox works great with Crossover, and probably with Wine. For filters, I use the up-to-date stuff from Germany. Check out [http://www.buerschgens.de/Prox/Seiten/Download/index.html](http://www.buerschgens.de/Prox/Seiten/Download/index.html)

If you don't read German (I don't), then you need to load the Foxlingo firefox extension. Surf back to the site after you get Foxlingo and click the "Autotrans" button. Read. I suggest that you download the "professional" version & install.

I've been testing several different Prox filter sets and--so far--the German edition really works best for me. Current too (the latest changes were in Feb. 2009!). :popcorn:

---

### Post by deadmanschest on 2009-02-21
> **invenit said:**
> I definitely use Proxomitron with my Web browsers in Ubuntu 8.10. .... :popcorn:

[snipped by dmc]

Hey invenit - thanks for the great response! Sounds very encouraging. I will follow up when I have a chance to try get Prox running in U8.10. 

Glad the config is working for you. I used JD5000 and then Grypen and some KyeU but pace has slowed in last years, and I'm not kidding anyone, I couldn't write a filter if it bit me....hehe

Thanks very much!

dmc :popcorn:

---

### Post by bodhi.zazen on 2009-02-21
Just my 2c ....

I have used privoxy and tor, mainly for privacy.

IMO it is simpler (and faster) to use Adblock + Noscript, the combination does a nice job.

With that said, privoxy is nice. tor is s ... l ... o ... w ...

Not heard of Proxyomitron, but instalilng wine just to use a proxy sounds like you are adding several layers of complexity that are likely unnecessary.

---

