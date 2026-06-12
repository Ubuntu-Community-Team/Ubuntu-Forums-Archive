---
title: "internet explorer"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by ryon341 on 2009-11-08
I need to use internet explorer for a couple ie-only websites.  Can anyone give me some direction?  I dowloaded ies4linux-2.99.0.tar.gz.  I have no idea if this is the correct file.  I just installed ubuntu 9.1.    

Thanks,

---

### Post by MelDJ on 2009-11-08
try IE under wine? [http://www.winehq.org/](http://www.winehq.org/)

do you mean you want to go to websites which use silverlight? then use moonlight for firefox and you will be able to view them. [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

---

### Post by ryon341 on 2009-11-08
I don't know what silverlight is.  I am only interested in accessing a few sites that require IE.   My company's website is setup for IE only.  I'll try the WINE link you sent.  Thanks.

---

### Post by Hetepeperfan on 2009-11-08
Hi,

If you want to install Windows programs. You need to get Wine. This program lets windows programs think they are running under windows while they are not.

See [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by MelDJ on 2009-11-08
> **ryon341 said:**
> I don't know what silverlight is.  I am only interested in accessing a few sites that require IE.   My company's website is setup for IE only.  I'll try the WINE link you sent.  Thanks.

see: [http://silverlight.net/](http://silverlight.net/)

---

### Post by hankinator on 2009-11-08
Also here is a link for IE8

[http://www.microsoft.com/windows/internet-explorer/worldwide-sites.aspx](http://www.microsoft.com/windows/internet-explorer/worldwide-sites.aspx)

---

### Post by SlickRick on 2009-11-08
there are two workarounds i know of for entering IE only sites. Either get the [user agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") add-on for firefox and set it to trick the website into thinking that you're using IE or download the [noscript]("https://addons.mozilla.org/en-US/firefox/addon/722") addon for firefox which will hopefully block the script that checks for your browser and you would be taken straight to the site.
Both of these will only allow you to go on the website, but this doesn't mean that the features intended for IE will work. If there are IE-specific features on the site then I agree with running IE under wine like some above posts suggested.

---

### Post by ryon341 on 2009-11-08
I loaded Wine from the Software Center. It appeared to load correctly.  I downloaded the IE8 from the link given by Hankinator.   When I right-click the link and choose "open with Wine Windows Program Loader", I receive the response:

Unable to find a volume for program extraction.  Please verify that you have proper permissions.

What am I missing?

---

### Post by Bruce H on 2009-11-08
I can't help with Wine, as I don't currently use it. For my own IE development projects, I simply run Windows in a virtual machine. I'm currently using VirtualBox OSE, available in Synaptic. It does the job, but it does require you to have a copy of Windows to install.

---

### Post by BeatnikBandit on 2009-11-08
I always use Wine in a last resort. I would try some of the workarounds as if the site wont let you in because you are using Firefox then do as stated above to make the server think it is IE. Now if that lets you in and everything works Great. Now if their is something on the page that doesn't work I would look into weather or not it is using silver light and if so that has been covered above. I think you can get into it with some tinkering.

If you cant you have 3 options, use wine, install windows as a virtual machine, or if you use windows for something (games?) you can dual boot but installing windows as a virtual machine or even a dual boot IMO is overkill for what you want to do. I sadly have not ever had a problem like yours so IMO i would try to find a way to get in using Firefox. although that's an opinion as how to do it has already been posted.

If for some reason you like something about UE Ubuntu add the repository and install whatever you want without getting things you dont want, IDK what comes with UE but i bet you wont use them ALL (even if its one application still you will need to remove it or deal with extra apps) 

But this is all just my two pieces of gold

---

