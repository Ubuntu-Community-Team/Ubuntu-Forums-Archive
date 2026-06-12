---
title: "What could be causing my browser to crash?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Michael Kaiser on 2010-02-09
Forgive me if this has been answered in another thread. I did search pretty extensively.


Both of my browsers - Chrome and Firefox (both seem to be the newest versions) completely close-out several times a day. They just flat-out disappear, and I have to re-launch. What should I check in order to find out what the problem is?

I prefer Chrome, but it crashes more often than Firefox. In fact, it just crashed twice while writing this post!

---

### Post by nhasian on 2010-02-09
i've never had any issues with either of those browsers crashing but i recommend that you launch them from a terminal.  that way if it does crash you can read the output message and get an idea of what happened.

---

### Post by Michael Kaiser on 2010-02-09
> **nhasian said:**
> i've never had any issues with either of those browsers crashing but i recommend that you launch them from a terminal.  that way if it does crash you can read the output message and get an idea of what happened.

Thanks for the suggestion! Still being an Ubuntu begginer - what is the command prompt?

---

### Post by sharrah on 2010-02-09
I'm willing to bet it has something to do with flash.

---

### Post by Michael Kaiser on 2010-02-09
> **sharrah said:**
> I'm willing to bet it has something to do with flash.

Would you recommend disabling Shockwave?

---

### Post by philinux on 2010-02-09
> **Michael Kaiser said:**
> Would you recommend disabling Shockwave?

I've not had any crashes with FF. 

Most likely cause is one of your addons. Try disabling them one by one.

Or run FF in safe mode.

```
firefox -safe-mode
```

---

### Post by x C0MMAND0 x on 2010-02-09
> **Michael Kaiser said:**
> Thanks for the suggestion! Still being an Ubuntu begginer - what is the command prompt?

Command Prompt = Terminal

Go to Applications > Accessories > Terminal. Then type in

```
google-chrome
``` and hit enter for Chrome and

```
firefox
``` and hit enter for Firefox browser.  Once it crashes, output information from the terminal here.

---

### Post by Michael Kaiser on 2010-02-09
> **x C0MMAND0 x said:**
> Command Prompt = Terminal

Go to Applications > Accessories > Terminal. Then type in

```
google-chrome
``` and hit enter for Chrome and

```
firefox
``` and hit enter for Firefox browser.  Once it crashes, output information from the terminal here.

Great. Thanks!

I did know that you meant the terminal. I didn't know what to type there Haha! Sorry 'bout that.

---

### Post by Michael Kaiser on 2010-02-09
> **philinux said:**
> I've not had any crashes with FF. 

Most likely cause is one of your addons. Try disabling them one by one.

Or run FF in safe mode.

```
firefox -safe-mode
```

Thank you! I've definitely got something duking it out with something else here.

---

### Post by nhasian on 2010-02-09
hopefully your not running swfdec or gnash.  for the best user experience you should only have adobe flash installed.  you can check in firefox by entering in the Firefox URL:

```
about:plugins
```

also you need to know wether your Ubuntu is 32 or 64 bit so you can install the correct adobe flash.  if your not sure you can find out from a command prompt with:

```
uname -a
```

> **Michael Kaiser said:**
> Would you recommend disabling Shockwave?

---

### Post by crienoloog on 2010-02-15
Just recently I found that Chrome crashes when in my webpage I try to edit something with the help of TinyMCE in my content management system.
I use Ubuntu 9.10 64-bit with Chrome 5.0.307.7 beta. If I edit in TinyMCE and hit carriage-return or back arrow, the page crashes. 
I turned of all extensions in Chrome, uninstalled Flash [doesn't work good anyway]. Could it be something to do with the IcedTea Java plugin? It was OK a few days back and I had a regular Ubuntu update recently when the problems occurred.

---

### Post by Soul-Sing on 2010-02-15
> **Michael Kaiser said:**
> Forgive me if this has been answered in another thread. I did search pretty extensively.


Both of my browsers - Chrome and Firefox (both seem to be the newest versions) completely close-out several times a day. They just flat-out disappear, and I have to re-launch. What should I check in order to find out what the problem is?

I prefer Chrome, but it crashes more often than Firefox. In fact, it just crashed twice while writing this post!

This behaviour didn't occur after installing additional sofware/plugins/addons like java, flash, etc.?

---

