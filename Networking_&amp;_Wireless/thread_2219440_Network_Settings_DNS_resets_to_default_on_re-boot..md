---
title: "Network Settings DNS resets to default on re-boot."
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by alec8 on 2014-04-24
Hello, I am new to Linux so please be gentle :)

I'm having a weird problem with my Internet / WiFi / DNS Settings, long story but the short of it is this.

First I'm running LinuxMint 16 Petra 32bit on a fresh install.

When I go to Menu > Admin > Network 

It pops up a box 'Network Settings', upon clicking the DNS tab, in there the setting is 127.0.1.1

The problem for me is some websites refuse to load, FB, Youtube, eBay and some random others I can't remember either do not load at all (Chrome just says Unable to connect to internet), or the page loads without any CSS making it un-usable. Weird right?

However, if I change the DNS settings in Network settings to 192.168.0.1 & 11.2.79.1 & 11.1.1.1 everything works as it should, I got those DNS settings from my routers setup page. I'm on a Static IP with my provider.

I've tried to load the script that I should follow to post back to you guys to help out but it's not working, here is what I get...

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-04-24 11:21:06--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 184.73.222.75
Connecting to dl.dropbox.com (dl.dropbox.com)|184.73.222.75|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-04-24 11:21:06--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... failed: Connection timed out.
wget: unable to resolve host address ‘dl.dropboxusercontent.com’



```

The problem for me is when I re-boot my machine, the DNS Settings I've entered in to the Network Settings DNS tab box revert to 127.0.1.1 and then I get the problems with the pages loading again or not at all, so I have to re-enter my DNS settings every time, quite a pain at the moment.

The other thing to query is I have to enter my password to change these settings, and the padlock says 'Click to prevent changes', yet something is making changes, so this can not be good.

I've spent quite a bit of time on this, I tried posting my problem in LinuxMint forums but they go unanswered, for the record, the links below show those posts.

[http://forums.linuxmint.com/viewtopic.php?f=47&t=145696](http://forums.linuxmint.com/viewtopic.php?f=47&t=145696)
Post about FB & other websites not loading correctly...

[http://forums.linuxmint.com/viewtopic.php?f=53&t=164132](http://forums.linuxmint.com/viewtopic.php?f=53&t=164132)
Post about not being able to connect to any other WiFi

[http://forums.linuxmint.com/viewtopic.php?f=157&t=165341](http://forums.linuxmint.com/viewtopic.php?f=157&t=165341)
Post about Network Settings DNS re-setting itself.

Any help on this or these matters would be most welcome.

Thank you for your time

:)

---

