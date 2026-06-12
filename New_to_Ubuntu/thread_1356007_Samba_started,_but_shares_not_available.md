---
title: "Samba started, but shares not available"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by JoeSolo on 2009-12-15
After each reboot, I have to restart Samba.  I've checked and Samba definitely starts with the OS.  I've followed instructions on other posts and check my init scripts ([http://www.debianhelp.co.uk/initscripts.htm]("http://www.debianhelp.co.uk/initscripts.htm")).

Any pointers?

---

### Post by doas777 on 2009-12-15
did you configure your network via /etc/network/interfaces
or are you using gnome-network-manager?

---

### Post by JoeSolo on 2009-12-15
I haven't fiddled with the network settings other than changing the static IP address on my machine.  I used GSAMBAD to configure the shares and specified the allowed networks, etc. (I used the GUI, so... yes I used gnome-network-manager)

If I restart the Samba daemon, the shares work fine...

---

### Post by doas777 on 2009-12-15
ok, if you use the gui to set your IP, then you will not have a network connection until after you login. in that case, samba will attempt to start at boot, but will not find any network interfaces to bind to (you should find a message to this effect in the dmesg log), so will not come up correctly (though smbd may actually be running, it won't use the network, so...)

try these instructions for configuring your /etc/network/interfaces file, instead of useing the network manager:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

good luck

---

### Post by JoeSolo on 2009-12-15
Worked like a charm!  Thank you.

... not to sound ungrateful, but now the network icon in my "task bar" shows that there's no network connection.  Is there a way to have the network configured as specified in the link and have the gnome-network-manager pick up the connection?

---

### Post by bodhi.zazen on 2009-12-15
You can use networkmanager, simply open network manager and select the "available to all users" box.

---

### Post by doas777 on 2009-12-15
> **bodhi.zazen said:**
> You can use networkmanager, simply open network manager and select the "available to all users" box.
I honestly don't know how that could have escaped me. I've always been under the assumption that that feature did something entirely different. perhaps I'm too used to doing it by hand...


op, if you want to take bodi's advice, you can just "unconfigure" your interfaces file, and configure NM as he recomends. glad it worked, but sorry bout taking you the long way around.

otherwise, if you do want to get rid of the NM icon, just go to system -> preferences -> startup applications (it's called "sessions" in 8.04), and uncheck "gnome network manager"

---

### Post by JoeSolo on 2009-12-16
I reverted the /etc/network/interfaces and tried the "available to all users" option in network manager... didn't work.  I figure maybe something is broken in my installation... when I'm on vacation next week I'll upgrade to 9.10 and try it again.  For now I'm gonna go with the /etc/network/interfaces option.

Thanks all!

---

### Post by bolucpap on 2009-12-16
I think as well as checking the "available to all users" box, you also have to check the "connect automatically" box, but I'm not 100% sure. Wouldn't hurt to try, tho.

---

### Post by doas777 on 2009-12-16
> **bolucpap said:**
> I think as well as checking the "available to all users" box, you also have to check the "connect automatically" box, but I'm not 100% sure. Wouldn't hurt to try, tho.

"Connect automatically" seems to only pertain to wireless connections.

---

