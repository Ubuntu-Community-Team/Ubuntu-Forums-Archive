---
title: "Remote access home desktop from work?"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by c-m on 2007-11-22
In my searching i have found this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_using_VNC)

Does this cover everything I need to be able setup both my Ubuntu box and my windows box to use remote desktop?

I want to be able to access my Ubuntu desktop (at home behind router) from my Vista PC at work (also behind router)

Is this possible? And in a secure enough manner?

---

### Post by el escocés on 2007-11-22
You will also have to do some port mapping in your router.  I will tell you what you needs to be done but not how to do it, if unsure google is your friend!

Apart from the firewall settings in windows you need to:

On your home router map ports (most likely using you NAT configuration) 5900-5904 to the internal IP address of your ubuntu machine.  Configure ubuntu to allow incoming desktop connections and set a password.  If you have a static home IP address perfect, if not you need to install a dns service in ubuntu so that you can connect to the machine even if it has a dynamic IP.

In windows, run VNC viewer and type in the IP address or dynamic address, password and you're in!!

Any probs let us know!

---

### Post by c-m on 2007-11-22
Cool.

By port mapping do you mean forwarding? thats not a problem. I think the link i posted shows how to configure Ubuntu for desktop sonnections.

behind my router my ubuntu box has a static ip, but my ISP uses dynamcIP (though this is almost always the same). The DNS service might throw me, but i'll look it up.

Is this method only as secure as the password i use, or are there other more serious security issues?

---

### Post by el escocés on 2007-11-22
Yep, port forwarding, I think that VNC isn't encrypted but at least you have a password check (although it could be sniffed).

I don't have experience in dns'ing ubuntu, but to point you in the right direction visit [http://www.dyndns.com/](http://www.dyndns.com/)

For a secure connection you could always install cygwin in windows and ssh into your ubuntu...

---

