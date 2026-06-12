---
title: "[SOLVED] Creation of SOCKS Proxy"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by Yuki_Nagato on 2008-09-25
Looking to setup a SOCKS Proxy.  I already have SSH working, and can surf the internet through it with XForwarding.  It is very slow, as it needs to send back the GUI data.

How would I go about getting Firefox to use that server as a SOCKS proxy.  The Networking Settings do not seem to work.  The closest I have gotten is a white screen within Firefox instead of the "refused connection" message.

Many people recommend using a "-D 'port'" flag on the SSH command, but this does not work either.

---

### Post by willca on 2008-09-26
If you try it with this...does it give an error message?

ssh -ND 8888 username@remotehost

Then if this works, do you enter proxy localhost into your socks instead of http in firefox?


I dont know why you want to do it this way but othen than this you can also try to use tor and privoxy.

if thats something you want its simple enough and requires no configuration except for firefox of course.

sudo apt-get install tor 
with firefox, just install add-on foxyproxy

---

### Post by Yuki_Nagato on 2008-09-26
I do not need anonymity here.  I need a secure connection through insecure areas such as Wireless.  I have used XForwarding, but this gets old, and I imagine SOCKS proxy is faster as it does not need to spit back the GUI data.

Perhaps I am asking, "what do I need to do to that SSH server I have to create a secure Proxy connection with Firefox?"  Or do I have to do more on the client side?

I am using a non-standard port (not 22) for my SSH connections.

---

### Post by Yuki_Nagato on 2008-09-30
Solved.

First, never try to use the default Firefox proxy configuration tools with a second proxy extension installed.  I had FoxyProxy installed, and by not using that, I was messing up the configuration.

To route data through a SOCKS proxy.

1. Open a terminal and run the command:

```
ssh -p XXXXX -ND 8888 Username@SOCKS.PROXY
```

The "-p XXXXX" is for freaks like me who play a shell game with their ports.  "XXXXX" is your SSH port.  Otherwise, the terminal needs to stay open, as this is a continueous command.  It is continueous because it is continuously forwarding your dynamic port (-ND 8888) to the SOCKS proxy you have set up.

2. Fire up Firefox, open up the FoxyProxy (or if you have no proxy extensions, the default will do.)  Now have all of your data sent through the port 8888 on your "_localhost_."  Because the port 8888 is already forwarded with the terminal command, that will send the data through the SOCKS proxy.

When you are done, edit your settings again.  Stop routing data through the SOCKS proxy, and turn all those extensions off.  Close Firefox.  Close the terminal.  If you do not remove the proxy settings before shuting down, the next time you start up, firefox may flip out with updates.  Or something.  It was odd.

---

