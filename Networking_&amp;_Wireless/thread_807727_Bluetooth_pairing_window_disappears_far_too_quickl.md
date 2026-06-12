---
title: "Bluetooth pairing window disappears far too quickly."
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by Sinkhead on 2008-05-26
Hi, I'm trying to pair my Motorola L6 with my Eee PC so I can use my phone as a modem, but I'm having some problems.

I make my phone 'discoverable' in Bluetooth then run the command
```
hcitool cc <mac address>
```
After a few seconds I can enter another command
```
hcitool auth <mac address>
```

I can't actually take a screenshot because it's too fast (and I have one arm in a sling at the moment) but I can see that it looks similar to this:

[IMG]http://www.belutz.net/blog/wp-content/uploads/2007/05/blutooth-pairing.png[/IMG]

And then if I manage to click it before it disappears I get this:

[IMG]http://www.belutz.net/blog/wp-content/uploads/2007/05/pin-request.png[/IMG]

Both disappear in under a second so I can't do anything with them  :(

Please can somebody help me pair these two devices? Thanks in advance!

---

### Post by spo0ner on 2008-10-27
I have had the same problem with several different bluetooth adapters and I can't believe no one has responded to your post by now.  We can't be the only two experiencing this issue.

---

### Post by lvictor on 2009-04-29
no you're not the only two persons facing this problem

It was running perfectly until I updated to jaunty and now I have the same problem you describe...

I also have problems with sound adapter, vlc...

I came from debian to mandriva 8 years ago because they couldn't seem to make the USB subsystem work properly... It's been 8 great years without a glitch and I had 6 major version upgrades...

I've given ubuntu/debian a chance because I like the community philosophy but I must confess that for two years now, I have never upgraded my ubuntu painlessly...

I 'd use bluetooth to connect to the one and only keyboard of my machine so this recurent problem is quite painful. And I have no clue of what is happening

syslog indicates link_key_request + pin_code_request ... so far so good but no error !

---

