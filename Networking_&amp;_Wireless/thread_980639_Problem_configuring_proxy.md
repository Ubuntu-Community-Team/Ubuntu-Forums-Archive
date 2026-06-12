---
title: "Problem configuring proxy"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by a2lkulkarni on 2008-11-13
Hi,

I have just moved from hardy to ibex and facing problem with proxy configuration. I can access internet through proxy with firefox proxy configuration. 

I can't ping urls/sites from the terminal and my synaptic package manager is also unable to use the proxy settings (though specified in its settings separately).

When I checked the apt.conf file the proxy string do not show the username and password which is seen in http_proxy environment variable. Is this right?

My aim is to get synaptic working as I need to proceed with some important installations. Could you please help?

---

### Post by a2lkulkarni on 2008-11-13
guys any ideas, how I can daignose it?

---

### Post by h4rdwire on 2008-11-13
Firewall entries possible ?

---

### Post by Gumm on 2008-11-14
Hi there,

Let me understand this? You are stuck behind a proxy, and can access the internet if you set up Firefox's proxy settings, but using apt from the console gets blocked?

Have you tried setting the http_proxy environmental variable?

If you have a proxy that requires authentication, then you set it with this comand:

```
export http_proxy=http://username:password@192.168.4.4:3128
```

replace 'username', 'password' and the IP address and port with your own...

to check if it was set, simply type ```
env
```

In Ubuntu proxy can be set in a number of places:
[LIST=1]
[*]as an envirometal variable
[*]inside the application itself (like Firefox provides)
[*]inside Gnome itself
[/LIST]

I seed my proxy settings directly in the gnome proxy tool (gnome-network-preferences) and wrote a little scrip that switches that on/off and sets the env.var according to where I am - either at work (behind a authenticating proxy, or at home with no proxy) This scrip runs directly after log-in, and that's the end of my trouble.

One interesting side note is that apt, run from the command line needs the environment variable http_proxy set. It does not read the gnome proxy settings. Interestingly Synaptic Package Manager also ignores the gnome proxy settings, so they have a application specific proxy settings. These are useful if no environment variable is set, but if any is set then the Synaptic proxy settings should not be filled, and the Proxy Server under Settings -> Preferences -> Network should be left at Direct connection to the internet.

If both the Gnome proxy and env.var http_proxy is set, then Firefox should be set to "Use system proxy settings" here: Firefox->Edit->Preferences->Advanced->Network->Settings

---

### Post by a2lkulkarni on 2008-11-15
Thanks guys! 

I have got synaptic working, somehow. I changed my password, which had a special character '@' in it and it worked. I didn't confirm this, as I had a little time when I got this working. I'll confirm it on Monday and let you know.

If one looks at the http_proxy variable then it seems that there might be parsing issue for proxy url (if password has a '@' character) which comes after password and '@'. 

Cheers,
-Atul

---

### Post by Gumm on 2008-11-15
I also had an '@' in my password at one stage, and dropped it for this very reason.
The '@' simply does not parse well when setting the env var.

Maybe someone knows how to do this, but its not me :)

---

### Post by iAlta on 2008-11-15
Thank you Gumm, you've answered the question I've been asking for a little over a year now.
> **Gumm said:**
> I also had an '@' in my password at one stage, and dropped it for this very reason.
The '@' simply does not parse well when setting the env var.

Maybe someone knows how to do this, but its not me :)
How about if you escape it with a backslash like this: '\@'? Shouldn't that work?

---

### Post by a2lkulkarni on 2008-11-20
No, it doesn't work. It gives following error:

"Resolving \... failed: Name or service not known.
 wget: unable to resolve host address `\'
"

---

