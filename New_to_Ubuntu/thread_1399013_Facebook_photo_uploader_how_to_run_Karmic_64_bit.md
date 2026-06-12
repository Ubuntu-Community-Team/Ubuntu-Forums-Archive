---
title: "Facebook photo uploader: how to run? Karmic 64 bit"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by The Bright Side on 2010-02-05
Hey guys,

probably a very easy question to answer, but I've been searching in the forums and couldn't find a solution to my problem. See, I'm trying to upload photos to my facebook, and I'm getting the following message:

"Want a better photo uploading experience?

You are using a simplified version of the Facebook photo uploader. A better experience is available, but not for your browser. You can use Firefox, Safari, or Internet Explorer to enjoy the full version."

Well I'm using Firefox 3.5.7 on Ubuntu 9.10, 64 bit. What's missing? I read there was a plugin somewhere that fixes it. Hope you guys can help me out!

---

### Post by tom.swartz07 on 2010-02-05
> **The Bright Side said:**
> Hey guys,

probably a very easy question to answer, but I've been searching in the forums and couldn't find a solution to my problem. See, I'm trying to upload photos to my facebook, and I'm getting the following message:

"Want a better photo uploading experience?

You are using a simplified version of the Facebook photo uploader. A better experience is available, but not for your browser. You can use Firefox, Safari, or Internet Explorer to enjoy the full version."

Well I'm using Firefox 3.5.7 on Ubuntu 9.10, 64 bit. What's missing? I read there was a plugin somewhere that fixes it. Hope you guys can help me out!

No biggie, you probably just dont have the right version of Java installed.

Follow the guide here: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

That will show you how to download the official x64 version of Java and then install it. After that, just close and restart your browser, and youre all set!


Let me know how it pans out

---

### Post by The Bright Side on 2010-02-06
Well the good thing is, I realized I really didn't have any version of Java installed (funny, I thought I'd installed it at some point or it came with the restricted extras or something).

So now I have it properly installed (the little checking tool on the Java site confirms it), but the photo uploader still gives me the very same message :-(

Any more ideas?
Thanks!

---

### Post by tom.swartz07 on 2010-02-06
> **The Bright Side said:**
> Well the good thing is, I realized I really didn't have any version of Java installed (funny, I thought I'd installed it at some point or it came with the restricted extras or something).

So now I have it properly installed (the little checking tool on the Java site confirms it), but the photo uploader still gives me the very same message :-(

Any more ideas?
Thanks!

No biggie- verify that your browser found it.

In the address bar, type ```
about:plugins
```
and see if Java is listed. Also, take a peek and see if you have gnash or swfdec listed there too under Flash

---

### Post by nhasian on 2010-02-06
it is possible to have multiple versions of java installed and its not using the correct one.  you should look here:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Basically you want to do:

```
sudo apt-get install sun-java6-bin
```

then

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by The Bright Side on 2010-02-06
Yeah I tried about:plugins and it gave me the expected feedback, I also installed Java again from the repos after installing the BIN from the Java web page. However, I haven't given

sudo update-java-alternatives -s java-6-sun

a try yet. I'll do that when I get back from work tonight :-)

Thanks!
M.

---

### Post by hyperdude111 on 2010-02-06
Also try sudo apt-get install ubuntu-restricted-extras for the other plugins as well.

---

### Post by The Bright Side on 2010-02-07
No... Still nothing. Whatever I do, it won't run...
Thanks for all your suggestions though!

tom.swartz07, I don't have gnash or swfdec - what makes them different from Adobe Flash?

I remember I used to have all three installed back when I had 8.10, my first Ubuntu: Firefox also had an option back then that let me choose which one to use for Flash. Now, after I install one Flash plugin, I no longer have any option to get the other ones as well, and also, that functionality that lets me choose a plugin seems to be gone.

---

### Post by nhasian on 2010-02-07
adobe flash is proprietary software from adobe and works best for flash websites.  swfdec and gnash are open source alternatives but dont support all the features and are still in development.

> **The Bright Side said:**
> 
tom.swartz07, I don't have gnash or swfdec - what makes them different from Adobe Flash?

---

### Post by eladamri on 2010-02-08
> **The Bright Side said:**
> Hey guys,

probably a very easy question to answer, but I've been searching in the forums and couldn't find a solution to my problem. See, I'm trying to upload photos to my facebook, and I'm getting the following message:

"Want a better photo uploading experience?

You are using a simplified version of the Facebook photo uploader. A better experience is available, but not for your browser. You can use Firefox, Safari, or Internet Explorer to enjoy the full version."

Well I'm using Firefox 3.5.7 on Ubuntu 9.10, 64 bit. What's missing? I read there was a plugin somewhere that fixes it. Hope you guys can help me out!

I am having the same problem. I do not believe it is a problem with Java but a user-agent problem (possibly on Facebook's side) that the browser type is not being correctly identified.
I installed the plug-in [user-agent switcher]("https://addons.mozilla.org/en-US/firefox/addon/59") and selected IE8 for Windows and no longer got the error . . . however it still did not work. It just tried to load Java forever which could be a problem with my computer or Facebook. Importantly, it at least tried to load it instead of saying I was using the wrong browser when I wasn't.

---

### Post by axelswe on 2010-02-09
Bump.
 I also figure this could have something to do with facebook. Can't get it to work neither

---

### Post by axelswe on 2010-02-10
I found a fix/workaround

> **eladamri said:**
> I am having the same problem. I do not believe it is a problem with Java but a user-agent problem....

I used eladamris idea to change the user agent.
[B]
THE FIX[/B]:
in the adressbar in firefox write: 
```
about:config
```It will warn you not to screw around with the settings there in. ignore the warning =) and continue
In the **Filter** field write:
```
user
``` This should narrow down your alternatives. Find the row that says:
**general.useragent.extra.firefox**
Rightclick it and choose "modify". Change the value from "Firefox/3.5.7" (in my case) to "Firefox/3.6.0" restart or reload Firefox and it should work!

---

