---
title: "How do I block a webpage in Firefox?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by jburrell on 2009-04-18
All,
I've got this webpage that opens automatically and I'm trying to block it so it can't open at all.  The http is:  [http://antimalware-scannerv2.com/1/?id=2006-60&back=%3DzQ10jDwMQQNMI%3DN](http://antimalware-scannerv2.com/1/?id=2006-60&back=%3DzQ10jDwMQQNMI%3DN)

How do I block this address from opening?  I've been in the preferences of Firefox but I can't figure out how to stop this from happening.

Thanks,
J.

---

### Post by gandaran on 2009-04-18
just clear firefox cache, should be enough.

---

### Post by jburrell on 2009-04-18
I did that but it keeps opening by itself.  I'll be on a website and the URL I listed above will automatically open and hijack the browswer...

---

### Post by ddrichardson on 2009-04-18
You can create an iptables rule to reject that address:```

sudo /sbin/iptables -A OUTPUT -d antimalware-scannerv2.com -j REJECT
```Should do it.
I'd disable all your extensions too, find out what's redirecting.

---

### Post by gandaran on 2009-04-18
> **jburrell said:**
> I did that but it keeps opening by itself.  I'll be on a website and the URL I listed above will automatically open and hijack the browswer...
are you using a windows firefox or linux firefox? that page is full of virus but it will only affect a windows firefox not linux!

---

### Post by jburrell on 2009-04-18
I'm running Ubuntu 8.10 and running Firefox inside of that so it should be Linux, right?

---

### Post by gandaran on 2009-04-18
> **jburrell said:**
> I'm running Ubuntu 8.10 and running Firefox inside of that so it should be Linux, right?
did you clear all private data including cookies?

---

### Post by abn91c on 2009-04-18
> **gandaran said:**
> did you clear all private data including cookies?
+1 get rid of the cookies

---

### Post by CatKiller on 2009-04-18
If there's any site that you don't ever want to visit (ad servers are a good choice) there's a simple trick to make them never appear again. Basically, you just tell your computer that that address actually resolves to your computer, so no request ever goes out. The file you need to edit is /etc/hosts, which you can do with

```
sudo nano /etc/hosts
```and put in a line to redirect that server to your local IP address. In this case, that line would be

```
127.0.0.1 antimalware-scannerv2.com
```

This will work for all browsers.

---

### Post by jburrell on 2009-04-18
I cut and pasted that command in the terminal and pressed enter.  Is it supposed to notify me that the change took effect in the terminal?

---

### Post by jburrell on 2009-04-18
Yes, cookies and private data have been cleared.

---

### Post by KIAaze on 2009-04-18
> **jburrell said:**
> I cut and pasted that command in the terminal and pressed enter.  Is it supposed to notify me that the change took effect in the terminal?

I think you misunderstood something. ^^

The first "code" he gave you is a command to open the file "/etc/hosts" in the editor "nano" as root:
```
sudo nano /etc/hosts
```

The second code is actually just the text you're supposed to type into the file opened previously:
```
127.0.0.1 antimalware-scannerv2.com
```

Use "ctrl+O" to save the file and "ctrl+X" to exit the editor. ("^" stands for "ctrl" in the help at the bottom of the editor)

If you really want to run just one command instead, you can use:
```
echo "127.0.0.1 antimalware-scannerv2.com" >> /etc/hosts
```

This is a really nice trick CatKiller gave you there. 8)

P.S: For safe surfing without any unwanted popups, flash ads, etc, use NoScript and eventually flashblock.
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

You might have to enable scripts on some of your favourite sites first, but after a while you won't have to do much anymore. Enabling/disabling scripts is very easy anyway.

---

### Post by lovinglinux on 2009-04-18
> **KIAaze said:**
> P.S: For safe surfing without any unwanted popups, flash ads, etc, use NoScript and eventually flashblock.
[https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

You can also use [AdBlock plus](https://addons.mozilla.org/en-US/firefox/addon/1865) for blocking ads and [Block Site](https://addons.mozilla.org/en-US/firefox/addon/3145) for blocking specific sites.

---

### Post by CatKiller on 2009-04-18
> **KIAaze said:**
> I think you misunderstood something. ^^

I think the OP was actually replying to ddrichardson

> This is a really nice trick CatKiller gave you there. 8)


Hey, thanks. Although I can't claim credit for it. I've been using a hosts file for about a decade now to block ads. I can't remember the Windows location for that file though, since I haven't used Windows for about half that time.

---

### Post by ddrichardson on 2009-04-18
Don't use 127.0.0.1 though, use 0.0.0.0 so it isn't actually trying to resolve anything.

---

### Post by Locke_99GS on 2009-04-18
> **ddrichardson said:**
> You can create an iptables rule to reject that address:```

sudo /sbin/iptables -A OUTPUT -d antimalware-scannerv2.com -j REJECT
```Should do it.
I'd disable all your extensions too, find out what's redirecting.

> **jburrell said:**
> I cut and pasted that command in the terminal and pressed enter.  Is it supposed to notify me that the change took effect in the terminal?

Most commands done in a shell will return nothing on success.

---

