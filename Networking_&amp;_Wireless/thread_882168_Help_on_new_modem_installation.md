---
title: "Help on new modem installation"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by echamp on 2008-08-06
I've just changed internet provider and the modem they sent me has wireless capabilities. I have two questions:

1- I have no intention on using the wireless capabilities so I'd like to disable them so that I don't have any security issues. How can I do that?

2- Although the Internet connection is working fine the Firestarter software does not start anymore. When trying to start it I get an error message saying that the device "eth0" is not ready. How can I fix this?

I'm using version 8.04, desktop edition.

Can anyone help??

Thanks!!!

---

### Post by xc3ll on 2008-08-06
I'm assuming your modem has a built in gateway. If you run "route", you should see a ip address under gateway. In your case, it'll most likely be 192.168.0.1 or similar. If you type that IP address in your browser, that should bring you to a login page.  Your login will most likely be some variation on username:admin password:admin.  If you can't figure it out, try googling the modem's model number, you should be able to figure it out (if you use comcast, note that they use different default configs).  

Once you're logged in, you should be able to change your wireless preferences.

Not sure what Firestarter is, so I can't help you there, sorry.

---

### Post by pytheas22 on 2008-08-06
> Although the Internet connection is working fine the Firestarter software does not start anymore. When trying to start it I get an error message saying that the device "eth0" is not ready. How can I fix this?


It's possible that the device is no longer named "eth0."  What is the output of:
```

ifconfig
lshw -C Network
```

---

