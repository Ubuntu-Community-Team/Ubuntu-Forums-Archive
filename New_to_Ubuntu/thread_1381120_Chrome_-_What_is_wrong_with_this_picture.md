---
title: "Chrome - What is wrong with this picture?"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by dmillerct on 2010-01-14
There is a subtle hint in the attachment.

Is there a way to change this?

---

### Post by tom.swartz07 on 2010-01-14
> **dmillerct said:**
> There is a subtle hint in the attachment.

Is there a way to change this?

I think you have to change the icons located in /opt/google/chrome

Those are the icons that chrome uses in the window hint.


Just make sure you have the same filename, and youre set.

---

### Post by mk1w86 on 2010-01-14
I am not sure how to change the icon but have you installed Google's build of Chrome or Chromium? :-k

---

### Post by doas777 on 2010-01-14
so you object to the use of red, yellow, blue, and green?

in the end, that is googles logo, and you are not allowed to change it, but with many OSS browsers, you can compile it without the corporate branding. never been worth the effort to me. iirc, if you compile FF without branding it comes out as "Ice Weasel". 

it may just be an icon, in which case, find the icon file, remane it somthing else, and replace it with an icon that you like (by reanming it to the previous name). it MAY work.

---

### Post by dmillerct on 2010-01-14
> **doas777 said:**
> so you object to the use of red, yellow, blue, and green?

in the end, that is googles logo, and you are not allowed to change it, but with many OSS browsers, you can compile it without the corporate branding. never been worth the effort to me. iirc, if you compile FF without branding it comes out as "Ice Weasel". 

it may just be an icon, in which case, find the icon file, remane it somthing else, and replace it with an icon that you like (by reanming it to the previous name). it MAY work.

Object is a strong word. It just clashes, badly. If this is an open source browser I don't think google would mind if I just change the color scheme of the icon. After all its not as if I am changing it to a big blue E. ;)

---

### Post by Kimm on 2010-01-14
I'm pretty sure you can change it anyway you like, as long as you don't distribute it :P

---

### Post by Merk42 on 2010-01-14
> **dmillerct said:**
> Object is a strong word. It just clashes, badly. If this is an open source browser I don't think google would mind if I just change the color scheme of the icon. After all its not as if I am changing it to a big blue E. ;)

You could use the same logic with Firefox's icon and, if it's still called "Firefox", they very much do mind that.

---

### Post by sailthesea on 2010-01-14
I agree It would be much nicer monochrome in that theme.....Which is it by the way??;)

---

### Post by tom.swartz07 on 2010-01-14
> **sailthesea said:**
> I agree It would be much nicer monochrome in that theme.....Which is it by the way??;)

its definitely the official chrome build. 
Like I said, you could change the icons by editing the pictures in /opt/google/chrome

theres 4 images, just replace them with the color-shifted ones you want.



If it were chromium, the icon would be blue and silver.

---

### Post by dmillerct on 2010-01-14
> **sailthesea said:**
> I agree It would be much nicer monochrome in that theme.....Which is it by the way??;)

It is a mix of Slickness Black and XNtriCity.

Well i replaced the icons except for one it is a .xpm file not sure exactly what this extension is about. Is there proper way to modify it or can I just save the monochrome icon file I am using as .xpm and be done with it?

---

### Post by Kimm on 2010-01-14
Btw... why dont you just run chromium instead? Its pretty much the same thing as Chrome, only a bit more cutting edge.

Easily installed and updated from the chromium-daily PPA too: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Also, this is how the chromium icon looks (pretty much the same, only different colors): [http://commons.wikimedia.org/wiki/File:Chromium_Icon.png](http://commons.wikimedia.org/wiki/File:Chromium_Icon.png)

---

### Post by sailthesea on 2010-01-14
[HTML][PHP]It is a mix of Slickness Black and XNtriCity.[/PHP][/HTML]

Thanks will try that out sometime!;)

