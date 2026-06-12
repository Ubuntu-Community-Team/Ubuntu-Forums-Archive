---
title: "Moonlight for Opera"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by d4nnyb0y on 2010-11-01
I'm relatively new to Ubuntu and still finding my feet with how to do things, so figured this was an appropriate place to post.
I am currently using Ubuntu 10.04 LTS - the Lucid Lynx. 

My question is in regard to Moonlight.
I was wondering if it is possible to get it to work in Opera.
I am using Opera 10.63.
I know it works in Firefox, but do not like Firefox as a browser.

Any help would be great!
Thanks.

---

### Post by gandaran on 2010-11-01
> **d4nnyb0y said:**
> I'm relatively new to Ubuntu and still finding my feet with how to do things, so figured this was an appropriate place to post.
I am currently using Ubuntu 10.04 LTS - the Lucid Lynx. 

My question is in regard to Moonlight.
I was wondering if it is possible to get it to work in Opera.
I am using Opera 10.63.
I know it works in Firefox, but do not like Firefox as a browser.

Any help would be great!
Thanks.
remove the firefox mozilla moonlight addon if you have it installed and install the moonlight-plugin-mozilla from the ubuntu software center or synaptic, all browsers will pick up the system installed moonlight plugin except chromium but then you can also install moonlight-plugin-chromium from the repositories.
another way is to just copy the mozillas addon moonlight file from firefox plugin folder and put it in the opera plugin folder.
to check if it is installed in opera type in opera url bar
```
about:plugins
```
it should be at the bottom of the list as silverlight plugin

---

### Post by lovinglinux on 2010-11-01
To test if it is working:

[http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)

---

### Post by philinux on 2010-11-01
I use sky player and they have moved to silverlight version 4 so moonlight is getting too far behind the curve. Having to use win7 to access sky player.

---

### Post by lovinglinux on 2010-11-01
> **philinux said:**
> I use sky player and they have moved to silverlight version 4 so moonlight is getting too far behind the curve. Having to use win7 to access sky player.

Not to mention the package from the repositories usually prevents Firefox from starting. I just tested if it was working on Opera and my Firefox 4 started to crash on start again. Not an issue for the OP I suppose, but I thought it would worth mentioning.

---

### Post by d4nnyb0y on 2010-11-01
> **gandaran said:**
> remove the firefox mozilla moonlight addon if you have it installed and install the moonlight-plugin-mozilla from the ubuntu software center or synaptic, all browsers will pick up the system installed moonlight plugin except chromium but then you can also install moonlight-plugin-chromium from the repositories.
another way is to just copy the mozillas addon moonlight file from firefox plugin folder and put it in the opera plugin folder.
to check if it is installed in opera type in opera url bar
```
about:plugins
```
it should be at the bottom of the list as silverlight plugin

I did this and at the bottom of the page it is listed.
It says:
Silverlight Plug-Inapplication/x-silverlight	     Novell Moonlight	      scr,xaml
application/x-silverlight-2		
/usr/lib/mozilla/plugins/libmoonloader.so
However I am still unable to view pages that require silverlight. Even the one posted by LovinLinux, so it is not just a Silverlight 4 issue.
However it does work in Firefox.
Am I doing something wrong??

---

### Post by d4nnyb0y on 2010-11-01
okay never mind I got it working.
I just downloaded the moonlight folder from go-mono.com/moonlight.
Then extracted it to a location and just told opera to look there.
Seems to be working.
Any idea how long it will take for a Silverlight 4 clone to be made?

---

### Post by lovinglinux on 2010-11-02
> **d4nnyb0y said:**
> okay never mind I got it working.
I just downloaded the moonlight folder from go-mono.com/moonlight.
Then extracted it to a location and just told opera to look there.
Seems to be working.
Any idea how long it will take for a Silverlight 4 clone to be made?

I never had to do that, but I'm using Opera 11 alpha on a 32bit Ubuntu.

---

