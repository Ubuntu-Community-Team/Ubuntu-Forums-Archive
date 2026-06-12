---
title: "Dual Boot Wireless?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Touch.Code on 2007-02-18
Hey,

This is a spererate question. If I have XP and 6.10 will my wireless be shared?

Thanks

---

### Post by mikewhatever on 2007-02-18
If you dual boot XP and 6.10, and your wireless card works with both, then yes, you should be able to use the same router to connect. Hope I got your question right :)

---

### Post by Touch.Code on 2007-02-18
So I have my wireless card with XP and its install. I dual boot with Linux and it will still work?

---

### Post by spottedhog on 2007-02-18
In most cases I am sure this would work.  I recently bought a new Gateway laptop which came with XP installed, and I put in Kubuntu and it recognized the wireless card with no effort.

---

### Post by Touch.Code on 2007-02-19
Thanks! Will it work on the LiveCD?

---

### Post by mikewhatever on 2007-02-19
Yes, if the wireless card is detected and supported, then it will work with the Live CD.

---

### Post by Touch.Code on 2007-02-19
Damn, I just put in the live CD but it wont allow Internet? What settings do I need to use?

---

### Post by jml on 2007-02-19
A little more detail would be helpful.  What is the brand of computer that you are using, and what type of wireless chip set does your wireless card use, (Intel, Broadcom, Atheros, etc)

Joe

---

### Post by mikewhatever on 2007-02-19
System->Administration->Networking. If the wireless card is detected, you should have wireless there. Click Properties and enter your network name.

---

### Post by Touch.Code on 2007-02-19
Right. I have a Netgear WG311 PCI card, which I brought yesterday. I have a dual boot with Windows XP and 6.10. It works with XP but not 6.10.

Need more info?

[b]Edit: When I do what Mike said, I get, "Wired Connection" and "Telephone". I do:
```

lspci

```

And it says Wireless Rev 03.

My computer is home built :P
[/b]

---

### Post by mikewhatever on 2007-02-19
I've just done a search on Netgear WG311 PCI
[http://ubuntuforums.org/search.php?searchid=14862645](http://ubuntuforums.org/search.php?searchid=14862645)
and it appears, that card needs ndisrapper, which is software to enable the use of Windows driver for that card. In other words, your card does not seem to have a linux driver, therefore, not supported out of the box, and you can't get it working from the live CD. You may want to go over some of the posts in the search to verify all that. The good news it that people report to have been able to get it working. You'll need to install Edgy to try to solve it. Here is the page on ndisrapper and wireless
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#wireless)

---

### Post by chili555 on 2007-02-19
> 
Code:

lspci

And it says Wireless Rev 03.

My computer is home built :P

Is this a test? Are you trying to see who can help you by giving them no useful information? How's that workin' for ya?

We all know lspci gives a lot more information than that, information that might just help us help you! But you won't share it!

As for computers being home built ( :P ), half the guys and gals in here built their frankenputers themselves. But, unless you started with a resistor and a soldering iron, you used commercially available parts that kick out information in response to lspci. 

We'd love to help you, but we need information to work with.

PS - Sorry for the rant.

---

