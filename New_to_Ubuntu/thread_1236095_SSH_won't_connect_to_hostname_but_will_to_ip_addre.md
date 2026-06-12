---
title: "SSH won't connect to hostname but will to ip address (LAN)"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by andnobodyslept on 2009-08-09
I feel like I'm missing something easy; so if it's easy someone will point it out quick, if not I don't feel bad about asking.

I have a home server set up with OpenSSH, my router has statically assigned a local ip address using the same host-name as the server.

When I try to ssh into my server from my local desktop, I can't connect when I use the hostname ie
               ssh main@home-server

but when I use the local ip address it works fine
                ssh [email]main@192.168.x.xxxxxx[/email]xx

I don't feel that it the router, since I had a similar set up before and it worked great.

When I run ssh with verbose output I get 
       ```
ssh -v main@home-server
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to home-server [24.28.193.9] port 22.
```

which seems strange since it seems to be trying to connect to a box not on my network.

If you got any ideas let me know
Thanks in advance

---

### Post by RealPSL on 2009-08-09
You might want to check what the fully qualified name for main really is. Meaning what IP address is that going to resolve to based on what you have defined in the /etc/resolv.conf. It seems like it is not resolving to the IP address that you are expecting it to.

---

### Post by andnobodyslept on 2009-08-09
well I guess I wasn't crazy, everything seemed fine with my two setups, all I needed to do was power cycle my router.

Thanks for the help, even though I didn't need it in the end, I learned something new

---