---

### Post by dmillerct on 2010-01-14
> **Kimm said:**
> Btw... why dont you just run chromium instead? Its pretty much the same thing as Chrome, only a bit more cutting edge.

Easily installed and updated from the chromium-daily PPA too: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Also, this is how the chromium icon looks (pretty much the same, only different colors): [http://commons.wikimedia.org/wiki/File:Chromium_Icon.png](http://commons.wikimedia.org/wiki/File:Chromium_Icon.png)

An interesting solution to the problem, What is the major difference between the two browsers? 

I just started using Chrome a few weeks ago due to an issue I was having with FF opening PDF files.

---

### Post by Dougie187 on 2010-01-14
Chrome is the google branded snapshot of chromium.

Chromium is the open sourced browser that is what becomes chrome, just without google's branding.

If you use the daily build ppa, chromium is updated every day. If you install chrome, it's only updated whenever google says it is.

---

### Post by tom.swartz07 on 2010-01-14
> **dmillerct said:**
> It is a mix of Slickness Black and XNtriCity.

Well i replaced the icons except for one it is a .xpm file not sure exactly what this extension is about. Is there proper way to modify it or can I just save the monochrome icon file I am using as .xpm and be done with it?

If im not mistaken, thats a vector file. you could open your icon in gimp, and save it as an .xpm file then.

That should clear it up.


The difference between chrome and chromium is not much. chromium updates just a bit more often, but they pretty much stay at the same pace.

ones just fully open source (chromium) and ones not (chrome).

---

### Post by dmillerct on 2010-01-14
> **tom.swartz07 said:**
> If im not mistaken, thats a vector file. you could open your icon in gimp, and save it as an .xpm file then.

That should clear it up.


The difference between chrome and chromium is not much. chromium updates just a bit more often, but they pretty much stay at the same pace.

ones just fully open source (chromium) and ones not (chrome).

Well then given the choice chromium here I come! Why even bother with chrome then? additional stability?

---

### Post by cascade9 on 2010-01-14
Ironic, having 'internet survival guide for traveling where privacy isn't respected'  and running chrome.

---

### Post by dmillerct on 2010-01-14
> **cascade9 said:**
> Ironic, having 'internet survival guide for traveling where privacy isn't respected'  and running chrome.

I guess it is. :D

That is just a lifehacker rss feed output to conky. They are hit an miss with there articles but every once in a while there is a real gem. 

I don't mean to derail my own thread here but I am getting an error when trying to add the chromium ppa key:

```
$ sudo add-apt-repository ppa:chromium-daily/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

---

### Post by dmillerct on 2010-01-14
I was able to install it without the key however I believe I will still need to add this key for future updates.

Does anyone have an idea why it would not be available? see previous post.

---

### Post by tom.swartz07 on 2010-01-14
> **dmillerct said:**
> I was able to install it without the key however I believe I will still need to add this key for future updates.

Does anyone have an idea why it would not be available? see previous post.

check and see. sometimes if you install with a .deb it automatically adds the repo

---

### Post by baddog144 on 2010-01-14
> **dmillerct said:**
> Well then given the choice chromium here I come! Why even bother with chrome then? additional stability?

[http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome]("http://code.google.com/p/chromium/wiki/ChromiumBrowserVsGoogleChrome") 
Sums it up nicely. And the answer is that there is very little difference between the two. :P

---

### Post by running_rabbit07 on 2010-01-14
Looks like a mini webcam. They're always watching.

---

### Post by running_rabbit07 on 2010-01-14
> **tom.swartz07 said:**
> check and see. sometimes if you install with a .deb it automatically adds the repo

I installed it two days ago and it did input the source and key for updates on its own.

---

### Post by dmillerct on 2010-01-14
Thanks guys I will mark this as solved. If I continue to have any key issues I will start a new thread as it is a bit off topic at this point.

Hvala!

---

