---
title: "Putty Connection Manager for Linux?"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by Sepiraph on 2010-04-18
Does anyone know if there is a linux version similar to the Connection Manager for Putty?  I am using Putty in GNS3 and it'd be great if there is something like Connection Manager available for Ubuntu.

---

### Post by kenada on 2010-04-18
For SSH?

You can use the terminal.

Or are you after something specific in putty?

---

### Post by asmoore82 on 2010-04-19
I think you will want to check out the package "sshmenu-gnome"

It installs a Gnome panel applet to launch preconfigured ssh sessions.
You have to log out and back in after installing to "refresh" the available applets,
Then right click the panel and "Add to panel" - search for "ssh" or just look near the bottom of the list.

See screenshot.

---

### Post by Sepiraph on 2010-04-19
I'll check out sshmenu-gnome.

But yes basically I'm looking for the tab-window feature in Connection Manager for Putty (to be used inside GNS3), it's easier to keep track of multiple sessions.

---

### Post by kuthulu on 2010-07-07
if you want a tabbed gui client like putty connection manager then you may want to check gcm (gnome connection manager)
download it from [http://kuthulu.com/gcm](http://kuthulu.com/gcm)

---

### Post by locodog on 2010-07-07
I've cross the idea to connect my mobile phone on my computer via internet. I've downloaded putty client for mobile phone. 
Can someone please explain to me how to setup telnet host on my computer? And what IP address to try connecting? Do I use address that i for example see when go to whatismyip.com? Or something else? I'm newbie to this stuff, so please be as detailed as possible. Thank you!

---

### Post by guerlloy on 2010-09-16
For locodog:

1) Install the openssh package in the host
2) Register to a dynamic dns site (dyndns.org, no-ip.info, etc). There you will get a url to point to.
3) Install and setup the dynamic dns client (provided by the site) in the host.
4) Point your mobile putty to the url the site gave you.

That's it!

---

### Post by Jeffbuntu on 2012-05-30
Has there been any update on this one?  I'm debating pulling the trigger on secureCRT for Linux but the price of $100 is pretty outrageous.

---

### Post by CharlesA on 2012-05-30
I don't know if Putty is available on Linux, but read this:
[http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/](http://nerderati.com/2011/03/simplify-your-life-with-an-ssh-config-file/)

Anyhow, back to sleep you go..

---