### Post by calande on 2011-08-17
Hi there. I installed the latest plugin but it seems to be v.3 while some web sites expect v.4 and refuse to work, i.e. [http://www.pluzz.fr/qatar-perle-d-avenir.html](http://www.pluzz.fr/qatar-perle-d-avenir.html) or here: [http://www.france5.fr/c-dans-l-air/index-fr.php?page=resume&id_article=7263](http://www.france5.fr/c-dans-l-air/index-fr.php?page=resume&id_article=7263)

---

### Post by lovinglinux on 2011-08-17
> **calande said:**
> Hi there. I installed the latest plugin but it seems to be v.3 while some web sites expect v.4 and refuse to work, i.e. [http://www.pluzz.fr/qatar-perle-d-avenir.html](http://www.pluzz.fr/qatar-perle-d-avenir.html) or here: [http://www.france5.fr/c-dans-l-air/index-fr.php?page=resume&id_article=7263](http://www.france5.fr/c-dans-l-air/index-fr.php?page=resume&id_article=7263)

Get Moonlight 4 preview at [http://www.go-mono.org/moonlight/download.aspx](http://www.go-mono.org/moonlight/download.aspx)

---

### Post by calande on 2011-08-17
Thanks, when I select "Nightlies", I get this page: [http://www.go-mono.org/moonlight/nightlies.aspx](http://www.go-mono.org/moonlight/nightlies.aspx) and there are no download links, it says "Your browser type could not be determined."

---

### Post by lovinglinux on 2011-08-18
> **calande said:**
> Thanks, when I select "Nightlies", I get this page: [http://www.go-mono.org/moonlight/nightlies.aspx](http://www.go-mono.org/moonlight/nightlies.aspx) and there are no download links, it says "Your browser type could not be determined."

Sorry, it seems to be available only for Firefox and Chrome.

---

### Post by calande on 2011-08-18
Yep...This Silverlight stuff stinks bad...It's yet another format alternative to Flash, and it's not even able to work with all browsers while the competition does...

---

### Post by matiasw on 2011-08-23
> **lovinglinux said:**
> Sorry, it seems to be available only for Firefox and Chrome.

The Firefox plugin works in Opera. Install:
```
sudo apt-get install moonlight-plugin-mozilla
```

Then go to [the plugins page]("opera:plugins#") and press Refresh. You should see a Silverlight Plug-in listed, for example mine was:
> 
Silverlight Plugin
Description: 3.0.40818.0
/usr/lib/mozilla/plugins/libmoonloader.soapplication/x-silverlight	Novell Moonlight	scr,xaml
application/x-silverlight-2		scr


---

### Post by calande on 2011-08-23
But the web site I visit requires Moonlight v.4 and it's not compatible with Firefox 6...

---

### Post by lovinglinux on 2011-08-24
> **calande said:**
> But the web site I visit requires Moonlight v.4 and it's not compatible with Firefox 6...

Have you tried it with compatibility check disabled?

---

### Post by jamesisin on 2011-08-26
> **lovinglinux said:**
> To test if it is working:

[http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html)

I installed the plugin via Synaptic as recommended, but this test did not work in Opera 11.50 (though it did in Ff).  I had to also enable JavaScript to get the animation to play.

---

### Post by Redsandro on 2012-01-04
Hmm, I feel bad for doubleposting, but this topic seems to be Opera related, just what I am looking for.

However, previous references to moonlight-plugin-mozilla are obsolete. For some reason the package was removed:

[http://www.ubuntuupdates.org/packages/show/345225](http://www.ubuntuupdates.org/packages/show/345225)
[https://launchpad.net/ubuntu/oneiric/amd64/moonlight-plugin-mozilla](https://launchpad.net/ubuntu/oneiric/amd64/moonlight-plugin-mozilla)

Why?

Similarly [these]("http://samiux.blogspot.com/2011/05/howto-moonlight-on-ubuntu-1104.html") outdated but widespread instructions no longer work, all moonlight related packages are removed:
```
E: Unable to locate package libmoon
E: Unable to locate package moonlight-plugin-mozilla
E: Unable to locate package moonlight-plugin-core
```

And finally, instructions to get moonlight from the official site do not work because [list=1][*]Recent Firefox is incompatible
[*]Nightly build url (just a thought) is not working at the moment
[*]Suggested Compatibility Reporter to circumvent #1 is also not working:
[img]http://ubuntuforums.org/attachment.php?attachmentid=210229&stc=1&d=1325658608[/img][/list]

What happened with this being easy? This used to be one of Novell's major tricks.

---

### Post by Redsandro on 2012-01-04
The accepted answer here is very useful:
[http://askubuntu.com/questions/80293/moonlight-extension-not-working-with-firefox-8](http://askubuntu.com/questions/80293/moonlight-extension-not-working-with-firefox-8)

It helps installing Moonlight with Firefox.

However, it is still quite impossible to link it to Opera. Plugin paths for Forefox are not accepted in the Opera configuration.

Also, noted interestingly from comments on that site:

> moonlight development has almost/has stopped. The developers have been laid off from Novell and the company that has taken over has stopped (for some unknown reason) the nightly builds. 

That's unfortunate. But I guess it's more clear now.

---

### Post by calande on 2012-01-04
> **Redsandro said:**
> However, it is still quite impossible to link it to Opera. Plugin paths for Forefox are not accepted in the Opera configuration.

We're in 2012, the Linux desktop has been around for more ten years now and there are still basic incompatibility headaches. Everyone programming on his end...Whatever explanations there might have, this drives me crazy...

---

