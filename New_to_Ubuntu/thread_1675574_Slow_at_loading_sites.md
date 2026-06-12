---
title: "Slow at loading sites"
date: 2011-01-25
forum: New to Ubuntu
---

### Post by stroyeror on 2011-01-25
OK so everything has been working fine on ubuntu 10.04,  but about a week ago  internet pages started to become slow at loading.  After the site loads and i start navigating the site it runs at normal speed.  If i go to a new site it takes long time load as well once it loads it runs fine.  Any one have any idea whats going on here?  Also i have tried windows machines and they run fine.  I have tried resetting the router still does the same thing.  I have also tried the hard line still loads slow.

---

### Post by ivanovnegro on 2011-01-25
Are you using Firefox? I am, and sometimes when I want to open sites with Flash content it slows the browser down.

---

### Post by stroyeror on 2011-01-25
yes using firefox,  The sites iam going too do not have flash content.  Even Google takes a while to load.

---

### Post by ivanovnegro on 2011-01-25
But your system is working flawless?
Have you got open many tabs?

---

### Post by cariboo on 2011-01-25
You can use a command line utility called mtr, to check if there are any problems between you and the website you are connecting to.:

```
mtr ubuntuforums.org
```

mtr is installed by default.

---

### Post by stroyeror on 2011-01-25
> **ivanovnegro said:**
> But your system is working flawless?
Have you got open many tabs?


Yes other than that system is running great,  I can have one tab open and it still does it.

---

### Post by stroyeror on 2011-01-25
> **cariboo907 said:**
> You can use a command line utility called mtr, to check if there are any problems between you and the website you are connecting to.:

```
mtr ubuntuforums.org
```mtr is installed by default.


0% loss

---

### Post by stroyeror on 2011-01-26
Any ideas?

---

### Post by ivanovnegro on 2011-01-27
Have you tried the commmand in the terminal?
Open the terminal and copy the command into it and post the results here.

---

### Post by stroyeror on 2011-01-27
See screen-shot.(attachment)

---

### Post by stroyeror on 2011-01-27
Ok i have reloaded Ubuntu and it is still slow at loading web-pages.

---

### Post by stroyeror on 2011-01-29
Ok i have used live cd fro mother distros and i still have the same issue,  Does any one have any ideas?

---

### Post by ivanovnegro on 2011-01-29
Really, Im not sure what could be the problem.
What are your hardware specs?
Do you run Maverick 10.10?

---

### Post by cgroza on 2011-01-29
Try disabling IPv6. I saw problems around the forum that found their solution like this.

---

### Post by stroyeror on 2011-01-29
> **ivanovnegro said:**
> Really, Im not sure what could be the problem.
What are your hardware specs?
Do you run Maverick 10.10?


no i run 10.04 but it does the same thing in other distros

---

### Post by stroyeror on 2011-01-29
> **cgroza said:**
> Try disabling IPv6. I saw problems around the forum that found their solution like this.


I Have done this:

> Ran into an issue on Ubuntu the other day in which network functions  were having issues. Through a little PD found that IPV6 was the culprit.  Here is a tip on how to disable IPV6 on Ubuntu 10.04.
 To check if IPv6 is disabled, run the following command:
 cat /proc/sys/net/ipv6/conf/all/disable_ipv6
 0 means it&#8217;s enabled and 1 &#8211; disabled.
 To disable IPv6, you have to add the following lines to /etc/sysctl.conf:
 #disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1[FONT=monospace]&

[/FONT]> Disable IPv6 in Firefox. Type about:config and search for:[INDENT]network.dns.disableIPv6
[/INDENT]and set it to TRUE


Still does not work Any ideas?

---

### Post by irv on 2011-01-29
Something to try:
If you have a friend with a laptop have them connect to your Internet and see if they have any problem.
The reason I say this, is I have a fast Internet, but there are time when it takes a long time to load a page, and I found out at times I have heavy traffic (peak times), things slow down.
This might not be the same case with your problem but I thought I would just mention it.

---

### Post by ivanovnegro on 2011-01-29
Maybe you could reset you router, I mean make it off and then again on to test this. Sometimes I have this issue when the router was nonstop on, I reset it and the internet is again faster or at normal speed.

---

