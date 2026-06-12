---
title: "Webpages slow to load on Lynx"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by weirdwisdom on 2011-06-19
I recently had a friend install Ubuntu Lynx on a laptop of mine, and everything seems to be working fine except for the fact that it loads webpages extremely slowly or not at all. I don't think it's my internet connection since it does detect my wi-fi, which works fine on my other computers. It also loads the home page decently fast, but it just seems to have trouble loading any webpage no matter what it is.

---

### Post by jerrrys on 2011-06-20
navigate to "users and groups" in your system menu and create a new user.  the new user FF will not have any addons and will let you see if thats a problem.

---

### Post by amjjawad on 2011-06-20
If the previous step did not work, you can install Chromium from Synaptic (or Terminal) and check whether you get the same issue or not?

---

### Post by weirdwisdom on 2011-06-21
I tried both and neither one seemed to help. I have noticed that it will bring up the homepage pretty quickly but after that it's very slow.

---

### Post by jerrrys on 2011-06-21
a suggestion:

your question may be better answered if you post here

[http://ubuntuforums.org/showthread.php?p=10965900#post10965900](http://ubuntuforums.org/showthread.php?p=10965900#post10965900)

---

### Post by weirdwisdom on 2011-06-22
Okay, I posted it there. Thanks

---

### Post by lovinglinux on 2011-07-20
Sorry to waste your time on the Firefox thread. Your issue is not Firefox related.

First, make sure you have Firefox 5 as your main Firefox version, installed via repositories. Remove those Firefox you have downloaded and installed manually. We are not going to need them.

Please post the results of the following commands:

```

time wget http://www.canonical.com/
time wget http://91.189.94.12
time wget www.webgapps.org
time wget http://209.190.61.25

```

Then visit [http://www.speedtest.net](http://www.speedtest.net) and post your speed results.

---

### Post by weirdwisdom on 2011-08-02
tiffany@tiffany-laptop:~$ time wget [http://www.canonical.com/](http://www.canonical.com/)
--2011-08-02 00:19:38--  [http://www.canonical.com/](http://www.canonical.com/)
Resolving [www.canonical.com](www.canonical.com)... 91.189.90.41
Connecting to [www.canonical.com|91.189.90.41|:80](www.canonical.com|91.189.90.41|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45797 (45K) [text/html]
Saving to: `index.html'

100%[======================================>] 45,797      99.6K/s   in 0.4s    

2011-08-02 00:19:39 (99.6 KB/s) - `index.html' saved [45797/45797]


real    0m1.102s
user    0m0.000s
sys    0m0.012s
tiffany@tiffany-laptop:~$ time wget [http://91.189.94.12](http://91.189.94.12)
--2011-08-02 00:19:39--  [http://91.189.94.12/](http://91.189.94.12/)
Connecting to 91.189.94.12:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.canonical.com/](http://www.canonical.com/) [following]
--2011-08-02 00:19:39--  [http://www.canonical.com/](http://www.canonical.com/)
Resolving [www.canonical.com](www.canonical.com)... 91.189.90.41
Connecting to [www.canonical.com|91.189.90.41|:80](www.canonical.com|91.189.90.41|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45797 (45K) [text/html]
Saving to: `index.html.1'

100%[======================================>] 45,797       100K/s   in 0.4s    

2011-08-02 00:19:41 (100 KB/s) - `index.html.1' saved [45797/45797]


real    0m2.743s
user    0m0.000s
sys    0m0.012s
tiffany@tiffany-laptop:~$ time wget [www.webgapps.org](www.webgapps.org)
--2011-08-02 00:19:41--  [http://www.webgapps.org/](http://www.webgapps.org/)
Resolving [www.webgapps.org](www.webgapps.org)... 209.190.61.215
Connecting to [www.webgapps.org|209.190.61.215|:80](www.webgapps.org|209.190.61.215|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.2'

    [  <=>                                  ] 27,792       127K/s   in 0.2s    

2011-08-02 00:19:42 (127 KB/s) - `index.html.2' saved [27792]


real    0m0.908s
user    0m0.004s
sys    0m0.004s
tiffany@tiffany-laptop:~$ time wget [http://209.190.61.25](http://209.190.61.25)

Ping=50ms
download speed=2.17 mbps
upload speed=.32 mbps

---

### Post by EkuquoL on 2011-08-02
[COLOR=Red][B]**Read theses directions COMPLETELY BEFORE CONTINUING**

[/B][/COLOR]You might need some drivers... Check for updates. You can find updates on Ubuntu's repository or your laptops manufacturer's hopepage.

{Especially if your monitor seems to create clipping frames when scrolling. That is a driver error.}

You can check out your systems variants loaded in Terminal Window.

Remember you are about to lose this screen -- **Press CTRL+ALT+F7 **to return to  this screen.

Go to your Terminal .. Press **CTRL+ALT+F2** .. login and 
type this command 

# sysctl -a

A list will form .. To scroll up the list , press "scroll lock" on your keyboard, then scroll up and find your hardwares information.

Becareful you can change many variables using that command and damage your system significantly if you are not aware of what you are doing .. Use it with caution.

[COLOR=Red]Remember press CTRL+ALT+F7 to return to this screen...[/COLOR]

---

### Post by lovinglinux on 2011-08-02
> **weirdwisdom said:**
> tiffany@tiffany-laptop:~$ time wget [http://www.canonical.com/](http://www.canonical.com/)
--2011-08-02 00:19:38--  [http://www.canonical.com/](http://www.canonical.com/)
Resolving [www.canonical.com](www.canonical.com)... 91.189.90.41
Connecting to [www.canonical.com|91.189.90.41|:80](www.canonical.com|91.189.90.41|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45797 (45K) [text/html]
Saving to: `index.html'

100%[======================================>] 45,797      99.6K/s   in 0.4s    

2011-08-02 00:19:39 (99.6 KB/s) - `index.html' saved [45797/45797]


real    0m1.102s
user    0m0.000s
sys    0m0.012s
tiffany@tiffany-laptop:~$ time wget [http://91.189.94.12](http://91.189.94.12)
--2011-08-02 00:19:39--  [http://91.189.94.12/](http://91.189.94.12/)
Connecting to 91.189.94.12:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://www.canonical.com/](http://www.canonical.com/) [following]
--2011-08-02 00:19:39--  [http://www.canonical.com/](http://www.canonical.com/)
Resolving [www.canonical.com](www.canonical.com)... 91.189.90.41
Connecting to [www.canonical.com|91.189.90.41|:80](www.canonical.com|91.189.90.41|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 45797 (45K) [text/html]
Saving to: `index.html.1'

100%[======================================>] 45,797       100K/s   in 0.4s    

2011-08-02 00:19:41 (100 KB/s) - `index.html.1' saved [45797/45797]


real    0m2.743s
user    0m0.000s
sys    0m0.012s
tiffany@tiffany-laptop:~$ time wget [www.webgapps.org](www.webgapps.org)
--2011-08-02 00:19:41--  [http://www.webgapps.org/](http://www.webgapps.org/)
Resolving [www.webgapps.org](www.webgapps.org)... 209.190.61.215
Connecting to [www.webgapps.org|209.190.61.215|:80](www.webgapps.org|209.190.61.215|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html.2'

    [  <=>                                  ] 27,792       127K/s   in 0.2s    

2011-08-02 00:19:42 (127 KB/s) - `index.html.2' saved [27792]


real    0m0.908s
user    0m0.004s
sys    0m0.004s
tiffany@tiffany-laptop:~$ time wget [http://209.190.61.25](http://209.190.61.25)

Ping=50ms
download speed=2.17 mbps
upload speed=.32 mbps

Doesn't look like you have a network problem. Try to disable ipv6 in Firefox:

[LIST]
[*]Type **about:config** in the address bar, press Enter.
[*]Find **network.dns.disableIPv6** in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]

---

### Post by weirdwisdom on 2011-08-03
> **lovinglinux said:**
> Doesn't look like you have a network problem. Try to disable ipv6 in Firefox:

[LIST]
[*]Type **about:config** in the address bar, press Enter.
[*]Find **network.dns.disableIPv6** in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
 
 
Alright so I did all that, and it set it to "false", and it made it no faster than it on before when it was set to "true".

---

### Post by lovinglinux on 2011-08-04
> **weirdwisdom said:**
> Alright so I did all that, and it set it to "false", and it made it no faster than it on before when it was set to "true".

Are you using a Proxy? Check Firefox network settings.

Also, install [Extended Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/extended-statusbar/") add-on, restart, then access the following addresses, annotate the time it takes to complete the page loading and post here.

[http:///www.canonical.com](http:///www.canonical.com)
[http://91.189.94.12](http://91.189.94.12)
[http://www.webgapps.org](http://www.webgapps.org)
[http://209.190.61.25](http://209.190.61.25)

---

### Post by weirdwisdom on 2011-08-06
> **lovinglinux said:**
> Are you using a Proxy? Check Firefox network settings.
 
Also, install [Extended Statusbar]("https://addons.mozilla.org/en-US/firefox/addon/extended-statusbar/") add-on, restart, then access the following addresses, annotate the time it takes to complete the page loading and post here.
 
[http:///www.canonical.com](http:///www.canonical.com)
[http://91.189.94.12](http://91.189.94.12)
[http://www.webgapps.org](http://www.webgapps.org)
[http://209.190.61.25](http://209.190.61.25)
 
 
It's set on "use system proxy settings". 
 
I downloaded the add-on but it didn't seem to show up.
 
The first two pages wouldn't load, and the other two loaded pretty fast.

---

### Post by lovinglinux on 2011-08-06
> **weirdwisdom said:**
> It's set on "use system proxy settings". 
 
I downloaded the add-on but it didn't seem to show up.
 
The first two pages wouldn't load, and the other two loaded pretty fast.

I have no idea what's going on. You don't seem to have a network problem, not even a DNS issue.

---

### Post by weirdwisdom on 2011-08-07
Okay, well thanks for trying to help me. Do you know where I can go to get help?

---

### Post by lovinglinux on 2011-08-07
> **weirdwisdom said:**
> Okay, well thanks for trying to help me. Do you know where I can go to get help?

I suppose you still have the Ubuntu Live CD. Instead of booting from your hard drive, try booting into a Live CD and test if you experience the same problems.

Also, try to connect to a different router to see if the problem can be replicated on another network.

---

