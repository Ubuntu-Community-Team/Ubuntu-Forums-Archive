---
title: "Setting up Proxy problems"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Vustom on 2011-08-02
I'm trying to setup this PC to use a proxy that I have, I'm currently using Ubuntu 10.4 and I'm having some trouble doing so.

I'll run through what I've done so far,
I first created a called Proxy and then edited with gedit and typed this:

> #! /bin/bash

ssh -D 42280 username@host

Also, the host isn't an IP, it's in a domain format.
Once I did that I ran the Proxy file in a Terminal and typed in my password for the Proxy server.

Once I did that I went into the Control Center > Internet and Network > Network Proxy and clicked Manual proxy configuration and in the socks tab I put localhost and as the port I put 42280.

I launched Chromium and the Proxy seems be having some connection issues, and this doesn't happen on Windows; the Proxy works really well on Windows..

The Proxy server is on socks5 as well.

But anyways, in the terminal I'm getting this error:

> channel 12: open failed: connect failed: Connection refused
channel 32: open failed: connect failed: Connection refused
channel 27: open failed: connect failed: Connection refused
channel 30: open failed: connect failed: Connection refused
channel 8: open failed: connect failed: Connection refused
channel 11: open failed: connect failed: Connection refused
channel 6: open failed: connect failed: Connection refused
channel 8: open failed: connect failed: Connection refused

  
And it keeps repeating but with a different channel number, when this does happen the connection to the Proxy server seems to dropout for a moment, and sometimes longer, but like I said, this doesn't happen when I'm on Windows..

Can someone help me fix this?

---

### Post by Vustom on 2011-08-03
Fix: 

Install Proxy Switchy!, set it up with the correct settings, then restart your PC and all should be well. 
This only works for Chrome, which is all I really use a Proxy with on Ubuntu, from what I know there seems to be some problems when using a socks5 proxy with the default system's proxy software, if you have this problem and want to use your socks5 Proxy outside of Chrome you could try using jsocks or proxychains.

---

### Post by Vustom on 2011-08-03
After using the Proxy for awhile with what I thought was a fix it seems as though I was wrong, using Proxy Switchy! did help a little bit seeing as my connection the proxy isn't dropping out as much, but I'm still getting the same error as I was to begin with.

Can anyone help me out?

---

