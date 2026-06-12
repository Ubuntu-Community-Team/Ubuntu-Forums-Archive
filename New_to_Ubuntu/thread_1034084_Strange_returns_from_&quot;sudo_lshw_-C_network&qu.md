---
title: "Strange returns from &quot;sudo lshw -C network&quot;"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by Lostin60's on 2009-01-07
I actually have this in another post, but it is an aside to the question in the title line, so I am posting it separately.
I am running Intrepid. In the help manual it says that the command sudo lshw -c network will return information along with the words, CLAIMED, UNCLAIMED,ENABLED, and DISABLED, and it tells you what they mean. Much of the rest of the help information is given depending on which words you have. I have only ever gotten DISABLED, and that was only on my bridge connection. On the connections I needed to know about, there was nothing. This made it a bit difficult to follow the rest. I ended up going to the end of the trouble shooting, and kind of reverse engineering the information. I figured it out(I'm here), but it was the long way around. Is this because the manual needs updating, is it that I am getting bad feedback from the command, or is it common and I am just missing something? Again, any and all help will be appreciated.
[COLOR="White"]a[/COLOR]

---

### Post by Iowan on 2009-01-08
Which help manual? I didn't see anything similar in **man lshw**.

---

### Post by Lostin60's on 2009-01-09
> **Iowan said:**
> Which help manual? I didn't see anything similar in **man lshw**.

It is in the  help manual in the desktop panel. Help>Connect to network>Section 3.1>Wireless troubleshooting
> Open a*Terminal*(Applications>Accessories>Terminal) and type the command
```
sudo lshw -C network
```
> You should see an output, along with the words "CLAIMED, UNCLAIMED, ENABLED, or DISABLED"
1. Claimed-this indicates the driver is loaded, but not functioning, see [COLOR="RoyalBlue"]Section 3.4-Using Windows Wireless Drivers.[/COLOR]
2. Unclaimed-there is no driver loaded, see [COLOR="RoyalBlue"]Section 3.4-Using Windows Wireless Drivers.[/COLOR]
3. Enabled-move on to if there is a driver listed, then  see [COLOR="RoyalBlue"]Section 3.3.3-Check for a connection to the router.[/COLOR]
4. Disabled-see [COLOR="RoyalBlue"]Section 3.3.1-Check that the device is on[/COLOR]
And, as I said, my wireless bridge says "disabled". My other connections show the info, but nothing about claimed, unclaimed, etc. In and of itself, it's no big deal, but I am curious as to why I don't get the output described.
[COLOR="White"]aa[/COLOR]

---

